# Adres Normalizasyonu ve NLP Tabanlı Çözümler

Bu proje, Türkiye'deki adres verilerinin normalizasyonu, ayrıştırılması ve eşleştirilmesi amacıyla doğal dil işleme (NLP) tekniklerini ve çeşitli açık kaynak kütüphaneleri kullanmaktadır. Proje, özellikle e-ticaret, lojistik ve kamu kurumları için büyük veriyle uğraşan uygulamalarda veri kalitesini artırmak amacı taşır.

## Kullanılan Teknolojiler ve Kütüphaneler

### 1. [libpostal](https://github.com/openvenues/libpostal)
- **Açıklama:** 
  - Adres parsing (ayrıştırma) ve normalizasyonu için geliştirilmiş bir C kütüphanesidir.
  - Çok dilli destek sunar ve Türkiye için de kullanılabilir.
- **Kullanım Alanları:**
  - Adres bileşenlerini (il, ilçe, mahalle, sokak, vb.) otomatik olarak ayırır.
  - Farklı yazım şekillerine sahip adresleri normalize ederek standartlaştırır.
- **Kurulum:**
```bash
# libpostal kurulumu
sudo apt-get install libpostal
cd libpostal
./bootstrap.sh
./configure
make
sudo make install
sudo ldconfig
```

---

### 2. [pypostal](https://github.com/openvenues/pypostal)
- **Açıklama:**
  - libpostal’ın Python wrapper’ıdır.
  - Python projelerinde libpostal’ın gücünü kullanmanızı sağlar.
- **Kullanım:**
```bash
pip install postal
```

```python
from postal.parser import parse_address

adres = "Mustafa Kemal Mah. 2134 Cad. No:12 Daire:5 Çankaya Ankara"
sonuc = parse_address(adres)
print(sonuc)
# [('mustafa kemal', 'road'), ('2134', 'house_number'), ('12', 'house'), ('5', 'unit'), ('çankaya', 'suburb'), ('ankara', 'city')]
```

---

### 3. [dedupe](https://github.com/dedupeio/dedupe)
- **Açıklama:**
  - Makine öğrenmesi tabanlı kayıt eşleştirme ve yinelenen kayıtları tespit etme kütüphanesi.
  - Özellikle adres, kişi, şirket adı gibi benzer kayıtların eşleştirilmesi için kullanılır.
- **Kullanım Senaryosu:**
  - Aynı kişiye/firmaya ait ama farklı yazılmış adres kayıtlarını gruplayarak birleştirir.

- **Kurulum:**
```bash
pip install dedupe
```

- **Örnek Kullanım:**
```python
import dedupe

data = {
    '1': {'adres': 'Mustafa Kemal Mah. 2134 Cd. No:12 Çankaya'},
    '2': {'adres': 'M. Kemal Mahallesi 2134 Caddesi No 12, Ankara'},
}

fields = [
    {'field': 'adres', 'type': 'String'},
]

deduper = dedupe.Dedupe(fields)
deduper.sample(data, 10)

# Manüel eğitim gerekebilir (etiketleme)
# deduper.markPairs({"match": [...], "distinct": [...]})

deduper.train()

clustered_dupes = deduper.match(data, 0.5)
print(clustered_dupes)
```

---

## Proje Kullanım Alanları
- **E-ticaret:** Yanlış girilen adreslerin doğru kişiye teslimi.
- **Kargo/lojistik:** Farklı yazılmış aynı adreslerin eşleştirilmesi.
- **Kamu:** Vatandaş adres kayıtlarının standardize edilmesi.

## Geliştirme Notları
- Türkiye’ye özgü adres formatları test edilerek optimize edilmelidir.
- Dedupe eğitimi için örnek veri seti hazırlamak önemlidir.
- Performans için büyük veri kümelerinde paralel işlemeye ihtiyaç duyulabilir.

## Katkı
Pull request’ler ve öneriler memnuniyetle karşılanır. Lütfen katkıda bulunmadan önce `CONTRIBUTING.md` dosyasını okuyunuz.

## Lisans
MIT Lisansı ile lisanslanmıştır.