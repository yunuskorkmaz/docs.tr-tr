---
title: Hizmetten hizmete iletişim
description: Arka uç bulutu yerel mikro hizmetlerinin diğer arka uç mikro hizmetleriyle nasıl iletişim kuracağını öğrenin.
author: robvet
ms.date: 09/09/2019
ms.openlocfilehash: 7a69678fd38a69c3c2d7e91d4aea019c39141cb6
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184675"
---
# <a name="service-to-service-communication"></a>Hizmetten hizmete iletişim

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Ön uç istemcisinden geçiş yapmak için artık arka uç mikro hizmetleri birbirleriyle iletişim kuracak şekilde adresliyoruz.

Bulutta yerel bir uygulama oluştururken, arka uç hizmetlerinin birbirleriyle iletişim kurmasına karşı hassas olması gerekir. İdeal olarak, hizmet içi iletişim, daha iyi. Bununla birlikte, arka uç hizmetleri genellikle bir işlemi tamamlamaya yönelik bir diğerine bağımlı olduğu için engelleme her zaman mümkün değildir.

Çapraz hizmet iletişimini uygulamak için yaygın olarak kabul edilen birkaç yaklaşım vardır. *İletişim etkileşiminin türü* genellikle en iyi yaklaşımı saptacaktır.

Aşağıdaki etkileşim türlerini göz önünde bulundurun:

- *Sorgu* – çağıran bir mikro hizmet, "Hey, belirli bir müşteri kimliği için alıcı bilgilerini ver" gibi adlı bir mikro hizmetten yanıt gerektirdiğinde.

- *Komut* – çağıran mikro hizmet, bir eylemi yürütmek için başka bir mikro hizmete ihtiyaç duyar ancak "Hey, bu siparişi gönder" gibi bir yanıt gerektirmez.

- *Olay* – yayımcı olarak adlandırılan bir mikro hizmet, durumun değiştiği veya bir eylemin gerçekleştiği bir olay oluşturur. Abone olarak adlandırılan diğer mikro hizmetler olaya uygun şekilde tepki verebilir. Yayımcı ve aboneler birbirleriyle uyumlu değildir.

Mikro hizmet sistemleri, genellikle çapraz hizmet etkileşimi gerektiren işlemleri yürütürken bu etkileşim türlerinin bir birleşimini kullanır. Her birine ve bunları nasıl uygulayabileceğinizi yakından inceleyelim.

## <a name="queries"></a>Sorgular

Birçok kez, bir mikro hizmetin bir işlemi tamamlamaya yönelik acil bir yanıt gerektiren başka bir şekilde *sorgu* yapması gerekebilir. Bir alışveriş sepeti mikro hizmeti, ürün bilgileri ve sepetine bir öğe eklemek için bir fiyat gerekebilir. Sorgu işlemlerini uygulamak için birkaç yaklaşım vardır.

### <a name="requestresponse-messaging"></a>İstek/yanıt Iletisi

Bu senaryoyu uygulamaya yönelik bir seçenek, arama arka uç mikro hizmeti 'nin sorgu yapması gereken mikro hizmetlere doğrudan HTTP istekleri yapmasını sağlamak için Şekil 4-8 ' de gösterilmiştir.

![Doğrudan HTTP iletişimi](./media/direct-http-communication.png)

**Şekil 4-8**. Doğrudan HTTP iletişimi

Mikro hizmetler arasındaki doğrudan HTTP çağrılarının uygulanması nispeten basittir, ancak bu uygulamayı en aza indirmek için dikkatli olunmalıdır. Başlamak için, bu çağrılar her zaman *zaman uyumludur* ve bir sonuç döndürülene veya istek zaman aşımlarına kadar işlemi engeller. Bağımsız olarak, bağımsız hizmetler, bağımsız olarak gelişebilir ve sık sık dağıtımı yapabildikleri için, artık birbirleriyle birbirine bağlanmış hale gelmiştir. Mikro hizmetler arasında bir eşlenme artışı artdıkça, bunların mimari avantajları azalmaktadır.

Başka bir mikro hizmete tek bir doğrudan HTTP çağrısı yapan seyrek erişimli bir isteğin yürütülmesi bazı sistemler için kabul edilebilir durumda olabilir. Ancak, birden fazla mikro hizmete doğrudan HTTP çağrıları çağıran yüksek hacimli çağrılar önerilmez. Gecikme süresini artırabilir ve sisteminizin performansını, ölçeklenebilirliğini ve kullanılabilirliğini olumsuz yönde etkileyebilir. Daha da kötüleşirse, uzun bir doğrudan HTTP iletişimi dizisi, Şekil 4-9 ' de gösterilen, zaman uyumlu mikro hizmet çağrılarının derin ve karmaşık zincirlerine yol açabilir:

![HTTP sorgularını zincirleme](./media/chaining-http-queries.png)

**Şekil 4-9**. HTTP sorgularını zincirleme

Önceki görüntüde gösterilen tasarımda riski tamamen hayal edebilirsiniz. 3\. adım \#başarısız olursa ne olur? Ya da \#8. adım başarısız oldu mu? Nasıl kurtarılır? Temel alınan hizmet \#meşgul olduğu için 6. adım yavaşsa ne olur? Nasıl devam edersiniz? Tümü doğru çalışıyor olsa bile, her adımın gecikme süresinin toplamı olan bu çağrının tabi olacağı gecikmeyi düşünün.

Önceki görüntüde geçen büyük ölçüde, hizmetlerin en iyi modellenmedi. Bu, takımın tasarımını yeniden ziyaret behoove.

### <a name="materialized-view-pattern"></a>Gerçekleştirilmiş görünüm deseninin

Mikro hizmet bağlantısını kaldırmaya yönelik popüler bir seçenek [gerçekleştirilmiş görünüm](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)modelidir. Bu düzende, bir mikro hizmet, diğer hizmetlere ait kendi yerel, Normalleştirilmemiş verileri saklar. Ürün kataloğunu ve fiyatlandırma mikro hizmetlerini sorgulayan alışveriş sepeti mikro hizmeti yerine, bu verilerin kendi yerel kopyasını tutar. Bu kalıp gereksiz kuponu ortadan kaldırır ve güvenilirliği ve yanıt süresini geliştirir. Tüm işlem tek bir işlem içinde yürütülür. Bölüm 5 ' teki bu model ve diğer veri sorunlarını araştırıyoruz.

### <a name="service-aggregator-pattern"></a>Hizmet toplayıcı stili

Mikro hizmet-micrservice bağlantısını kaldırmaya yönelik başka bir seçenek de Şekil 4-10 ' de mor renkte gösterilen bir [toplayıcı mikro hizmetidir](https://devblogs.microsoft.com/cesardelatorre/designing-and-implementing-api-gateways-with-ocelot-in-a-microservices-and-container-based-architecture/). 

![Toplayıcı hizmeti](./media/aggregator-service.png)

**Şekil 4-10**. Toplayıcı mikro hizmeti

Bu model, birden fazla arka uç mikro hizmetine çağrı yapan ve mantığını özel bir mikro hizmet halinde sunan bir işlemi yalıtır.  Önceki şekildeki mor kullanıma alma toplayıcısı mikro hizmeti, kullanıma alma işlemi için iş akışını düzenler. Sıralı bir düzende birkaç arka uç mikro hizmet çağrısı içerir. İş akışındaki veriler toplanır ve çağırana döndürülür. Doğrudan HTTP çağrıları uyguladığından toplayıcı mikro hizmeti, arka uç mikro hizmetleri arasındaki doğrudan bağımlılıkları azaltır. 

### <a name="requestreply-pattern"></a>İstek/yanıt kalıbı

Zaman uyumlu HTTP iletilerini ayrışmaya yönelik başka bir yaklaşım, kuyruğa alma iletişimini kullanan bir [istek-yanıt Örünğidir](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RequestReply.html). Bir kuyruk kullanan iletişim, bir üretici tarafından iletiyi gönderen ve tüketiciye alan tek yönlü bir kanaldır. Bu düzende, Şekil 4-11 ' de gösterilen bir istek kuyruğu ve yanıt kuyruğu uygulanır.

![İstek-yanıt kalıbı](./media/request-reply-pattern.png)

**Şekil 4-11**. İstek-yanıt kalıbı

Burada ileti üreticisi, benzersiz bir bağıntı KIMLIĞI içeren sorgu tabanlı bir ileti oluşturur ve bunu bir istek kuyruğuna koyar. Tüketen hizmet iletileri kuyruktan kaldırır, işler ve yanıtı aynı bağıntı KIMLIĞI ile yanıt kuyruğuna koyar. Üretici hizmeti iletiyi kuyruktan kaldırır, bağıntı KIMLIĞIYLE eşleşmez ve işlemeye devam eder. Sonraki bölümde kuyrukları ayrıntılı olarak ele aldık.

## <a name="commands"></a>Komutlar

Başka bir iletişim etkileşimi türü bir *komuttur*. Bir mikro hizmetin bir eylemi gerçekleştirmesi için başka bir mikro hizmet gerekebilir. Sipariş mikro hizmeti, onaylanmış bir sipariş için bir sevkiyat oluşturmak üzere, gönderim mikro hizmeti 'ne ihtiyaç duyuyor olabilir. Şekil 4-12 ' de, üretici olarak adlandırılan bir mikro hizmet, başka bir mikro hizmet olan tüketiciye bir ileti gönderir ve bunu bir şey yapması için iletir. 

![Kuyrukla komut etkileşimi](./media/command-interaction-with-queue.png)

**Şekil 4-12**. Kuyrukla komut etkileşimi

Çoğu zaman, üretici bir yanıt gerektirmez ve iletiyi *başlatamaz ve unutabilirler* . Bir yanıt gerekiyorsa, tüketici başka bir kanalda üretici 'ya ayrı bir ileti gönderir. Bir komut iletisi en iyi şekilde bir ileti kuyruğu ile zaman uyumsuz olarak gönderilir. bir hafif ileti Aracısı tarafından desteklenir. Önceki diyagramda, bir sıranın her iki hizmeti nasıl ayırdığına ve bunların nasıl ayrılmış olduğuna ilişkin bir sıra.

İleti kuyruğu, bir üreticinin ve tüketicinin ileti iletgeçen bir ara yapısıdır. Kuyruklar, zaman uyumsuz, noktadan noktaya mesajlaşma düzenlerini uygular. Üretici bir komutun doğru bir şekilde gönderilmesi ve yönlendirilmesi gereken yerleri bilir. Sıra, bir iletinin, kanaldan okuyan tüketici örneklerinden tam olarak bir ileti ile işlenmesini güvence altına alır. Bu senaryoda, üretici veya tüketici hizmeti diğerini etkilemeden ölçeği değiştirebilir. Ayrıca, teknolojiler her bir tarafta farklı olabilir, yani bir [Golang](https://golang.org) mikro hizmeti çağıran bir Java mikro hizmeti olabilir. 

Bölüm 1 ' de, *yedekleme hizmetleri*hakkında konuşuyoruz. Yedekleme Hizmetleri, bulutta yerel sistemlerin bağımlı olduğu yardımcı kaynaklardır. İleti kuyrukları Hizmetleri yedekliyor. Azure bulutu, bulutta yerel sistemlerinizin komut iletilerini uygulamak için tüketebileceği iki tür ileti kuyruğu destekler: Azure depolama kuyrukları ve Azure Service Bus kuyrukları.

### <a name="azure-storage-queues"></a>Azure depolama kuyrukları

Azure depolama kuyrukları, hızlı, ekonomik ve Azure depolama hesapları tarafından desteklenen basit bir sıraya alma altyapısı sunar.

[Azure depolama kuyrukları](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction) , güvenilir ve kalıcı mesajlaşma ile REST tabanlı bir sıraya alma mekanizması özelliği. Bunlar en az bir özellik kümesi sağlar, ancak ucuzdur ve milyonlarca ileti depolar. Kapasite aralıkları 500 TB 'a kadar değişir. Tek bir ileti boyutu 64 KB 'ye kadar olabilir.

HTTP veya HTTPS kullanarak kimliği doğrulanmış çağrılar aracılığıyla dünyanın her yerinden iletilere erişebilirsiniz. Depolama kuyrukları, trafik artışlarını işlemek için çok sayıda eşzamanlı istemciye ölçeklenebilir.

Bu, hizmetle ilgili sınırlamalar vardır:

- İleti sırası garanti edilmez.

- İleti, otomatik olarak kaldırılmadan önce yedi gün boyunca devam edebilir.

- Durum yönetimi için destek, yinelenen algılama veya işlemler kullanılamıyor.

Şekil 4-13 ' de bir Azure depolama sırasının hiyerarşisi gösterilmektedir.

![Depolama kuyruğu hiyerarşisi](./media/storage-queue-hierarchy.png)

**Şekil 4-13**. Depolama kuyruğu hiyerarşisi

Önceki şekilde, depolama sıralarının iletilerini temel alınan Azure depolama hesabında nasıl depolamalarını aklınızda bir yere göz önüne alın.

Geliştiriciler için Microsoft, depolama kuyruğu işleme için birkaç istemci ve sunucu tarafı kitaplığı sağlar. .NET, Java, JavaScript, Ruby, Python ve go dahil çoğu büyük platform desteklenir. Geliştiriciler hiçbir şekilde doğrudan bu kitaplıklarla iletişim kurmamalıdır. Bunun yapılması, mikro hizmet kodunuzu Azure depolama Kuyruk hizmeti sıkı bir şekilde daha sıkı bir şekilde ister. API 'nin uygulama ayrıntılarını tahmin etmek daha iyi bir uygulamadır. Genel işlemleri sunan ve somut kitaplığı kapsülleyen bir intermediation katmanını veya ara API 'yi tanıtın. Bu gevşek bağlantısı, ana hat Hizmeti kodunda değişiklik yapmak zorunda kalmadan bir sıraya alma hizmetini başka bir sıraya takabilmenizi sağlar. 

Azure depolama kuyrukları, bulutta yerel uygulamalarınızda komut mesajlaşmasını uygulamak için ekonomik bir seçenektir. Özellikle bir sıra boyutu 80 GB 'ı aşacağından veya basit bir özellik kümesi kabul edilebilir. Yalnızca iletilerin depolanması için ödeme yaparsınız; Sabit saatlik ücret yoktur.

### <a name="azure-service-bus-queues"></a>Azure Service Bus kuyrukları

Daha karmaşık mesajlaşma gereksinimleri için Azure Service Bus kuyrukları göz önünde bulundurun.

Güvenilir bir ileti altyapısı [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) , *aracılı bir mesajlaşma modelini*destekler. İletiler, tüketici tarafından alınana kadar güvenilir bir şekilde bir aracıda (kuyruk) depolanır. Kuyruk, iletilerin kuyruğa eklenme sırasını önceden belirleyen Ilk/Ilk çıkar (FıFO) ileti teslimini garanti eder.

Bir iletinin boyutu, 256 KB 'a kadar çok daha büyük olabilir. İletiler kuyrukta sınırsız bir süre için kalıcıdır. Service Bus yalnızca HTTP tabanlı çağrıların değil, ayrıca [Ampq Protokolü](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-amqp-overview)için tam destek sağlar. AMPQ, bir ikili Protokolü ve daha yüksek düzeyde güvenilirliği destekleyen satıcılar genelinde açık bir standarttır.

Service Bus, [işlem desteği](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions) ve [yinelenen bir algılama özelliği](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection)de dahil olmak üzere zengin bir özellik kümesi sağlar. Kuyruk, ileti başına "en fazla bir kez teslimi" garantisi verir. Zaten gönderilen bir iletiyi otomatik olarak atar. Bir üretici şüpheli ise, aynı iletiyi yeniden gönderebilir ve Service Bus yalnızca tek bir kopyanın işleneceğini garanti eder. Yinelenen algılama, sizi ek altyapı sıhhi tesisat oluşturmak zorunda kalmaktan kurtarır.

Daha fazla kurumsal özellik bölümlendirme ve oturumlardır. Geleneksel Service Bus kuyruğu tek bir ileti Aracısı tarafından işlenir ve tek bir ileti deposunda depolanır. Ancak [Service Bus bölümleme](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) , kuyruğu birden çok ileti aracılarında ve ileti depolarında yayar. Genel aktarım hızı artık tek bir ileti aracısının veya mesajlaşma deposunun performansıyla sınırlı değildir. Bir mesajlaşma deposunun geçici bir kesinti, bölümlenmiş bir kuyruğu kullanılamaz olarak işlemez.

[Service Bus oturumlar](https://codingcanvas.com/azure-service-bus-sessions/) , gruplandırılmanız için bir yol sağlar. İletilerin birlikte işlenmesi ve işlemin sonunda tamamlanması gereken bir iş akışı senaryosu düşünün. Tüm avantajlardan yararlanmak için, oturum açık olarak Kuyruk için etkin olmalıdır ve ilgili her bir ileti aynı oturum KIMLIĞINI içermelidir.

Ancak bazı önemli uyarılar vardır: Service Bus kuyruğu boyutu 80 GB ile sınırlıdır ve bu, mağaza kuyruklarından kullanılabilir olandan çok daha küçüktür. Ayrıca, Service Bus kuyruklar bir temel maliyet ve işlem başına ücretlendirilir.

Şekil 4-14 Service Bus sırasının üst düzey mimarisini özetler.

![Service Bus kuyruğu](./media/service-bus-queue.png)

**Şekil 4-14**. Service Bus kuyruğu

Önceki şekilde, noktadan noktaya ilişkisini aklınızda yapın. Aynı sağlayıcının iki örneği iletileri tek bir Service Bus kuyruğuna sıraya ayırır. Her ileti, sağdaki üç tüketici örneğinin yalnızca biri tarafından kullanılır. Daha sonra, farklı tüketicilerin aynı iletiyle ilgilendiği mesajlaşmayı nasıl uygulayabileceğinizi anladık.

## <a name="events"></a>Olaylar

Message Queuing, bir üreticinin zaman uyumsuz olarak bir tüketici ileti gönderebildiği iletişim uygulamak için etkili bir yoldur. Ancak, aynı iletiyle *birçok farklı tüketici* ilgilendiğinde ne olur? Her tüketiciye yönelik adanmış bir ileti kuyruğu iyi ölçeklendirilmez ve yönetimi zor hale gelir. 

Bu senaryoyu ele almak için, üçüncü ileti etkileşim türüne ( *olay*) geçeceğiz. Bir mikro hizmet, bir eylemin oluştuğunu duyurur. Diğer mikro hizmetler, ilgileniyorsa eyleme veya olaya tepki verir. 

Olay iki adımlı bir işlemdir. Bir mikro hizmet, belirli bir durum değişikliği için ileti aracısına bir olay yayımlar ve bunu başka bir ilgilenen mikro hizmet tarafından kullanılabilir hale getirir. İleti aracısıdır olayına abone olunarak ilgilendiğimiz mikro hizmet bildirilir. [Olay tabanlı iletişim](https://docs.microsoft.com/dotnet/standard/microservices-architecture/multi-container-microservice-net-applications/integration-event-based-microservice-communications)uygulamak için [Yayımla/abone ol](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) ' a gidin.

Şekil 4-15 ' de, bir olay yayımlayan bir alışveriş sepeti mikro hizmeti, diğer iki mikro hizmetle abone olur.

![Olay odaklı mesajlaşma](./media/event-driven-messaging.png)

**Şekil 4-15**. Olay odaklı mesajlaşma

İletişim kanalının ortasında bulunan *olay veri yolu* bileşenini unutmayın. Bu, ileti Aracısı 'nı kapsülleyen ve temel alınan uygulamadan ayrışlayan özel bir sınıftır. Sıralama ve stok mikro hizmetleri, olayı birbirleriyle veya alışveriş sepeti mikro hizmeti olmadan bağımsız olarak çalışır. Kayıtlı olay, olay veri yoluna yayımlandığında, üzerinde işlem görür.

Olay ile, sıraya alma teknolojisinden *konulara*geçiş yaptık. Bir [Konu](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions) bir sıraya benzer, ancak bire çok mesajlaşma düzenlerini destekler. Bir mikro hizmet bir ileti yayımlar. Birden çok abone mikro hizmet, bu iletiyi almayı ve üzerinde işlem yapmak için seçim yapabilir. Şekil 4-16, bir konu mimarisini gösterir.

![Konu mimarisi](./media/topic-architecture.png)

**Şekil 4-16**. Konu mimarisi

Önceki şekilde, yayımcılar konuya iletiler gönderir. Son sırada aboneler aboneliklerden ileti alır. Ortasında, konu, koyu mavi kutular halinde gösterilen bir dizi *kurala*göre iletileri aboneliklere iletir. Kurallar, belirli iletileri bir aboneliğe ileten bir filtre işlevi görür. Burada, abonelik \#1 ve abonelik \#3 \#' e (abonelik 2 ' ye değil) bir "CreateOrder" olayı gönderilebilir. Abonelik \#2 ve abonelik \#3 ' e bir "ordercompleted" olayı gönderilebilir.

Azure bulutu iki farklı konu hizmetini destekler: Azure Service Bus konuları ve Azure EventGrid.

### <a name="azure-service-bus-topics"></a>Azure Service Bus konuları

Aynı güçlü aracılı ileti modelinin en üstünde oturur Azure Service Bus kuyrukları [Azure Service Bus konulardır](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Bir konu, birden fazla bağımsız yayımcıların iletilerini alabilir ve en fazla 2.000 aboneye ileti gönderebilir. Abonelikler, sistemi durdurmadan veya konu başlığı oluşturmadan dinamik olarak çalışma zamanında eklenebilir veya kaldırılabilir.

Azure Service Bus kuyruklardan birçok gelişmiş özellik, [yinelenen algılama](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection) ve [işlem desteği](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions)dahil olmak üzere konular için de kullanılabilir. Varsayılan olarak, Service Bus konular tek bir ileti Aracısı tarafından işlenir ve tek bir ileti deposunda depolanır. Ancak [Service Bus bölümlendirme](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) , bir konuyu birçok ileti aracılarına ve ileti depolarına yayarak ölçeklendirir.

[Zamanlanan Ileti teslimi](https://docs.microsoft.com/azure/service-bus-messaging/message-sequencing) , işlenmek üzere belirli bir zamana sahip bir iletiyi etiketleyen bir ileti. İleti, ilgili zamandan önceki konu başlığında görünmez. [Ileti erteleme](https://docs.microsoft.com/azure/service-bus-messaging/message-deferral) , bir iletinin daha sonra bir kez alınmasını ertelemenize olanak sağlar. Her ikisi de genellikle işlemlerin belirli bir sırada işlendiği iş akışı işleme senaryolarında kullanılır. Önceki iş tamamlanana kadar alınan iletilerin işlenmesini erteleyebilirsiniz.

Service Bus konular, bulutta yerel sistemlerinizde yayımlama/abone olma iletişimini etkinleştirmeye yönelik sağlam ve kanıtlanmış bir teknolojidir.

### <a name="azure-event-grid"></a>Azure Event Grid

Azure Service Bus, bir çift kurumsal özellikler kümesiyle test edilmiş bir mesajlaşma Aracısı olsa da, bloktaki yeni çocuk [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) .

İlk bakışta Event Grid yalnızca başka bir konu tabanlı mesajlaşma sistemine benzeyebilir. Ancak, bu birçok şekilde farklıdır. Olay odaklı iş yüklerine odaklandığı için, gerçek zamanlı olay işleme, derin Azure tümleştirmesi ve bir açık platform olan, sunucusuz altyapıda daha az bir altyapı sunar. Modern bulutla yerel ve sunucusuz uygulamalar için tasarlanmıştır

Merkezi bir *olay biriktirme düzeyi*veya kanal olarak Event Grid Azure kaynakları içindeki olaylara ve kendi hizmetlerinize yeniden işlem yapar.

Olay bildirimleri, her olayı bir aboneliğe yönlendiren bir Event Grid konuya yayımlanır. Aboneler aboneliklerle eşlenir ve olayları tüketir. Service Bus gibi, Event Grid, bir aboneliğin alması istediği olaylar için kural ayarlayan *filtrelenmiş bir abone modelini* destekler. Event Grid, yaklaşık gerçek zamanlı teslimin en fazla Azure Service Bus oluşturabileceği kadar çok daha fazlasını sağlayan, saniyede 10.000.000 olay garantisi sağlar.

Event Grid SWE, Azure altyapısının dokusuna yönelik derin tümleştirmedir. Cosmos DB gibi bir Azure kaynağı, yerleşik olayları özel koda gerek duymadan doğrudan diğer Azure kaynaklarına yayımlayabilirler. Event Grid, bir Azure aboneliğinden, kaynak grubundan veya hizmetten olay yayımlayabilir, geliştiricilerin bulut kaynakları yaşam döngüsü üzerinde ayrıntılı denetim sağlayabilir. Ancak Event Grid Azure ile sınırlı değildir. Bu, uygulamalardan veya üçüncü taraf hizmetlerden yayınlanan özel HTTP olaylarını kullanabilen ve olayları dış abonelere yönlendiren açık bir platformdur.

Azure kaynaklarından yerel olayları yayımlarken ve abone olurken, kodlama gerekmez. Basit yapılandırma sayesinde, bir Azure kaynağından olayları, konular ve abonelikler için yerleşik bir tesisten yararlanarak tümleştirebilirsiniz. Şekil 4-17 Event Grid ' nin anatommumu gösterir.

![Event Grid anatomi](./media/event-grid-anatomy.png)

**Şekil 4-17**. Event Grid anatomi

EventGrid ve Service Bus arasındaki önemli bir fark, temeldeki *ileti değişim*modelidir.

Service Bus, aşağı akış abonenin yeni iletiler için konu aboneliğini etkin bir şekilde yokladığı eski bir stil *çekme modeli* uygular. Bu yaklaşım, en sonunda aboneye iletileri işleyen hızda abone tam denetim sağlar. Bu, belirli bir zamanda ne zaman ve kaç mesaj işleyeceğini denetler. Okunmamış iletiler, işlenene kadar abonelikte kalır. Önemli bir Short, olayın oluşturulduğu zaman ve bu iletiyi işlenmek üzere abone 'e çeken yoklama işlemi arasındaki gecikmedir. Ayrıca, sonraki olay için sabit yoklamanın ek yükü kaynakları ve paradan tüketir.

Ancak EventGrid farklı. Olayların EventHandlers gönderildiği şekilde gönderildiği ve gerçek zamanlı olay teslimi sağlayan bir *anında iletme modeli* uygular. Hizmetin yalnızca bir olayı tüketmesi gerektiğinde tetiklendiği ve sürekli olarak yoklama ile olduğu gibi, maliyeti de düşürür. Bu şekilde, bir olay işleyicisinin gelen yükü işlemesi ve kendisini korumak için azaltma mekanizmaları sağlaması gerekir. Azure Işlevleri ve Logic Apps gibi bu olayları kullanan pek çok Azure hizmeti, daha fazla yükü işlemek için otomatik otomatik ölçeklendirme özellikleri sağlar.  

Event Grid, tam olarak yönetilen bir sunucusuz bulut hizmetidir. Bu, trafiğinizi temel alarak dinamik olarak ölçeklendirin ve yalnızca gerçek kullanımınız için ücretlendirilirken, önceden satın alınmış kapasiteye değil, size Ayda ilk 100.000 işlem ücretsiz – olay girişi (gelen olay bildirimleri), abonelik teslim denemeleri, yönetim çağrıları ve konuya göre filtreleme olarak tanımlanmakta olan operasyonlardır. % 99,99 kullanılabilirlik ile EventGrid, başarısız teslimat için yerleşik yeniden deneme işlevselliği ile, bir olayın 24 saatlik bir süre içinde teslimini garanti eder. Teslim edilmemiş iletiler, çözüm için "atılacak mektup" kuyruğuna taşınabilir.  Azure Service Bus farklı olarak, Event Grid hızlı performans için ayarlanmıştır ve sıralı mesajlaşma, işlemler ve oturumlar gibi özellikleri desteklemez.

### <a name="streaming-messages-in-the-azure-cloud"></a>Azure bulutu 'nda akış iletileri

Azure Service Bus ve Event Grid, bir Cosmos DB 'e eklenen yeni bir belge gibi tek ve ayrı olaylar sunan uygulamalar için harika destek sağlar. Ancak, bulutta yerel sisteminizin *ilgili olayların akışını*işlemesi gerekiyorsa ne olacak? [Olay akışları](https://msdn.microsoft.com/magazine/dn904671.aspx?f=255&MSPPError=-2147217396) daha karmaşıktır. Bunlar genellikle birbirleriyle sıralanmıştır ve bir grup olarak işlenmelidir.

[Azure Olay Hub](https://azure.microsoft.com/services/event-hubs/) 'ı, olayları toplayan, dönüştüren ve depolayan bir veri akışı platformu ve olay alma hizmetidir. Bir telemetri bağlamından yayılan sürekli olay bildirimleri gibi akış verilerini yakalamak için ince ayar yapılır. Hizmet yüksek oranda ölçeklenebilir ve [saniye başına milyonlarca olayı depolayıp işleyebilir](https://docs.microsoft.com/azure/event-hubs/event-hubs-about). Şekil 4-18 ' de gösterildiği gibi, genellikle olay işlem hattının bir ön kapıdır ve olay tüketimine ait alma akışını ayırır.

![Azure Olay Hub'ı](./media/azure-event-hub.png)

**Şekil 4-18**. Azure Olay Hub'ı

Olay Hub 'ı, düşük gecikme süresini ve yapılandırılabilir zaman bekletmesini destekler. Kuyrukların ve konuların aksine, bir tüketici tarafından okunduktan sonra olay verilerini saklayın Event Hubs. Bu özellik, iç ve dış diğer veri analizi hizmetlerinin, daha fazla analiz için verileri yeniden oynamalarını sağlar. Olay Hub 'ında depolanan olaylar yalnızca, varsayılan olarak bir gün olan ancak yapılandırılabilir olan bekletme döneminin süresi dolduktan sonra silinir.

Olay Hub 'ı, HTTPS ve AMQP dahil olmak üzere ortak olay yayımlama protokollerini destekler. Ayrıca Kafka 1,0 de desteklenir. Mevcut Kafka uygulamaları, büyük Kafka kümelerinin yönetilmesine alternatif sağlayan Kafka protokolünü kullanarak [Olay Hub 'ı ile iletişim](https://docs.microsoft.com/azure/event-hubs/event-hubs-for-kafka-ecosystem-overview) kurabilir. Birçok açık kaynaklı bulut Yerel sistemi emayraç Kafka.

Event Hubs, her tüketicinin ileti akışının yalnızca belirli bir alt kümesini veya bölümünü okuduğu [bölümlenmiş bir tüketici modeli](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) aracılığıyla ileti akışı uygular. Bu düzende olay işleme için inanılmaz yatay ölçek etkinleştirilir ve sıralarda ve konularda kullanılamayan diğer akışa odaklanmış özellikler sağlanır. Bölüm bir olay hub'ında tutulan olayların sıralı dizisidir. Daha yeni olaylar geldikçe, bu sıranın sonuna eklenir. Şekil 4-19 bir olay hub 'ında Bölümlendirmeyi gösterir.

![Olay Hub 'ı bölümlendirme](./media/event-hub-partitioning.png)

**Şekil 4-19**. Olay Hub 'ı bölümlendirme

Aynı kaynaktan okumak yerine, her tüketici grubu ileti akışının bir alt kümesi veya bölümü üzerinde okur. 

Çok sayıda olayı akışı gereken bulutta yerel uygulamalar için, Azure Olay Hub 'ı sağlam ve uygun maliyetli bir çözüm olabilir.

>[!div class="step-by-step"]
>[Önceki](front-end-communication.md)
>[İleri](rest-grpc.md) <!-- Next Chapter -->
