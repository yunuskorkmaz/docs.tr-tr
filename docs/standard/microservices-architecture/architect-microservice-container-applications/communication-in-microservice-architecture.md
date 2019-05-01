---
title: Mikro hizmet mimarisinde iletişim
description: Zaman uyumlu ve zaman uyumsuz yöntemler etkilerini anlama, mikro hizmetler iletişimin farklı yolları keşfedin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 364bd4eb82907fcf0fbcc850eca839f676a2dbf8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909506"
---
# <a name="communication-in-a-microservice-architecture"></a>Mikro hizmet mimarisinde iletişim

Tek bir işlemde çalışan tek parçalı bir uygulamada dil düzeyi yöntemi veya işlev çağrıları kullanarak birbirine bileşenleri çağırma. Nesneleri koduyla oluşturuyorsanız bunlar kesinlikle eşleştirilmek (örneğin, `new ClassName()`), veya somut bir nesne örneği yerine soyutlama başvurarak bağımlılık ekleme kullanıyorsanız, ayrılmış bir şekilde çağrılabilir. Her iki durumda da, nesneleri aynı işlem içinde çalışır. Bir mikro hizmet tabanlı uygulama için tek parça bir uygulamayı değiştirirken en büyük güçlük iletişim mekanizması değiştirmekle arasındadır. RPC çağrıları hizmetlerine işlem içi yöntemi çağrılarını doğrudan dönüştürme bir geveze neden olur ve ortamları da gerçekleştiremiyor değil verimli bir iletişim dağıtılır. Dağıtılmış sisteme düzgün şekilde tasarlamanın zorluklarını olduğunu bile olarak bilinen bir canon yeterince iyi bilinen [dağıtılan bilgi işlem hataları](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) geliştiriciler genellikle tek parçalı gelen taşırken olun varsayımlar listeler Dağıtılmış tasarımları için.

Tek bir çözüm, ancak birkaç yoktur. Bir çözümü mümkün olduğunca iş mikro Hizmetleri ayırma içerir. Daha sonra iç mikro hizmetler arasında zaman uyumsuz iletişim kullanın ve işlem içi iletişimi sertifikalarıdır kaba iletişimle nesneler arasındaki normal ayrıntılı iletişimine değiştirin. Çağrıları gruplandırma ve toplayan istemciye birden çok iç çağrı sonucunu veriyor bunu yapabilirsiniz.

Mikro hizmet tabanlı bir uygulama, birden çok işlemler veya hizmetler, birden fazla sunucu veya ana bilgisayar genellikle çift çalışan dağıtılmış bir sistemdir. Her hizmet örneği, genellikle bir işlemdir. Bu nedenle, hizmetler, örneğin HTTP, AMQP veya ikili bir protokol, TCP gibi her hizmetin doğasına bağlı olarak bir işlemler arası iletişim protokolünü kullanarak etkileşim kurmalıdır.

Mikro hizmet topluluk felsefesini yükseltir "[akıllı uç noktaları ve dumb kanallar](https://simplicable.com/new/smart-endpoints-and-dumb-pipes)" Bu sloganı mikro hizmetler arasında olabildiğince ve tek bir mümkün olduğunca cohesive gibi ayrılmış bir tasarımı teşvik eder. mikro hizmet. Daha önce açıklandığı gibi her bir mikro hizmet kendi verilerini ve kendi etki alanı mantığı sahip olur. Ancak mikro hizmetlerin uçtan uca uygulama oluşturma genellikle yalnızca REST iletişimleri yerine WS - gibi karmaşık protokoller kullanarak choreographed\* ve Merkezi yerine esnek olay tabanlı iletişim İş-işlem-düzenleyiciler.

HTTP istek/yanıt kaynak (tüm çoğunu sorgulanırken) API'leri ile iki yaygın olarak kullanılan protokol olan ve basit zaman uyumsuz iletişim kurarken Mesajlaşma birden fazla mikro hizmetler arasında güncelleştirir. Bunlar aşağıdaki bölümlerde daha ayrıntılı açıklanmıştır.

## <a name="communication-types"></a>İletişim türleri

İstemci ve hizmet iletişimi, her biri farklı bir senaryo ve hedefler hedefleyen birçok farklı türde iletişim kurabilir. Başlangıçta, bu tür iletişimler iki eksenleri sınıflandırılabilir.

Protokol, zaman uyumlu veya zaman uyumsuz olması durumunda ilk ekseni tanımlar:

- Zaman uyumlu protokolü. Zaman uyumlu bir protokol HTTP'dir. İstemci bir istek gönderir ve hizmetten bir yanıt bekler. Zaman uyumlu istemci kodu yürütülmesini bağımsız olan (iş parçacığı engellendi) veya zaman uyumsuz (değil iş parçacığı engellenir ve yanıt bir geri çağırma sonunda ulaşır). Burada önemli olan nokta, protokol (HTTP/HTTPS) zaman uyumlu ve HTTP sunucu yanıtı aldığında istemci kodu yalnızca görevini devam ' dir.

- Zaman uyumsuz protokolü. AMQP (çok sayıda işletim sistemleri ve bulut ortamları tarafından desteklenen bir Protokolü) gibi diğer protokoller, zaman uyumsuz iletileri kullanın. İstemci kodu veya ileti gönderen, genellikle bir yanıt beklemez. Yalnızca iletiyi RabbitMQ kuyruk ya da herhangi bir ileti aracısı için bir ileti gönderirken, gönderir.

Tek bir alıcı ya da birden çok alıcı iletişimi varsa, ikinci bir eksen tanımlar:

- Tek bir alıcı. Her istek tam olarak bir alıcı veya hizmet tarafından işlenmesi gerekir. Bu iletişim örneğidir [komut deseni](https://en.wikipedia.org/wiki/Command_pattern).

- Birden çok alıcı. Her istek, sıfır olarak birden çok alıcılar tarafından işlenebilir. Bu tür bir iletişim zaman uyumsuz olması gerekir. Bir örnek [yayımlama/abone olma](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) desenleri gibi kullanılan mekanizma [olay denetimli mimari](https://microservices.io/patterns/data/event-driven-architecture.html). Bu olaylar ile birden çok mikro hizmetler arasında veri güncelleştirmelerini yayma, bir olay veri yolu arabirimi ya da ileti Aracısı dayanır; genellikle bir service bus veya gibi benzer yapıya aracılığıyla uygulanır [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) kullanarak [konuları ve abonelikleri](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions).

Mikro hizmet tabanlı bir uygulama genellikle bu iletişim stilleri bir birleşimini kullanır. En yaygın türü tek bir alıcı gibi HTTP/HTTPS zaman uyumlu bir protokol olan normal bir Web API HTTP hizmeti çağrılırken iletişimdir. Mikro hizmetler, mikro hizmetler arasında zaman uyumsuz iletişim için ayrıca genellikle Mesajlaşma protokolleri kullanın.

Bu eksen üzerinde olası iletişim mekanizmasını anlaşılabilir olması adına sahip ancak önemli endişelere yer bırakmadan mikro hizmetler oluştururken olmadıklarını öğrenmek uygundur. Ne zaman uyumsuz istemci iş parçacığı yürütme yapısını ne de seçilen protokol zaman uyumsuz yapısını bazı önemli noktalar mikro Hizmetleri Tümleştirme. Hangi *olduğu* önemli mikro hizmetlerin zaman uyumsuz olarak bağımsızlığı, mikro hizmetler, korurken aşağıdaki bölümde açıklandığı gibi tümleştirebilir yapılıyor.

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>Zaman uyumsuz bir mikro hizmet tümleştirmesi mikro hizmet'ın bağımsız çalışma sınırı uygular.

Belirtildiği gibi bir mikro hizmet tabanlı uygulama oluştururken önemli olan nokta, mikro hizmetler tümleştirme yoludur. İdeal olarak, iç mikro hizmetler arasındaki iletişimin en aza indirmeyi denemelisiniz. Mikro hizmetler, iyi arasında daha az iletişim. Ancak, çoğu durumda, mikro hizmetler şekilde tümleştirmek zorunda kalırsınız. Bunu yapmak, ihtiyacınız olduğunda, kritik kuralı buraya mikro hizmetler arasındaki iletişimi zaman uyumsuz olması gerekliliğidir. Bu işlem, belirli bir Protokolü (örneğin, zaman uyumsuz zaman uyumlu HTTP ileti) kullanmak zorunda gelmez. Yalnızca mikro hizmetler arasındaki iletişimi yalnızca verileri zaman uyumsuz olarak yayma tarafından yapılması gerekir, ancak diğer iç mikro hizmetler üzerinde ilk hizmetin HTTP istek/yanıt işleminin bir parçası bağımlı olmadan deneyin anlamına gelir.

Mümkünse, hiçbir zaman bile sorgular için birden fazla mikro hizmetler arasında zaman uyumlu iletişim (istek/yanıt) bağlıdır. Her mikro hizmet hedefi aşağı veya sağlıksız uçtan uca uygulamanın parçası olan diğer hizmetler olsa bile, otonom ve istemci tüketici için kullanılabilir olacak. Bir mikro hizmet bir çağrıdan (bir HTTP isteği için bir veri sorgusu gerçekleştirmek) gibi diğer mikro hizmetlere almanız gereken düşünüyorsanız, bir istemci uygulamanın yanıt sağlamak üzere kullanabilmek için bazı mikro hizmetler başarısız olduğunda dayanıklı olmayacak bir mimari gerekir.

Ayrıca, uzun oluştururken, HTTP istek/yanıt döngüleriyle zincirleri, Şekil 4 ',-15, ilk bölümde gösterildiği gibi istek gibi mikro hizmetler arasındaki HTTP bağımlılıklarına sahip değil yalnızca mikro hizmetlerin değil otonom sağlar ancak Ayrıca, performansı Bu zincirdeki hizmetlerden biri iyi değil olarak etkilenmiş.

Sorgu istekleri gibi bir mikro hizmetler arasında zaman uyumlu bağımlılıkları daha eklemeniz, istemci uygulamaları için yarışacağından genel yanıt süresini alır.

![Zaman uyumlu iletişimde istekleri "zinciri" istemci isteği hizmet çalışırken, mikro hizmetler arasında oluşturulur. Bu koruma bir desendir. Zaman uyumsuz iletişime mikro hizmetler, zaman uyumsuz iletileri veya diğer mikro hizmetler ile iletişim kurmak için yoklama http kullanır. ancak istemci isteği hemen sunulur.](./media/image15.png)

**Şekil 4-15**. Anti-desenleri ve mikro hizmetler arasındaki iletişimi desenleri

Başka bir işlem başka bir mikro hizmet içinde yükseltmek, mikro hizmet gerekiyorsa, mümkünse, bu eylem zaman uyumlu ve özgün mikro hizmet istek ve yanıt işleminin parçası olarak gerçekleştirme. Bunun yerine, bunu zaman uyumsuz olarak (kullanarak zaman uyumsuz Mesajlaşma veya tümleştirme olayları, kuyruklar vb.). Ancak, mümkün olan en kısa kadar özgün eşzamanlı istek ve yanıt işleminin parçası olarak zaman uyumlu olarak eylemin çağırma kullanılamaz.

Son olarak (ve bu sorunların çoğu, mikro hizmetler oluştururken burada ortaya), ilk, mikro hizmet başlangıçta diğer mikro hizmetler tarafından sahip olunan veri gerekiyorsa, bu veriler için zaman uyumlu istekleri yapan güvenmeyin. Bunun yerine, çoğaltma veya nihai tutarlılık (genellikle tümleştirme olayları, sonraki bölümlerde açıklandığı gibi) kullanarak bu verileri (yalnızca gereksinim duyduğunuz öznitelikleri) ilk hizmetin veritabanına yayar.

Önceki bölümde belirtildiği gibi [her mikro hizmet için etki alanı modeli sınırlarını tanımlama](identify-microservice-domain-model-boundaries.md), birden fazla mikro hizmetler arasında veri çoğaltma, hatalı bir tasarım değildir — tam, ne zaman, yapılması Çevir verileri belirli bir dil veya ek etki alanı veya içerik sınırlanmış koşulları. Örneğin, [hizmetine uygulama](https://github.com/dotnet-architecture/eShopOnContainers) kullanıcı adında bir varlıkla kullanıcının verilerin çoğu sorumlu olan identity.api adlı bir mikro hizmet vardır. Kullanıcı sıralama mikro hizmet içinde ilgili verileri depolamak gerekir, ancak, bunu alıcı adlı farklı bir varlık olarak saklayın. Alıcı varlık özgün kullanıcı varlığı ile aynı kimliği paylaşıyor, ancak yalnızca sıralama etki alanı ve tam kullanıcı profili gereken birkaç özniteliklere sahip.

İletişim ve veri nihai tutarlılığa sahip olmak için mikro hizmetler arasında zaman uyumsuz olarak yaymak için herhangi bir protokolünü kullanabilirsiniz. Belirtildiği gibi bir olay veri yolu veya ileti aracısı veya hatta HTTP diğer hizmetleri yoklayarak kullanabilirsiniz kullanarak tümleştirme olayları kullanabilirsiniz. Önemi yoktur. Önemli, mikro hizmetler arasında zaman uyumlu bağımlılıkları oluşturmamayı kuralıdır.

Aşağıdaki bölümlerde mikro hizmet tabanlı bir uygulama kullanmayı birden fazla iletişim stilleri açıklanmaktadır.

## <a name="communication-styles"></a>İletişim stilleri

Birçok protokolleri ve kullanmak istediğiniz iletişim türüne bağlı olarak, iletişimi için kullanabileceğiniz seçenekleri vardır. Bir eş zamanlı istek/yanıt tabanlı iletişim mekanizması kullanıyorsanız, özellikle hizmetleriniz Docker konağı veya mikro hizmet küme dışındaki yayımlıyorsanız HTTP ve diğer yaklaşımlar gibi en yaygın kurallarıdır. Dahili olarak (Docker konağı veya mikro hizmetler kümeniz içindeki) Hizmetleri arasındaki iletişim, ikili biçimi (Service Fabric uzaktan iletişimini veya TCP ve ikili biçimi kullanarak WCF gibi) iletişim mekanizmasını kullanmak isteyebilirsiniz. Alternatif olarak, zaman uyumsuz, ileti tabanlı iletişim mekanizmasını AMQP gibi kullanabilirsiniz.

Vardır da JSON veya XML gibi birden çok ileti formatları veya bile ikili biçimden daha verimli olabilir. Seçilen bir ikili biçimi standart değilse, bu biçimi kullanarak kendi hizmetlerinizi herkese açık şekilde yayımlamak için iyi bir fikirdir olmayabilir. Mikro hizmetlerin dahili iletişim için standart bir biçim kullanabilirsiniz. Docker konağı veya mikro hizmet kümenizi (Docker düzenleyiciler veya Azure Service Fabric) veya konuşma mikro hizmetler için özel istemci uygulamaları için mikro hizmetler arasında iletişim kurarken bunu yapabilirsiniz.

### <a name="requestresponse-communication-with-http-and-rest"></a>HTTP ve REST ile istek/yanıt iletişim

Bir istemci istek/yanıt iletişim kullandığında, istek bir hizmet, hizmet işlemleri için bir istek gönderir ve bir yanıtı geri gönderir. İstek/yanıt iletişimi, özellikle de istemci uygulamalardan gelen gerçek zamanlı bir kullanıcı Arabirimi (dinamik kullanıcı arabirimi) için veri sorgulama için uygundur. Bu nedenle, bir mikro hizmet mimarisinde, büyük olasılıkla bu iletişim mekanizması sorguların çoğu, Şekil 4-16 gösterildiği gibi kullanırsınız.

![İstemci isteği bir API ağ geçidi için kısa bir süre içinde mikro hizmetler yanıttan ulaşır varsayılarak gönderdiğinde, Canlı sorgular için istek/yanıt iletişimi kullanabilirsiniz.](./media/image16.png)

**Şekil 4-16**. HTTP istek/yanıt iletişimi (zaman uyumlu veya zaman uyumsuz) kullanma

Bir istemci istek/yanıt iletişim kullandığında, yanıt kısa bir süre içinde genellikle bir saniyeden az veya birkaç saniye en fazla ulaşır olduğunu varsayar. Gecikmeli yanıtlar için göre zaman uyumsuz iletişim uygulamak gereken [Mesajlaşma desenleri](https://docs.microsoft.com/azure/architecture/patterns/category/messaging) ve [teknolojileri Mesajlaşma](https://en.wikipedia.org/wiki/Message-oriented_middleware), biz sonraki bölümde açıklanmaktadır ve farklı bir yaklaşım olan.

İstek/yanıt iletişim için popüler bir mimari stil olan [REST](https://en.wikipedia.org/wiki/Representational_state_transfer). Bu yaklaşım için açık ve sıkı eşleşmiş tabanlı [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) protokolü, HTTP fiilleri gibi GET, POST, benimsemenin ve yerleştirin. REST en sık kullanılan mimari iletişim hizmetleri oluştururken bir yaklaşımdır. ASP.NET Core Web API Hizmetleri geliştirirken REST Hizmetleri uygulayabilirsiniz.

HTTP REST Hizmetleri, arabirim tanımı dili olarak kullanılırken ek değer yoktur. Örneğin, kullanırsanız [Swagger meta verileri](https://swagger.io/) hizmet API'nizi açıklamak için doğrudan bulabilir ve hizmetlerinizi kullanan istemci saptamalar Oluştur araçları kullanabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Martin Fowler. Uludağ olgunluk modelini** REST modeli açıklaması. \
  <https://martinfowler.com/articles/richardsonMaturityModel.html>

- **Swagger** resmi sitesi. \
  <https://swagger.io/>

### <a name="push-and-real-time-communication-based-on-http"></a>Anında iletme ve HTTP tabanlı gerçek zamanlı iletişim

Başka bir (genellikle farklı dışındaki amaçlarla REST) bir olasılıktır üst düzey çerçeveleri ile gerçek zamanlı ve bire çok bir iletişim gibi [ASP.NET SignalR](https://www.asp.net/signalr) ve protokoller gibi [WebSockets](https://en.wikipedia.org/wiki/WebSocket).

Şekil 4-17 gösterildiği gibi HTTP iletişimi için gerçek zamanlı yeni veri istemek bir istemci için bekleyin sunucusuna sahip olmak yerine veri kullanılabilir olduğunda içeriği bağlı istemcilere göndermek sunucu kodu olabilir anlamına gelir.

![SignalR, bir arka uç sunucusundan istemcilere içerik dağıtmaya için gerçek zamanlı iletişim elde etmek için iyi bir yoludur.](./media/image17.png)

**Şekil 4-17**. Gerçek zamanlı bire bir zaman uyumsuz ileti iletişimi

Gerçek zamanlı olarak iletişim olduğundan, istemci uygulamaları değişiklikleri neredeyse anında gösterir. Bu genellikle birçok WebSockets bağlantıları (istemci başına bir adet) kullanarak, WebSockets gibi bir protokol tarafından işlenir. Aynı anda çok sayıda istemci web Apps'e Spor oyunu puanı değişikliği hizmet iletişim kurduğunda, tipik bir örnektir.

>[!div class="step-by-step"]
>[Önceki](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
>[İleri](asynchronous-message-based-communication.md)
