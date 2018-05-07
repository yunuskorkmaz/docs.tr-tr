---
title: Mikro hizmet mimarisi iletişimi
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro hizmet mimarisi mimarileri iletişimi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 12899f7ee0f95ccc38d7de152c316442e9bcc8e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="communication-in-a-microservice-architecture"></a>Mikro hizmet mimarisi iletişimi

Tek bir işlem üzerinde çalışan tek yapılı bir uygulamada birbirine dil düzeyi yöntemi veya işlev çağrılarını kullanarak bileşenleri çağırma. Nesneleri koduyla oluşturuyorsanız, bu kesinlikle eşleştirilmek (örneğin, `new ClassName()`), veya somut nesne örneklerini yerine soyutlamalar başvurarak bağımlılık ekleme kullanıyorsanız, ayrılmış bir şekilde çağrılabilir. Her iki durumda da nesneleri aynı işlem içinde çalışır. Mikro tabanlı bir uygulama için tek yapılı bir uygulamadan değiştirirken en büyük zorluk iletişim mekanizması değiştirme arasındadır. RPC çağrıları hizmetlerine işlemdeki yöntemi çağrılarını doğrudan dönüştürme bir chatty neden olur ve ortamlar da buna gerçekleştirmez değil verimli iletişimi dağıtılır. Dağıtılmış Sistem düzgün tasarlama zorluklar olduğunu bile olarak bilinen bir canon yeterince iyi bilinen [dağıtılmış bilgi işlem Fallacies](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) geliştiriciler genellikle gelen tek yapılı taşırken olun varsayımlar listeler Dağıtılmış tasarımları için.

Bir çözüm değildir, ancak birkaç yoktur. Bir çözüm, mümkün olduğunca iş mikro yalıtma içerir. Ardından iç mikro arasındaki zaman uyumsuz iletişim kullanın ve düzey kaba iletişimde nesneler arasındaki işlem içi iletişimi normal hassas iletişimi değiştirin. Çağrıları gruplandırma ve istemci için birden çok dahili çağrı sonuçları toplar veri döndüren bunu yapabilirsiniz.

Mikro tabanlı bir uygulama birden çok işlemler veya hizmetler, birden fazla sunucu veya ana bilgisayarlar arasında genellikle bile çalışan dağıtılmış bir sistemdir. Her hizmet örneği genellikle bir işlemdir. Bu nedenle, hizmetler, örneğin HTTP, AMQP veya TCP gibi ikili olarak iletişim kuralı her hizmetin yapısına bağlı olarak bir işlemler arası iletişim protokolü kullanarak etkileşim kurmalıdır.

Mikro hizmet topluluk, felsefesi yükseltir "[akıllı uç noktaları ve dumb kanallar](https://simplicable.com/new/smart-endpoints-and-dumb-pipes)." Bu sloganı ayrılmış mikro arasındaki olası ve tek bir mikro hizmet içinde mümkün olduğunca bağlı olan bir tasarım önerir. Daha önce açıklandığı gibi her mikro hizmet kendi veri ve kendi etki alanı mantığı sahip olur. Ancak bir uçtan uca uygulama oluşturma mikro genellikle yalnızca WS - gibi karmaşık protokoller yerine REST iletişimleri kullanarak choreographed\* ve esnek olay denetimli iletişimleri yerine Merkezi İş-işlem-orchestrators.

İki sık kullanılan HTTP istek/yanıt (tüm çoğunu sorgulanırken) API'leri kaynakla kurallarıdır ve basit zaman uyumsuz iletişim kurarken Mesajlaşma arasında birden çok mikro güncelleştirir. Bunlar aşağıdaki bölümlerde daha ayrıntılı olarak açıklanmıştır.

## <a name="communication-types"></a>İletişim türleri

İstemci ve hizmetler farklı türlerde iletişim, her biri farklı bir senaryo ve hedefler hedefleme iletişim kurabilir. Başlangıçta, bu tür iletişim iki eksenleri sınıflandırılabilir.

Protokol zaman uyumlu veya uyumsuz ise ilk ekseni tanımlama:

-   Zaman uyumlu protokolü. HTTP zaman uyumlu bir protokoldür. İstemcinin bir isteği gönderir ve hizmetinden bir yanıt bekler. Zaman uyumlu olarak istemci kodu yürütülmesi bağımsız olan (iş parçacığı engellendi) veya zaman uyumsuz (iş parçacığı engellenmez ve yanıt bir geri çağırma ulaşırsınız). Burada önemli olan nokta protokol (HTTP/HTTPS) zaman uyumlu olarak ve HTTP sunucu yanıtı aldığında istemci kodu görevini yalnızca devam edebilirsiniz ' dir.

-   Zaman uyumsuz iletişim kuralı. AMQP (birçok işletim sistemleri ve bulut ortamları tarafından desteklenen bir protokol) gibi diğer protokoller zaman uyumsuz ileti kullanın. İstemci kodu veya ileti gönderen için bir yanıt genellikle beklemez. Yalnızca iletiyi olarak RabbitMQ sıra ya da başka bir ileti aracısı için bir ileti gönderirken, gönderir.

Tek bir alıcı veya birden çok alıcı iletişimi varsa, ikinci eksen tanımlama:

-   Tek alıcı. Her istek tam olarak bir alıcı veya hizmeti tarafından işlenmesi gerekir. Bu iletişim örneğidir [komutu düzeni](https://en.wikipedia.org/wiki/Command_pattern).

-   Birden çok alıcı. Her isteği, birden çok alıcı sıfıra tarafından işlenebilir. Bu tür iletişim zaman uyumsuz olması gerekir. Örnek [Yayınla/Abone ol](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) gibi düzenleri kullanılan mekanizma [olay denetimli mimarisi](https://microservices.io/patterns/data/event-driven-architecture.html). Bu bir olay-bus arabirimi veya ileti Aracısı olaylar ile birden çok mikro arasında veri güncelleştirmeleri yayılıyor bağlıdır; genellikle bir hizmet veri yolu veya benzer yapıya gibi aracılığıyla uygulanır [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) kullanarak [konuları ve abonelikleri](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions).

Mikro hizmet tabanlı bir uygulama, genellikle bu iletişim stilleri bileşimini kullanır. En yaygın tür tek alıcı HTTP/HTTPS gibi zaman uyumlu bir protokolle normal bir Web API HTTP hizmeti başlatılırken iletişimidir. Mikro de genellikle mikro arasında zaman uyumsuz iletişim için Mesajlaşma protokolleri kullanır.

Bu eksenler daha anlaşılır olması olası iletişim mekanizmalarına sahip, ancak bunlar önemli sorunları mikro oluştururken değil şekilde bilmek iyi. Ne istemci iş parçacığı yürütme zaman uyumsuz yapısını ve seçilen protokol zaman uyumsuz yapısını mikro tümleştirdiğinizde önemli noktaları değildir. Ne *olan* önemli, mikro zaman uyumsuz olarak mikro, bağımsızlığı korurken aşağıdaki bölümde açıklandığı gibi tümleştirebilir yapılıyor.

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>Zaman uyumsuz mikro hizmet tümleştirme mikro'nın otonomisi zorlar

Belirtildiği gibi mikro tabanlı bir uygulama oluştururken en önemli nokta, mikro tümleştirmek yoludur. İdeal olarak, iç mikro arasındaki iletişimi en aza indirmeye çalışmanız. Daha az arasındaki iletişim mikro, o kadar iyi olur. Ancak, çoğu durumda, şekilde mikro tümleştirmek gerekir. Bunu yapmak gereksinim duyduğunuzda, kritik burada mikro arasındaki iletişimi zaman uyumsuz olması gerektiğini kuralıdır. Bu, belirli bir protokol (örneğin, zaman uyumsuz zaman uyumlu HTTP Mesajlaşma) kullanmak zorunda gelmez. Yalnızca mikro arasındaki iletişimi yalnızca verileri zaman uyumsuz olarak yayılıyor tarafından yapılması gerekir, ancak diğer iç mikro üzerinde ilk hizmetin HTTP istek/yanıt işleminin bir parçası bağımlı değil deneyin anlamına gelir.

Mümkünse, hiçbir zaman bile sorgular için birden çok mikro arasında zaman uyumlu iletişim (istek/yanıt) bağlıdır. Her mikro hizmet uçtan uca uygulamanın parçası olan diğer hizmetlerin aşağı ya da sağlıksız olsa bile otonom ve istemci tüketici için kullanılabilir olmasını hedefidir. İçinde bir mikro hizmet çağrısından (bir HTTP isteği için bir veri sorgusu gerçekleştirerek) gibi diğer mikro için yapmanız gereken düşünüyorsanız, bir istemci uygulaması için bir yanıt sağlamak için sipariş, bazı durumlarda dayanıklı olmayacak bir mimari sahip mikro başarısız.

Ayrıca, HTTP bağımlılıkları uzun oluştururken, istek/yanıt döngüleri HTTP ile zincirleri, ilk bölümü, Şekil 4-15'nde gösterildiği gibi istemek gibi mikro arasında kalmaz, mikro değil otonom sağlar ancak kendi performansını da değil Bu zincirdeki hizmetlerden biri de gerçekleştirmiyor hemen etkilenmiş. 

Sorgu istekleri gibi mikro arasındaki zaman uyumlu bağımlılıkları daha ekleyin, kötü genel yanıt süresi için istemci uygulamaları alır.

![](./media/image15.png)

**Şekil 4-15**. Koruma desenleri ve mikro hizmetler arasındaki iletişim düzenleri

Başka bir işlem başka bir mikro hizmet olarak yükseltmek, mikro hizmet alması gerekiyorsa Mümkünse, bu eylem eş zamanlı olarak ve özgün mikro hizmet isteği ve yanıtlama işleminin parçası olarak gerçekleştirme. Bunun yerine, bunu zaman uyumsuz olarak (kullanarak zaman uyumsuz Mesajlaşma veya tümleştirme olaylarını, kuyruklar vb.). Ancak, mümkün olduğunca çok eylem özgün eşzamanlı istek ve yanıt işleminin parçası olarak zaman uyumlu çağırma kullanılamaz.

Ve son olarak (ve bu sorunların çoğunu mikro oluştururken burada ortaya), ilk mikro diğer mikro tarafından başlangıçta ait veri gerekiyorsa, bu veriler için zaman uyumlu istekleri yapan güvenmeyin. Bunun yerine, çoğaltma veya nihai tutarlılık (genellikle tümleştirme olaylarını yaklaşan bölümlerde açıklandığı gibi) kullanarak bu verileri (yalnızca gereksinim duyduğunuz öznitelikleri) ilk hizmetin veritabanına yayar.

Önceki bölümünde belirtildiği gibi [her mikro hizmet için etki alanı modeli sınırları tanımlayan](#identifying-domain-model-boundaries-for-each-microservice), bazı veriler arasında birkaç mikro çoğaltma yanlış bir tasarım değildir — tersine, ne zaman bu şey Çevir verileri belirli bir dil veya ek etki alanı veya sınırlanmış bağlam koşulları. Örneğin, [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) adlı kullanıcının sahip bir varlık kullanıcının verilerin çoğu sorumlu olan identity.api adlı mikro hizmet sahip uygulama. Sıralama mikro hizmet içinde kullanıcı hakkındaki verileri depolamak gerektiğinde, ancak, siz onu alıcı adlı farklı bir varlık olarak saklayın. Alıcı varlık aynı kimliğe sahip özgün kullanıcı varlık paylaşır, ancak yalnızca sıralama etki alanı ve tüm kullanıcı profili tarafından gereken birkaç özniteliklere sahip.

İletişim kurmak ve veri nihai tutarlılık olması için mikro arasında zaman uyumsuz olarak yayılması için herhangi bir iletişim kuralı kullanabilirsiniz. Belirtildiği gibi bir olay veri yolu veya ileti aracısı veya hatta HTTP diğer hizmetlerin yoklayarak kullanabilirsiniz kullanarak tümleştirme olayları kullanabilirsiniz. Bu önemli değildir. Önemli, mikro arasındaki zaman uyumlu bağımlılıkları oluşturmamayı kuralıdır.

Aşağıdaki bölümlerde mikro hizmet tabanlı bir uygulama kullanmayı birden çok iletişim stilleri açıklanmaktadır.

## <a name="communication-styles"></a>İletişim stilleri

Birçok protokolleri ve kullanmak istediğiniz iletişim türüne bağlı olarak iletişim için kullanabileceğiniz seçenekleri vardır. Eşzamanlı istek/yanıt tabanlı iletişim mekanizması kullanıyorsanız, özellikle hizmetlerinizi Docker ana bilgisayar veya mikro hizmet küme dışındaki yayımlıyorsanız HTTP ve REST yaklaşımlar gibi en yaygın protokollerdir. Dahili (kümedeki, Docker ana bilgisayar veya mikro) hizmetleri arasında iletişim kuran varsa (örneğin, Service Fabric remoting veya TCP ve ikili biçimi kullanarak WCF) ikili biçimi iletişim mekanizmasını kullanmak isteyebilirsiniz. Alternatif olarak, zaman uyumsuz, ileti tabanlı iletişim mekanizmasını AMQP gibi kullanabilirsiniz.

Ayrıca vardır JSON veya XML gibi birden çok ileti formatları ya da daha etkili olabilir bile ikili biçimleri. Seçilen, ikili biçimi bir standart değilse, bunu genel olarak hizmetlerinizin bu biçimi kullanarak yayımlamak için iyi bir fikir değil büyük olasılıkla. Standart olmayan bir biçimde, mikro arasında iç iletişim için kullanabilirsiniz. Mikro Docker ana bilgisayar veya mikro hizmet kümenizi (Docker orchestrators veya Azure Service Fabric) içinde ya da mikro konuşun özel istemci uygulamaları için arasında iletişim kurarken bunu yapabilirsiniz.

### <a name="requestresponse-communication-with-http-and-rest"></a>HTTP ve REST istek/yanıt iletişim 

Bir istemci istek/yanıt iletişimi kullanırken, bir istek bir hizmete, ardından hizmet işlemleri isteği gönderir ve bir yanıtı geri gönderir. İstek/yanıt iletişimi, özellikle de istemci uygulamalarından gerçek zamanlı bir kullanıcı Arabirimi (dinamik kullanıcı arabirimi) için veri sorgulama için uygundur. Bu nedenle, bir mikro hizmet mimarisi, büyük olasılıkla bu iletişim mekanizması sorguların çoğu için Şekil 4-16'da gösterildiği gibi kullanır.

![](./media/image16.png)

**Şekil 4-16**. HTTP istek/yanıt iletişimi (zaman uyumlu veya zaman uyumsuz) kullanma

Bir istemci istek/yanıt iletişimi kullanırken, yanıt kısa bir süre içinde genellikle saniyeden az veya birkaç saniye en uygun şekilde ulaşacağını varsayar. Gecikmeli yanıtlar için göre zaman uyumsuz iletişim uygulamanız gereken [desenleri Mesajlaşma](https://docs.microsoft.com/azure/architecture/patterns/category/messaging) ve [teknolojileri Mesajlaşma](https://en.wikipedia.org/wiki/Message-oriented_middleware), biz sonraki bölümde açıklanmaktadır farklı bir yaklaşım olduğu.

İstek/yanıt iletişimi için popüler bir mimari stili [REST](https://en.wikipedia.org/wiki/Representational_state_transfer). Bu yaklaşım için açık ve sıkı şekilde bağlı dayalı [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) protokolü, HTTP fiilleri gibi GET, POST, kucaklamakta ve yerleştirin. REST en yaygın kullanılan mimari iletişim hizmetleri oluştururken bir yaklaşımdır. ASP.NET Core Web API Hizmetleri geliştirirken REST Hizmetleri uygulayabilirsiniz.

HTTP REST Hizmetleri arabirim tanımı diliniz kullanılırken ek değer yoktur. Örneğin, kullanırsanız [Swagger meta verileri](https://swagger.io/) hizmeti API'si açıklamak için doğrudan bulabilir ve hizmetlerinizi tüketen istemci saplamalar oluşturma araçları kullanabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Martin Fowler. Uludağ olgunluk modeli.** REST modelin açıklaması.
    [*https://martinfowler.com/articles/richardsonMaturityModel.html*](https://martinfowler.com/articles/richardsonMaturityModel.html)

-   **Swagger.** Resmi sitesi.
    [*https://swagger.io/*](https://swagger.io/)

### <a name="push-and-real-time-communication-based-on-http"></a>Anında iletme ve HTTP tabanlı gerçek zamanlı iletişim

Diğer bir olasılık (genellikle farklı amaçlar için REST daha) olan üst düzey çerçeveleri ile gerçek zamanlı ve bir çok bir iletişim gibi [ASP.NET SignalR](https://www.asp.net/signalr) ve gibi protokoller [WebSockets](https://en.wikipedia.org/wiki/WebSocket).

Şekil 4-17 gösterildiği gibi gerçek zamanlı HTTP iletişimi yeni veri istemek bir istemci için bekleme sunucusunun yerine veriler kullanılabilir olduğunda içeriği bağlı istemcilere dağıtmaya sunucu kodu olabilir anlamına gelir.

![](./media/image17.png)

**Şekil 4-17**. Bire bir gerçek zamanlı zaman uyumsuz ileti iletişimi

Gerçek zamanlı olarak iletişim olduğuna göre istemci uygulamaları değişiklikleri neredeyse anında gösterir. Bu, genellikle gibi birçok WebSockets bağlantıları (istemci başına bir tane) kullanarak WebSockets protokolü tarafından işlenir. Aynı anda çok sayıda istemci web uygulamaları için Spor oyun puanı değişikliği bir hizmet iletişim kurduğunda, tipik bir örnektir.


>[!div class="step-by-step"]
[Önceki] (direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) [sonraki] (zaman uyumsuz-ileti-tabanlı-communication.md)
