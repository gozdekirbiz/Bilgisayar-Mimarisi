#**HYPERTHREADING**
**GÖZDE KIRBIZ**
**191180053**
**İÇİNDEKİLER**
###### ÖZET
###### HYPERTHREADING ÖNCESİNDEKİ TEKNOLOJİ
###### HYPERTHREADING MİMARİSİ VE AMAÇLARI
###### HYPERTHREADING PERFORMANS ANALİZLERİ
###### SONUÇ
###### KAYNAKÇA

**ÖZET**  
Hızla gelişen teknolojiyle beraber performans artışının talep görmesi ve internetin ortaya çıkması ile sunucuların sık kullanılmaya başlaması ile işlemci üreticileri yeni teknoloji arayışlarına girmişlerdir. Hyperthreading, Intel firmasının 2002 yılının Şubat ayında Xeon serisi ile piyasaya sürdüğü ve performans artışının amaçlandığı bir teknolojidir. Bu teknoloji ile bir adet fiziksel işlemcinin iki lojikal işlemci gibi algılanması sağlanmıştır. Aynı anda iki ayrı işi yapabilmeye imkan sağlayan hyperthreading, işlemciye işlemlerin düzenlenmesi esnasında esneklik, veri transferi sırasında oluşan gecikmenin etkisini en aza indirme fırsatı, dahili kaynakların daha verimli kullanılması ve genel anlamda performans artışını sunmaktadır.

Bu çalışmada 1.kısımda Hyperthreading öncesi teknolojiler ve Hyperthreading&#39;in çıkış amaçları incelenecektir. 2.kısımda Hyperthreading mimarisi ve birimlerinin görevlerine değinilecektir. 3.kısımda ise Hyperthreading&#39;in farklı alanlarda performans analizlerine grafikleri ile beraber yer verilecektir.

**HYPERTHREADING ÖNCESİNDEKİ TEKNOLOJİ**

Hyperthreading teknolojisini anlayabilmek için öncesindeki teknolojilerin sağladıklarını ve dezavantajlarını incelemek önemlidir. CPU, RAM ve diğer donanımlara göre çok daha hızlı çalışabilme kapasitesine sahip bir birimdir. Fakat CPU her ne kadar hızlı olursa olsun, asıl hız belirleyen unsur verinin RAM&#39;den CPU&#39;ya ne kadar sürede gittiğidir. Bir başka deyişle hızı yavaş olan birim belirlemektedir. CPU işlerini hızla bitirip yeni verinin gelmesini beklerken beklenen süre israftır. Bu sebeple bekleme süresini aza indirgeme amaçlı birtakım yöntemler geliştirilmiştir. Yüksek clock frekansı bu yöntemlerden biridir fakat gelen işlemler bozulmaya uğrayabilir ve cache kaybı gibi sorunlar gözlemlenebilir. Diski RAM olarak kullanmak da başka bir yöntemdir ama yine de yavaşlık istenen derece giderilemez. Cache yönelimi oldukça kullanışlı ve etkili olsa da büyük verilerin cachelerini tutmak ve işlemek de yine zaman kaybına neden olmaktadır. Bu sebeple küçük ve en çok kullanılan veriler cache bellekte tutulur. Bu yöntemler her ne kadar performansı artırıyor olsa da %100 verim sağlamamaktadır. Günümüzdeki yaklaşımlar thread&#39;ler üzerine kurulmuştur. Paralel çalışma yöntemini benimseyen bu yönelimde aynı anda işlemlerin yapılması sağlanır. Thread temelli yöntemlerde Time-sliced multithreading, switch-on-event gibi yaklaşımlar vardır. Bu iki yaklaşımın temelinde de işlemciler arasında threadlerin değişimi vardır. Takas zamandan tasarruf ettiriyor olsa da, değiştirme aşamasında sorun çıkması muhtemeldir, dolayısıyla optimal değildir. Hyperthreading teknolojisi de thread tabanlı bir yöntemdir. Aynı anda iki işlemin tek bir işlemcide ve takas yapılmadan gerçekleştirilmesini sağlar.

Hyperthreading teknolojisinin geliştirilme sebeplerinden bir başkası da , &quot;die&quot; adı verilen ve işlemcinin kesit alanı kadar yer kaplayan yarı iletken maddenin artışının performans artışına göre daha hızlı ilerlemesidir. (bknz. Figür 1) Mimaride yer sorununa sebep olacağı için birden çok işlemci kullanmak yerine daha az alanda çok iş planlamasına gidilmiştir.

![](https://user-images.githubusercontent.com/77017691/151712853-8f4de6da-ce67-4580-a512-dcf0d0a2f247.png)
	**Figür 1:Die / Performans grafiği[1]**
![](https://user-images.githubusercontent.com/77017691/151712862-f18e20c9-df0c-4ac1-9054-13aeb7a54328.png) 
![](https://user-images.githubusercontent.com/77017691/151712863-0654e545-d50b-4f75-bd83-c07c0e4e0c90.png)
  **Figür 2:Hyperthreading işlemcisi (a) ve iki çekirdekli işlemci (b)**

**HYPERTHREADING MİMARİSİ VE AMAÇLARI**

![](https://user-images.githubusercontent.com/77017691/151712864-247bf0cd-e567-47d6-9ca0-d936ef2f92cc.png)  
**Figür 3: Xeon işlemci ailesinin pipeline’ı [1]**  
Hyperthreading teknolojisi kullanan bir işlemcinin mimarisine bakıldığında kontrol registerları, genel kullanım için registerlar, APIC(Advanced Programmable Interrupt Controller) register gibi birtakım registerlar görülür. Her lojikal işlemcinin kendine ait kontrolcü ya da APIC registerı bulunur. Gönderilen hatalar sadece o lojik işlemciyi etkiler. Diğer donanımların büyük kısmı fiziksel (ana) işlemciyle paylaşılır. Örneğin gelen emirlerin düzenlendiği ve takip edildiği TC birimine iki lojikal işlemci de ulaşmak isterse alternatif clock döngüsü ile önce birine izin verilir ve sonraki clock döngüsünde diğer işlemcinin kullanması sağlanır. Her lojikal işlemcinin kendisine ait 64 byte&#39;lık streaming buffer&#39;ı vardır. Aynı şekilde return bufferları az yer kapladıkları ve birden fazla olmalarının performansa katkısı yüksek olduğundan her lojikal işlemcide bulunur.Lojikal işlemcilerin birbirine üstünlüğü yoktur. İşlem sırası ilk gelene göre belirlenir.

 Hyperthreading amaçlarından diğeri, lojikal işlemcilerden birisi durduğunda diğerinin işe devam ederek ilerlemeyi sürdürdüğünden emin olmaktır. Buffer sıraları kontrol edilerek herhangi bir lojikal işlemcinin tüm işlem girişlerine erişmesi engellenmiştir. Bir başka amaç ise, o an sadece tek bir thread varsa, Hyperthreading teknolojisine sahip işlemcinin normal bir işlemci hızıyla çalışması ve parçalanmış işler varsa en sonda birleştirilmesi gerekmektedir.

Diğer donanımların büyük kısmı fiziksel (ana) işlemciyle paylaşılır. Örneğin gelen emirlerin düzenlendiği ve takip edildiği TC birimine iki lojikal işlemci de ulaşmak isterse alternatif clock döngüsü ile önce birine izin verilir ve sonraki clock döngüsünde diğer işlemcinin kullanması sağlanır. Her lojikal işlemcinin kendisine ait 64 byte&#39;lık streaming buffer&#39;ı vardır. Aynı şekilde return bufferları az yer kapladıkları ve birden fazla olmalarının performansa katkısı yüksek olduğundan her lojikal işlemcide bulunur.Lojikal işlemcilerin birbirine üstünlüğü yoktur. İşlem sırası ilk gelene göre belirlenir.

Hyperthreading özelliğine sahip bir işlemci sıradan bir işlemci gibi de çalıştırılabilir. Bu ayarlamayı işletim sistemleri yapar. İşletim sistemlerinin bu işlemleri yapabilmesi için iki optimizasyon yapması gerekir. Eğer çoklu işlem yapılmıyorsa HALT adı verilen fonksiyonun çalışması gerekir. Bu fonksiyonu kullanıcıların çağırması Intel tarafından engellenmiştir. İkinci optimizasyonda ise işletim sisteminin gelen işleri farklı fiziksel işlemcilere dağıtarak performansı artırması hedeflenmektedir. [1]

**HYPERTHREADING PERFORMANS ANALİZLERİ**  
![](https://user-images.githubusercontent.com/77017691/151712865-50419665-260b-4863-81e8-5332c63a94db.png)  **Figür 3-4: HT Cache Kaybı Grafikleri [4]**  
![](https://user-images.githubusercontent.com/77017691/151712866-fbfe7fc5-cc64-403a-af3f-b8a4bc3f6f58.png)  
Veritabanı alanında Hyperthreading etkisine bakıldığında, oldukça etkili olduğu söylenebilir. Veritabanları büyük cache kayıpları ve düşük CPU optimizasyonu ile çalıştığından, Hyperthreading teknolojisi bu alanda çok etkili olmuştur. Cache verileri Hyperthreading teknolojisinde tüm threadler arasında paylaşılır. Bu paylaşım faydalı olacağı gibi zararlı da olabilir. Örneğin bir thread diğer thread için veri getirip götürebilirken, eğer bu iki thread arasında hata oluşursa büyük cache kayıpları söz konusu olabilir. Yapılan araştırmaya göre Hyperthreading veri TLB&#39;lerinde kayıpları artırırken, komut TLB&#39;lerindeki kaybı yaklaşık %66 kadar azaltmaktadır. Bunun sebebi veriler paylaşılırken, komutların kopyalanarak kullanılmasıdır. Önemli veritabanı fonksiyonlarında da %72 oranında cache kaybının azaldığı kaydedilmiştir.

 Hyperthreading ile uygun şartlar altında genellikle %30 oranında performans artışı gözlenmektedir. [3] Birçok alanda Hyperthreading etkisi üzerine araştırma yapılmıştır: Genetik, hesaplanabilir kimya, mekanik tasarım analizi, hava durumu modellemesi, akışkan dinamiği, sonlu element analizi, medya verileri, veri tabanları, bulut sistemleri ve sanal makineler. Yapılan çalışmalarda ortak görülen sonuç, Hyperthread teknolojisinin multithread koşulları altında çok daha iyi çalıştığıdır. İncelenen makaleler genellikle 2002-2003 senelerinden olsa da, hyperthreading&#39;in ilerdeki işlemcilerde daha genel bir SMT teknolojisiyle üretileceği ön görülmüş, bu sebeple de multithreading özelliğinin daha yaygınlaştırılması önerilmiştir. Bunun için uygun araçların oluşturulması, derleyicilerin ve programlama dillerinin yazılımcıya daha çok imkan sağlaması gerektiği gibi konulara değinilmiştir.[2,3]
Bundan sonra incelenecek her çalışmada da görülecek olan bu sonuç, Hyperthreading teknolojisinin eşzamanlılık arttıkça daha verimli çalıştığını, tek işlemin gerçekleştiği durumlarda verimin çok az seviyede kaldığını göstermektedir.[4]
  ![](https://user-images.githubusercontent.com/77017691/151712867-3100b91a-088e-410e-a2c4-91f4fa8242a6.png)  
  **Figür 5: Eşzamanlılık ve HT ilişkisi[4]**
  Örneğin bir thread diğer thread için veri getirip götürebilirken, eğer bu iki thread arasında hata oluşursa büyük cache kayıpları söz konusu olabilir. Yapılan araştırmaya göre Hyperthreading veri TLB&#39;lerinde kayıpları artırırken, komut TLB&#39;lerindeki kaybı yaklaşık %66 kadar azaltmaktadır. Bunun sebebi veriler paylaşılırken, komutların kopyalanarak kullanılmasıdır. Önemli veritabanı fonksiyonlarında da %72 oranında cache kaybının azaldığı kaydedilmiştir.
Medya işleme alanında Hyperthreading, iki farklı şekilde gerçekleşebilir. Örneğin, bir videonun her bir karesini işliyor olalım. İlk yaklaşım, görüntünün yarısını bir lojikal işlemciye, diğer yarısını da diğerine işletmektir. İki iş de benzer olduğundan aynı anda bitmesi beklenmektedir. Bazı durumlarda işlenen yarı görsel diğerinden daha karışık olabilir. Bu durumlarda bir lojikal işlemci boş kalır ve bu pek istenen bir durum değildir. Bu yönteme statik ayırma denir. Diğer yaklaşım ise dinamik ayırmadır ve görüntü dilim dilim işlenir. Her dilim threadi işi bitmiş lojikal işlemciye aktarılır. Bu yöntemde hangi lojikal işlemcinin ne işlemi yaptığı bilinmez ve işin bitmesi aynı olmayabilir. Hyperthreading&#39;in iyi çalışabilmesi için iki lojikal işlemciye eşit ağırlıkta iş verilmesi gerekir. Çünkü ikisi de tek bir fiziksel işlemciden veri almaktadır. Bu yüzden dinamik ayırma yöntemi Hyperthreading ile iyi çalışmaktadır. Yapılan çalışmalara göre bu alanda Hyperthreading %7 ile %18 arasında iyileştirme sağlamaktadır. Ayrıca Hyperthreading&#39;in sabit görevlerde enerji tasarrufu sağladığı da belirtilmiştir.[5]
   ![Shape6](https://user-images.githubusercontent.com/77017691/151712868-fee021a0-38d7-4f27-9578-4d1de5852dfe.png)
   **Figür 6: HT&#39;in medya işlemedeki performansı [5]**
   ![Shape6](https://user-images.githubusercontent.com/77017691/151712857-9101d10d-9de9-4bb4-b0a2-4a8ebf3249ce.png)

  **Figür 7: HT&#39;in enerji tasarrufu grafiği [5]**

  Hyperthreading teknolojisinin bulut bilişim alanındaki etkilerine bakıldığında, benzer noktalara değinmek mümkündür. Yapılan araştırmalara göre çoklu işlem ortamında Hyperthreading&#39;in daha verimli olduğu gözlenmiştir. Integer hesaplamalarında %10&#39;luk bir artış gözlemlenirken, sistem çağrıları bazında bu artışın %50 civarında olduğu görülmüştür. Thread sayısı 1 ve 2 iken neredeyse aynı sonuçların elde edildiği, 4 thread&#39;lik bir işte %4.5&#39;luk bir artış görülürken, thread sayısı 8,16,32 ve 64 olduğunda artışlar şu şekilde kaydedilmiştir: %9.9, %9.5, %9.5 ve %9.4. Tüm çalışmalarda görüldüğü gibi, thread sayısı ile çekirdek sayısı eşit olduğunda maksimum verim elde edilmektedir. Bu sonuçlar doğrultusunda Intel tarafından hesaplama işlemleri için Hyperthreading özelliğinin devre dışı bırakılması tavsiye edilmiştir. Yine Intel tarafından programların ek threadler yardımıyla açılıyor olmasının önemli olduğu ifade edilmiştir.

Sanal makinelerde Hyperthreading etkisine bakıldığında, ekonomik fayda sağlanabildiği gözlemlenmiştir. Sanal bir CPU, fiziksel bir CPU&#39;ya göre daha yavaş çalışır. Fakat yapılan araştırmalarda 2 adet sanal CPU&#39;nun Hyperthreading teknolojisi kullanılarak bir fiziksel CPU&#39;dan daha iyi çalıştığı görülmüştür. Bu sayede büyük firmaların sanal CPU ve HT kullanarak maliyette azalmaya gidebilecekleri söylenmiştir. [6]

  ![Shape6](https://user-images.githubusercontent.com/77017691/151712858-3ef6fc3f-37ad-4274-a1ba-b519ccca2b90.png)
  **Figür 8: HT&#39;nin sanal makinede performansa etkisi [6]**
  ![Shape5](https://user-images.githubusercontent.com/77017691/151712860-20663337-e95e-40f9-9b22-a85e9a8cc93b.png)
  **Figür 9: Çekirdek sayısının HP&#39;e etkisi [6]**

  **SONUÇ**

Hızlı çalışan CPU&#39;nun diğer donanım birimlerini beklemesinden dolayı ortaya çıkan zaman kaybını iyileştirmek için bazı yöntemler denenmiştir. Bunlardan birisi de Intel&#39;in Hyperthreading yöntemidir. Hyperthreading, bir fiziksel CPU&#39;nun iki lojikal işlemci sayesinde iki CPU varmış gibi davranmasını sağlama ve aynı anda birden fazla işin yapılmasını gerçekleştirme işidir. Birçok alanda kullanılan bu teknoloji genel anlamda %30&#39;a yakın performans iyileştirmesi sunmaktadır. Bunun yanı sıra die boyutunu çok genişletmeden performans artışı gösterdiği için mimari alanında önemi büyüktür. Çoklu threadlerin kullanıldığı programlarda performans artışı daha fazla olmaktadır. Bu sebeple bu alanda yeniliklerin yapılması beklenmektedir. Ayrıca Hyperthreading enerji tasarrufu ve maliyetin azalmasını da sağlamaktadır.

**KAYNAKÇA**

1. Intel Technology Journal Q1, Hyper-Threading Technology Architecture and
Microarchitecture, 2002. Vol. 6 Issue 1.

1. Intel Technology Journal Q1, Hyper-Threading Technology: Impact on Compute-Intensive Workloads, 2002. Vol. 6 Issue 1.
2. L. Bononi, M. Bracuto, G. D&#39;Angelo and L. Donatiello, &quot;Exploring the Effects of Hyper-Threading on Parallel Simulation,&quot; 2006 Tenth IEEE International Symposium on Distributed Simulation and Real-Time Applications, 2006, pp. 257-260, doi: 10.1109/DS-RT.2006.18.
3. Hassanein, W.M., Rashid, L.K. &amp; Hammad, M.A. Analyzing the Effects of Hyperthreading on the Performance of Data Management Systems. Int J Parallel Prog 36, 206–225 (2008). https://doi.org/10.1007/s10766-007-0066-x
4. Intel Technology Journal Q1, Media Applications on Hyper-Threading Technology, 2002. Vol. 6 Issue 1.
5. Zhang X., Li A., Zhang B., Liu W., Zhao X., Li Z. (2016) The Cost Performance of Hyper-Threading Technology in the Cloud Computing Systems. In: Tan Y., Shi Y., Li L. (eds) Advances in Swarm Intelligence. ICSI 2016. Lecture Notes in Computer Science, vol 9713. Springer, Cham. https://doi.org/10.1007/978-3-319-41009-8\_63




