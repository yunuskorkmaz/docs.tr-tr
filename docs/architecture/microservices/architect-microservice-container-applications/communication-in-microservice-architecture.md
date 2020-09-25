---
title: Mikro hizmet mimarisinde iletişim
description: Mikro hizmetler arasındaki iletişimin farklı yollarını inceleyerek, zaman uyumlu ve zaman uyumsuz yolların etkilerini anlayın.
ms.date: 01/30/2020
ms.openlocfilehash: f1a240609b898fe8f365c39ba0c95f486377c445
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169264"
---
# <a name="communication-in-a-microservice-architecture"></a>Mikro hizmet mimarisinde iletişim

Tek bir işlemde çalışan tek parçalı bir uygulamada, bileşenler dil düzeyi Yöntem veya işlev çağrıları kullanarak bir diğeri çağırır. Bunlar, kod içeren nesneler oluşturuyorsanız (örneğin, `new ClassName()` ) veya somut nesne örnekleri yerine soyutlamalar ekleyerek bağımlılık ekleme 'yi kullanıyorsanız ayrılmış bir şekilde çağrılabilir. Her iki durumda da nesneler aynı işlem içinde çalışır. Tek parçalı bir uygulamadan mikro hizmet tabanlı bir uygulamaya geçiş yaparken en büyük zorluk, iletişim mekanizmasını değiştirme ' de yer alır. İşlem içi Yöntem çağrısı, hizmetlere yönelik RPC çağrılarına doğrudan dönüştürülür, dağıtılmış ortamlarda iyi bir şekilde karşılaşmayacak bir geveze ve verimli bir iletişim yapmaz. Dağıtılmış Sistem tasarlama sorunları, geliştiricilerin tek parçalı olarak dağıtılmış tasarımlara geçiş yaparken kullandığı varsayımları listeleyen, [dağıtılmış bilgi işlem](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) , yaygın olarak bilinen bir Canon 'nin de bilinen bir Canon 'nin yaygın olduğu bilinmektedir.

Tek bir çözüm yoktur, ancak birkaç. Bir çözüm, iş mikro hizmetlerinin mümkün olduğunca yalımasını içerir. Daha sonra, iç mikro hizmetler arasında zaman uyumsuz iletişim kullanır ve kaba iletişim ile nesneler arasında işlem içi iletişimde tipik olan ayrıntılı iletişimin yerini alır. Bu, çağrıları gruplandırarak ve birden çok iç çağrının sonuçlarını toplayan verileri istemciye döndürerek yapabilirsiniz.

Mikro hizmet tabanlı bir uygulama, genellikle birden çok sunucu veya ana bilgisayar üzerinde bile birden çok işlem veya hizmette çalışan dağıtılmış bir sistemdir. Her hizmet örneği genellikle bir işlemdir. Bu nedenle hizmetlerin, her bir hizmetin doğasına bağlı olarak HTTP, AMQP veya TCP gibi bir ikili protokol gibi işlem temelli iletişim protokolü kullanarak etkileşimde olması gerekir.

Mikro hizmet topluluğu, "[akıllı uç noktalar ve Dumb kanallarının](https://simplicable.com/new/smart-endpoints-and-dumb-pipes)" felsefesini yükseltir. bu Sloga, mikro hizmetler arasında mümkün olduğunca bir tasarımı ve tek bir mikro hizmette mümkün olduğunca ortak bir şekilde teşvik eder. Daha önce açıklandığı gibi, her mikro hizmet kendi verilerini ve kendi etki alanı mantığını sahibidir. Ancak, uçtan uca bir uygulama oluşturan mikro hizmetler genellikle, \* merkezi iş-işlem-düzenleme işlemleri yerıne WS-ve esnek olay odaklı iletişimler yerıne Rest iletişimleri kullanılarak kolayca gerçekleştirilebilir.

Yaygın olarak kullanılan iki protokol, kaynak API 'Leri ile HTTP isteği/yanıtı ve birden çok mikro hizmette güncelleştirme haberleşirken hafif zaman uyumsuz mesajlaşma. Bunlar aşağıdaki bölümlerde daha ayrıntılı olarak açıklanmıştır.

## <a name="communication-types"></a>İletişim türleri

İstemci ve hizmetler, her biri farklı bir senaryoyu ve hedefi hedefleyen birçok farklı iletişim türü aracılığıyla iletişim kurabilir. Başlangıçta, bu tür iletişimler iki eksende sınıflandırılabilirler.

İlk eksen, protokolün zaman uyumlu veya zaman uyumsuz olduğunu tanımlar:

- Zaman uyumlu protokol. HTTP, zaman uyumlu bir protokoldür. İstemci bir istek gönderir ve hizmetten bir yanıt bekler. Bu, zaman uyumlu olabilecek (iş parçacığı engellenmiş) veya zaman uyumsuz (iş parçacığı engellenmeyen) istemci kodu yürütmesinden bağımsızdır ve yanıt sonunda geri aramaya ulaşılacaktır. Buradaki önemli nokta, protokolün (HTTP/HTTPS) zaman uyumlu olması ve istemci kodunun yalnızca HTTP sunucusu yanıtını aldığında görevi devam edevidir.

- Zaman uyumsuz protokol. AMQP (birçok işletim sistemi ve bulut ortamı tarafından desteklenen bir protokol) gibi diğer protokoller zaman uyumsuz iletileri kullanır. İstemci kodu veya ileti gönderici genellikle yanıt beketmez. Yalnızca bir kbıbitmq kuyruğuna ya da başka bir ileti aracısına ileti gönderirken iletiyi gönderir.

İkinci eksen, iletişimin tek bir alıcıya veya birden çok alıcıya sahip olup olmadığını tanımlar:

- Tek alıcı. Her isteğin tam olarak bir alıcı veya hizmet tarafından işlenmesi gerekir. Bu iletişimin bir örneği [komut deseninin](https://en.wikipedia.org/wiki/Command_pattern)bir örneğidir.

- Birden çok alıcı. Her istek, birden çok alıcıya sıfır ile işlenebilir. Bu tür bir iletişim zaman uyumsuz olmalıdır. Örnek olarak, [olay odaklı mimari](https://microservices.io/patterns/data/event-driven-architecture.html)gibi desenlerinde kullanılan [Yayımlama/abone olma](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) mekanizması vardır. Bu, olaylar aracılığıyla birden çok mikro hizmet arasında veri güncelleştirmeleri yayılırken bir olay veri yolu arabirimine veya ileti aracısına dayanır; genellikle [, konuları ve abonelikleri](/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions)kullanarak [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) gibi bir hizmet veri yolu veya benzer yapıt aracılığıyla uygulanır.

Mikro hizmet tabanlı bir uygulama, genellikle bu iletişim stillerinin birleşimini kullanır. En yaygın tür, düzenli bir Web API HTTP hizmeti çağrılırken HTTP/HTTPS gibi zaman uyumlu bir protokolle tek alıcıdır. Mikro hizmetler Ayrıca mikro hizmetler arasındaki zaman uyumsuz iletişim için mesajlaşma protokollerini kullanır.

Bu eksenler, olası iletişim Mekanizmalarını açıklığa kavuşturmak için idealdir, ancak mikro hizmetler oluşturulurken önemli konular değildir. İstemci iş parçacığı yürütmesinin zaman uyumsuz doğası veya seçili protokolün zaman uyumsuz yapısı, mikro hizmetleri tümleştirilirken önemli noktalardır. Önemli *olan* özellikler, mikro hizmetlerinizi, aşağıdaki bölümde açıklandığı gibi mikro hizmetlerin bağımsızlığını koruyarak zaman uyumsuz olarak tümleştiriyor.

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>Zaman uyumsuz mikro hizmet tümleştirmesi, mikro hizmetin bağımsız çalışma sınırı zorlar

Belirtildiği gibi, mikro hizmetler tabanlı bir uygulama oluşturmanın önemli noktaları, mikro hizmetlerinizi tümleştirmeniz yöntemidir. İdeal olarak, iç mikro hizmetler arasındaki iletişimi en aza indirmeye çalışırsınız. Mikro hizmetler arasındaki daha az iletişim, daha iyidir. Ancak çoğu durumda, mikro hizmetleri bir şekilde tümleştirmeniz gerekecektir. Bunu yapmanız gerektiğinde, mikro hizmetler arasındaki iletişimin zaman uyumsuz olması gereken önemli kuraldır. Bu, belirli bir Protokolü (örneğin, zaman uyumsuz mesajlaşma ve zaman uyumlu HTTP) kullanmanız gerektiğini ifade etmez. Yalnızca, mikro hizmetler arasındaki iletişimin yalnızca zaman uyumsuz olarak veri yayarak yapılması ve ilk hizmetin HTTP istek/yanıt işleminin bir parçası olarak diğer iç mikro hizmetlere bağımlı olmaması anlamına gelir.

Mümkünse, sorgular için de değil, birden fazla mikro hizmet arasında zaman uyumlu iletişime (istek/yanıt) hiçbir zaman bağlı değildir. Her mikro hizmetin hedefi, uçtan uca uygulamanın parçası olan diğer hizmetler doğru veya sağlıksız olsa bile, istemci tüketicisi için otonom ve kullanılabilir olmalıdır. Bir mikro hizmetten diğer mikro hizmetlere (bir veri sorgusu için HTTP isteği gerçekleştirmek gibi) bir istemci uygulamasına yanıt sağlayabilmek için bir çağrı yapmanız gerektiğini düşünüyorsanız, bazı mikro hizmetler başarısız olduğunda dayanıklı olmayan bir mimariniz vardır.

Üstelik, Şekil 4-15 ' in ilk bölümünde gösterildiği gibi, HTTP istek zincirleriyle uzun istek/yanıt döngüleri oluştururken olduğu gibi, mikro hizmetler arasında HTTP bağımlılıklarına sahip olmak gibi, yalnızca mikro hizmetlerinizin otonom olmaması, ancak aynı zamanda o zincirdeki hizmetlerden biri de bundan sonra performansından etkilenmesidir.

Diğer bir deyişle, sorgu istekleri gibi mikro hizmetler arasında zaman uyumlu bağımlılıklar eklediğinizde, istemci uygulamaları için genel yanıt süresinin ne kadar kötüleştiğini.

![Mikro hizmetler genelinde üç tür iletişim gösteren diyagram.](./media/communication-in-microservice-architecture/sync-vs-async-patterns-across-microservices.png)

**Şekil 4-15**. Mikro hizmetler arasındaki iletişimde koruma ve desenler

Yukarıdaki diyagramda gösterildiği gibi, zaman uyumlu iletişimde istemci isteğine hizmet verirken mikro hizmetler arasında isteklerin "Zinciri" oluşturulur. Bu bir anti-model. Zaman uyumsuz iletişim mikro hizmetleri, diğer mikro hizmetlerle iletişim kurmak için zaman uyumsuz mesajlar veya http yoklaması kullanır, ancak istemci isteği hemen kullanıma sunulur.

Mikro hizmetinizin başka bir mikro hizmette ek bir eylem oluşturması gerekiyorsa, bu eylemi zaman uyumlu olarak ve özgün mikro hizmet isteği ve yanıt işleminin bir parçası olarak gerçekleştirmeyin. Bunun yerine, zaman uyumsuz olarak (zaman uyumsuz mesajlaşma veya tümleştirme olayları, kuyruklar vb. kullanarak) bunu yapın. Ancak mümkün olduğunca, orijinal zaman uyumlu istek ve yanıt işleminin bir parçası olarak eylemi zaman uyumlu olarak çağırmayın.

Son olarak (ve mikro hizmetleri oluştururken çoğu sorun oluşur), ilk mikro hizmetiniz ilk olarak diğer mikro hizmetlere ait veriler istiyorsa, bu veriler için zaman uyumlu istek yapmaya güvenmeyin. Bunun yerine, nihai tutarlılık (genellikle, yaklaşan bölümlerde açıklandığı gibi tümleştirme olaylarını kullanarak) kullanarak bu verileri (yalnızca ihtiyacınız olan öznitelikleri) ilk hizmetin veritabanına çoğaltın veya yayın.

Daha önce [her bir mikro hizmet için etki alanı modeli sınırlarının tanımlanması](identify-microservice-domain-model-boundaries.md) bölümünde belirtildiği gibi, birkaç mikro hizmette bazı verilerin çoğaltılması yanlış bir tasarım değildir — bu durumda, verileri bu ek etki alanı veya sınırlanmış bağlamın belirli diline veya koşullarına çevirebilir. Örneğin, [Eshoponcontainers uygulamasında](https://github.com/dotnet-architecture/eShopOnContainers) , `identity-api` adında bir varlık olan Kullanıcı verilerinin çoğunun ücretlendirme adlı bir mikro hizmetiniz vardır `User` . Ancak, mikro hizmette Kullanıcı hakkında veri depolamanız gerektiğinde `Ordering` , bunu adlı farklı bir varlık olarak depoladığınızda `Buyer` . `Buyer`Varlık, özgün varlıkla aynı kimliği paylaşır `User` , ancak `Ordering` Kullanıcı profilinin tamamını değil, yalnızca etki alanı için gereken birkaç özniteliğe sahip olabilir.

Nihai tutarlılığı sağlamak için, mikro hizmetlerde verileri zaman uyumsuz olarak iletmek ve yaymak için herhangi bir protokol kullanabilirsiniz. Belirtildiği gibi, bir olay veri yolu veya ileti Aracısı kullanarak tümleştirme olaylarını kullanabilir veya bunun yerine diğer hizmetleri yoklayarak HTTP 'yi de kullanabilirsiniz. Bunun önemi yoktur. Önemli kural, mikro hizmetleriniz arasında zaman uyumlu bağımlılıklar oluşturmamalıdır.

Aşağıdaki bölümlerde, mikro hizmet tabanlı bir uygulamada kullanmayı düşünebileceğiniz birden fazla iletişim stili açıklanmaktadır.

## <a name="communication-styles"></a>İletişim stilleri

Kullanmak istediğiniz iletişim türüne bağlı olarak, iletişim için kullanabileceğiniz pek çok protokol ve seçenek vardır. Zaman uyumlu bir istek/yanıt tabanlı iletişim mekanizması kullanıyorsanız, özellikle hizmetlerinizi Docker konağı veya mikro hizmet kümesi dışında yayımlıyorsanız, HTTP ve REST yaklaşımları gibi protokoller en yaygın olarak kullanılır. Hizmetler arasında dahili olarak (Docker ana bilgisayarınız veya mikro hizmetler kümeniz) iletişim kurıyorsanız, ikili biçimi iletişim Mekanizmalarını (TCP ve ikili biçimi kullanan WCF gibi) de kullanmak isteyebilirsiniz. Alternatif olarak, AMQP gibi zaman uyumsuz, ileti tabanlı iletişim mekanizmaları de kullanabilirsiniz.

Ayrıca, JSON veya XML gibi birden çok ileti biçimi ve hatta ikili biçimler de vardır ve bu da daha verimli olabilir. Seçtiğiniz ikili biçim standart değilse, bu biçimi kullanarak hizmetlerinizi herkese açık bir şekilde yayımlamak iyi bir fikir değildir. Mikro hizmetleriniz arasında dahili iletişim için standart olmayan bir biçim kullanabilirsiniz. Bu işlem, Docker konağı veya mikro hizmet kümeniz (örneğin, Docker orchestrators) içindeki mikro hizmetler arasında iletişim kurarken veya mikro hizmetlerle iletişim kuran özel istemci uygulamaları için yapabilirsiniz.

### <a name="requestresponse-communication-with-http-and-rest"></a>HTTP ve REST ile istek/yanıt iletişimi

İstemci, istek/yanıt iletişimini kullandığında, hizmete bir istek gönderir ve ardından hizmet isteği işler ve bir yanıt gönderir. İstek/yanıt iletişimi, istemci uygulamalarından gerçek zamanlı bir kullanıcı arabirimi (canlı bir kullanıcı arabirimi) için verileri sorgulamak üzere özellikle idealdir. Bu nedenle, bir mikro hizmet mimarisinde, Şekil 4-16 ' de gösterildiği gibi büyük olasılıkla çoğu sorgu için bu iletişim mekanizmasını kullanacaksınız.

![Canlı sorgular ve güncelleştirmeler için istek/yanıt yazışmalar 'yi gösteren diyagram.](./media/communication-in-microservice-architecture/request-response-comms-live-queries-updates.png)

**Şekil 4-16**. HTTP istek/yanıt iletişimini kullanma (zaman uyumlu veya zaman uyumsuz)

Bir istemci, istek/yanıt iletişimini kullandığında, yanıtın kısa bir süre içinde, genellikle bir saniyeden daha az veya en çok birkaç saniye ulaştığını varsayar. Gecikmeli yanıtlar için, sonraki bölümde açıklandığımız farklı bir yaklaşım olan [mesajlaşma desenleri](/azure/architecture/patterns/category/messaging) ve [mesajlaşma teknolojileri](https://en.wikipedia.org/wiki/Message-oriented_middleware)temelinde zaman uyumsuz iletişim uygulamanız gerekir.

İstek/yanıt iletişimi için popüler bir mimari stili [rest](https://en.wikipedia.org/wiki/Representational_state_transfer). Bu yaklaşım, [http](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) PROTOKOLÜNE ve Get, post ve put gibi http fiillerini benimseme ve sıkı bir şekilde bağlanmış. REST, hizmetler oluştururken en yaygın olarak kullanılan mimari iletişim yaklaşımına sahiptir. Web API hizmetlerini ASP.NET Core geliştirirken REST hizmetlerini uygulayabilirsiniz.

Arabirim tanım diliniz olarak HTTP REST hizmetlerini kullanırken ek bir değer vardır. Örneğin, hizmet API 'nizi anlatmak için [Swagger meta verilerini](https://swagger.io/) kullanırsanız, hizmetlerinizi doğrudan keşfedebileceği ve kullanabilen istemci saplamaları üreten araçları kullanabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Marwler. Richardson vade** MODELI Rest modelinin açıklamasını. \
  <https://martinfowler.com/articles/richardsonMaturityModel.html>

- **Swagger** Resmi site. \
  <https://swagger.io/>

### <a name="push-and-real-time-communication-based-on-http"></a>HTTP tabanlı gönderim ve gerçek zamanlı iletişim

Başka bir olasılık (genellikle REST 'den farklı amaçlar için) [ASP.NET SignalR](https://www.asp.net/signalr) ve [WebSockets](https://en.wikipedia.org/wiki/WebSocket)gibi protokoller gibi daha yüksek düzey çerçeveler ile gerçek zamanlı ve bire çok bir iletişimdir.

Şekil 4-17 ' de gösterildiği gibi, gerçek zamanlı HTTP iletişimi, sunucunun bir istemcinin yeni veri istemesine izin vermek yerine, bağlı istemcilere içerik gönderen sunucu koduna sahip olabileceği anlamına gelir.

![SignalR tabanlı gönderim ve gerçek zamanlı yazışmalar 'yi gösteren diyagram.](./media/communication-in-microservice-architecture/one-to-many-communication.png)

**Şekil 4-17**. Bire bir gerçek zamanlı zaman uyumsuz ileti iletişimi

SignalR, bir arka uç sunucusundan istemcilere içerik dağıtmaya yönelik gerçek zamanlı iletişim elde etmenin iyi bir yoludur. İletişim gerçek zamanlı olduğundan, istemci uygulamaları değişiklikleri neredeyse anında gösterir. Bu genellikle, birçok WebSockets bağlantısı (istemci başına) kullanarak WebSockets gibi bir protokol tarafından işlenir. Tipik bir örnek, bir hizmetin bir spor oyunundaki bir değişikliği aynı anda birçok istemci Web uygulaması ile iletişim kurduğuna yönelik bir örnektir.

>[!div class="step-by-step"]
>[Önceki](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) 
> [Sonraki](asynchronous-message-based-communication.md)
