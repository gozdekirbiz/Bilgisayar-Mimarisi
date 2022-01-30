**GÖZDE KIRBIZ**
#
# İçindekiler Tablosu

**ÖZET**

**İşlemcilerin Tanıtılması**

Intel i9 işlemciler

AMD Ryzen işlemciler

**Komut Setleri**

Komut setinin özellikleri

Streaming SIMD Extensions Instructions (SSE) Komut Setleri

SSE4.1 4-5

SSE4.2 6

SSE4a 7

Intel Advanced Vector Extensions (AVX2) Komut Seti

**Komut Setlerinin Karşılaştırılması**

**SONUÇ**

**KAYNAKÇA**

# ÖZET

Yüksek seviyeli dillerde yazdığımız programları bilgisayarın algılayabilmesi için 0 ve 1&#39;ler ile binary halde ifade edilmesi gerekir. Her bilgisayar yüksek dilde yazılmış karmaşık kodları, komut seti adı verilen sınırlı sayıda ve basit işlemlerden oluşan birtakım komutlar ile gerçekleştirir. Intel i9 işlemcilerinde Intel® SSE4.1, Intel® SSE4.2, Intel® AVX2 komut setlerini kullanmaktadır. AMD Ryzen işlemcilerinde SSE (SSE4a) ve diğer setlerden faydalanmaktadır. SSE komut seti ile AVX2 komut setinin amaçları hemen hemen aynıdır, AVX2 SSE komutlarının 256 bitlik geliştirilmiş versiyonudur. Genel olarak floating point verilerin küsüratlı kısımlarının daha fazla bitle temsil edilmesi üzerine doğruluk oranının artırılması hedeflenmiştir. String ve text komutları ile stringlerin 16 bitlik parçalara bölünmesi ve karşılaştırılması işlemleri yapılmaktadır. Komutlar günümüz şartlarına uyacak şekilde, video editi, oyun, bilimsel hesaplamalar ve yapay zekaya optimize olacak şekilde geliştirilmiştir. İki işlemcinin komut setleri karşılaştırılacak olursa, performansı asıl etkileyen CPU&#39;nun donanımsal özellikleri ve uygulamaların optimizasyonu olduğu göz önünde bulundurularak şunu söylemek mümkündür: Intel işlemcilere optimize edilmiş bir program AMD işlemcilerde daha yavaş çalışacağı veya AMD işlemcilere optimize edilmiş bir uygulamanın Intel işlemcide daha yavaş çalışacağı söylenebilir.

Bu çalışma üç ana başlıktan meydana gelmektedir. İlk kısımda i9 ve Ryzen işlemciler tanıtılmış, kullandıkları teknolojiler ve donanımsal özellikleri hakkında bilgi verilmiştir. İkinci kısımda komut setleri tanıtılmış ve bazı fonksiyonları diyagram ve tablolarla gösterilmiştir. Üçüncü kısımda karşılaştırma hakkında yorumlar yapılmıştır.

# **Intel i9 İşlemcilerin Genel Özellikleri**

i9 işlemciler, Intel&#39;in 2018 yılının 2.çeyreğinde i9-8950HK modeli ile piyasaya sürdüğü Intel Core İşlemci ailesinin, X serisinden sonra gelen en üst segmentteki işlemcilerdir. Gelişen teknoloji ile beraber, işlemci üreticilerin her yeni nesilde odaklandıkları konular da farklılıklar gösterebilmektedir. Son senelerde gelişmekte olan yapay zeka, 4K-8K video editleri ve bilgisayar oyunlarının yüksek gereksinimlerinin bir sonucu olarak i9 işlemciler de bu alanlarda yüksek perfromans vermek amacıyla tasarlanmışlardır. Oyun alanında daha yumuşak geçişli bir oyun deneyimi, yüksek FPS gibi özellikler işlemcinin &quot;overclocking&quot; özelliğinin kullanarak performansını en üst seviyede göstermesi ile sağlanmıştır. Ayrıca aynı anda oyun oynayıp yayın yapıp ve yayını kaydetmek, i9 işlemcilerde daha stabil hale getirilmiştir.

i9 işlemcilerde kullanılan Thunderbolt​™ teknolojisi ile önceden birden fazla farklı giriş bulunduran bilgisayarlar, artık tek bir genel giriş ile tüm USB girişlerine bağlanabilmektedir. Bu sayede bağlantı hızı ve güvenliği artırılmıştır. Optane teknolojisi kullanılan i9 işlemcilerde, hafıza ve bellek hiyerarşisinin yeniden düzenlenmesi ile bottleneck sorunları indirgenmiş, veri gecikmesi süresi azaltılmıştır. Ayrıca, bloklar birlikte çalışarak paralel olmayan çalışma fırsatı sunulmuştur. Intel Thermal Velocity Boost (Intel TVB) ile 50 derecelik bir sıcaklıkta işlemci en yüksek çekirdek frekansı ile çalışabilir hale getirilmiştir. Geliştirilen bu yeni teknoloji ile Turbo Boost teknolojisine göre daha fazla verim elde edilmiş olmuştur.[3,4,5,7]

i9 işlemcilerin teknik özellikleri her modeline göre değişiyor olsa da belli aralıklar belirtmek gerekirse;

- 12 MB ile 30 MB arası cache bellek,
- 4.80 GHz ile 5.20 GHz arasında maksimum turbo frekansı
- 6 ile 16 arasında çekirdek sayısı
- Maksimum 64 GB ile 128 GB arası belleklerle uyumlu çalışabilme
- Intel® SSE4.1, Intel® SSE4.2, Intel® AVX2 komut setleri kullanılmaktadır.
![1](https://user-images.githubusercontent.com/77017691/151715307-661c3a27-874e-4d63-bd79-7f48f7689025.png)
 _**Figür 1.i9-9900K board tasarımı [8]**_

# **AMD Ryzen İşlemcilerin Genel Özellikleri**

AMD, Ryzen serisinin ilk işlemcisini Mart 2017&#39;de piyasaya sunmuştur. Ryzen serisinin ana hedefi sunucular, masaüstü bilgisayarlar, iş yerleridir. AMD, grafik alanındaki başarısını oyun alanında da göstermeyi hedeflemiş ve oyun performansını geliştirecek uygun fiyatlı işlemcilerini satışa sunmuştur. Zen mimarisinden faydalanan bu işlemciler, Simultaneous Multi-Threading adı verilen AMD&#39;ye ait teknolojiyi kullanmaktadır. Zen mimarisi gelişen teknolojiye ayak uydurarak gelişme göstermiştir ve şu an kullanılan Zen mimarisi ile yüksek bant genişliğine sahip, bir clock&#39;ta daha çok komut alabilen, gecikme seviyesi indirgenmiş Ryzen işlemciler üretilmektedir.

![2](https://user-images.githubusercontent.com/77017691/151715311-80f112fa-0f5f-4598-81e1-c286e17d52e4.jpg)

**Figür2. AMD Ryzen 7 1800X board tasarımı [AMD]**

AMD Ryzen işlemcilerin genel özelliklerine bakılacak olursa;

- 12 MB ile 64 MB arası cache,
- 3.9 GHz ile 4.7 GHz maksimum frekans,
- 4 ile 16 arasında çekirdek sayısı,
- SSE4a komut seti

kullanıldığı görülür.[1]

# **Komut Setlerinin Özellikleri**

Yüksek seviyeli dillerde yazdığımız programları bilgisayarın algılayabilmesi için 0 ve 1&#39;ler ile binary halde ifade edilmesi gerekir. Bu işlemi yapmak çok zor olduğundan Assembly dilinde makine diline yakın seviyede bir dil oluşturulmuştur. Her bilgisayar yüksek dilde yazılmış karmaşık kodları, komut seti adı verilen sınırlı sayıda ve basit işlemlerden oluşan birtakım komutlar ile gerçekleştirir. Mimariden mimariye komut setlerindeki komut sayısı, adres operandları, opcode genişliği gibi özellikler değişiklik göstermektedir. Intel i9 işlemcilerde Intel® SSE4.1, Intel® SSE4.2, Intel® AVX2 komut setleri kullanılırken, AMD Ryzen işlemcilerde SSE1,SSE2,SSE3,SSE4a, • x87 Floating-Point Instructions, Multimedia Extension Instructions gibi setler kullanılmaktadır.

**Streaming SIMD Extensions Instructions (SSE) Komut Setleri**

Bu komut kümesinde lokal bir kaydedicide tutulan veriler üzerinde load, store ve manipülatif işlemler yapabilen komutlar bulunmaktadır. SSE komutları integer ve floating-point komutlarını vektörel ve skaler bir şekilde gerçekleştirebilmektedir. Vektör komutlar bağımsız ve aynı anda birden fazla data üzerinde bir adet işlem yapabildiklerinden dolayı, bu komutlara singleinstruction, multiple-data (SIMD) komutları da denir. Vektör komutlar ile medya ve bilimsel işlemler yüksek performans ile gerçekleştirilebilmektedir.

- **SSE4.1**

SSE komutlarını Intel ve AMD, birkaç yıl önce aldıkları karar ile gelişmeler söz konusu olduğunda birbirleri ile paylaşacakları bir ortamda geliştirmeye başlamışlardır. Intel&#39;in geliştirdiği SSE4 (SSE4.1 ve SSE4.2) 3D işlemler, medya işlenmesi ve görsel oluşturulması gibi alanlarda iyileştirmeler yapmak için geliştirilmiştir. SSE4.1 komutları 128 bit integer ve floating point verileri ile çalışabilmektedir. 64 biti desteklememektedir.SSE4.1 ile double precision ve single precision floating point verilerin nokta çarpımı yapılabilmektedir. Ayrıca 16x2 şeklinde çift wordden oluşan DWordlerin çarpımı özelliği de eklenmiştir. Böylece 32 bit x 32 bit çarpımı yapılabilmektedir. Float-point değerlerin yuvarlanması ile alakalı SSE4.1 ile 4 farklı komut eklenmiştir (ROUNDPS, ROUNDPD, ROUNDSS, ROUNDSD).

Bu komutlar, önceden kullanılan ceil(), floor(), trunc(), rint(), nearbyint() gibi fonksiyonları engellemektedir. Çünkü fonksiyonlar ile yeni komutların çalışma şekli farklıdır. SSE4.1 ile Horizontal Search adı verilen bir arama komutu da eklenmiştir. Integer değerlerinin daha geniş integer tipine dönüştürülebilmesi adına 12 adet yeni komut eklenmiştir. Kaynak operand XMM Register&#39;ı, hedef operand ise bellek veya register olabilmektedir. [6]

Aşağıda bahsedilen bazı komutların Intel tarafından hazırlanmış tabloları gösterilmektedir:

![3](https://user-images.githubusercontent.com/77017691/151715312-31c67555-23c9-406e-b2d1-b1ffdccf045a.png)
![4](https://user-images.githubusercontent.com/77017691/151715313-2dceecfe-7c06-4583-8def-81476743aed4.png)

_**Figür 3-4. SSE4.1 fonksiyonları (Dönüşümler ve Çarpımlar) [6]**_

- **SSE4.2**

SSE4.2 ile string ve text üzerine komutlar geliştirilmiştir. String ve text işlemlerine yönelik, string karşılaştırmaları, 16 bitlik string parçalarının düzenlenmesi, çift yönlü indexleme gibi komutlar bulunmaktadır. Yedi komuttan beş tanesinin kaynak operandı XMM Registerları, hedef operandları bellek veya registerdır. Ayrıca, akümülatöre yönelik birtakım komutlar da bulunmaktadır. SSE4.1 komut setinde de olduğu gibi 128 bit desteklenmekte fakat 64 bit SIMD komutları desteklenmemektedir. [6]

- **SSE4a**

EXTRQ ile 64 bit içinden belirtilen bitler çıkarılır, çıkarılan bitler XMM registerındaki quadword&#39;lerin en az anlamlı bit kısmına kaydedilir.

SSE4a, AMD&#39;nin geliştirmiş olduğu bir komut setidir. SSE4&#39;e ek olarak EXTRQ, INSERTQ, MOVNTSS ve MOVNTSD komutları eklenmiştir. [1]

 ![5](https://user-images.githubusercontent.com/77017691/151715314-cbcfd4cf-2e07-4540-82ef-3e797e7e346e.png)

_**Figür 5. AMD SSE4a EXTRQ diyagramı [1]**_


INSERTQ kaynağın alt 64 bitini, hedefin 64 bitine ekler. Hedefin alt 64 bitindeki diğer bitler değiştirilmez. Hedefin üst 64 biti tanımsızdır.

 ![6](https://user-images.githubusercontent.com/77017691/151715304-cf7862b7-7808-4962-b581-77d54e8d1a0e.png)

_**Figür 6. AMD SSE4a INSERTQ diyagramı [1]**_

**Intel Advanced Vector Extensions (AVX2) Komut Seti**

SSE komutlarının gelişmiş bir versiyonu olan AVX2, bilimsel ve mühendislik alanlardaki hesaplamalar, oyun, fizik, kriptografi ve diğer alanlar için vektörel floating point performansını artırmayı hedeflemektedir. [2]

 ![7](https://user-images.githubusercontent.com/77017691/151715306-13c0cbbf-6ddf-4f83-a711-08f8985bdbf5.png)

_**Figür 7. AVX2 256 bit yapının diyagramı[2]**_

Paralel threading, vektör uzunluğunda data gibi tekniklerden yararlanır. Segmentleri efektif bir şekilde bloklara ayırır ve floating point verilerin küsüratlı kısmında tutulabilecek bit sayısını artırarak daha doğru hesaplamalar yapmayı sağlar. Çok işlemcili bilgisayarlarda performansı artırır. SIMD registerları ile beraber çalışır ve 256 biti destekler. Daha esnek ve kolay bir dil kullanımı için syntaxta da değişiklikler yapılmıştır.

**Intel i9 İşlemcilerin ve AMD Ryzen İşlemcilerin Komut Setlerinin Karşılaştırılması**

Intel ve AMD, önceden yaptıkları anlaşma ile komut setlerine beraber katkı vereceklerini belirtmişlerdir. Bu sebeple iki firmanın da benzer komut setlerini kullandığı görülmektedir. Her ne kadar komutları beraber geliştireceklerine dair anlaşma yapmış olsalar da iki firma arasında komut setleri geliştirmede rekabet ortaya çıkmıştır. Bunun bir sonucu olarak, firmalar var olan komut setlerini kendilerine uyarlayacak şekilde birtakım eklemeler yapmıştır. Intel ayrıca, AVX2&#39;yi de kullanmaktadır. Benzer komutların kullanılıyor olması aynı performansı verecekleri anlamına gelmez, sadece aynı isimdeki fonksiyonlarla registerlar üzerinde aynı etkiyi yarattıkları anlamına gelir. Örneğin AVX2&#39;nin geliştiricisi Intel olduğu için, son çıkan Intel işlemcilerde AVX2 komutları 1 clock pulse ile yapılırken, AMD&#39;de 2 clock pulse ile yapılır. Buna rağmen performansı etkileyen asıl faktörler arasında optimizasyon, CPU&#39;nun donanımsal özellikleri ve programların CPU ile aynı teknikleri kullanarak çalışıyor olmasıdır. (Multithreading- gibi) Örneğin, Intel işlemcilere optimize edilmiş bir program AMD işlemcilerde daha yavaş çalışacaktır. Tam tersi durum da geçerlidir. Bunun sebebi dolaylı yoldan komut setlerinde görülen farklılıklar olsa da, asıl nedeni optimizasyondur.

# **SONUÇ**

Intel i9 işlemcilerinde Intel® SSE4.1, Intel® SSE4.2, Intel® AVX2 komut setlerini kullanmaktadır. AMD Ryzen işlemcilerinde SSE (SSE4a) ve diğer setlerden faydalanmaktadır. SSE komut seti ile AVX2 komut setinin amaçları hemen hemen aynıdır, AVX2 SSE komutlarının 256 bitlik geliştirilmiş versiyonudur. Komut setlerinin farkı ve performanstaki etkisi karşılaştırılmak istendiğinde bu çok sağlıklı bir karşılaştırma olmaz. Performansı asıl etkileyen CPU&#39;nun donanımsal özellikleri ve uygulamaların optimizasyonudur. Buna göre Intel işlemcilere optimize edilmiş bir program AMD işlemcilerde daha yavaş çalışacağı veya AMD işlemcilere optimize edilmiş bir uygulamanın Intel işlemcide daha yavaş çalışacağı söylenebilir.

# **KAYNAKÇA**

1. AMD64 Architecture Programmer&#39;s Manual Volume 4: 128-Bit and 256-Bit Media Instructions, Mayıs 2013.
2. Intel(R) Advanced Vector Extensions Programming Reference, Haziran 2011.
3. Intel i9 işlemciler web sayfası,

https://www.intel.com/content/www/us/en/products/details/processors/core/i9.html

1. Intel Thunderbolt Teknolojisi web sayfası,

https://www.intel.com/content/www/us/en/products/docs/io/thunderbolt/thunderbolt-technology-general.html

1. Intel® Optane™ Technology web sayfası,

https://www.intel.com/content/www/us/en/architecture-and-technology/intel-optane-technology.html

1. Intel® SSE4 Programming Reference, Mayıs 2007.
2. 12th Generation Intel® Core™ Processors, Kasım 2021.
3. https://en.wikichip.org/wiki/intel/core\_i9/i9-9900k
