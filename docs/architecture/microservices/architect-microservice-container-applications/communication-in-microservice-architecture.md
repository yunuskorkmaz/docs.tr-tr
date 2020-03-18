---
title: Mikro hizmet mimarisinde iletişim
description: Mikro hizmetler arasındaki farklı iletişim yollarını keşfedin, senkron ve eşzamanlı yöntemlerin etkilerini anlayın.
ms.date: 01/30/2020
ms.openlocfilehash: f2d6e78966bb7d5f481de6db0ab1dcfe2812a1b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401657"
---
# <a name="communication-in-a-microservice-architecture"></a>Mikro hizmet mimarisinde iletişim

Tek bir işlemüzerinde çalışan yekpare bir uygulamada, bileşenler dil düzeyinde yöntem veya işlev çağrıları kullanarak birbirlerini çağırır. Bunlar, kodlu nesneler oluşturuyorsanız (örneğin,) `new ClassName()`güçlü bir şekilde birleşebilir veya somut nesne örnekleri yerine soyutlamalara başvurarak Bağımlılık Enjeksiyonu kullanıyorsanız, ayrılmış bir şekilde çağrılabilir. Her iki durumda da, nesneler aynı işlem içinde çalışıyor. Yekpare bir uygulamadan mikrohizmet tabanlı bir uygulamaya geçerken en büyük zorluk iletişim mekanizmasının değiştirilmesidir. İşlem içi yöntem çağrılarından rpc çağrılarına doğrudan dönüşüm, dağıtılmış ortamlarda iyi performans göstermeyen geveze ve verimli olmayan bir iletişime neden olur. Dağıtılmış sistemi düzgün bir şekilde tasarlamanın zorlukları, geliştiricilerin yekpare tasarımlardan dağıtılmış tasarımlara geçiş yaparken sıklıkla yaptıkları varsayımları listeleyen [dağıtılmış bilgi işlemin Fallacies'i](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) olarak bilinen bir kanon bile olduğu yeterince iyi bilinmektedir.

Tek bir çözüm değil, birkaç tane var. Bir çözüm mümkün olduğunca iş mikrohizmetleri izole içerir. Daha sonra dahili mikro hizmetler arasında eşzamanlı iletişim kullanır ve nesneler arasındaki işlem içi iletişimde tipik olan ince taneli iletişimi kaba taneli iletişimle değiştirirsiniz. Bunu, çağrıları gruplandırma kılarak ve birden çok dahili aramanın sonuçlarını istemciye toplayan verileri döndürerek yapabilirsiniz.

Mikro hizmetler tabanlı bir uygulama, genellikle birden çok sunucu veya ana bilgisayarda bile birden çok işlem veya hizmet üzerinde çalışan dağıtılmış bir sistemdir. Her hizmet örneği genellikle bir işlemdir. Bu nedenle, hizmetlerin her hizmetin yapısına bağlı olarak HTTP, AMQP veya TCP gibi ikili bir iletişim protokolü gibi bir işlem içi iletişim protokolü kullanarak etkileşimde kullanılması gerekir.

Microservice topluluk felsefesi teşvik "[akıllı uç noktaları ve aptal borular](https://simplicable.com/new/smart-endpoints-and-dumb-pipes)" Bu slogan mikro hizmetler arasında mümkün olduğunca ayrılmış bir tasarım teşvik, ve tek bir microservice içinde mümkün olduğunca uyumlu. Daha önce açıklandığı gibi, her microservice kendi veri ve kendi etki alanı mantığı na sahip. Ancak uçtan uca bir uygulama oluşturan mikro hizmetler genellikle merkezi iş-süreç-orkestratörleri yerine\* WS gibi karmaşık protokoller ve esnek olay odaklı iletişimler yerine REST iletişimi kullanılarak koreografisini yapılır.

Sık kullanılan iki protokol, kaynak API'leri ile HTTP isteği/yanıtı (en çok sorgulanırken) ve güncelleştirmeleri birden çok mikro hizmet üzerinden iletirken hafif asynchronous iletileridir. Bunlar aşağıdaki bölümlerde daha ayrıntılı olarak açıklanmıştır.

## <a name="communication-types"></a>İletişim türleri

İstemci ve hizmetler, her biri farklı bir senaryo ve hedefi hedefleyen birçok farklı iletişim türü aracılığıyla iletişim kurabilir. Başlangıçta, bu tür iletişimler iki eksen halinde sınıflandırılabilir.

İlk eksen, protokolün senkron veya eşzamanlı olup olmadığını tanımlar:

- Senkron protokol. HTTP eşzamanlı bir protokoldür. İstemci bir istek gönderir ve hizmetten yanıt bekler. Bu, senkron (iş parçacığı engellenmiş) veya eşzamanlı (iş parçacığı engellenmez ve yanıt sonunda bir geri arama ulaşacaktır) olabilir istemci kodu yürütme bağımsızdır. Burada önemli olan nokta, protokolün (HTTP/HTTPS) senkron olması ve istemci kodunun yalnızca HTTP sunucu yanıtını aldığında görevine devam edebildiğidir.

- Asynchronous protokolü. AMQP (birçok işletim sistemi ve bulut ortamları tarafından desteklenen bir protokol) gibi diğer protokoller eşzamanlı iletiler kullanır. İstemci kodu veya ileti gönderen genellikle bir yanıt beklemez. Sadece bir RabbitMQ kuyruk veya başka bir ileti aracısı bir mesaj gönderir gibi ileti gönderir.

İkinci eksen, iletişimin tek bir alıcısı veya birden çok alıcısı olup olmadığını tanımlar:

- Tek alıcı. Her istek tam olarak bir alıcı veya hizmet tarafından işlenmelidir. Bu iletişimin bir örneği [Komut desenidir.](https://en.wikipedia.org/wiki/Command_pattern)

- Birden fazla alıcı. Her istek sıfırile birden çok alıcıya işlenebilir. Bu tür bir iletişim eşzamanlı olmalıdır. Olay [odaklı mimari](https://microservices.io/patterns/data/event-driven-architecture.html)gibi desenlerde kullanılan [yayımlama/abone etme](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) mekanizması buna bir örnektir. Bu, olaylar aracılığıyla birden çok mikro hizmet arasında veri güncelleştirmeleri yayılırken bir olay-veri birimi arabirimi veya ileti aracısı dayanmaktadır; genellikle [konular ve abonelikler](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions)kullanılarak Bir servis veri kurumu veya [Azure Servis Veri Servisi](https://azure.microsoft.com/services/service-bus/) gibi benzer bir yapı aracılığıyla uygulanır.

Mikro hizmet tabanlı bir uygulama genellikle bu iletişim stillerinin bir birleşimini kullanır. En yaygın tür, normal bir Web API HTTP hizmetini çağırırken HTTP/HTTPS gibi eşzamanlı bir protokoliçeren tek alıcılı iletişimdir. Mikro hizmetler, genellikle mikro hizmetler arasındaki eşzamanlı iletişim için mesajlaşma protokollerini de kullanır.

Bu eksenler, olası iletişim mekanizmaları üzerinde netlik var, ancak mikro hizmetler inşa ederken önemli endişeleri değil bilmek iyidir. Ne istemci iş parçacığı yürütmenin eşzamanlı doğası ne de seçilen protokolün eşzamanlı yapısı mikro hizmetleri tümleştirirken önemli noktalar dır. Önemli *olan,* aşağıdaki bölümde açıklandığı gibi, mikro hizmetlerin bağımsızlığını korurken mikro hizmetlerinizi senkronize bir şekilde entegre edebilmektir.

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>Asynchronous microservice entegrasyonu microservice'in özerkliğini zorlar

Belirtildiği gibi, mikro hizmet tabanlı bir uygulama kurarken önemli olan nokta, mikro hizmetlerinizi entegre etme şeklinizdir. İdeal olarak, dahili mikro hizmetler arasındaki iletişimi en aza indirmeye çalışmalısınız. Mikro hizmetler arasındaki iletişim ne kadar azsa o kadar iyi. Ama birçok durumda, bir şekilde mikro hizmetleri entegre etmek gerekir. Bunu yapmanız gerektiğinde, buradaki kritik kural, mikro hizmetler arasındaki iletişimin eşzamanlı olması gerektiğidir. Bu, belirli bir protokol kullanmanız gerektiği anlamına gelmez (örneğin, senkron http'ye karşı eşzamanlı mesajlaşma). Bu sadece mikro hizmetler arasındaki iletişimin yalnızca verileri eşzamanlı olarak yayılarak yapılması gerektiği, ancak ilk hizmetin HTTP istek/yanıt işleminin bir parçası olarak diğer dahili mikro hizmetlere bağımlı olmamak anlamına gelir.

Mümkünse, sorgular için bile birden çok mikro hizmet arasında eşzamanlı iletişim (istek/yanıt) asla bağlı değildir. Her microservice'in amacı, uçtan uca uygulamanın bir parçası olan diğer hizmetler aşağı veya sağlıksız olsa bile, özerk ve istemci tüketiciiçin kullanılabilir olmaktır. Bir istemci uygulamasına yanıt verebilmek için bir mikro hizmetten diğer mikro hizmetlere (örneğin, veri sorgusu için HTTP isteği gerçekleştirmek gibi) bir arama yapmanız gerektiğini düşünüyorsanız, bazı mikro hizmetler başarısız olduğunda esnek olmayacak bir mimariye sahipsiniz.

Ayrıca, Şekil 4-15'in ilk bölümünde gösterildiği gibi, HTTP istek zincirleriyle uzun istek/yanıt döngüleri oluştururken olduğu gibi mikro hizmetler arasındaki HTTP bağımlılıklarına sahip olmak, yalnızca mikro hizmetlerinizi özerk hale getirmiyor, aynı zamanda bu zincirdeki hizmetlerden biri iyi performans göstermez etkide de etkiliyor.

Sorgu istekleri gibi mikro hizmetler arasında eşzamanlı bağımlılıklar ne kadar eklerseniz, istemci uygulamaları için genel yanıt süresi o kadar kötü olur.

![Mikro hizmetler arasında üç tür iletişimgösteren diyagram.](./media/communication-in-microservice-architecture/sync-vs-async-patterns-across-microservices.png)

**Şekil 4-15**. Mikro hizmetler arasındaki iletişimde anti-desen ve desenler

Yukarıdaki diyagramda gösterildiği gibi, senkron iletişimde istemci isteğine hizmet verirken mikro hizmetler arasında bir "istek zinciri" oluşturulur. Bu bir anti-desen. Asynchronous iletişim mikroservices diğer mikro hizmetler ile iletişim kurmak için asynchronous mesajları veya http yoklama kullanın, ancak istemci isteği hemen servis edilir.

Microservice'inizin başka bir microservice'te ek bir eylem yükseltmesi gerekiyorsa, mümkünse, bu eylemi eşzamanlı olarak ve orijinal microservice isteği ve yanıtlama işleminin bir parçası olarak gerçekleştirin. Bunun yerine, eşzamanlı olarak yapın (eşzamanlı mesajlaşma veya tümleştirme olayları, kuyruklar, vb. kullanarak). Ancak, mümkün olduğunca, özgün senkron istek ve yanıt işleminin bir parçası olarak eylemi eşzamanlı olarak çağırmayın.

Ve son olarak (ve bu sorunların çoğu mikro hizmetler inşa ederken ortaya çıkar), ilk microservice aslında diğer mikro hizmetler tarafından sahip olunan veri ihtiyacı varsa, bu veriler için eşzamanlı istekte bulunmaya güvenmeyin. Bunun yerine, nihai tutarlılık kullanarak (genellikle gelecek bölümlerde açıklandığı gibi tümleştirme olaylarını kullanarak) bu verileri (yalnızca ihtiyacınız olan öznitelikler) ilk hizmetin veritabanına çoğaltın veya çoğaltın.

Daha önce her mikro hizmet bölümü [için etki alanı modeli sınırlarını tanımlamada](identify-microservice-domain-model-boundaries.md) belirtildiği gibi, bazı verileri çeşitli mikro hizmetler arasında çoğaltmak yanlış bir tasarım değildir— tam tersine, verileri belirli bir etki alanı nın veya Bağlı Bağlamın belirli bir dile veya koşullarına çevirebileceğinizi yaparken. Örneğin, [eShopOnContainers uygulamasında,](https://github.com/dotnet-architecture/eShopOnContainers) kullanıcıverilerinin çoğundan sorumlu `identity-api` olan ve adlı `User`bir kuruluşa sahip bir microservice'invar. Ancak, `Ordering` kullanıcı hakkındaki verileri mikro hizmet içinde depolamanız gerektiğinde, bu verileri `Buyer`başka bir varlık olarak depolarsınız. Varlık `Buyer` özgün `User` varlıkla aynı kimliği paylaşır, ancak tüm kullanıcı profilinideğil, etki alanının `Ordering` gerektirdiği yalnızca birkaç özniteliği olabilir.

Nihai tutarlılığa sahip olmak için verileri mikro hizmetler arasında eşit bir şekilde iletmek ve yaymak için herhangi bir protokol kullanabilirsiniz. Belirtildiği gibi, bir olay veri meseni veya ileti aracısı kullanarak entegrasyon olayları kullanabilirsiniz veya hatta yerine diğer hizmetleri yoklama tarafından HTTP kullanabilirsiniz. Fark etmez. Önemli kural, mikro hizmetleriniz arasında eşzamanlı bağımlılıklar oluşturmamaktır.

Aşağıdaki bölümlerde, mikrohizmet tabanlı bir uygulamada kullanmayı düşünebileceğiniz birden çok iletişim stili açıklanabilir.

## <a name="communication-styles"></a>İletişim stilleri

Kullanmak istediğiniz iletişim türüne bağlı olarak iletişim için kullanabileceğiniz birçok protokol ve seçenek vardır. Eşzamanlı istek/yanıt tabanlı iletişim mekanizması kullanıyorsanız, özellikle hizmetlerinizi Docker ana bilgisayarı veya mikro hizmet kümesi dışında yayınlıyorsanız, HTTP ve REST yaklaşımları gibi protokoller en yaygın olanıdır. Hizmetler arasında dahili olarak iletişim kuruyorsanız (Docker ana bilgisayarveya mikro hizmetler kümenizde), ikili biçimli iletişim mekanizmalarını da (TCP ve ikili biçim kullanarak WCF gibi) kullanmak isteyebilirsiniz. Alternatif olarak, AMQP gibi asynchronous, ileti tabanlı iletişim mekanizmaları kullanabilirsiniz.

JSON veya XML gibi birden çok ileti biçimi, hatta ikili biçimler de vardır, bunlar daha verimli olabilir. Seçtiğiniz ikili biçim bir standart değilse, bu biçimi kullanarak hizmetlerinizi herkese açık olarak yayımlamak büyük olasılıkla iyi bir fikir değildir. Mikro hizmetleriniz arasındaki dahili iletişim için standart olmayan bir biçim kullanabilirsiniz. Bunu, Docker ana bilgisayarınızdaki veya mikro hizmet kümenizdeki mikro hizmetler (örneğin, Docker orchestrators) veya mikro hizmetlerle konuşan özel istemci uygulamaları arasında iletişim kurarken yapabilirsiniz.

### <a name="requestresponse-communication-with-http-and-rest"></a>HTTP ve REST ile istek/yanıt iletişimi

İstemci istek/yanıt iletişimini kullandığında, bir hizmete istek gönderir, ardından hizmet isteği işler ve bir yanıtı geri gönderir. İstek/yanıt iletişimi, istemci uygulamalarından gerçek zamanlı bir kullanıcı arabirimi (canlı kullanıcı arabirimi) için veri sorgulamak için özellikle uygundur. Bu nedenle, bir microservice mimarisinde, şekil 4-16'da gösterildiği gibi, büyük olasılıkla çoğu sorgu için bu iletişim mekanizmasını kullanırsınız.

![Canlı sorgular ve güncelleştirmeler için istek/yanıt iletişimini gösteren diyagram.](./media/communication-in-microservice-architecture/request-response-comms-live-queries-updates.png)

**Şekil 4-16**. HTTP istek/yanıt iletişimini kullanma (senkron veya eşzamanlı)

İstemci istek/yanıt iletişimini kullandığında, yanıtın genellikle bir saniyeden kısa veya en fazla birkaç saniye içinde kısa bir süre içinde geleceğini varsayar. Gecikmiş yanıtlar için, bir sonraki bölümde açıkladığımız farklı bir yaklaşım olan [mesajlaşma modellerine](https://docs.microsoft.com/azure/architecture/patterns/category/messaging) ve [mesajlaşma teknolojilerine](https://en.wikipedia.org/wiki/Message-oriented_middleware)dayalı eşzamanlı iletişim uygulamanız gerekir.

İstek/yanıt iletişimi için popüler bir mimari stil [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)olduğunu. Bu yaklaşım, [GET,](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) POST ve PUT gibi HTTP fiillerini kucaklayan HTTP protokolüne dayanır ve sıkıca birleştiğinde kullanılır. REST, hizmet oluştururken en sık kullanılan mimari iletişim yaklaşımıdır. Core Web API hizmetlerini ASP.NET geliştirdiğinizde REST hizmetlerini uygulayabilirsiniz.

ARAYÜZ tanım diliniz olarak HTTP REST hizmetlerini kullanırken ek bir değer vardır. Örneğin, hizmet API'nizi açıklamak için [Swagger meta verilerini](https://swagger.io/) kullanırsanız, hizmetlerinizi doğrudan keşfedebilen ve tüketebilen istemci saplamaları oluşturan araçları kullanabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Martin Fowler' ı. Richardson Olgunluk Modeli** REST modelinin açıklaması. \
  <https://martinfowler.com/articles/richardsonMaturityModel.html>

- **Swagger** Resmi site. \
  <https://swagger.io/>

### <a name="push-and-real-time-communication-based-on-http"></a>HTTP'ye dayalı push ve gerçek zamanlı iletişim

Başka bir olasılık (genellikle REST daha farklı amaçlar için) [ASP.NET SignalR](https://www.asp.net/signalr) ve [WebSockets](https://en.wikipedia.org/wiki/WebSocket)gibi protokoller gibi üst düzey çerçeveler ile gerçek zamanlı ve bir-çok iletişim.

Şekil 4-17'nin de gösterdiği gibi, gerçek zamanlı HTTP iletişimi, sunucunun istemcinin yeni veri istemesini beklemek yerine, veriler kullanılabilir hale geldikçe içeriği bağlı istemcilere itmesini sağlayan sunucu kodunun olması anlamına gelir.

![SignalR'a dayalı itme ve gerçek zamanlı iletişimleri gösteren diyagram.](./media/communication-in-microservice-architecture/one-to-many-communication.png)

**Şekil 4-17**. Bire bir gerçek zamanlı asynchronous ileti iletişimi

SignalR, içeriği arka uç sunucudan istemcilere itmek için gerçek zamanlı iletişim elde etmenin iyi bir yoludur. İletişim gerçek zamanlı olduğundan, istemci uygulamaları değişiklikleri neredeyse anında gösterir. Bu genellikle websockets gibi bir protokol tarafından, birçok WebSockets bağlantıları (istemci başına bir) kullanılarak işlenir. Tipik bir örnek, bir hizmetin bir spor oyununun skorundaki bir değişikliği aynı anda birçok istemci web uygulamasına iletmesidir.

>[!div class="step-by-step"]
>[Önceki](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
>[Sonraki](asynchronous-message-based-communication.md)
