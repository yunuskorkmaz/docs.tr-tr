---
title: API ağ geçidi düzeni karşı doğrudan istemci mikro hizmet iletişim
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | API ağ geçidi düzeni karşı doğrudan istemci mikro hizmet iletişim
keywords: Docker, mikro, ASP.NET, kapsayıcı, API ağ geçidi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fa3f4bb97cf942ee7698b1efa1dcd09b3f2ca571
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="direct-client-to-microservice-communication-versus-the-api-gateway-pattern"></a>API ağ geçidi düzeni karşı doğrudan istemci mikro hizmet iletişim

Mikro mimarisinde her mikro hizmet (genellikle) fine‑grained uç noktalar kümesi sunar. Bu bölümde açıklandığı gibi bu olgu client‑to‑microservice iletişim etkileyebilir.

## <a name="direct-client-to-microservice-communication"></a>Doğrudan istemci mikro hizmet iletişim

Bir doğrudan istemci mikro hizmet iletişim mimarisi kullanan olası bir yaklaşımdır. Bu yaklaşımda, bir istemci uygulaması mikro doğrudan bazıları için Şekil 4-12'de gösterildiği gibi isteğinde bulunabilir.

![](./media/image12.png)

**Şekil 4-12**. Bir doğrudan istemci mikro hizmet iletişim mimarisi kullanma

Bu yaklaşım. Her mikro hizmet bazen her mikro hizmet için farklı bir TCP bağlantı noktası ile ortak bir uç nokta vardır. Belirli bir hizmet için bir URL örneği Azure aşağıdaki URL'de olabilir:

<http://eshoponcontainers.westus.cloudapp.azure.com:88/>

URL kümede kullanılan yük dengeleyiciye eşleyen bir küme, temel bir üretim ortamında hangi sırayla isteklerini mikro arasında dağıtır. Üretim ortamlarında gibi uygulama teslim denetleyici (ADC) olabilir [Azure uygulama ağ geçidi](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) , mikro ve Internet arasında. Bu, yalnızca Yük Dengeleme gerçekleştirir, ancak SSL sonlandırma sunarak hizmetlerinizi korur saydam bir katmanı görür. Bu CPU-yoğun SSL sonlandırma ve Azure uygulama ağ geçidi için yönlendirme diğer görevlerini boşaltarak konaklarınızın yükünü artırır. Herhangi bir durumda, bir yük dengeleyici ve ADC bir mantıksal uygulama mimarisi açısından bakıldığında görünmez.

Bir doğrudan istemci mikro hizmet iletişim mimarisi özellikle istemci uygulaması bir ASP.NET MVC uygulaması gibi bir sunucu tarafı web uygulaması ise küçük mikro hizmet tabanlı bir uygulama için iyi yeterli olabilir. Ancak, büyük ve karmaşık mikro hizmet tabanlı uygulamalar (örneğin, mikro hizmet türleri düzinelerce işlerken) derlerken ve özellikle istemci uygulamaları uzak mobil uygulamalar veya SPA web uygulamaları olduğunda bu yaklaşımı bazı sorunlar yüzler.

Mikro üzerinde temel büyük bir uygulama geliştirirken, aşağıdaki soruları göz önünde bulundurun:

-   *Nasıl istemci uygulamaları arka uç isteklerine sayısını en aza indirmek ve birden çok mikro chatty iletişimi azaltmak?*

Tek bir kullanıcı Arabirimi ekran oluşturmak için birden çok mikro etkileşim Internet üzerinden gidiş-dönüş sayısını artırır. Bu gecikme süresi ve kullanıcı Arabirimi tarafında karmaşıklığını artırır. İdeal olarak, yanıtları verimli bir şekilde sunucu tarafı toplanması gerektiğini — Bu paralel olarak birden çok veri parçalarını geri dönün ve hazır olduğunda hemen bazı kullanıcı Arabirimi verileri gösterebilir beri gecikmesini azaltır.

-   *Nasıl arası kesme sorunları yetkilendirme, veri dönüşümleri ve dinamik istek gönderme gibi işleyebilir?*

Güvenlik ve yetkilendirme her mikro hizmet üzerinde önemli geliştirme çaba gerektirebilir gibi güvenlik ve çapraz kesme sorunları uygulama. Dışarıdan kendilerine doğrudan erişimi kısıtlamak için ve bir API ağ geçidi gibi merkezi bir yerde bu arası kesme sorunları uygulamak için bu hizmetlerin Docker ana bilgisayar veya iç küme içinde sahip olası bir yaklaşımdır.

-   *İstemci uygulamaları Internet kolay protokoller kullanan Hizmetleri ile nasıl iletişim kurabilir?*

(AMQP veya ikili protokolleri gibi) sunucu tarafında kullanılan protokoller istemci uygulamaları genellikle desteklenmez. Bu nedenle, istekleri HTTP/HTTPS gibi protokoller üzerinden gerçekleşen ve gerekir diğer protokoller için daha sonra çevrilmesi. A *man-in--middle* yaklaşım, bu durumda yardımcı olabilir.

-   *Nasıl özellikle mobil uygulamalar için yapılan bir cephesi Şekil?*

Birden çok mikro API için farklı istemci uygulamalarının ihtiyaçlarını iyi tasarlanmamış olabilir. Örneğin, bir mobil uygulama gereksinimlerini bir web uygulaması gereksinimlerini farklı olabilir. Mobil uygulamalar için daha veri yanıtları daha etkili olması için en iyi duruma gerekebilir. Birden çok mikro veri toplayarak ve tek bir veri kümesi döndüren ve bazı durumlarda mobil uygulama tarafından gerekli değildir yanıt herhangi bir veri ortadan bunu yapabilirsiniz. Ve tabi ki, bu verileri sıkıştırmak. Yeniden cephesi veya mobil uygulama ve mikro hizmetler arasında API bu senaryo için kullanışlı olabilir.

## <a name="using-an-api-gateway"></a>Bir API ağ geçidi kullanma

Tasarım ve büyük veya karmaşık mikro hizmet tabanlı uygulamaları birden çok istemci uygulamaları oluşturmak, dikkate alınması gereken iyi bir yaklaşım olabilir bir [API ağ geçidi](https://microservices.io/patterns/apigateway.html). Bu, tek giriş noktası belirli mikro grupları sağlayan bir hizmettir. Aşağıdakine benzer [cephesi düzeni](https://en.wikipedia.org/wiki/Facade_pattern) object‑oriented tasarımdan ancak bu durumda, dağıtılmış bir sistemde bir parçasıdır. API ağ geçidi düzeni bazen "arka uç ön uç için" olarak bilinen [(BFF)](https://samnewman.io/patterns/architectural/bff/) istemci uygulaması gereksinimlerini düşünmek sırasında oluşturmak için.

Şekil 4-13 özel bir API ağ geçidi mikro hizmet tabanlı bir mimariye nasıl sığabilecek gösterir.
Bu diyagramda vurgulamak önemlidir, birden çok bakan tek özel API ağ geçidi hizmeti kullanarak ve farklı istemci uygulamaları. Olgu API ağ geçidi hizmetinizi büyüyen gelişen ve için önemli bir risk olabilir istemci uygulamalardan birçok farklı gereksinimlerine göre. Sonuç olarak, bu farklı ihtiyaçları bloated olacak ve etkili bir şekilde bir tek yapılı uygulama veya tek yapılı hizmet oldukça benzer olabilir. Çok API ağ geçidi birden çok hizmet ya da birden çok daha küçük API ağ geçidi, form faktörünün türü, her bir örneği için bölmeniz önerilir nedeni budur.

![](./media/image13.png)

**Şekil 4-13**. Bir API ağ geçidi kullanılarak uygulanan özel bir Web API hizmet olarak

Bu örnekte, bir kapsayıcı olarak çalışan özel bir Web API hizmeti olarak API ağ geçidi uygulanması.

Böylece her istemci uygulaması gereksinimleri için farklı bir cephesi sahip belirtildiği gibi birkaç API ağ geçidi uygulaması gerekir. Her API ağ geçidi farklı bir sağlayabilir API uyarlanmış büyük olasılıkla bile istemci form faktörünü hangi underneath çağırır birden çok dahili mikro belirli bağdaştırıcı kodu uygulayarak göre her bir istemci uygulama için.

Özel bir API ağ geçidi genellikle bir veri toplayıcısı olduğundan, kendisiyle dikkatli olmanız gerekir. Genellikle tek bir API uygulamanızın tüm iç mikro toplayarak ağ geçidi için iyi bir fikir değil. Bulursa, bir tek yapılı toplayıcısı veya orchestrator olarak davranır ve tüm mikro eşleyerek mikro hizmet otonomisi ihlal ediyor. Bu nedenle, API ağ geçitleri iş sınırları ve değil act bağlı olarak tüm uygulama için bir Toplayıcıya yinelenmeli.

Bazen ayrıntılı bir API ağ geçidi, bir mikro hizmet kendisi de ve bir etki alanı veya iş adı ve ilgili verileri bile sahip. İş veya etki alanı tarafından dikte API ağ geçidi sınırları daha iyi bir tasarım almak için yardımcı olur.

Hassas bir API ağ geçidi kavramı bir UI birleşim hizmetine benzer olduğundan ayrıntı düzeyi API ağ geçidi katmanındaki mikro üzerinde göre daha gelişmiş bileşik UI uygulamalar için özellikle yararlı olabilir. Daha sonra bu konuda aşağıdakiler ele [bileşik kullanıcı Arabirimi oluşturma tabanlı mikro üzerinde](#creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices).

Bu nedenle, birçok Orta ve büyük-ölçekli uygulamalar için özel olarak geliştirilmiş bir API ağ geçidi genellikle iyi bir yaklaşım kullanmaktır ancak tek tek yapılı toplayıcısı ya da benzersiz merkezi özel API ağ geçidi olarak değil.

Başka bir yaklaşım gibi bir ürün kullanmaktır [Azure API Management](https://azure.microsoft.com/services/api-management/) Şekil 4-14'te gösterildiği gibi. Bu yaklaşım yalnızca API ağ geçidi gereksinimlerinizi çözer, ancak, API'lerden Öngörüler toplama gibi özellikler sağlar. API yönetim çözümünü kullanıyorsanız, bir API ağ geçidi yalnızca bir bu tam API yönetimi çözümü içinde bileşenidir.

![](./media/image14.png)

**Şekil 4-14**. API ağ geçidiniz için Azure API Management kullanma

Bu tür bir API ağ geçidi "ince" olduğundan Azure API Management, tek bir API ağ geçidi olabilir olgu gibi bir ürün kullanarak kadar riskli olmadığı durumlarda, bu durumda, bir tek yapılı gelişmesi özel C# kod uygulamaz anlamına gelir Bileşen. 

Bu tür bir ürünün daha giriş iletişimi, burada, ayrıca iç mikro API'lerden filtre yanı sıra bu tek katmandaki yayımlanan API'ler yetkilendirme uygulamak için ters proxy gibi davranır.

Bir API Management sistem Yardım'dan kullanılabilir bilgiler Apı'lerinizi nasıl kullanılacağı konusunda bilgi edinmek ve nasıl performans gösterdiğini. Gerçek zamanlı analiz raporları görüntülemenize izin vererek ve işinizin etkileyebilecek eğilimleri tanımlama bunu. Ayrıca, hakkında daha fazla çevrimiçi ve çevrimdışı analiz için istek ve yanıt etkinlik günlükleri olabilir.

Azure API Management ile bir anahtar, bir belirteç ve IP filtresini kullanarak Apı'lerinizi güvenliğini sağlayabilirsiniz. Bu özellikler, esnek ve hassas kotaları zorlamak ve oran sınırları, Şekil ve ilkelerini kullanarak Apı'lerinizi davranışını değiştirmek ve yanıt önbelleğe alma ile performansı sağlar.

Bu kılavuz ve başvuru örnek uygulaması (eShopOnContainers), biz mimarisi daha basit ve özel yapılan kapsayıcılı mimarisi için Azure API Management gibi PaaS ürünler kullanmadan düz kapsayıcılarında odaklanmak için kısıtlayan. Ancak, Microsoft Azure'da dağıtılan büyük mikro hizmet tabanlı uygulamalar için gözden geçirmek ve Azure API Management temel olarak, API ağ geçitleri için benimsemek için öneririz.

## <a name="drawbacks-of-the-api-gateway-pattern"></a>API ağ geçidi düzeni eksileri

-   En önemli dezavantajı, bir API ağ geçidi uyguladığınızda, iç mikro ile bu katmanı Kuplaj olmasıdır. Bu gibi bağlantı uygulamanız için ciddi sorunlar getirebilir. Bu olası güçlük "Yeni ESB" olarak kaldırmalıdır Vaster Clemens Azure Service Bus ekibine adresindeki Mimarı başvurur "[Mesajlaşma ve mikro](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" GOTO 2016 oturumunda.

-   Mikro API ağ geçidi kullanarak bir ek olası tek hata noktası oluşturur.

-   Bir API ağ geçidi artan yanıt süresi ek ağ çağrısı nedeniyle ortaya çıkarabilir. Ancak, bu ek çağrı genellikle, arabirim, bir istemcinin doğrudan iç mikro çağırma çok chatty olandan daha az etkisi yoktur.

-   Out düzgün ölçeklendirilmiş değil, API ağ geçidi bir ayak bağı olabilir.

-   Özel mantık ve verileri toplama içeriyorsa, bir API ağ geçidi ek geliştirme maliyetini ve gelecekteki bakım gerektirir. Geliştiriciler API ağ geçidi her mikro 's uç noktalarını kullanıma sunmak için güncelleştirmeniz gerekir. Ayrıca, uygulama değişiklikleri iç mikro API ağ geçidi düzeyinde kod değişiklikleri neden olabilir. Ancak, API ağ geçidi yalnızca güvenlik, günlüğe kaydetme ve sürüm oluşturma uygulama varsa (as Azure API Management kullanırken), bu ek geliştirme maliyet geçerli.

-   API ağ geçidi tek bir takım tarafından geliştirilen bir geliştirme performans sorunu olabilir. Birkaç fined düzey API farklı istemci ihtiyaçlarına yanıt veren ağ geçitleri için daha iyi bir yaklaşım neden olan başka bir neden de budur. Ayrıca API ağ geçidi dahili olarak birden çok alanları veya iç mikro üzerinde çalışan farklı ekip tarafından sahip olunan Katmanlar kurabilmeleri.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Charles Uludağ. Desen: API ağ geçidi / arka uç için ön uç**
    [*https://microservices.io/patterns/apigateway.html*](https://microservices.io/patterns/apigateway.html)

-   **Azure API Yönetimi**
    [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

-   **UDI Dahan. Birleşim hizmet odaklı**\
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

-   **Clemens Vasters. Mesajlaşma ve mikro GOTO 2016 adresindeki** (video) [*https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)


>[!div class="step-by-step"]
[Önceki] (tanımlamak-mikro hizmet-etki-model-boundaries.md) [sonraki] (iletişimi-içinde-mikro hizmet-architecture.md)
