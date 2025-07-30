# 🧠 Yapay Zeka Destekli Adres Çözümleme Hackathon Rehberi

Bu rehber, TEKNOFEST 2025 kapsamında Hepsiburada işbirliğiyle düzenlenen "Adres Eşleştirme / Çözümleme" temalı hackathon için referans alınabilecek açık kaynak projeleri içermektedir. Adres verileriyle çalışırken kullanabileceğiniz NLP, veri madenciliği ve coğrafi bilgi sistemleri tabanlı araçlar aşağıda sıralanmıştır.

---

## 📦 1. Adres Normalizasyonu ve NLP Tabanlı Çözümler

* 🔗 [libpostal](https://github.com/openvenues/libpostal): Adres parsing ve normalizasyonu için en güçlü açık kaynak araçlardan biri.
* 🔗 [pypostal](https://github.com/openvenues/pypostal): libpostal'ın Python wrapper'ı.
* 🔗 [dedupe](https://github.com/dedupeio/dedupe): ML tabanlı adres eşleştirme ve veri birleştirme aracı.

---

## 🧮 2. Adres Benzerlik Skorlaması ve Veri Temizleme

* 🔗 [fuzzywuzzy](https://github.com/seatgeek/fuzzywuzzy): Metin benzerliği hesaplamak için.
* 🔗 [rapidfuzz](https://github.com/maxbachmann/RapidFuzz): fuzzywuzzy'nin hızlı versiyonu.
* 🔗 [recordlinkage](https://github.com/J535D165/recordlinkage): Veri eşleştirme, duplicate tespiti için kullanışlı.

---

## 🗺️ 3. Coğrafi Bilgi Sistemleri (GIS) ile Destekli Çözümler

* 🔗 [geopy](https://github.com/geopy/geopy): Adresleri koordinatlara çevirmek için.
* 🔗 [OpenStreetMap Nominatim](https://github.com/osm-search/Nominatim): Açık kaynak geocoding servisi.
* 🔗 [pelias](https://github.com/pelias/pelias): Büyük ölçekli açık kaynak arama ve geocoding motoru.

---

## 🤖 4. Hazır Proje ve Uygulamalar

* 🔗 [AddressNet](https://github.com/ukgovdatascience/address-net): Derin öğrenme tabanlı adres çözümleyici.
* 🔗 [usaddress](https://github.com/datamade/usaddress): ABD adresleri için, ancak mantığı Türkiye’ye uyarlanabilir.
* 🔗 [data-cleaning](https://github.com/learnDataSci/data-cleaning): Veri temizleme ve adres işlemeye dair örnekler içeriyor.

---

## 🔧 Yapılabilecek Kombinasyonlar (Pipeline Önerileri)

1. **Libpostal + Rapidfuzz** kombinasyonu ile adres normalizasyonu + benzerlik skoru hesaplama.
2. **Geopy + Nominatim** ile konumsal doğrulama.
3. **Dedupe** ile adres kayıtlarındaki çoğaltmaları (duplicate) temizleme.

---

## 🚀 Öneri

Bu repoları harmanlayarak **Türkiye adreslerine özel çalışan bir yapay zeka destekli adres çözümleme sistemi** oluşturabilirsin.

Dilersen temel bir GitHub iskeleti, örnek veri ve çalışır bir pipeline hazırlayabilirim. Kullanmak istediğin teknolojileri (örneğin libpostal mı, dedupe mi?) belirtmen yeterli. 🙌
