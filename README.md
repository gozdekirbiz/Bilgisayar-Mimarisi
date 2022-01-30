#INTERRUPT
## **İçindekiler Tablosu**
##### **Özet** 
##### **Interrupt** 
###### Interrupt çeşitleri
##### Bilgisayar Mimarilerinde Interrupt**
###### RISC-CISC Mimarileri ve Farkları
##### **Sonuç**
##### **Kaynakça**
**ÖZET**

  Kesme, bir programın çalışırken çeşitli sebeplerden ötürü işlemciye gelen bir sinyal ile çalışmasının durdurulması ve onun yerine başka bir programın çalışmaya başlaması ile akışı değiştirilmesidir. Interruptlar maskelenebilir/maskelenemez şeklinde veya iç/dış etkilerle interrupt şeklinde sınıflandırılabilir. Interruptların işlenmesinde kesme kaydedicileri kullanılır. Bazı kesmelerde veri kaybı görülebilir. Farklı mimarilerde kesmeler benzer şekilde ele alınsa da, mimarilerin pipelining ve hız gibi özellikleri interrupt gecikmesi adı verilen gecikmeyi etkilemektedir. Interruptlarda query ve vektör modu kullanabilir, vektör modu daha hızlı çalışır fakat ekstra donanım ve alana ihtiyaç duyar.

Bu çalışmanın ilk bölümünde interrupt tanımı yapılacak ve çeşitleri aktarılacaktır. İkinci bölümde interruptların çalışma şekli anlatılacak ve farklı mimarilerin özelliklerine değinilecektir. Üçüncü bölümde RISC ve CISC mimarisindeki birtakım analizler paylaşılacaktır.
**Interrupt ( Kesme)**

Kesme, bir programın çalışırken çeşitli sebeplerden ötürü işlemciye gelen bir sinyal ile çalışmasının durdurulması ve onun yerine başka bir programın çalışmaya başlaması ile akışı değiştirir. Kesme adı altında mikroişlemcilerin yaptığı başka bir işlem daha vardır. Bu işlemde, işletim sistemleri önceliği olan bazı işlemleri (örneğin G/Ç işlemi) hızlı yapabilmek için normal bir fonksiyon çağrısından yararlanmak yerine, kesme gerçekleştirmeye zorlar. Böyle bir işlem kesmeden farklıdır çünkü aniden değil, programdaki kodların işleyişi ile gerçekleşmiştir. Buna trap adı da verilmektedir. [1]

**Interrupt Çeşitleri**

Interrupt çeşitleri birçok şekilde gruplanabilmektedir. Bazı interrupt çeşitleri şu şekilde sıralanabilir:

- Timer: Program önceden belirlenmiş bir zaman süresine göre çalışır. Genellikle zaman paylaşımlı sistemler için tercih edilir. Bu sistemlerde bir program çalıştırıldıktan belli bir süre sonra başka bir program çalıştırılmaya başlar. Bu kesme çeşidi için aşağı sayıcılar kullanılır. Donanım-dış (Hardware-External) kesmelere örnektir. Önceliği yüksektir.
- I/O: I/O denetleyicileri ile kontrol edilir. Hardware-External ve Non-Maskable (Maskelenemeyen) interrupta örnektir. İptal edilemez, hemen gerçekleşir. Bu yüzden maskelenemeyen kesmedir.
- Donanım hataları: Donanımda gerçekleşen herhangi bir hata, tüm sistemin çalışmasını etkileyebilir. Bu nedenle önceliği yüksektir, maskelenemez.
- Sanal hafıza: Bazı hafıza adresleri istenen alanda bulunamadığında ortaya çıkar. Internal ve önceliği yüksek bir interruptır.
- Program kesmeleri (Exception): Underflow,overflow, 0&#39;a bölünme gibi hatalarla karşılaşıldığında ortaya çıkar. Düzeltilmesi gerekir. Düzeltme yollarından biri önceden belirlenmiş bir değeri sonuç olarak kabul etmek olabileceği gibi hata mesajı verip programın sonlandırılması da olabilir. Internal ve maskelenebilir. [2]
_**Maskelenemeyen Kesme**_

Bu kesme gerçekleştiğinde önlenmesi mümkün değildir, herhangi bir yolla durdurulamaz. Maskelenemeyen kesme geldiğinde işlemci o anda çalıştığı komutu bitirir, kaydedicilerdeki kayıtlar yığına atılır ve kesme vektör tablosundaki ilgili kesmenin adresi alınır. Kesme sona erdikten sonra ana program kaldığı yere geri dönebilir. Resetleme durumlarında daha farklı bir yol izlenir ve kaydedicilerdeki bilgilerin aktarılmasına gerek yoktur. Maskelenemeyen kesmeler, bazı sistemlerde ani ve zararlı durumlar için de kullanılmaktadır.

_**Maskelenebilir Kesme**_

CPU&#39;nun kolaylıkla gözardı edebileceği kesmelerdir. Meydana geldiğinde sistem tarafından ilgili komutlar bittikten sonra düzeltilir. Düşük öncelik seviyesine sahiptir. Maskelenemeyen kesmelere göre tepki süresi oldukça yüksektir.

**Bilgisayar Mimarilerinde Interrupt**

Bir kesme şu şartlar sağlandığında gerçekleşir:

1. Kesme bekliyor.
2. İşlemcinin kesme biti hazır hale geliyor.
3. Kesmeye özel kesme biti hazır hale geliyor.
4. Başka bir işi yapmakta olan işlemci ilgili kesmenin işlemlerini gerçekleştiriyor. Pipeline teknolojisi kullanan işlemcilerde bekleyen kesmeleri kontrol etme evresi gibi çözümler uygulanır
5. 1-4 arasındaki şartları sağlayan öncelikli kesme var mı kontrol ediliyor.

Interrupt latency (kesme gecikmesi) adı verilen gecikme, bir kesmenin oluşmasından kesmenin gerçekleştirilmesi arasındaki zaman farkını verir. Yukarıdaki beş şartın her biri gecikmeyi etkilemektedir. Interrupt analizinin yapılması için bu gecikme incelenir. Gecikmenin farklı bilgisayar mimarisinde incelenebilmesi için öncelikle iki mimarinin farklarına bakmak gerekir. [3]

**RISC-CISC Mimarileri ve Farkları**

Gelişen teknoloji ve hız ihtiyacının artması ile işlemci üreticileri yeni mimarileri denemektedirler. Bunlardan adını sıklıkla duyduğumuz iki mimari RISC ve CISC mimarileridir.

RISC mimarisi basit düzeyde komutlarla tasarlanmış bir mimariyken CISC mimarisi karmaşık komut setinden oluşur. CISC mimarisinde değişen uzunlukta komutlar olabilir ve bu da her komutun aynı sürede bitirilmesini engeller. RISC yazılıma daha dayalı iken CISC her zaman donanıma dayalı çalışır. CISC mimarisinde RISC&#39;e göre çok az sayıda register bulunur. RISC teknolojisinde sadece load-store adı verilen bir komutla hafıza ve CPU arasında iletişim sağlanırken, CISC mimarisinde görülmez. Interrupt analizinde en büyük farkı sağlayan pipeline teknolojisini RISC kullanırken, CISC mimarisinde pipeline teknolojisi yoktur. RISC çipleri CISC çiplerine göre daha hızlıdır. Karşılaştırılacak olursa CISC çipi bir komutu 2 ile 10 cycle&#39;da tamamlıyorsa, RISC tek bir cycle&#39;da tamamlar. Bu da RISC ile CISC mimarisini ayıran önemli bir faktördür. [4]

Interrupt handling RISC ve CISC mimarilerinde benzer şekilde yürütülür. RISC-V (Linux işletim sistemi ile beraber çalışabilen açık kodlu bir RISC mimari çipi) mimarisinde bir interrupt meydana geldiğinde Machine Exception Program Counter(mepc) adı verilen sayaca o anda program counterda yazılı olan komut kaydedilir. Machine Status Register adı verilen kaydedici global interrupt enable&#39;larını tutar ve enable biti geçerli ise interrupt gerçekleşir. Machine Cause Register ile hangi hatanın oluştuğu belirlenir. Machine Trap Vector Base Address Register ile işlemcinin hangi adrese atlanacağı tutulur. RISC-V mimarisinde otomatik kayıt sağlayan bir donanım desteği yoktur, bu sebeple veri kaybı olmaması için yazılımların kayıt işlemini gerçekleştirmesi beklenir.

RISC-V mimarisinde interruptlar query modunda veya vector modunda işlenebilmektedir. Yapılan araştırmalara göre vektör modunu kullanmak, query moduna göre oldukça hızlı olmaktadır çünkü mcause aşaması atlanılmaktadır. Ayrıca query modunda cevap verme süresi interruptın bulunduğu konuma göre değişiklik göstermektedir fakat vektör modunda böyle bir durum söz konusu değildir. Vektör modu ile cevap zamanının %38 ile %71.4 arasında azaldığı tespit edilmiştir. Fakat vektör modunun kullanılabilmesi için ekstra donanım ve yer gerekmektedir. Buna göre gereklı alan %48 artmış, enerji tüketimi de %39.8 oranında artmıştır. [5,6]

İlgili çalışmanın verileri aşağıda verilmiştir:
![Shape5](https://user-images.githubusercontent.com/77017691/151714119-2608b5cf-1d56-4cdc-a454-e7417764aca6.png)

 **Fig 1**. RISC-V Mimarisinde Query Mode ve Vector Mode Karşılaştırması_

![](https://user-images.githubusercontent.com/77017691/151714169-03e1e1ab-e5f5-45ff-a353-adfac9089f53.png)

 **Fig 2**. Farklı modlarda alan ve güç tüketimi sonuçları_

RISC ve CISC mimarisindeki interrupt analizi için şunlar söylenebilir:

- RISC mimarisi normal şartlarda CISC mimarisinden hızlı çalışmaktadır. Bunun sebebi hem komutların tek bir cycle ile bitirilebilmesi, hem de pipeline teknolojisini kullanmasıdır. Ayrıca RISC mimarisinde, önceden CISC işlemcisinin interruptlarla alakalı yaptığı işlemler interrupt servis rutini ile kontrol edilmektedir. Böylece işlemcinin yükü azaltılmıştır.[5]
- RISC mimarisi pipeline&#39;ın faydalarından yararlanarak hızlı çalışsa da precise interruptlar pipeline özelliğini kısıtlamaktadır. Pipelinenin out-of-order execution (sırasız yürütüm) özelliğinden faydalanırken, precise interrupt sıralı bir şekilde çalışmayı ister. Bu da pipelining kısıtlamasına ve cycle zamanlarının artmasıyla performans azalmasına sebep olur.[2]

**SONUÇ**

Interrupt, belli bir sinyal ile işlemcinin çalıştırdığı programın durdurulması ve gelen sinyale göre istenen diğer programın çalıştırılmasına denir. Interrupt sınıflandırması kaynaktan kaynağa değişse de maskelenebilen/maskelenemeyen olarak ayrılabilir. Alt başlıklarında timer, I/O, program ve donanım hataları gibi interrupt çeşitleri görülebilir. Interruptların işlenmesi mimarilerde çok fark etmese de işlemcinin kullandığı pipelining teknolojisi ve işlemcinin kendi hızı etkili olmaktadır. RISC ve CISC mimarileri karşılaştırıldığında RISC mimarisinde interruptların daha hızlı işlediği görülür. RISC mimarisinde interruptlar query ve vektör modunda sıralanabilir. Yapılan araştırmalara göre vektör modunun daha hızlı çalıştığı fakat ekstra donanıma, fiziksel alana ve daha çok güce ihtiyaç duyduğu belirtilmiştir.

**KAYNAKÇA**

1. _Dr. Nurettin Topaloğlu, Salih Görgünoğlu. Mikroişlemciler ve Mikrodenetleyeciler. ISBN: 978-9753-4771-16, Türkçe, 1. basım, 2003._
2. _Mayan Moudgilly , Stamatis Vassiliadis. On Precise Interrupts,1996._
3. _Regehr, J., Safe and structured use of interrupts in real-time and embedded software, in: I. Lee, J. Y.-T.Leung and S. Son, editors, Handbook of Real-Time and Embedded Systems, CRC Press, 2007 ._
4. _Farooui, Saira &amp; Zahra, Benish &amp; Samreen, &amp; Ahmed, Jamil. (2020). Comparative Study of Instruction Set Computer CISC And RISC. 3. 54-50._
5. _Steve Heath. Microprocessor Architectures. RISC, CISC and DSP. Book • Second Edition,1995._
6. _Xu K., Li Y., Yuan B., Su D. (2019) Evaluation and Optimization of Interrupt Response Mechanism in RISC-V Architecture. In: Xu W., Xiao L., Li J., Zhu Z. (eds) Computer Engineering and Technology. NCCET 2019. Communications in Computer and Information Science, vol 1146. Springer, Singapore. https://doi.org/10.1007/978-981-15-1850-8\_17_
