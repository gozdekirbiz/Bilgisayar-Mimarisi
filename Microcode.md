# MICROCODE
**GÖZDE KIRBIZ**
#
## İçindekiler Tablosu

**ÖZET**

**Mikroprogramlanmış Kontrol Birimleri**

Single Level

İki Seviyede

**Mikroprogramlanmış Kontrol Birimlerinin Kullanıldığı Mimariler**

**Mikroprogramlanmış Kontrol Birimlerinin Getirdiği İmkanlar**

**Mikroprogramlanmış Kontrol Birimleri ile Hardwire&#39;ın Karşılaştırılması**

**SONUÇ**

**KAYNAKÇA**

# **ÖZET**

Mikroişlem bir işlemcinin en önemli işlevlerinden biridir. Mikroişlemler ne kadar hızlı yapılırsa performans da o kadar iyi olmaktadır. Günümüzde iki çeşit mikroişlem kontrol birimi bulunmaktadır: Hardwire ve Mikroprogramlanmış. Mikroprogramlanmış kontrol birimleri komutların düzenlenmesini yazılım kısmında halletmeyi hedefler. İki tür mikroprogramlanmış kontrol tipi vardır: Single level ve multiple level. Mikroprogramlanmış kontrol kolay değiştirilebilme, hızlı uyum, karmaşık kodların sinyallerinin kolay sağlanması ve düşük maliyet gibi imkanlar sağlar. Fakat yazılım bazlı çalıştığından hardwire teknolojisine göre yavaş kalmaktadır. Uzun bir süre özellikle CISC mimarisinde bu yapı kullanılmış olsa da artık günümüzde performans düşüklüğü sebebiyle pek tercih edilmemektedir. Onun yerine donanım ile çalıştığı için performansı yüksek olan Hardwire kullanılmaktadır. Hardwire devrelerden oluştuğu için maliyetli ve karmaşık kodların çözümlenmesinde oldukça karmaşık devreler gerektirmesine rağmen günümüzde performans daha önemli olduğu için tercih edilmektedir.

Bu araştırmanın ilk kısmında genel hatlarıyla mikroprogramlanmış kontrol birimleri hakkında bilgi verilecek, neden iki tür mikroprogramlanmış kontrolün ortaya çıktığı anlatılacaktır. Alt başlıklarda bu iki türün çalışma prensiplerinden bahsedilecek ve ikinci kısımda ise farklı mimarilerde mikroprogramlama yönelimi hakkında bilgi verilecektir. Üçüncü kısımda mikroprogramlamanın faydaları üzerinde durulacak ve son kısımda Hardwire ile karşılaştırması ve yorumlanmasına yer verilecektir.


**Mikroprogramlanmış Kontrol Birimleri**

Mikroişlem bir işlemcinin en önemli işlevlerinden biridir. Bir komut bir veya birden fazla mikroişlem ile oluşturulur. Mikroişlemler ne kadar hızlı yapılırsa performans da o kadar iyi olmaktadır. Bu sebeple bilgisayar mimarisi ile ilgilenen bilim insanları bu konuda farklı fikirler ortaya çıkararak sistemi geliştirmeyi hedeflemişlerdir. Günümüzde iki çeşit mikroişlem kontrol birimi bulunmaktadır: Hardwire ve Mikroprogramlanmış.

Bir bilgisayarın temelde çalışmasını sağlayan unsurlar sinyallerdir. Mikroişlemlerin sonuçlarına göre birtakım sinyallerin meydana gelmesi ile bilgisayar komutları işlemektedir. Mikroprogramlanmış kontrol birimleri isminden de anlaşılacağı üzere komutların düzenlenmesini yazılım kısmında halletmeyi hedefler. Özel bir bellek bölgesinde ilgili komutlara ait kontrol sinyalleri bulundurulur. Bu bellek bölgesine &quot;control store&quot; veya &quot;microprogram&quot; adı verilmektedir.Kontrol belleğinin kapasitesi, mikro komut kelime uzunluğunun ve mikro komutun toplam sayısının çarpımıdır. Bir mikro komut iki bölümden oluşur: kontrol alanı ve adres alanı. Mikro komutun kontrol alanını kodlamak için geleneksel yaklaşımlar, tam kodlamayı (dikey mikro programlama), doğrudan kontrolü (encoding yok), alan kodlamasını içerir. Alan kodlama tekniği, alan doğrudan kodlamayı ve alan dolaylı kodlamayı içerir. Alan kodlama tekniği, çoğu mikro programlanmış kontrol bilgisayarı tarafından kullanılır ve doğrudan kontrol ve tam kodlamanın avantajlarına sahiptir. Yapılan araştırmalar sonucunda mikro komutun kontrol alanının uzunluğunu azaltarak kontrol belleğinin kapasitesini daha etkili bir şekilde azaltmak mümkündür.

 ![1](https://user-images.githubusercontent.com/77017691/151716347-299d5e2b-d252-478b-a763-b12847be7c60.png)
 
 Öncelikle, set-direct-control tekniği kullanılarak, kontrol alanının uzunluğunu azaltmaya çalışan single kontrol alanı içeren mikro komutlar tasarlanır. Daha sonra, çoklu kontrol alanı tekniği kullanılarak, N kontrol alanı içeren mikro komutlar tasarlanır, basit bir komutun yorumlanması için N kontrol alanlarının yalnızca bir mikro komutuna ihtiyaç duyulur ve karmaşık komutun yorumlanması genel olarak N kontrol alanının iki mikro komutuna ihtiyaç duyar.Bir makine komutunun yürütülmesi genellikle birkaç mikro komut tarafından yorumlanır ve daha sonra her bir mikro komutu kontrol belleğine getirmesi gerekir.

Mikro komutların yürütülmesi seridir.Mikro programlı kontrol, mikro komutların fetch edilmesini ve execute edilmesini, zaman içinde örtüşen iki işlemi yapan paralellizm tekniğini kullanarak yapar. Yapılan çalışmalarda mikroprogramlanmış yapılarda bir komutun fetch edilmesinin execute edilmesinden daha uzun sürdüğü görülmüştür. Bu yüzden mikro komutun execute süresi öncelikle mikro komutu fetch etmek için gereken kontrol belleğine erişim zamanına bağlı olduğundan, kontrol belleğine erişim süresini azaltmak için mikro komutun yürütme süresini etkili bir şekilde azaltmalıdır. Bunu sağlamak için çoklu kontrol alanı tekniği geliştirilmiştir. Çoklu kontrol alanı tekniği, bir makine komutunu yorumlamak için N mikro komutunu, uzun bir mikro komutu olan ve N tane kontrol alanı içeren tek bir mikro komutta birleştirmektir.[2]

 ![2](https://user-images.githubusercontent.com/77017691/151716350-7250309e-e9ff-47a6-8bc2-acd5f0ff3830.png)

# _ **Single Level Mikroprogramlama** _
 ![3](https://user-images.githubusercontent.com/77017691/151716351-2e325712-6a52-42dd-867b-12de21db4aec.png)
 Instruction register&#39;dan komutun opcode&#39;u mikrokomut adres kaydedicisine getirilir ve kod çözülür. Control store kısmında komutların opcodelarına göre belirlenmiş sinyaller bulunur. Bu sinyaller birkaç bitlik alandan oluşmaktadır. Çözümlenen kodda bir sonraki mikroişleme dair adres bilgileri ve kontrol alanı bilgileri bulunur. Ayrıca hangi adresleme modunun uygulanacağının bilgisi vardır. Koşullu adresleme modu kullanırsa kontrol alanında tutulan bayraklar ile durum bilgileri tutulur. Mikroprogramın son mikrokomutu bir sonra gelecek olan komutu ana bellekten instruction register&#39;a fetch eder.[1,3]

# _ **İki seviyeli Mikroprogramlama** _
 ![4](https://user-images.githubusercontent.com/77017691/151716352-884b6a19-129f-4532-9383-050c080fbaaa.png)
 
 Mikroprogramlama iki seviye ile de gerçekleştirilebilir. Tek seviyeli yapıya ek olarak nano komut belleği bulundurur. Nano komut belleği bir bilgisayardaki nano komut setinde bulunabilecek tüm komutlara dair oluşabilecek tüm kombinasyonlarla sinyaller içerir. Bu şekilde, mikro komutların aynı işlem bölümlerinin fazladan depolanması önlenir. Böyle bir kontrol ünitesinde, mikro komutlar kodlanmış kontrol sinyalleri içermez. Mikro komutların işlem kısmı, kodlanmış kontrol sinyallerini içeren nano komut belleğindeki kelimenin adresini içerir. Bu sayede bir mikrokomut uzunluğu tek seviyeli mikrokomut uzunluğuna göre daha kısa olmaktadır. Bunun bir sonucu olarak da kontrol belleğinin tüm hacmi azalmaktadır. Mikro komut belleği, ardışık mikro komutların seçimi için kontrol içerirken, bu kontrol sinyalleri nano komutlar temelinde üretilir. Nano komutlarda, kontrol sinyalleri sıklıkla kod çözmeyi ortadan kaldıran 1 bit/1 sinyal yöntemi kullanılarak kodlanır. Ancak, kod çözme talep eden çok bitli alanlarda sinyal kodlaması da mümkündür.[1,4]

**Mikroprogramlanmış Kontrol Birimlerinin Kullanıldığı Mimariler**

Mikroprogramlanmış kontrol birimleri genellikle CISC mimarisinde görülmektedir. RISC mimarisinin ilk oluşumlarında da kullanıldığı görülmüştür. CISC mimarisinde mikroprogramlanmış kontrol birimlerinin RISC&#39;e göre daha fazla görülmesinin sebebi şudur: RISC mimarisi az sayıda, indirgenmiş ve uzunluğu kısa olan basit komutlardan oluşmaktadır. Böyle bir mimariyi yazılım yerine hardwire olarak inşa etmek performans artışı sağlamıştır. Fakat CISC mimarisinde komutlar birden farklı tipte, farklı uzunluklarda olabilmektedir. Böyle bir mimarinin hardwire tasarımı oldukça karmaşık devreleri beraberinde getirmektedir. Her ne kadar 1990&#39;lı yıllarda CISC mimarisi de hardwire teknolojiden faydalanmış olsa da, düşük performanslı CISC işlemciler ve tek çip mikrobilgisayarlar hala mikro programlı kontrol kullanılmaktadır. Çünkü düşük kaliteli ürünler için komut setinin uyumluluğu ve maliyeti düşürmek, işlem hızından daha önemlidir. Ayrıca düşük clock frekans şartları altında mikro programlanmış kontrol kullanmak maliyeti azaltacaktır.[2,5]

**Mikroprogramlanmış Kontrol Birimlerinin Sağladığı İmkanlar**

Mikroprogramlanmış kontrol birimlerinin sağladığı imkanlara bakılacak olursa,

- Düşük maliyetli tasarım
- Komut kümesi ile uyumlu hale getirilebilmesi kolay
- Üzerinde değişiklik yapmaya izin veren bir yapıya sahip
- Komut eklemek veya düzenlemek kolay
- Organize ve sistematik

**Hardwired-Mikroprogramlanmış Kontrol Birimi Karşılaştırması**

Öncelikle bu bölümde kullanmak üzere araştırdığımda Hardwired ile Mikroprogramlanmış Kontrol karşılaştırılmasının ACM tarafından yapıldığını gördüm. Makaleyi okuduğumda benzer şeyler anlatılıyordu fakat karşılaştırma kısmında bilgisayarların en çok mikroprogramlanmış olarak tasarlandığını söylüyordu. Bunun sebebinin de mikroprogramlanmış kontrolün kolaylıkla modifiye edilip yeni komut kümelerine uyum sağlayabilmesi olduğu söyleniyordu. Hardwire teknolojisinde ise donanım üzerine kurulu olduğu için herhangi bir değişiklik yapmak çok zordur. Her ne kadar bu açıdan mantıklı gözükse de, dersten de bildiğim üzere günümüzde mikroprogramlanmış kontrol pek tercih edilmemektedir. ACM&#39;in yayınlamış olduğu makale eski olduğu için böyle bir sonuç çıktığını düşünmekteyim. Bu yüzden o makaleyi size sunmuyorum fakat referanslarıma ekleyeceğim. [5]

Karşılaştırma yapılacak olursa, hardwire teknolojisi donanım üzerine çalıştığı için daha hızlı sonuçlar üretir. Komutların fetch edilmesi, mikroprogramlanmış kontrole göre daha kolaydır. Devre kapıları ile kurulduğu içim maliyeti yüksektir. Ayrıca hardwire teknolojisinde değişiklik yapmak pek mümkün değildir, yapılsa bile çok maliyetli olacaktır. Ayrıca çok uzun ve karmaşık komutlar söz konusu olduğunda devre karmaşıklığı artmaktadır. Bu yüzden daha basit komutlar kullanan RISC mimarisinde hardwire tercih edilmesi daha hızlı gerçekleştirmiştir.

Mikroprogramlanmış kontrol ise modifiye edilmesi kolay, yazılım odaklı çalışan, maliyeti oldukça düşüren bir tekniktir. Fakat yazılım odaklı olması performans düşüklüğüne sebep olmaktadır. Karmaşık kodların sinyallerini üretmek sorun teşkil etmez. Donanım bazlı olmadığı için yeni bir komuta kolaylıkla uyum sağlayabilir. Bu özellikleri nedeniyle uzun bir süre CISC mimarisinde tercih edilmiştir.

**SONUÇ**

Mikroprogramlanmış kontrol birimleri komutların düzenlenmesini yazılım kısmında halletmeyi hedefler. Özel bir bellek bölgesinde ilgili komutlara ait kontrol sinyalleri bulundurulur. İki tür mikroprogramlanmış kontrol tipi vardır: Single level ve multiple level. Bu türlerin çıkma sebebi mikroprogramlı kontrolü hızlandırmaktır. Fetch kısmındaki iş yükünü azaltarak hızlanma sağlanmış olsa da hardwire ile karşılaştırıldığında mikroprogramlama yavaş kalmaktadır. Fakat mikroprogramlamanın da kendine özgü iyi tarafları vardır: kolay değiştirilebilme, hızlı uyum ve düşük maliyet gibi. Günümüzde maliyetten daha çok performans önemli olduğu için artık birçok bilgisayarda hardwire teknolojisi kullanılmaktadır.

**KAYNAKÇA**

1. Marek Tudruj, Polish Academy of Computer Science, https://edux.pjwstk.edu.pl/mat/264/lec/main75.html
2. Jian-Lun, Sheng. (2010). Researches on the technology of high performance microprogrammed control. 10.1109/ICEIT.2010.5608448.
3. G. B. Gerace, &quot;Microprogrammed Control for Computing Systems,&quot; in IEEE Transactions on Electronic Computers, vol. EC-12, no. 6, pp. 733-747, Dec. 1963, doi: 10.1109/PGEC.1963.263557.
4. John D. Roberts, J. Ihnat, and W. R. Smith. 1972. Microprogrammed control unit (MCU) programming reference manual. SIGMICRO Newsl. 3, 3 (October 1972), 18–57. DOI:https://doi.org/10.1145/1316540.1316544
5. ACM SIGCSE Bulletin,Volume 20,Issue 3 Sept. 1988 pp 13–22, https://doi.org/10.1145/51594.51598

