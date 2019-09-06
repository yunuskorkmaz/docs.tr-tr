---
title: API ağ geçidi düzenine ve doğrudan istemciden mikro hizmete iletişime karşı
description: API Gateway deseninin ve doğrudan istemciden mikro hizmet iletişiminin farklılıklarını ve kullanımlarını anlayın.
ms.date: 01/07/2019
ms.openlocfilehash: c54287ea3e99ff7fe9faf02898b8c322b756e26f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "70296818"
---
# <a name="the-api-gateway-pattern-versus-the-direct-client-to-microservice-communication"></a>API ağ geçidi düzenine ve doğrudan istemciden mikro hizmete iletişime karşı

Mikro hizmetler mimarisinde, her mikro hizmet hassas uç noktalar kümesi (genellikle) sunar. Bu olgu, bu bölümde açıklandığı gibi istemciden mikro hizmet iletişimini etkileyebilir.

## <a name="direct-client-to-microservice-communication"></a>Doğrudan istemciden mikro hizmete iletişim

Olası bir yaklaşım doğrudan istemciden mikro hizmet iletişim mimarisini kullanmaktır. Bu yaklaşımda, bir istemci uygulaması, Şekil 4-12 ' de gösterildiği gibi, mikro hizmetlerden bazılarına doğrudan istek yapabilir.

![Her uygulamanın tek tek mikro hizmetlerle iletişim kurduğu doğrudan istemciden mikro hizmet iletişim mimarisini gösteren diyagram.](./media/image12.png)

**Şekil 4-12**. Doğrudan istemciden mikro hizmete iletişim mimarisi kullanma

Bu yaklaşımda her mikro hizmet, bazen her mikro hizmet için farklı bir TCP bağlantı noktasıyla birlikte ortak bir uç noktaya sahiptir. Azure 'da, belirli bir hizmet için URL 'nin bir örneği aşağıdaki URL olabilir:

`http://eshoponcontainers.westus.cloudapp.azure.com:88/`

Bir küme temelli bir üretim ortamında, bu URL kümede kullanılan yük dengeleyiciye eşlenir ve bu da istekleri mikro hizmetlere dağıtır. Üretim ortamlarında, mikro hizmetleriniz ve Internet arasında [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) gibi bir uygulama teslim DENETLEYICISI (ADC) olabilir. Bu, yalnızca yük dengeleme gerçekleştirmeyen, ancak SSL sonlandırması sunarak hizmetlerinizin güvenliğini sağlayan saydam bir katman gibi davranır. Bu, CPU kullanımı yoğun SSL sonlandırmasını ve diğer yönlendirme görevlerini Azure Application Gateway yük devrederken konaklarınızın yükünü geliştirir. Herhangi bir durumda, bir yük dengeleyici ve ADC, bir mantıksal uygulama mimarisi görünüm noktasından saydamdır.

Özellikle, istemci uygulaması ASP.NET MVC uygulaması gibi bir sunucu tarafı Web uygulaması ise, doğrudan istemciden mikro hizmet iletişim mimarisi küçük bir mikro hizmet tabanlı uygulama için yeterince iyi olabilir. Ancak, büyük ve karmaşık mikro hizmet tabanlı uygulamalar oluşturduğunuzda (örneğin, onlarca mikro hizmet türünü işlerken) ve özellikle de istemci uygulamaları uzak mobil uygulamalar veya SPA Web uygulamaları olduğunda, bu yaklaşım birkaç soruna yaklaşımlar.

Mikro hizmetlere dayalı büyük bir uygulama geliştirirken aşağıdaki soruları göz önünde bulundurun:

- *İstemci uygulamaları arka uca istek sayısını en aza indirir ve birden fazla mikro hizmete geveze iletişimini azaltır mı?*

Tek bir kullanıcı arabirimi ekranı oluşturmak için birden fazla mikro hizmet ile etkileşim kurmak, Internet üzerindeki gidiş dönüş sayısını artırır. Bu, UI tarafında gecikme ve karmaşıklık düzeyini artırır. İdeal olarak, yanıtlar sunucu tarafında etkin bir şekilde toplanmalıdır. Bu, birden çok veri parçası paralel olarak geri geldiğinden ve bazı Kullanıcı arabirimi, verileri kullanılabilir duruma geldiğinde gösterebilir.

- *Yetkilendirme, veri dönüştürmeleri ve dinamik istek dağıtma gibi çapraz kesme sorunlarını nasıl işleyeirsiniz?*

Her mikro hizmette güvenlik ve yetkilendirme gibi güvenlik ve çapraz kesme sorunları uygulamak, önemli geliştirme çabalarını gerektirebilir. Olası bir yaklaşım, bu hizmetlerin, dışarıdan doğrudan erişimini kısıtlamak ve bu çapraz kesme sorunlarını bir API ağ geçidi gibi merkezi bir yerde uygulamak için, Docker konağı veya iç küme içinde bu hizmetlerden biridir.

- *İstemci uygulamaları, Internet 'e yönelik olmayan protokoller kullanan hizmetlerle nasıl iletişim kurabilir?*

Sunucu tarafında kullanılan protokoller (AMQP veya binary protokolleri gibi) genellikle istemci uygulamalarında desteklenmez. Bu nedenle, isteklerin HTTP/HTTPS gibi protokoller aracılığıyla gerçekleştirilmesi ve daha sonra diğer protokollere çevrilmesi gerekir. *Orta noktadan adam* yaklaşımı bu durumda yardımcı olabilir.

- *Mobil uygulamalar için özellikle bir façlade 'yi nasıl şekillendirebilirsiniz?*

Birden fazla mikro hizmetin API 'SI, farklı istemci uygulamalarının ihtiyaçları için iyi tasarlanmayabilir. Örneğin, bir mobil uygulamanın ihtiyaçları bir Web uygulamasının ihtiyaçlarına göre farklı olabilir. Mobil uygulamalar için, veri yanıtlarının daha verimli olması için daha da iyi hale getirmeniz gerekebilir. Bunu, birden fazla mikro hizmetten veri toplayarak ve tek bir veri kümesi döndürerek ve bazen, yanıtta, mobil uygulama için gerekli olmayan verileri ortadan kaldırarak yapabilirsiniz. Tabii ki, bu verileri sıkıştırabilirsiniz. Yine, mobil uygulama ve mikro hizmetler arasında bir façlade veya API, bu senaryoya uygun olabilir.

## <a name="why-consider-api-gateways-instead-of-direct-client-to-microservice-communication"></a>İstemci-mikro hizmet iletişimi için API ağ geçitlerini neden kabul etmeliyim?

Mikro hizmetler mimarisinde, istemci uygulamalarının genellikle birden fazla mikro hizmetten işlevselliği kullanması gerekir. Bu tüketim doğrudan gerçekleştirilirse, istemcinin mikro hizmet uç noktalarına birden çok çağrı işlemesi gerekir. Uygulama geliştikçe ve yeni mikro hizmetler tanıtıldığında veya var olan mikro hizmetler güncelleştirilirse ne olur? Uygulamanızda çok sayıda mikro hizmet varsa, istemci uygulamalarından çok sayıda uç nokta bu şekilde işlenerek bir nightmcan olabilir. İstemci uygulaması bu iç uç noktalara bağlı olduğundan, mikro hizmetleri gelecekte gelişen istemci uygulamalar için yüksek etkiye neden olabilir.

Bu nedenle, bir ara düzeyi veya yöneltme (ağ geçidi) katmanının olması, mikro hizmet tabanlı uygulamalar için çok kullanışlı olabilir. API ağ geçitleriniz yoksa, istemci uygulamalar istekleri doğrudan mikro hizmetlere göndermelidir ve aşağıdaki sorunlar gibi sorunlar oluşturur:

- **Kuponu**: API ağ geçidi stili olmadan, istemci uygulamaları iç mikro hizmetlere bağlanmış demektir. İstemci uygulamaları, uygulamanın birden çok alanının mikro hizmetlerde nasıl parçalanduğuna bilmelidir. İç mikro hizmetleri geliştirme ve yeniden düzenleme işlemleri sırasında, istemci uygulamalarından gelen iç mikro hizmetlere doğrudan başvuru nedeniyle istemci uygulamalarında olumsuz değişikliklere neden olduğu için bu eylemlerin bakımı oldukça kötü olur. İstemci uygulamalarının sıklıkla güncelleştirilmeleri gerekir, çözüm daha zor hale getirir.

- **Gidiş dönüş sayısı çok fazla**: İstemci uygulamasındaki tek bir sayfa/ekran birden çok hizmete birkaç çağrı gerektirebilir. Bu, istemci ile sunucu arasında birden çok ağ gidiş dönüşde oluşmasına neden olabilir, önemli gecikme süresi ekler. Ara düzeyde işlenen toplama, istemci uygulaması için performans ve Kullanıcı deneyimini iyileştirebilir.

- **Güvenlik sorunları**: Ağ Geçidi olmadan, tüm mikro hizmetler "dış dünya" olarak sunulmalıdır, böylece istemci uygulamaları tarafından doğrudan kullanılmayan iç mikro hizmetleri gizleyerek saldırı yüzeyi daha büyük olur. Saldırı yüzeyi ne kadar küçük olursa, uygulamanız daha güvenli olabilir.

- **Çapraz kesme sorunları**: Herkese açık yayımlanan her mikro hizmet, yetkilendirme, SSL vb. gibi sorunları ele almalıdır. Birçok durumda, iç mikro hizmetlerin basitleşilmesi için bu konular tek bir katmanda işlenebilir.

## <a name="what-is-the-api-gateway-pattern"></a>API ağ geçidi deseninin anlamı nedir?

Birden çok istemci uygulaması ile büyük veya karmaşık mikro hizmet tabanlı uygulamalar tasarladığınızda ve derlediğinizde, bir [API ağ geçidi](https://microservices.io/patterns/apigateway.html)olması iyi bir yaklaşım olabilir. Bu, belirli mikro hizmet grupları için tek girişli bir nokta sağlayan bir hizmettir. Nesne odaklı tasarımın on [yıl düzenine](https://en.wikipedia.org/wiki/Facade_pattern) benzer, ancak bu durumda dağıtılmış bir sistemin parçasıdır. Ayrıca, istemci uygulamanın ihtiyaçlarını düşünirken sizin oluşturduğunuz için, API ağ geçidi, bazen "ön uç için arka uç" ([BFF](https://samnewman.io/patterns/architectural/bff/)) olarak da bilinir.

Bu nedenle, API Gateway istemci uygulamaları ve mikro hizmetler arasında yer alır. Ters proxy görevi görür ve istekleri istemcilerden hizmetlere yönlendirme. Ayrıca kimlik doğrulaması, SSL sonlandırma ve önbellek gibi ek çapraz kesme özellikleri de sağlayabilir.

Şekil 4-13, özel bir API ağ geçidinin yalnızca birkaç mikro hizmetle basitleştirilmiş bir mikro hizmet tabanlı mimariye nasıl uyadığını gösterir.

![Özel bir hizmet olarak uygulanan bir API ağ geçidini gösteren diyagram, böylece uygulamalar tek bir uç noktaya bağlanır, bu da istekleri bağımsız mikro hizmetlere iletmek üzere yapılandırılmıştır.](./media/image13.png)

**Şekil 4-13**. Özel hizmet olarak uygulanan bir API ağ geçidi kullanma

Bu örnekte, API Gateway bir kapsayıcı olarak çalışan özel bir ASP.NET Core WebHost hizmeti olarak uygulanır.

Bu diyagramda, birden çok ve farklı istemci uygulamalarına yönelik tek bir özel API Gateway hizmeti kullandığınızı vurgulamak önemlidir. API Gateway hizmetiniz, istemci uygulamalarından birçok farklı gereksinime göre büyümekte ve gelişeceğinden, bu olgu önemli bir risk olabilir. Sonuç olarak, bu farklı gereksinimler ve etkili bir şekilde tek parçalı bir uygulamaya veya tek parçalı bir hizmete benzer bir şekilde, bu uygulama için de şişecektir. Bu nedenle, API ağ geçidini birden çok hizmete veya birden çok daha küçük API ağ geçidine, örneğin istemci uygulaması form faktörü türüne göre ayırmak çok fazla önerilir.

API ağ geçidi modelini uygularken dikkatli olmanız gerekir. Genellikle uygulamanızın tüm iç mikro hizmetlerini toplayarak tek bir API ağ geçidinin olması iyi bir fikir değildir. Bunu yapıyorsa, tek parçalı bir toplayıcı veya Orchestrator gibi davranır ve mikro hizmet bağımsız çalışma sınırı tüm mikro hizmetlere eşlenerek çiğneniyor.

Bu nedenle, API ağ geçitleri iş sınırlarına ve istemci uygulamalarına göre ayrılmış olmalıdır ve tüm iç mikro hizmetler için tek bir toplayıcı işlevi görür.

API ağ geçidi katmanını birden çok API ağ geçidine bölmek için, uygulamanızın birden çok istemci uygulaması varsa, bu, birden çok API ağ geçidi türü tanımlanırken birincil bir Özet olabilir, böylece her bir istemci uygulamasının ihtiyaçlarına yönelik olarak farklı bir façlade sağlayabilirsiniz. Bu durum, her API ağ geçidinin her bir istemci uygulama türü için uyarlanmış farklı bir API sağlayabildiği ([BFF](https://samnewman.io/patterns/architectural/bff/)) adlı bir modeldir. Aşağıdaki görüntüde gösterildiği gibi birden çok iç mikro hizmet:

![API ağ geçitlerinin istemci türüne göre birbirinden ayrılmış olduğu birden çok özel API ağ geçidini gösteren diyagram; biri mobil istemciler ve bir Web istemcileri için. Geleneksel bir Web uygulaması, Web API ağ geçidini kullanan bir MVC mikro hizmetine bağlanır.](./media/image13.1.png)

**Şekil 4-13.1**. Birden çok özel API ağ geçidi kullanma

Önceki görüntüde, çok ayrıntılı API ağ geçitleri olan basitleştirilmiş bir mimari gösterilmektedir. Bu durumda, her API ağ geçidi için tanımlanan sınırlar yalnızca, istemci uygulaması başına gereken API 'yi temel alan "ön uç için arka uç" ([BFF](https://samnewman.io/patterns/architectural/bff/)) düzenine dayanır. Ancak, daha büyük uygulamalarda Ayrıca daha fazla da ilerlemelidir ve ikinci bir tasarım özeti olarak iş sınırlarına göre ek API ağ geçitleri oluşturmalısınız.

## <a name="main-features-in-the-api-gateway-pattern"></a>API ağ geçidi düzenindeki ana Özellikler

Bir API ağ geçidi, birden çok özellik sunabilir. Ürüne bağlı olarak, daha zengin veya daha basit özellikler sunabilir, ancak herhangi bir API ağ geçidi için en önemli ve temel özellikler aşağıdaki tasarım desenlerinden gelir:

**Ters proxy veya ağ geçidi yönlendirmesi.** API Gateway, istekleri (katman 7 yönlendirme, genellikle HTTP istekleri) iç mikro hizmetlerin uç noktalarına yönlendirmek veya yönlendirmek için ters bir ara sunucu sunar. Ağ Geçidi, istemci uygulamaları için tek bir uç nokta veya URL sağlar ve istekleri dahili bir mikro hizmet grubuyla dahili olarak eşler. Bu yönlendirme özelliği, istemci uygulamalarını mikro hizmetlerden ayırt etmeye yardımcı olur, ancak tek parçalı API ve istemci uygulamaları arasındaki API ağ geçidine oturarak tek parçalı bir API 'YI modernleştirirken oldukça uygun hale gelir ve yeni mikro hizmet olarak yeni API 'Ler ekleyebilirsiniz hala eski monoparçalı API 'YI kullanırken, daha sonra çok sayıda mikro hizmete bölünene kadar. API ağ geçidi nedeniyle, kullanılmakta olan API 'Lerin iç mikro hizmetler veya tek parçalı bir API olarak uygulanıp, tek parçalı API 'yi, API ağ geçidi yönlendirmesi sayesinde mikro hizmetlere geliştirmekte ve yeniden düzenlemeye karşı daha önemlisi, istemci uygulamaları fark görmez , istemci uygulamaları herhangi bir URI değişikliğine etkilenmeyecek.

Daha fazla bilgi için bkz. [ağ geçidi yönlendirme model](https://docs.microsoft.com/azure/architecture/patterns/gateway-routing).

**Toplama istekleri.** Ağ Geçidi deseninin bir parçası olarak, birden çok iç mikro hizmeti tek bir istemci isteğinde hedefleyen birden çok istemci isteğini (genellikle HTTP istekleri) toplayabilirsiniz. Bu model, bir istemci sayfası/ekranının birkaç mikro hizmetten bilgi ihtiyacı olduğunda özellikle kullanışlıdır. Bu yaklaşımda istemci uygulaması, API ağ geçidine, iç mikro hizmetlere birkaç istek gönderen ve sonra sonuçları toplayan ve her şeyi istemci uygulamasına gönderen tek bir istek gönderir. Bu tasarım deseninin başlıca avantajı ve hedefi, istemci uygulamaları ile arka uç API 'SI arasındaki azaltmaya azaltmaktır. Bu, özellikle de mikro hizmetlerin canlı olduğu veri merkezinde (örneğin, mobil uygulamalar veya SPA uygulamalarından gelen istekler gibi) uzak uygulamalar için önemlidir. istemci uzak tarayıcılarında Javascript 'ten gelin. Sunucu ortamındaki istekleri gerçekleştiren düzenli Web uygulamaları için (ASP.NET Core MVC web uygulaması gibi), gecikme süresi uzak istemci uygulamalarına göre çok daha küçük olduğu için bu model bu kadar önemli değildir.

Kullandığınız API Gateway ürününe bağlı olarak, bu toplamayı gerçekleştirebilir. Bununla birlikte, çoğu durumda, API ağ geçidinin kapsamı altında toplama mikro hizmetleri oluşturmak daha esnektir, bu yüzden toplama 'yı kodda (yani, C# kod) tanımlayın:

Daha fazla bilgi için bkz. [ağ geçidi toplama stili](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation).

**Çapraz kesme sorunları veya ağ geçidi boşaltma.** Her bir API ağ geçidi ürünü tarafından sunulan özelliklere bağlı olarak, her bir mikro hizmetten bağımsız olarak tek bir katmanda çapraz kesme sorunlarını birleştirerek her bir mikro hizmetin uygulanmasını kolaylaştıran ağ geçidine işlevsellik devreolursunuz. Bu özellikle, aşağıdaki işlev gibi her iç mikro hizmette düzgün şekilde uygulanması karmaşık olabilecek özelleştirilmiş özellikler için kullanışlıdır:

- Kimlik doğrulaması ve yetkilendirme
- Hizmet bulma tümleştirmesi
- Yanıtları Önbelleğe Alma
- Yeniden deneme ilkeleri, devre kesici ve QoS
- Hız sınırlandırma ve kısıtlama
- Yük Dengeleme
- Günlüğe kaydetme, izleme, bağıntı
- Üstbilgiler, sorgu dizeleri ve talep dönüştürme
- IP beyaz listesi

Daha fazla bilgi için bkz. [ağ geçidi boşaltma model](https://docs.microsoft.com/azure/architecture/patterns/gateway-offloading).

## <a name="using-products-with-api-gateway-features"></a>API Gateway özellikleriyle ürünleri kullanma

Her uygulamaya bağlı olarak API ağ geçitleri ürünleri tarafından sunulan çok sayıda çapraz kesme konusu bulunabilir. Buradan keşfetmeye başlayacağız:

- [Azure API Management](https://azure.microsoft.com/services/api-management/)
- [Ocelot](https://github.com/ThreeMammals/Ocelot)

### <a name="azure-api-management"></a>Azure API Management

[Azure API Management](https://azure.microsoft.com/services/api-management/) (Şekil 4-14 ' de gösterildiği gibi) yalnızca API ağ geçidi ihtiyaçlarınızı çözmemektedir, ancak API 'lerinizden öngörüleri toplama gibi özellikler sağlar. Bir API Management çözümü kullanıyorsanız, API Gateway yalnızca bu tam API Yönetimi çözümünde bulunan bir bileşendir.

![Azure API Management, API ağ geçidinizi ve günlük, güvenlik, ölçüm vb. gibi yönetim gereksinimlerinizi çözer.](./media/api-gateway-azure-api-management.png)

**Şekil 4-14**. API ağ geçidiniz için Azure API Management kullanma

Bu durumda, Azure API Management gibi bir ürün kullanırken, bu tür API ağ geçitleri "THINNER" C# olduğundan, bir API ağ geçidine sahip olabilirsiniz. tek parçalı bileşen. 

API Gateway ürünleri, genellikle iç mikro hizmetlerden API 'Leri filtreleyebileceğiniz ve bu tek katmandaki yayımlanmış API 'lere yetkilendirme yapan giriş iletişimi için ters bir ara sunucu gibi davranır.

API Management bir sistem tarafından sunulan Öngörüler, API 'lerinizin nasıl kullanıldığını ve nasıl çalıştığını anlayabilmeniz için size yardımcı olur. Bu, neredeyse gerçek zamanlı analiz raporlarını görüntülemenize ve işinizi etkileyebilecek eğilimleri tanımlamaya izin vererek bunu yapabilirler. Ayrıca, daha fazla çevrimiçi ve çevrimdışı analiz için istek ve yanıt etkinliği ile ilgili günlüklere sahip olabilirsiniz.

Azure API Management ile API 'lerinizi bir anahtar, belirteç ve IP filtrelemesi kullanarak güvenli hale getirebilirsiniz. Bu özellikler esnek ve ayrıntılı kotaları ve oran sınırlarını zorlamanıza, ilkeleri kullanarak API 'lerinizin şeklini ve davranışını değiştirmenize ve yanıt önbelleğe alma ile performansı iyileştirmenize olanak tanır.

Bu kılavuzda ve başvuru örnek uygulamasında (eShopOnContainers), mimari Azure API Management gibi PaaS ürünlerini kullanmadan düz kapsayıcılara odaklanmak için daha basit ve özel olarak oluşturulmuş bir mimari ile sınırlandırılmıştır. Ancak Microsoft Azure dağıtılan büyük mikro hizmet tabanlı uygulamalar için, Azure API Management 'YI üretimde API ağ geçitlerinizin temeli olarak değerlendirmenizi öneririz.

### <a name="ocelot"></a>Ocelot

[Ocelot](https://github.com/ThreeMammals/Ocelot) , daha basit yaklaşımlar için önerilen hafıf bir API ağ geçididir. Ocelot, özellikle sistemlerinde Birleşik giriş noktaları gerektiren mikro hizmetler mimarisi için oluşturulmuş açık kaynaklı bir .NET Core API ağ geçididir. Hafif, hızlı, ölçeklenebilir ve diğer birçok özellik arasında yönlendirme ve kimlik doğrulaması sağlar.

[Eshoponcontainers başvuru uygulaması](https://github.com/dotnet-architecture/eShopOnContainers) Için Ocelot ' ı seçme ana nedeni, Ocelot 'nin mikro hizmetlerinizi dağıttığınız uygulama dağıtım ortamına dağıtabileceğiniz bir .NET Core hafif API ağ geçidi olmasından kaynaklanır/ Docker Konağı, Kubernetes vb. gibi kapsayıcılar. .NET Core temel alınarak, Linux veya Windows üzerinde dağıtmanıza izin veren platformlar arası bir platformdur.

Kapsayıcılarda çalışan özel API ağ geçitlerini gösteren önceki diyagramlar, bir kapsayıcıda ve mikro hizmet tabanlı bir uygulamada Ocelot 'yi de nasıl çalıştıracağınızı tam olarak nasıl kullanabileceğinizi gösterir.

Ayrıca, Pazar sunumu API ağ geçitleri özelliklerinde, Apiayıklanan, Kong, MuleSoft, WSO2 ve hizmet ağı giriş denetleyicisi özellikleri için Linkerd ve Istio gibi diğer ürünlerden daha birçok ürün vardır.

İlk mimari ve desenler açıklaması bölümlerinden sonra, sonraki bölümlerde, [Ocelot](https://github.com/ThreeMammals/Ocelot)Ile API ağ geçitlerinin nasıl uygulanacağı açıklanmaktadır.

## <a name="drawbacks-of-the-api-gateway-pattern"></a>API ağ geçidi deseninin dezavantajları

- En önemli sakıncası, bir API ağ geçidini uyguladığınızda bu katmana iç mikro hizmetlerle geçidinizin verilir. Bunun gibi bir başvuru, uygulamanız için ciddi zorluklar ortaya çıkarabilir. Azure Service Bus ekibinden bir mimari olan Clemens vaster, "[mesajlaşma ve mikro hizmetler](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" oturumunda "yeni ESB" olarak, goto 2016 adresindeki bu olası zorluklar anlamına gelir.

- Mikro hizmetler API ağ geçidi kullanmak olası bir tek hata noktası oluşturur.

- API ağ geçidi, ek ağ çağrısı nedeniyle daha fazla yanıt süresi ortaya çıkarabilir. Ancak, bu ek çağrı genellikle iç mikro hizmetleri doğrudan çağıran çok geveze bir istemci arabirimine sahip olmaktan daha az etkiye sahiptir.

- Düzgün şekilde ölçeklenmiyorsa, API Gateway bir performans sorunu olabilir.

- API ağ geçidi, özel mantık ve veri toplamayı içeriyorsa ek geliştirme maliyeti ve gelecekteki bakım gerektirir. Geliştiriciler, her mikro hizmetin uç noktalarını göstermek için API ağ geçidini güncelleştirmelidir. Üstelik, iç mikro hizmetlerde yapılan uygulama değişiklikleri API ağ geçidi düzeyinde kod değişikliklerine neden olabilir. Ancak, API Gateway yalnızca güvenlik, günlüğe kaydetme ve sürüm oluşturma (Azure API Management kullanırken olduğu gibi) uygualıyorsa, bu ek geliştirme maliyeti uygulanmayabilir.

- API Gateway tek bir takım tarafından geliştirilirse, bir geliştirme sorunu olabilir. Bu, farklı istemci ihtiyaçlarına yanıt veren birkaç fined API ağ geçidine sahip olmak için daha iyi bir yaklaşıma neden olur. Ayrıca, API ağ geçidini dahili mikro Hizmetlerde çalışan farklı takımların sahip olduğu birden çok alana veya katmana ayırabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

- **Chris Richardson. Kalıp Ön uç için API ağ geçidi/arka uç** \
  <https://microservices.io/patterns/apigateway.html>

- **API ağ geçidi kalıbı** \
  <https://docs.microsoft.com/azure/architecture/microservices/gateway>

- **Toplama ve oluşturma deseninin** \
  <https://microservices.io/patterns/data/api-composition.html>

- **Azure API Management** \
  <https://azure.microsoft.com/services/api-management/>

- **UDI Dahan. Hizmet odaklı bileşim** \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

- **Clemens Valar. GIT 2016 ' de mesajlaşma ve mikro hizmetler (video)**  \
  <https://www.youtube.com/watch?v=rXi5CLjIQ9k>

- **Bir Nutshell Içinde API ağ geçidi** (ASP.net Core API Gateway öğreticisi serisi) \
  <https://www.pogsdotnet.com/2018/08/api-gateway-in-nutshell.html>

>[!div class="step-by-step"]
>[Önceki](identify-microservice-domain-model-boundaries.md)İleri
>[](communication-in-microservice-architecture.md)
