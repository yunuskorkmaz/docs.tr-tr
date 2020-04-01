---
title: Servise servis iletişimi
description: Arka uç bulut yerel mikro hizmetlerin diğer arka uç mikro hizmetlerle nasıl iletişim kurduğunu öğrenin.
author: robvet
ms.date: 09/09/2019
ms.openlocfilehash: 926be3c2eb4513c89ebcd1f31dceb7d58639dc6f
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523558"
---
# <a name="service-to-service-communication"></a>Servise servis iletişimi

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Ön uç istemciden hareket lediğimizde, artık arka uçtaki mikro servislerin birbirleriyle iletişim kurmasına değiniyoruz.

Bulut açi tabanlı bir uygulama yaparken, arka uç hizmetlerin birbiriyle nasıl iletişim kurduğukonusunda duyarlı olmak istersiniz. İdeal olarak, daha az hizmet arası iletişim, daha iyi. Ancak, arka uç hizmetleri genellikle bir işlemi tamamlamak için birbirlerine güvendiğinden kaçınma her zaman mümkün değildir.

Hizmet ler arası iletişimi uygulamak için yaygın olarak kabul görmüş birçok yaklaşım vardır. *İletişim etkileşimi türü* genellikle en iyi yaklaşımı belirleyecektir.

Aşağıdaki etkileşim türlerini göz önünde bulundurun:

- *Sorgu* – bir arama microservice gibi bir microservice bir yanıt gerektirir, gibi, "Hey, bana belirli bir müşteri Kimliği için alıcı bilgilerini verin."

- *Komut* – arama microservice bir eylem yürütmek için başka bir microservice ihtiyacı ama bir yanıt gerektirmez, gibi, "Hey, sadece bu sipariş gemi."

- *Olay* – yayımcı adı verilen bir mikro hizmet, durum değişti veya bir eylem oluştu bir olay yükseltir. İlgilenen aboneler olarak adlandırılan diğer mikro hizmetler, olaya uygun şekilde tepki verebilir. Yayıncı ve aboneler birbirlerinden haberdar değil.

Microservice sistemleri genellikle çapraz hizmet etkileşimi gerektiren işlemleri yürütürken bu etkileşim türlerinin bir birleşimini kullanır. Her biri ve bunları nasıl uygulayabileceğinizi yakından inceleyelim.

## <a name="queries"></a>Sorgular

Çoğu zaman, bir microservice bir işlemi tamamlamak için hemen yanıt gerektiren, başka bir *sorgu* gerekebilir. Bir alışveriş sepeti microservice ürün bilgileri ve sepetine bir öğe eklemek için bir fiyat gerekebilir. Sorgu işlemlerini uygulamak için bir dizi yaklaşım vardır.

### <a name="requestresponse-messaging"></a>İstek/Yanıt Mesajlaşması

Bu senaryoyu uygulamak için bir seçenek, arama arka uç mikro hizmetinin, Şekil 4-8'de gösterilen sorgulaması gereken mikro hizmetlere doğrudan HTTP isteklerini yapmasıdır.

![Doğrudan HTTP iletişimi](./media/direct-http-communication.png)

**Şekil 4-8**. Doğrudan HTTP iletişimi

Mikro hizmetler arasındaki doğrudan HTTP çağrılarının uygulanması nispeten basit olmakla birlikte, bu uygulamayı en aza indirmek için dikkatli olunmalıdır. Başlamak için, bu aramalar her zaman *eşzamanlıdır* ve bir sonuç döndürülene veya istek süreleri çıkana kadar işlemi engeller. Bir zamanlar bağımsız olarak evrimleşebilen ve sık sık konuşlandırılabilen bağımsız hizmetler, artık birbiriyle birleşti. Mikro hizmetler arasındaki bağlantı arttıkça mimari faydaları da azalır.

Başka bir microservice için tek bir doğrudan HTTP arama yapar seyrek bir istek yürütme bazı sistemler için kabul edilebilir olabilir. Ancak, birden çok mikro hizmete doğrudan HTTP çağrıları çağıran yüksek hacimli aramalar tavsiye edilmez. Gecikme yi artırabilir ve sisteminizin performansını, ölçeklenebilirliğini ve kullanılabilirliğini olumsuz etkileyebilir. Daha da kötüsü, doğrudan HTTP iletişim uzun bir dizi senkron mikrohizmetler aramaları derin ve karmaşık zincirleri yol açabilir, Şekil 4-9 gösterilen:

![HTTP sorgularını zincirleme](./media/chaining-http-queries.png)

**Şekil 4-9**. HTTP sorgularını zincirleme

Bir önceki resimde gösterilen tasarımdaki riski kesinlikle hayal edebilirsiniz. Adım \#3 başarısız olursa ne olur? Ya \#da Adım 8 başarısız oldu mu? Nasıl iyileşirsin? Temel hizmet \#meşgul olduğu için Adım 6 yavaşsa ne olur? Nasıl devam ediyorsun? Tüm doğru çalışsa bile, bu çağrının neden olacağı gecikmeyi düşünün, bu da her adımın gecikme sinin toplamıdır.

Önceki resimdeki büyük bağlantı derecesi, hizmetlerin en iyi şekilde modellenmediğini göstermektedir. Ekibin tasarımlarını tekrar gözden geçirmesi gerekir.

### <a name="materialized-view-pattern"></a>Gerçekleştirilmiş Görünüm düzeni

Mikro hizmet bağlantısını kaldırmak için popüler bir seçenek [Maddeleştirilmiş Görünüm desenidir.](https://docs.microsoft.com/azure/architecture/patterns/materialized-view) Bu desenle, bir microservice diğer hizmetlere ait olan verilerin kendi yerel, denormalize kopyasını depolar. Ürün Kataloğu ve Fiyatlandırma mikrohizmetlerini sorgulayan Alışveriş Sepeti microservice yerine, bu verilerin kendi yerel kopyasını korur. Bu desen gereksiz bağlantı ortadan kaldırır ve güvenilirlik ve yanıt süresini artırır. Tüm işlem tek bir işlem içinde yürütülür. Bu deseni ve diğer veri endişelerini Bölüm 5'te inceliyoruz.

### <a name="service-aggregator-pattern"></a>Hizmet Toplayıcı Deseni

Mikrohizmet-mikrohizmet bağlantı ortadan kaldırmak için başka bir seçenek bir [Toplayıcı microservice](https://devblogs.microsoft.com/cesardelatorre/designing-and-implementing-api-gateways-with-ocelot-in-a-microservices-and-container-based-architecture/), Şekil 4-10 mor gösterilir.

![Toplayıcı hizmeti](./media/aggregator-service.png)

**Şekil 4-10**. Toplayıcı mikroservice

Desen, birden çok arka uç mikro hizmeti çağıran bir işlemi yalıtır ve mantığını özel bir mikro hizmete merkezileştirerek.  Önceki figürdeki mor ödeme toplayıcı mikrohizmeti, Ödeme işlemi için iş akışını yönetir. Sıralı bir sırada birkaç arka uç mikro hizmetine yapılan çağrıları içerir. İş akışından elde edilen veriler toplanır ve arayana döndürülür. Hala doğrudan HTTP çağrıları uygular iken, toplayıcı microservice arka uç mikro hizmetler arasında doğrudan bağımlılıkları azaltır.

### <a name="requestreply-pattern"></a>İstek/Yanıt Deseni

Senkron HTTP iletilerini ayrıştırmak için başka bir yaklaşım, sıraya alma iletişimini kullanan Bir [İstek-Yanıt Deseni'dir.](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RequestReply.html) Sıra yı kullanan iletişim her zaman tek yönlü bir kanaldır ve bir üretici ileiletiyi gönderir ve tüketici mesajı alır. Bu desenle, Şekil 4-11'de gösterilen hem istek sırası hem de yanıt sırası uygulanır.

![İstek-yanıt deseni](./media/request-reply-pattern.png)

**Şekil 4-11**. İstek-yanıt deseni

Burada, ileti oluşturici benzersiz bir korelasyon kimliği içeren sorgu tabanlı bir ileti oluşturur ve bunu istek kuyruğuna yerleştirir. Tüketen hizmet iletileri sıradan ayırıyor, işler ve yanıtı aynı korelasyon kimliğiyle yanıt kuyruğuna yerleştirir. Üretici hizmeti iletiyi sıradan ayırıyor, korelasyon kimliğiyle eşleşiyor ve işleme devam ediyor. Bir sonraki bölümde kuyrukları ayrıntılı olarak ele alıyoruz.

## <a name="commands"></a>Komutlar

İletişim etkileşiminin bir diğer türü de *komutdur.* Bir microservice bir eylem gerçekleştirmek için başka bir microservice gerekebilir. Sipariş microservice onaylı bir sipariş için bir sevkiyat oluşturmak için Nakliye microservice gerekebilir. Şekil 4-12'de, Üretici adı verilen bir microservice, başka bir microservice,Tüketiciye bir mesaj gönderir ve bir şeyler yapmasını emreder.

![Sırayla komut etkileşimi](./media/command-interaction-with-queue.png)

**Şekil 4-12**. Sırayla komut etkileşimi

Çoğu zaman, Üretici bir yanıt gerektirmez ve mesajı *ateşleyebilir ve unutabilir.* Yanıt gerekirse, Tüketici başka bir kanalda Üretici'ye ayrı bir ileti gönderir. Komut iletisi en iyi ileti sırası ile eşzamanlı olarak gönderilir. hafif bir mesaj aracısı tarafından desteklenir. Önceki diyagramda, bir sıranın her iki hizmeti nasıl ayırdığını ve ayırdığını unutmayın.

İleti sırası, üretici ve tüketicinin bir iletiyi iletdiği bir aracı yapıdır. Kuyruklar, noktadan noktaya ileti deseni uygular. Üretici, bir komutun nereye gönderilmesi gerektiğini bilir ve uygun şekilde yönlendirir. Kuyruk, bir iletinin kanaldan okunan tüketici örneklerinden biri tarafından işlenmesini garanti eder. Bu senaryoda, üretici veya tüketici hizmeti diğerini etkilemeden ölçeklenebilir. Yanı sıra, teknolojiler her iki tarafta farklı olabilir, bir Java microservice bir [Golang](https://golang.org) microservice çağıran olabilir anlamına gelir.

Bölüm 1'de, *hizmetleri desteklemekten*bahsettik. Destek hizmetleri, bulut açi sistemlerinin bağlı olduğu yardımcı kaynaklardır. İleti kuyrukları hizmetleri destekler. Azure bulutu, bulut tabanlı sistemlerinizin komut iletisi uygulamak için tüketebileceği iki tür ileti kuyruğunu destekler: Azure Depolama Kuyrukları ve Azure Hizmet Veri Sırası.

### <a name="azure-storage-queues"></a>Azure Depolama Kuyrukları

Azure depolama kuyrukları, hızlı, uygun fiyatlı ve Azure depolama hesapları tarafından desteklenen basit bir kuyruk altyapısı sunar.

[Azure Depolama Kuyrukları,](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction) güvenilir ve kalıcı iletiiçeren REST tabanlı bir kuyruk mekanizmasına sahiptir. Bunlar en az özellik kümesi sağlar, ancak ucuzdur ve milyonlarca ileti depolar. Kapasiteleri 500 TB'ye kadar değişmektedir. Tek bir ileti 64 KB boyutuna kadar olabilir.

Http veya HTTPS kullanarak kimlik doğrulaması yapılan aramalar aracılığıyla dünyanın her yerinden mesajlara erişebilirsiniz. Depolama kuyrukları, trafik artışlarını işlemek için çok sayıda eşzamanlı istemciye ölçeklenebilir.

Bununla birlikte, hizmetle ilgili sınırlamalar vardır:

- İleti siparişi garanti değildir.

- İleti otomatik olarak kaldırılmadan önce yalnızca yedi gün süreyle devam edebilir.

- Devlet yönetimi, yinelenen algılama veya hareketler için destek kullanılamıyor.

Şekil 4-13, Azure Depolama Kuyruğu'nun hiyerarşisini gösterir.

![Depolama sırası hiyerarşisi](./media/storage-queue-hierarchy.png)

**Şekil 4-13**. Depolama sırası hiyerarşisi

Önceki şekilde, depolama kuyruklarının iletilerini temel Azure Depolama hesabında nasıl depolatadığını unutmayın.

Geliştiriciler için Microsoft, Depolama sıra işleme için birkaç istemci ve sunucu tarafı kitaplıkları sağlar. .NET, Java, JavaScript, Ruby, Python ve Go dahil olmak üzere en önemli platformlar desteklenir. Geliştiriciler bu kitaplıklarla asla doğrudan iletişim kurmamalıdır. Bunu yapmak, mikro hizmet kodunuzu Azure Depolama Sırası hizmetiyle sıkı bir şekilde biraraya getirecektir. API'nin uygulama ayrıntılarını yalıtmak daha iyi bir uygulamadır. Genel işlemleri ortaya çıkaran ve beton kitaplığı kapsülleyen bir ara bağlantı katmanı veya ara API tanıtın. Bu gevşek bağlantı, ana hat hizmet kodunda değişiklik yapmak zorunda kalmadan bir kuyruk hizmetini başka bir hizmetle değiştirmenizi sağlar.

Azure Depolama kuyrukları, bulut tası uygulamalarınızda komut iletisi uygulamak için ekonomik bir seçenektir. Özellikle bir kuyruk boyutu 80 GB'ı aşacaksa veya basit bir özellik kümesi kabul edilebilirse. Yalnızca iletilerin depolanması için ödeme yapıyorsun; sabit saatlik ücret yoktur.

### <a name="azure-service-bus-queues"></a>Azure Service Bus Kuyrukları

Daha karmaşık ileti gereksinimleri için Azure Servis Veri Servisi sıralarını göz önünde bulundurun.

Sağlam bir ileti altyapısının üzerinde oturan [Azure Servis Veri Servisi,](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) aracılı bir *mesajlaşma modelini*destekler. İletiler, tüketici tarafından alınana kadar bir brokerda (kuyrukta) güvenilir bir şekilde depolanır. Kuyruk, iletilerin sıraya eklenme sırasına göre İlk Giren/İlk Çıkış (FIFO) ileti teslimini garanti eder.

İletinin boyutu 256 KB'ye kadar çok daha büyük olabilir. İletiler sınırsız bir süre için kuyrukta kalıcıdır. Servis Veri Servisi yalnızca HTTP tabanlı aramaları desteklemekle kalmıyor, aynı zamanda [AMPQ protokolü](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-amqp-overview)için tam destek de sağlar. AMPQ, ikili protokolü ve daha yüksek güvenilirlik derecelerini destekleyen satıcılar arasında açık standarttır.

Service Bus, [işlem desteği](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions) ve yinelenen algılama [özelliği](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection)de dahil olmak üzere zengin bir özellik kümesi sağlar. Sıra, ileti başına "en fazla bir kez teslimat" garantisi vetir. Önceden gönderilmiş bir iletiyi otomatik olarak atar. Bir üreticinin şüphesi varsa, aynı iletiyi yeniden gönderebilir ve Servis Veri Servisi yalnızca bir kopyanın işlenmesini garanti eder. Yinelenen algılama, ek altyapı tesisatı oluşturmak zorunda kalmanızı sağlar.

İki kurumsal özellik daha bölümleme ve oturumlar vardır. Geleneksel Bir Hizmet Veri Servisi sırası tek bir ileti aracısı tarafından işlenir ve tek bir ileti deposunda depolanır. Ancak, [Servis Veri Servisi Bölümleme](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) birden çok ileti aracısı ve ileti mağazaları arasında kuyruk yayılır. Genel iş ortası artık tek bir ileti aracıcısının veya mesajlaşma mağazasının performansıyla sınırlı değildir. İleti deposunun geçici kesintisi, bölümlenmiş bir sırayı kullanılamaz hale getirmez.

[Servis Veri Yolu Oturumları,](https://codingcanvas.com/azure-service-bus-sessions/) grupla ilgili iletilere giden bir yol sağlar. İletilerin birlikte işlenmesi ve işlemin sonunda tamamlanması gereken bir iş akışı senaryosu düşünün. Bu avantajdan yararlanmak için, sıra için oturumların açıkça etkinleştirilmesi ve ilgili iletilerin her birinin aynı oturum kimliğini içermesi gerekir.

Ancak, bazı önemli uyarılar vardır: Servis Veri Servisi kuyrukları boyutu 80 GB ile sınırlıdır ve bu da mağaza kuyruklarında mevcut olandan çok daha küçüktür. Ayrıca, Servis Veri Servisi kuyrukları işlem başına temel maliyet ve ücrete tabidir.

Şekil 4-14, Servis Veri Servisi kuyruğunun üst düzey mimarisini özetlemektedir.

![Service Bus kuyruğu](./media/service-bus-queue.png)

**Şekil 4-14**. Service Bus kuyruğu

Önceki şekilde, noktadan noktaya ilişkiye dikkat edin. Aynı sağlayıcının iki örneği, iletileri tek bir Hizmet Veri Günü kuyruğuna sıralıyor. Her ileti, sağdaki üç tüketici örneğinden yalnızca biri tarafından tüketilir. Daha sonra, farklı tüketicilerin aynı mesajın ilginizi çekebileceği mesajlaşmanın nasıl uygulanacağını tartışıyoruz.

## <a name="events"></a>Olaylar

İleti sıraya bir üretici eşsenkronize bir tüketici bir mesaj gönderebilirsiniz iletişim uygulamak için etkili bir yoldur. Ancak, birçok *farklı tüketici* aynı mesajla ilgilendiğinde ne olur? Her tüketici için özel bir ileti sırası iyi ölçek olmaz ve yönetmek zor olur.

Bu senaryoyu ele almak için, üçüncü ileti etkileşimi türüne, *olaya*geçiyoruz. Bir microservice bir eylem meydana geldiğini duyurdu. Diğer mikro hizmetler, eğer ilgileniyorsa, eyleme veya olaya tepki verir.

Olay iki adımlı bir işlemdir. Belirli bir durum değişikliği için, bir microservice bir ileti aracısına bir olay yayınlar ve bu da olayı diğer ilgili microservice'ler için kullanılabilir hale getirir. İlgili microservice mesaj komisyoncusu olay abone tarafından bildirilir. [Olay tabanlı iletişimi](https://docs.microsoft.com/dotnet/standard/microservices-architecture/multi-container-microservice-net-applications/integration-event-based-microservice-communications)uygulamak için [Yayımla/Abone Ol](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) modelini kullanırsınız.

Şekil 4-15 bir alışveriş sepeti microservice diğer iki mikro hizmetler abone bir olay yayın gösterir.

![Olay Odaklı mesajlaşma](./media/event-driven-messaging.png)

**Şekil 4-15**. Olay Odaklı mesajlaşma

İletişim kanalının ortasında bulunan *olay veri yolunda* bileşene dikkat edin. İleti aracısını kapsülleyen ve temel uygulamadan ayıran özel bir sınıf. Sipariş ve envanter mikrohizmetleri, ne birbirlerinden hiçbir bilgi olmadan ne de alışveriş sepeti microservice olmadan olay bağımsız olarak çalışır. Kayıtlı olay olay otobüsüne yayınlandığında, buna göre hareket ederler.

Eventing ile, biz *konulara*kuyruk teknolojisi hareket . [Bir konu](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions) kuyruğa benzer, ancak bir-çok ileti deseni destekler. Bir microservice bir ileti yayımlar. Birden fazla abone mikro hizmetleri almak ve bu ileti üzerine hareket seçebilirsiniz. Şekil 4-16 bir konu mimarisini gösterir.

![Konu mimarisi](./media/topic-architecture.png)

**Şekil 4-16**. Konu mimarisi

Önceki şekilde, yayıncılar konuya ileti gönderir. Sonunda, aboneler aboneliklerden ileti alır. Ortada, konu iletileri koyu mavi kutularda gösterilen bir dizi *kurala*göre aboneliklere iletilir. Kurallar, belirli iletileri aboneye ileden bir filtre görevi görede dir. Burada, Bir "CreateOrder" etkinliği Abonelik \#1 \#ve Abonelik 3'e gönderilir, ancak Abonelik \#2'ye gönderilmez. Abonelik 2 ve Abonelik \# \#3'e bir "Sipariş Tamamlandı" etkinliği gönderilir.

Azure bulutu iki farklı konu hizmetini destekler: Azure Hizmet Veri Veri Günü Konuları ve Azure EventGrid.

### <a name="azure-service-bus-topics"></a>Azure Service Bus Konuları

Azure Hizmet Veri Servisi Veri Hizmetleri kuyruklarının aynı sağlam aracılı ileti modelinin üzerinde oturan [Azure Hizmet Veri Meskeni Konularıdır.](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions) Bir konu birden çok bağımsız yayımcıdan ileti alabilir ve en fazla 2.000 aboneye ileti gönderebilir. Abonelikler, sistemi durdurmadan veya konuyu yeniden oluşturmadan çalışma zamanında dinamik olarak eklenebilir veya kaldırılabilir.

[Yinelenen Algılama](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection) ve [İşlem desteği](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions)de dahil olmak üzere konular için Azure Servis Veri Servisi veri hizmeti kuyruklarından birçok gelişmiş özellik de mevcuttur. Varsayılan olarak, Hizmet Veri Mes'i konuları tek bir ileti aracısı tarafından işlenir ve tek bir ileti deposunda depolanır. Ancak, [Servis Veri Hizmetleri Bölümleme](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) birçok mesaj broker ve mesaj mağazaları arasında yayArak bir konu ölçekler.

[Zamanlanmış İleti Teslimi,](https://docs.microsoft.com/azure/service-bus-messaging/message-sequencing) işleme için belirli bir zamanı olan bir iletiyi etiketler. İleti bu tarihten önce konuiçinde görünmez. [İleti Erteleme,](https://docs.microsoft.com/azure/service-bus-messaging/message-deferral) iletinin alınmasını daha sonraki bir zamana ertelemenizi sağlar. Her ikisi de, işlemlerin belirli bir sırada işlendiği iş akışı işleme senaryolarında yaygın olarak kullanılır. Alınan iletilerin işlenmesini önceki çalışma tamamlanana kadar erteleyebilirsiniz.

Servis Veri Mes'i konuları, bulut tabanlı sistemlerinizde yayın/abone iletişimi etkinleştirmek için sağlam ve kanıtlanmış bir teknolojidir.

### <a name="azure-event-grid"></a>Azure Event Grid

Azure Hizmet Veri Yolu, tam kurumsal özelliklere sahip savaş testine tabi bir mesajlaşma aracısı olsa da, [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) bloktaki yeni çocuktur.

İlk bakışta, Olay Izgara sadece başka bir konu tabanlı mesajlaşma sistemi gibi görünebilir. Ancak, birçok yönden farklı. Olay odaklı iş yüklerine odaklanan bu proje, gerçek zamanlı etkinlik işleme, derin Azure tümleştirmesi ve sunucusuz altyapıda açık bir platform sağlar. Çağdaş bulut tabanlı ve sunucusuz uygulamalar için tasarlanmıştır

Merkezi bir *olay arka düzlemi*veya boş tabiri olarak, Olay Grid Azure kaynakları içindeki ve kendi hizmetlerinizdeki olaylara tepki verir.

Olay bildirimleri, sırayla her olayı bir aboneye yönlendirir bir Olay Izgara Konusu'nda yayınlanır. Aboneler aboneliklerin haritasını çıkarır ve olayları tüketir. Hizmet Veri Servisi gibi, Olay Izgara sıda almak istediği etkinlikler için abonelik kuralını ayarladığı *filtrelenmiş* bir abone modelini destekler. Olay Izgarası, azure servis veri hizmeti veri nelerinin oluşturabileceğinden çok daha fazla gerçek zamanlı teslimatı sağlayan saniyede 10 milyon olay garantisi ile hızlı iş artışı sağlar.

Event Grid için tatlı bir nokta, Azure altyapısının dokusuna derin entegrasyonudur. Cosmos DB gibi bir Azure kaynağı, yerleşik olayları özel koda gerek kalmadan doğrudan diğer ilgili Azure kaynaklarına yayınlayabilir. Olay Ağıt, bir Azure Aboneliği, Kaynak Grubu veya Hizmetten etkinlikler yayımlayarak geliştiricilere bulut kaynaklarının yaşam döngüsü üzerinde ince düzeyli denetim sağlar. Ancak, Olay Izgarası Azure ile sınırlı değildir. Uygulamalardan veya üçüncü taraf hizmetlerden yayınlanan özel HTTP olaylarını tüketebilen ve olayları harici abonelere yönlendirebilen açık bir platformdur.

Azure kaynaklarından yerel etkinlikleryayımlanır ken ve abone yken kodlama gerekmez. Basit yapılandırmayla, etkinlikleri bir Azure kaynağından diğerine, Konular ve Abonelikler için yerleşik tesisattan yararlanarak entegre edebilirsiniz. Şekil 4-17 Olay Izgara anatomisi gösterir.

![Olay Izgara anatomisi](./media/event-grid-anatomy.png)

**Şekil 4-17**. Olay Izgara anatomisi

EventGrid ve Servis Veri Servisi arasındaki önemli bir fark, temel *ileti alışverişi desenidir.*

Service Bus, alt akış abonesinin yeni iletiler için konu aboneliğini etkin olarak yokladığı eski bir stil *çekme modeli* uygular. İyi tarafından bakarsak, bu yaklaşım aboneye iletileri işleyen hızı tam olarak kontrol eder. Herhangi bir zamanda ne zaman ve kaç iletinin işletileceğini denetler. Okunmamış iletiler işlenene kadar abonelikte kalır. Önemli bir eksiklik, olayın oluşturulduğu saat ile bu iletiyi işleme için aboneye çeken yoklama işlemi arasındaki gecikmedir. Ayrıca, bir sonraki olay için sürekli yoklama yükü kaynakları ve para tüketir.

Ancak EventGrid farklıdır. Olayların alındığı gibi EventHandlers'a gönderildiği bir *itme modeli* uygular ve neredeyse gerçek zamanlı etkinlik teslimi verir. Ayrıca, hizmet yalnızca bir olayı tüketmek gerektiğinde tetiklendiğinden ( sürekli olarak yoklamada olduğu gibi değil- maliyeti azaltır. Bununla ilgili olarak, bir olay işleyicisi gelen yükü işlemeli ve kendini bunalmayı korumak için azaltma mekanizmaları sağlamalıdır. Azure İşlevleri ve Mantıksal Uygulamalar gibi bu olayları tüketen birçok Azure hizmeti, artan yükleri işlemek için otomatik otomatik ölçekleme özellikleri sağlar.  

Olay Grid tamamen yönetilen sunucusuz bir bulut hizmetidir. Trafiğinize göre dinamik olarak ölçeklendirilir ve önceden satın alınan kapasiteiçin değil, yalnızca gerçek kullanımınız için ücretlendirilir. Ayda ilk 100.000 işlem ücretsizdir – etkinlik girişi (gelen olay bildirimleri), abonelik teslim girişimleri, yönetim çağrıları ve konuya göre filtreleme olarak tanımlanan işlemler. %99,99 kullanılabilirlik ile EventGrid, başarısız teslimat için yerleşik yeniden deneme işleviyle bir etkinliğin 24 saatlik bir süre içinde teslim ini garanti eder. Teslim edilmeyen iletiler çözüm için "ölü harf" kuyruğuna taşınabilir.  Azure Servis Veri Servisi'nin aksine, Event Grid hızlı performans için ayarlanmıştır ve sipariş edilen ileti, işlem ve oturum gibi özellikleri desteklemez.

### <a name="streaming-messages-in-the-azure-cloud"></a>Azure bulutunda ileti akışı

Azure Hizmet Veri Servisi ve Etkinlik Ağıtı, Cosmos DB'ye yeni bir belge eklenmiş gibi tek ve ayrı olayları ortaya çıkaran uygulamalar için büyük destek sağlar. Ancak, bulut tabanlı *sisteminizin ilgili olaylar akışını işlemesi*gerekiyorsa ne olur? [Olay akışları](https://docs.microsoft.com/archive/msdn-magazine/2015/february/microsoft-azure-the-rise-of-event-stream-oriented-systems) daha karmaşıktır. Genellikle zaman sıralı, birbiriyle ilişkili ve bir grup olarak işlenmesi gerekir.

[Azure Event Hub,](https://azure.microsoft.com/services/event-hubs/) olayları toplayan, dönüştüren ve depolayan bir veri akış platformu ve etkinlik hizmetidir. Telemetri bağlamından yayılan sürekli olay bildirimleri gibi akış verilerini yakalamak için ince ayar lı. Hizmet son derece ölçeklenebilir ve saniyede milyonlarca olayı depolayabilir ve [işleyebilir.](https://docs.microsoft.com/azure/event-hubs/event-hubs-about) Şekil 4-18'de gösterildiği gibi, genellikle bir olay boru hattı için bir ön kapıdır ve akış ları olay tüketiminden ayırır.

![Azure Event Hub](./media/azure-event-hub.png)

**Şekil 4-18**. Azure Event Hub

Olay Hub düşük gecikme süresi ve yapılandırılabilir zaman tutma destekler. Sıraların ve konuların aksine, Olay Hub'ları olay verilerini bir tüketici tarafından okunduktan sonra saklar. Bu özellik, diğer veri analitik hizmetlerinin, hem dahili hem de harici olarak, daha fazla analiz için verileri yeniden oynatmasını sağlar. Olay merkezinde depolanan olaylar yalnızca bekletme süresinin sona ermesinden sonra silinir, bu da varsayılan olarak bir gün, ancak yapılandırılabilir.

Olay Hub' ı HTTPS ve AMQP gibi yaygın olay yayımlama protokollerini destekler. Ayrıca Kafka 1.0 destekler. Mevcut Kafka uygulamaları, büyük Kafka kümelerini yönetmeye alternatif sağlayan Kafka protokolünü kullanarak [Event Hub ile iletişim kurabilir.](https://docs.microsoft.com/azure/event-hubs/event-hubs-for-kafka-ecosystem-overview) Birçok açık kaynak bulut-yerli sistemleri Kafka kucaklamak.

Olay Hub'ları, her tüketicinin ileti akışının yalnızca belirli bir alt kümesini veya bölümlerini okuduğu [bölümlenmiş](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) bir tüketici modeli aracılığıyla ileti akışı uygular. Bu desen, olay işleme için muazzam yatay ölçek sağlar ve kuyruklarda ve konularda kullanılamayan diğer akış odaklı özellikler sağlar. Bölüm bir olay hub'ında tutulan olayların sıralı dizisidir. Yeni olaylar geldikçe, bu dizinin sonuna eklenir.Şekil 4-19, Bir Olay Hub'ında bölümleme gösterir.

![Olay Hub bölümleme](./media/event-hub-partitioning.png)

**Şekil 4-19**. Olay Hub bölümleme

Her tüketici grubu, aynı kaynaktan okumak yerine, ileti akışının bir alt kümesini veya bölümlerini okur.

Azure Etkinlik Hub'ı, çok sayıda etkinlik akışı yapması gereken bulut tabanlı uygulamalar için sağlam ve uygun maliyetli bir çözüm olabilir.

>[!div class="step-by-step"]
>[Önceki](front-end-communication.md)
>[Sonraki](grpc.md)
