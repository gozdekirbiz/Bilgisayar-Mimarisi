# MULTIPROCESSORS

## **İçindekiler Tablosu**

**ÖZET**

**Çok İşlemcili Sistemler**

Çok İşlemcili Sistemlerin Tarihi 
Çok İşlemcili Sistemlerin Sınıflandırılması
Çok İşlemcili Sistemlerde Çıkan Sorunlar

**SONUÇ**

**KAYNAKÇA**

# **ÖZET**

Bilgisayar geliştirilmeye başlandığından bu yana, bilgisayar mimarisinde odaklanılan en önemli faktör performans olmuştur. Bilgisayarda performans artışı için birtakım yöntemler geliştirilmiştir. Çok işlemcili sistemler de performans artışını hedefleyerek tasarlanmıştır. Bir işin birden çok işlemci ile yapılması hedeflenmiştir. Bilgisayar mimarilerinin ve çok işlemcili sistemlerin sınıflandırılması için birden fazla taksonomi oluşturulmuştur. Örneğin Flynn&#39;nin 1966&#39;da oluşturduğu taksonomi ve 1983&#39;te Giloi&#39;nin yazılım ve işletim sistemlerine göre yaptığı gruplama söylenebilir. Senkronizasyon başta olmak üzere, çok işlemcili sistemler sağladıkları avantajların yanında bazı sorunları da beraberinde getirir.

Bu araştırmanın ilk kısmında çok işlemcili sistemlerin sınıflandırılması, ikinci kısmında ise ortaya çıkan sorunların anlatılması ve varsa uygulanan çözüm yöntemleri anlatılacaktır.

# **Çok İşlemcili Sistemlerin Tarihsel Gelişimi ve Sınıflandırılması**

Bilgisayar geliştirilmeye başlandığından bu yana, bilgisayar mimarisinde odaklanılan en önemli faktör performans olmuştur. Bilgisayarda performans artışı için birtakım yöntemler geliştirilmiştir. Bunlardan bazıları paralel çalışma, pipelining, superscalar işlemciler gibi yöntemlerdir. Aynı zamanda yazılımsal alanda da paralellik sağlanmaya çalışılmıştır. Örneğin bir program proseslere ve threadlere ayrılarak aynı anda birden fazla iş yapılması hedeflenmiştir. [1,3]

Çok işlemcili sistemler de performans artışını hedefleyerek tasarlanmıştır. Bir işin birden çok işlemci ile yapılması hedeflenmiştir. Bunun sebebi şundan kaynaklanmaktadır: Maksimum hızlanma, görevin tek bir iş parçacığında ilerlemesi gereken zamanın kesrinin tersidir. Böylece, bir görevin zamanın %1&#39;inde seri olarak devam etmesi gerekiyorsa, sonucu 100 kat daha hızlı üretmek için en fazla 100 işlemci kullanılabilir. eğer yararlı görevlerin seri olarak yürütüldüğü zaman dilimi büyükse, çok işlemciler çok az performans kazancı sunacaktır. Bu argümanı Amdalh öne sürmüştür.[3]


 Bilgisayar mimarilerinin ve çok işlemcili sistemlerin sınıflandırılması için birden fazla taksonomi oluşturulmuştur. Bunlardan ilki Flynn&#39;nin 1966&#39;da oluşturduğu taksonomidir. Bu taksonomiye göre sistemler şu şekilde ayrıştırılmıştır:

![1](https://user-images.githubusercontent.com/77017691/151716086-d537459a-c3f8-4262-ba82-8e2da19ddca2.png)

**Figür 1. Flynn Taksonomisi [2]**

Flynn taksonomisine göre seri çalışan sistemler SISD sistemlerdir. Tek bir processor ile çalışırlar. Tek komut ve tek veri ile çalışırlar.

Paralel sistemler ise üçe ayrılır: SIMD, MISD ve MIMD.

**SIMD:** Tek komut ile çoklu veri işlenir. Kontrol birimi, işlem birimi ve bellek modüllerinden oluşur. Her işlem biriminin kendine ait bellek modülü vardır. Bu sayede o anda yürütülen komut farklı veriler üzerinde paralel işlem yapar. Örneğin vektör ve dizi işlemcileri bu mantık ile çalışır.[1,5]

**MISD:** Çok komut ile tek verinin işlenmesidir. Pazarda bu işlemciler üretilmez ve tercih edilmez. Fakat test için aynı veriler üzerinde aynı sonuçların üretilmesi bekleniyorsa o amaçla kullanılabilmektedir. [1,5]

**Paylaşılmış bellekli:** Sıkı bağlı (tightly coupled) adı da verilir. Kontrol birimi, işlem birimi, komut ve veri steamlerinden oluşur. İşlemciler ortak bir belleği paylaşırlar ve bu bellek üzerinden veri iletişimi sağlanır. İşlemcilerde yerel bellek de bulunabilir. üzerinden veri iletişimi sağlanır. İşlemcilerde yerel bellek de bulunabilir. [5,6]

**MIMD:** Çok komut ile çok veri işlenir. İkiye ayrılır: Paylaşılan bellekli ve dağıtılmış bellekli.

 ![2](https://user-images.githubusercontent.com/77017691/151716090-5f9ff908-cfe2-4976-bb51-0d6096bb6051.png)

_**Figür 2. Paylaşılmış Bellek Gösterim[1]**_

Paylaşılmış bellekli işlemciler ikiye ayrılır : Simetrik Çok İşlemcili (SMP) veya Bir Örnek Bellek Erişimli(UMA) ve Farklı Bellek Erişimli (NUMA) Sistemler.


Tek bir ortak adres uzayı ve tek bir işletim sistemi ile çalışır. Aynı özelliklere sahip iki veya daha fazla işlemci ile oluşturulur. Tüm işlemciler aynı işlevleri yerine getirir ise simetrik olur. . İşlemciler aynı belleği paylaştığından bellek erişim süresi hangi adrese erişildiği fark etmeksizin tüm işlemciler için hemen hemen aynıdır. Sistemdeki elemanlar ortak bir bus üzerinden veya crossbar switch ile bağlanır.

# _**Simetrik Çok İşlemcili(SMP)/ Bir Örnek Bellek Erişimli(UMA) Sistemlerin Özellikleri**_

![3](https://user-images.githubusercontent.com/77017691/151716092-778f0d28-3417-497f-b6e6-2b2ccc4f7fc3.png)

_**Figür 3. SMP Gösterimi [1]**_

Zaman paylaşımı yapmak için yol hakemliği gerekebilir. Basit, yeni işlemci eklemek kolay ve güvenilirdir. Bir elemanın arızalanması tüm sistemin devre dışı kalmasına sebep olmaz. Fakat performans açısından dezavantajlıdır. Bus sistemi sistemin hızını sınırlar. Sistemde bulunabilecek merkezi işlem birimi de sınırlıdır.


SMP sistemlerindeki bazı eksikleri gidermek amacıyla tasarlanmıştır. SMP&#39;nin avantajlarının korunarak gerçekleştirilmiştir. Tek adres alanı ve tek işletim sistemi ile çalışabilir. Paylaşılan bellek, fiziksel olarak Merkezi İşlem Birimlerine dağıtılır. Bir MİB, kendi bellek modülüne diğer modüllerden daha hızlı erişebilir. Uygun bir düzenleme ile her birimin öncelikle kendi belleğine erişmesi sağlanırsa performans artar.[3,4]

# _**Farklı Bellek Erişimli (NUMA) Sistemlerin Özellikleri**_

**Dağıtılmış bellekli:** Gevşek bağlı (loosely coupled) adı da verilir. Paylaşımlı belleklideki gibi kontrol birimleri,işlem birimleri,komut ve veri steamlerinden oluşur. Paylaşımlıdan farkı ise işlemciler bağımsızdır ve bir arabağlantı ağı ile bağlanır ve bir cluster oluştururlar. Bilgisayar arasındaki iletişim sabit bağlantılarla veya bilgisayar ağları ile sağlanır.

  ![4](https://user-images.githubusercontent.com/77017691/151716096-4ff479e2-dd6f-4a43-bd57-213f9d026bf8.png)
 _**Figür 4. NUMA Gösterimi[1]**_
 
Dağıtılmış bellekli sistemlerde, her bir işlemci kendi fiziksel adres alanına sahiptir. İşlemciler mesaj aktarımı ile haberleşir. Mesajlaşma yöntemlerinden en yaygın olanı clustering metodudur. Kümelerin boyutu on binleri buldukça bulut sistemlerinde kullanılabilir. Dağıtık sistemlere kümelere yeni sistem eklemek suretiyle yeni işlemci eklemek mümkündür. Kümedeki her bilgisayar bağımsız olduğundan arıza durumlarında diğer bilgisayarlar etkilenmez. Ayrıca maliyeti düşürür.
 ![5](https://user-images.githubusercontent.com/77017691/151716099-1747db1d-1658-4b6d-9978-aa6736c6f3b3.png)
 _**Figür 5. Dağıtılmış Bellekli Sistem Gösterimi[1]**_

 ![6](https://user-images.githubusercontent.com/77017691/151716101-840bfe41-1076-41ef-9ed9-eb6dfa76d260.png)
_**Figür 6. Dağıtılmış Bellekli Sistem Gösterimi[1]**_

Baer ise 1973&#39;de paralel sistemleri şu şekilde ayırmıştır:

Pipelinelanmış: Senkronize geçici paralelizm kullanılır. Fonksiyonel özelleşme vardır.

Array Processor: Senkron uzaysal (spatial) paralelizm kullanılır. Fonksiyonel kimlik vardır.

Homojen olmayan: Zaman ve yer için asenkron paralelizm ve fonksiyonel özelleşme vardır.

Homojen Çok İşlemcili Sistemler: Zaman ve yer için asenkron paralelizm kullanılır. Fonksiyonel kimlik vardır. [3]

Bu taksonomi sistemleri günümüzdeki geçerli sistemleri sınıflamada yetersiz kalmaktadır. Bu sebeple 1983&#39;te Giloi&#39;nin yazılım ve işletim sistemlerine göre yaptığı gruplama ile daha başarılı sonuçlar alınmıştır. Giloi&#39;nin taksonomosi şu şekildedir:

Bellek mimarisi: Paylaşımlı veya ayrı

Kaynak Tahsis Sistemi: Ortak veya ayrı

Senkronizasyon önceliği: Yüksek hız, atomik veya düşük hız

Karşılıklı güven: İsteklerin izinlerinin alınması

1984&#39;te Clausing&#39;in incelemeleri üzerine çok işlemcili bir bilgisayarın şunlardan sonra senkronize olması gerekir:

- bir iş veya program
- bir görev veya prosedür
- bir komut
- parçalı bir sonuç

Senkronizasyon başta olmak üzere, çok işlemcili sistemler sağladıkları avantajların yanında bazı sorunları da beraberinde getirir. Bu sorunlar kategorize edilecek olursa,

**Prosesör Mimarisi:**

Mimaride kullanılan işlemci sayısı arttıkça gereken bellek ve fiziksel adres alanı da artmalıdır. Her bir işlemcinin istenen dataya yalnızca bir birim zaman içinde ulaşması istenmektedir. Bunu sağlamak için ekstra alana ihtiyaç duyulur. Aynı zamanda değişkenlerin senkronize edilmesi için yazılım aşamasında gerekli düzenlemelerin yapılması gerekmektedir. Bu durum kodların karmaşıklaşmasına ve gereken alanın artmasına sebep olur. Ayrıca komutların ilgili işlemcilere göre düzenlenmesi ve tekrar sıralanması gibi işlemler de gereken zamanı artırmaktadır. Bu zamanın azaltılması için bağlam değişikliğinin iyi organize edilmesi gerekmektedir.

**Bant genişliği:**

Düzgün çalışan bir sistemde işlemcinin gücü ile giriş/çıkış birimlerinin ve bellek sisteminin bant genişliği arasında bir denge vardır.

**Ön Bellek Tutarlılığı:**

Bu başlık daha önceki haftalarda &quot;Çok İşlemcili Ssistemlerde Ön Bellek Tutarlılığı Ödevi&quot; adı altında irdelendiği için tekrar anlatılmamıştır.

**Belleğe bağlantı yapıları:**

Bellek bant genişliği sistemin çalışmasına doğrudan etkilidir. Belleğe yapılabilecek bağlantılar üç çeşittir:

_Zaman paylaşımlı bus:_ En düşük maliyete ve karmaşıklığa sahip olan yöntemdir. Fiziksel olarak donanımın yeniden düzenlenmesi kolaydır. Tüm sistemin kapasitesi bustaki transfer hızına bağlıdır. Busta bir sıkıntı olduğunda sistem çökebilir. Sistemi yeni ünitelerle genişletmek performans artışı sağlayabilir, buna rağmen üç yöntem arasında en düşük sistem verimliliği bu yöntemdedir. Bu sebeple küçük sistemlerde kullanılabilir.

_Crossbar switch:_ En karmaşık sistemdir, fakat en yüksek hızın görülme ihtimali bu yöntemle sağlanabilir. Fonksiyonel birimler ucuz ve kolay bulunabilir. Ayrıca sadece matrislerle yapılan bir yapılandırma ile uygulandığından maliyet düşüktür. Sistemdeki birimlerin artırılması ile performans artışı sağlanabilir. Teknik olarak performans artışını matris boyutu sınırlasa da segmentasyon yöntemleri ile bu durum değiştirilebilmektedir.

_Multiport bellek:_ En maliyetli yöntemdir çünkü kontrol ve anahtar devreleri bellek sisteminin içine kuruludur. Yüksek bir hız oranına erişme imkanı vardır. Sistemin genişletilmesi ve yapılandırması uygun bellek girişlerinin olması ile mümkündür. Fakat bellek girişlerinin tasarımı ilk başta yapıldığı için modifiye edilmesi zordur. Fazla sayıda kablo ve konektöre ihtiyaç vardır.

# **İşletim Sistemi ile İşlemci arasındaki ilişki:**

Seri çalışan bir işletim sisteminde görevlerin düzenlenmesi ve anahtarlanması, kaynakların tahsis edilmesi, giriş/çıkış birimlerinin kurulması ve kullanılması için görevlendirilmiştir. Üç adet işletim sistemi stratejisi bulunmaktadır:

_Her bir işlemcide ayrı denetçi (supervisor):_ Her işlemci kendine ait giriş/çıkış elemanlarına ve dosyalarına sahiptir. Bu dosya ve elemanların diğer işlemcilerdeki kopyalarından ayrılmaları için denetçi bulunması gerekir. Her denetçinin kendine ait gizli tabloları bulunur, fakat duruma göre bu tablolar paylaşılabilir. Bu durum da tabloya erişim problemleri oluşturmaktadır. Bu yöntem efendi-köle (master-slave) yaklaşımı kadar hassastır fakat bir işlemcinin yeniden başlatılması efendi-köle yöntemine göre daha zordur. Çünkü bu yöntemde giriş/çıkış birimlerinin manual olarak ayarlanması gerekmektedir.

_Efendi-köle:_ Yönetici fonksiyonları her zaman aynı işlemci içinde gerçekleştirilir. Eğer köle (slave) denetçinin yapması gereken bir servise ihtiyaç duyarsa, efendi işlemcideki işlemin kesilmesini ve denetçiye sevk edilmesini beklemek zorundadır. Sadece bir işlemcide denetçi fonksiyonların çalışması tablolarda oluşan sorunları ve kilitlenmeleri azaltır. Fakat bu yöntemde sistemin modifiye edilmesi imkansıza yakındır.

_Floating-supervisor:_ Efendi bir işlemciden diğerine kayarak çalışır, fakat birden çok işlemci aynı anda denetçi fonksiyonları çalıştırabilir. Bu sistemlerde kaynakların yüklenme performansı daha başarılı olmaktadır. Ortaya çıkacak çakışma ve sorunlar önceden statik veya dinamik kontrolle tanımlanan öncelik değerleri ile çözülebilmektedir. Genellikle denetçi kodlar tekrar tekrar çalıştırılmak zorundadır. Tablo erişimi gibi sorunların önlenmesi mümkün değildir. [1,3]

# **SONUÇ**

Bilgisayar mimarilerinde hedeflenen performans artışı için çok işlemcili sistemler kullanılmaya başlanmıştır. Bu sistemler birden çok çeşitten oluşmaktadır. Her birinin belleğe ulaşım stili farklıdır. Bu sebeple bilgisayarla ilgilenen bilim insanları yıllar içinde birden fazla taksonomi yöntemi geliştirmişlerdir. Çok işlemcili sistemler performans artışı sağlasa da beraberinde bazı senkronizasyon sorunlarını beraberinde getirmektedir. Bu sorunların birden fazla çözüm yöntemi bulunmaktadır. Maliyet, esneklik ve efektif olmalarına göre tercih edilme durumları değişmektedir.

# **KAYNAKÇA**

1. Feza BUZLUCA, Bilgisayar Mimarisi Ders Notları, Bölüm 09, Çok İşlemcili Sistemler (Multiprocessor Systems)
2. David P. Rodgers. 1985. Improvements in multiprocessor system design. SIGARCH Comput. Archit. News 13, 3 (June 1985), 225–231. DOI:https://doi.org/10.1145/327070.327215
3. Inter Processor Communication and Synchranization, https://www.ioenotes.edu.np/media/notes/computer-organization-and-architecture-coa/Chapter8-Multiprocessors.pdf
4. 19.11.14 - Kirstin Heidler - NUMA Seminar
5. M.Morris Mono, Digital Design 4th Edition.
6. Frank, S J. Tightly coupled multiprocessor system speeds memory-access times. United States: N. p., 1984. Web.

