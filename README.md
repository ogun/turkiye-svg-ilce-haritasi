# Türkiye İlçeleri
Türkiye'nin tüm ilçelerine ait bir SVG haritasının olmaması ve olanların da parayla satılıyor olması nedeniyle bir ilçe haritasını GitHub'a yüklemeye karar verdim. Proje üzerinden bu dosyaya ulaşabilirsiniz.

## Harita
Herhangi bir yanlışı GitHub üzerinden bildirebilir ve düzeltilmesi için katkıda bulunabilirsiniz.

<img src="https://github.com/matasoy/turkiye-svg-ilce-haritasi/blob/master/turkiye.gif">
<img src="https://raw.githubusercontent.com/ogun/turkiye-svg-ilce-haritasi/master/turkiye-ilceler.svg?sanitize=true">

## Kullanılan Kaynaklar

### Wikipedia
User: [Chumwa](https://commons.wikimedia.org/wiki/User:Chumwa), File: [Map of the administrative divisions of Turkey.svg](https://commons.wikimedia.org/wiki/File:Map_of_the_administrative_divisions_of_Turkey.svg)


### Overpass API Örnekleri
[Overpass QL Documentation](https://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL)

Sorgu örneklerini aşağıdaki site üzerinde çalıştırabilirsiniz:
https://overpass-turbo.eu/

#### Ülke
```Overpass QL
[timeout:600][out:json];
area["ISO3166-1"="TR"]->.country;
rel["ISO3166-1"="TR"]["type"="boundary"]["admin_level"="2"];
(
    way(r)["maritime" != "yes"];
    way(area.country)["natural"="coastline"];
);
(._;>;);
out;
```

#### Şehir
```Overpass QL
[timeout:600][out:json];
area["ISO3166-2"~"^TR"]->.country;
rel["ISO3166-2"~"^TR"]["type"="boundary"]["admin_level"="4"];
(
    way(r)["maritime" != "yes"];
    way(area.country)["natural"="coastline"];
);
(._;>;);
out;
```

#### İlçe
```Overpass QL
[timeout:600][out:json];
area["ISO3166-2"~"^TR"]->.country;
rel(area.country)["boundary"="administrative"]["admin_level"="6"];
out;
way(r);
out geom;
```

### GADM
GADM, tüm ülkeler ve alt bölümleri için haritalar ve mekansal veriler sağlar.

https://gadm.org/download_country_v3.html

### Map Shaper
Shapefile, GeoJSON, TopoJSON ve CSV dosyalarını düzenleme aracı. GADM üzerinden indirdiğimiz yüksek ayrıntıya sahip shape dosyasının ayrıntılarını azaltma ve SVG formatına çevirmek için kullanıyoruz.

https://mapshaper.org/

### MDN Web Docs
SVG dosyasıyla ilgili tanımlamaları öğrenmemizi sağlar.

https://developer.mozilla.org/en-US/docs/Web/SVG

### Türkiye Mülki İdare Bölümleri Envanteri
İl ve ilçe isimleri için resmi kaynak.

https://www.e-icisleri.gov.tr/Anasayfa/MulkiIdariBolumleri.aspx

### Güncellemeler
2022 Şubat ayında Türkiye Mülki İdare Bölümleri Envanterinden il, ilçe, köy, belde ve mahalle bilgileri çekilerek haritaya işlenmiştir. İlçeye tıkladığınızda ilçede bulunan tüm mahalle köy ve beldeler tablo şeklinde listelenmektedir. HTML sayfa olarak hazırlanan etkileşimli harita bootstrap, jquery ve datatables scripleri ile birlikte hazırlanmıştır. Mahalle köy veya belde sınırlarının her ilçede var olup olmadığını bilemediğim için haritada ayrı olarak gösterilmemektedir. Bu sınırlar Trabzon için bulup githuba koydum, isteyen bu https://github.com/matasoy/Trabzon-Svg adresten inceleyebilir.

### Nerede Kullanılır
🟩 Ülke içinde yapılacak ve konumların önemli olduğu derlem çalışmalarında 
🟩 Araç takip sistemlerinde
🟩 İstatistiki veriler oluşturmak istendiğinde

Kaynakları paylaştığı için https://github.com/ogun'a teşekkürler.
