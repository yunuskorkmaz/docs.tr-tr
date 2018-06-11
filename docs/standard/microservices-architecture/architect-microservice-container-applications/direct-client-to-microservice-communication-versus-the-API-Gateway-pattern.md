---
title: API ağ geçidi düzeni doğrudan istemci mikro hizmet iletişim karşılaştırması
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | API ağ geçidi düzeni doğrudan istemci mikro hizmet iletişim karşılaştırması
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/07/2018
ms.openlocfilehash: 75a7c0557319ca948d2112ba0a58f1761368e6f3
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231557"
---
# <a name="the-api-gateway-pattern-versus-the-direct-client-to-microservice-communication"></a>API ağ geçidi düzeni doğrudan istemci mikro hizmet iletişim karşılaştırması

Mikro mimarisinde her mikro hizmet (genellikle) fine‑grained uç noktalar kümesi sunar. Bu bölümde açıklandığı gibi bu olgu client‑to‑microservice iletişim etkileyebilir.

## <a name="direct-client-to-microservice-communication"></a>Doğrudan istemci mikro hizmet iletişim

Bir doğrudan istemci mikro hizmet iletişim mimarisi kullanan olası bir yaklaşımdır. Bu yaklaşımda, bir istemci uygulaması mikro doğrudan bazıları için Şekil 4-12'de gösterildiği gibi isteğinde bulunabilir.

![Doğrudan istemci mikro hizmet iletişim mimarisi gösteren diyagram](./media/image12.png)

**Şekil 4-12**. Bir doğrudan istemci mikro hizmet iletişim mimarisi kullanma

Bu yaklaşım. Her mikro hizmet bazen her mikro hizmet için farklı bir TCP bağlantı noktası ile ortak bir uç nokta vardır. Belirli bir hizmet için bir URL örneği Azure aşağıdaki URL'de olabilir:

<http://eshoponcontainers.westus.cloudapp.azure.com:88/>

URL kümede kullanılan yük dengeleyiciye eşleyen bir küme, temel bir üretim ortamında hangi sırayla isteklerini mikro arasında dağıtır. Üretim ortamlarında gibi uygulama teslim denetleyici (ADC) olabilir [Azure uygulama ağ geçidi](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) , mikro ve Internet arasında. Bu, yalnızca Yük Dengeleme gerçekleştirir, ancak SSL sonlandırma sunarak hizmetlerinizi korur saydam bir katmanı görür. Bu CPU-yoğun SSL sonlandırma ve Azure uygulama ağ geçidi için yönlendirme diğer görevlerini boşaltarak konaklarınızın yükünü artırır. Herhangi bir durumda, bir yük dengeleyici ve ADC bir mantıksal uygulama mimarisi açısından bakıldığında görünmez.

Bir doğrudan istemci mikro hizmet iletişim mimarisi özellikle istemci uygulaması bir ASP.NET MVC uygulaması gibi bir sunucu tarafı web uygulaması ise küçük mikro hizmet tabanlı bir uygulama için iyi yeterli olabilir. Ancak, büyük ve karmaşık mikro hizmet tabanlı uygulamalar (örneğin, mikro hizmet türleri düzinelerce işlerken) derlerken ve özellikle istemci uygulamaları uzak mobil uygulamalar veya SPA web uygulamaları olduğunda bu yaklaşımı bazı sorunlar yüzler.

Mikro üzerinde temel büyük bir uygulama geliştirirken, aşağıdaki soruları göz önünde bulundurun:

- *Nasıl istemci uygulamaları arka uç isteklerine sayısını en aza indirmek ve birden çok mikro chatty iletişimi azaltmak?*

Tek bir kullanıcı Arabirimi ekran oluşturmak için birden çok mikro etkileşim gidiş dönüş sayısı Internet üzerinden artırır. Bu gecikme süresi ve kullanıcı Arabirimi tarafında karmaşıklığını artırır. İdeal olarak, yanıtları sunucu tarafı verimli bir şekilde toplanması. Paralel olarak birden çok veri parçalarını geri dönün ve hazır olduğunda hemen bazı kullanıcı Arabirimi verileri gösterebilir beri gecikmesini azaltır.

- *Nasıl arası kesme sorunları yetkilendirme, veri dönüşümleri ve dinamik istek gönderme gibi işleyebilir?*

Güvenlik ve yetkilendirme her mikro hizmet üzerinde önemli geliştirme çaba gerektirebilir gibi güvenlik ve çapraz kesme sorunları uygulama. Bu hizmetleri, Docker ana bilgisayar veya iç küme dışarıdan kendilerine doğrudan erişimi kısıtlamak için ve bir API ağ geçidi gibi merkezi bir yerde bu arası kesme sorunları uygulamak için içinde olası bir yaklaşımdır.

- *İstemci uygulamaları Internet kolay protokoller kullanan Hizmetleri ile nasıl iletişim kurabilir?*

(AMQP veya ikili protokolleri gibi) sunucu tarafında kullanılan protokoller istemci uygulamaları genellikle desteklenmez. Bu nedenle, istekleri HTTP/HTTPS gibi protokoller üzerinden gerçekleşen ve gerekir diğer protokoller için daha sonra çevrilmesi. A *man-in--middle* yaklaşım, bu durumda yardımcı olabilir.

- *Nasıl özellikle mobil uygulamalar için yapılan bir cephesi Şekil?*

Birden çok mikro API için farklı istemci uygulamalarının ihtiyaçlarını iyi tasarlanmamış olabilir. Örneğin, bir mobil uygulama gereksinimlerini bir web uygulaması gereksinimlerini farklı olabilir. Mobil uygulamalar için daha veri yanıtları daha etkili olması için en iyi duruma gerekebilir. Birden çok mikro veri toplayarak ve tek bir veri kümesi döndüren ve bazı durumlarda mobil uygulama tarafından gerekli değildir yanıt herhangi bir veri ortadan bunu yapabilirsiniz. Ve tabi ki, bu verileri sıkıştırmak. Yeniden cephesi veya mobil uygulama ve mikro hizmetler arasında API bu senaryo için kullanışlı olabilir.

## <a name="why-consider-api-gateways-instead-of-direct-client-to-microservice-communication"></a>Neden yerine doğrudan istemci mikro hizmet iletişim API ağ geçitleri göz önünde bulundurun

Mikro mimarisinde, birden fazla mikro hizmet işlevselliği kullanmak istemci uygulamaları genellikle gerekir. Bu tüketim doğrudan gerçekleştirilirse, istemcinin mikro hizmet uç noktaları için birden çok çağrıları işlemek gerekir. Uygulama dönüşmesi ve yeni mikro sunulan veya varolan mikro güncelleştirilmiş ne olur? Uygulamanız çok sayıda mikro varsa, istemci uygulamalardan çok fazla sayıda uç işleme bir onarımı kabus olabilir. İstemci uygulaması bu dahili Uç noktalara bağlı olduğundan, mikro gelecekte gelişen istemci uygulamaları için yüksek etkisi neden olabilir.

Bu nedenle, bir ara düzeyi veya yöneltme (ağ geçidi) katmanına sahip mikro hizmet tabanlı uygulamalar için çok kullanışlı olabilir. API ağ geçidi yoksa, istemci uygulamaları isteklerini doğrudan mikro hizmetler göndermelidir ve aşağıdaki sorunları gibi sorunlar başlatır:

- **Kuplaj**: API ağ geçidi deseni istemci uygulamaları için iç mikro bağlı değildir. İstemci uygulamaları, uygulamanın birden çok alanlarında mikro içinde nasıl ayrılmış bilmeniz gerekir. Gelişen ve iç mikro yeniden düzenleme, bu eylemleri etkisi zaman bakım asıl hatalı bunlar önemli değişiklikler iç mikro doğrudan başvurusunu istemciden nedeniyle istemci uygulamaları için uygulamaları nedeni. Çözüm gelişmesi daha zor hale sık güncelleştirilmesi istemci uygulamaları gerekir.

- **Çok fazla gidiş dönüş**: tek bir sayfa/ekran istemci uygulamasında birden fazla hizmet birkaç çağrı gerektirebilir. Birden fazla ağ sonuç dönüşleri önemli gecikme ekleme, sunucu ile istemci arasında yuvarlak. Bir ara düzeyinde ele toplama istemci uygulaması performans ve kullanıcı deneyimini iyileştirmek.

- **Güvenlik sorunları**: bir ağ geçidi tüm mikro "saldırı yüzeyini doğrudan istemci uygulamaları tarafından kullanılan iç mikro Gizle durumunda büyük yapmadan dış dünya" sunulmalıdır. Daha küçük saldırı yüzeyini, uygulamanızı daha güvenli olabilir.

- **Çapraz kesme sorunları**: genel olarak yayımlanan her mikro hizmet sorunları işlemelidir yetkilendirme gibi SSL, vb. Böylece iç mikro basit çoğu durumda, bu sorunları tek bir katmanında ele alınması.

## <a name="what-is-the-api-gateway-pattern"></a>API ağ geçidi düzeni nedir?

Tasarım ve büyük veya karmaşık mikro hizmet tabanlı uygulamaları birden çok istemci uygulamaları oluşturmak, dikkate alınması gereken iyi bir yaklaşım olabilir bir [API ağ geçidi](https://microservices.io/patterns/apigateway.html). Bu, tek giriş noktası belirli mikro grupları sağlayan bir hizmettir. Aşağıdakine benzer [cephesi düzeni](https://en.wikipedia.org/wiki/Facade_pattern) object‑oriented tasarımdan ancak bu durumda, bu kullanıcının dağıtılmış bir sistemde bir parçası.
API ağ geçidi düzeni bazen "arka uç ön uç için" olarak bilinen [(BFF)](https://samnewman.io/patterns/architectural/bff/) istemci uygulaması gereksinimlerini düşünmek sırasında oluşturmak için.

Bu nedenle, API ağ geçidi istemci uygulamalar ve mikro hizmetler arasında bulunur. Yönlendirme isteklerine Hizmetleri istemcilerinden gelen ters bir proxy işlevi görür. Ayrıca, kimlik doğrulaması, SSL sonlandırma ve önbellek gibi ek arası kesme özellikler sağlar.

Şekil 4-13 Basitleştirilmiş mikro hizmet tabanlı mimari birkaç mikro ile içine nasıl özel bir API ağ geçidi getireceğinizi gösterir.

![Bir API ağ geçidi özel bir hizmet olarak uygulanan gösteren diyagram](./media/image13.png)

**Şekil 4-13**. Bir API ağ geçidi kullanılarak uygulanan özel bir hizmet olarak

Bu örnekte, bir kapsayıcı olarak çalışan özel bir ASP.NET Core WebHost hizmeti olarak API ağ geçidi uygulanması.

Bu diyagramda vurgulamak önemlidir, birden çok bakan tek özel API ağ geçidi hizmeti kullanarak ve farklı istemci uygulamaları. Olgu API ağ geçidi hizmetinizi büyüyen gelişen ve için önemli bir risk olabilir istemci uygulamalardan birçok farklı gereksinimlerine göre. Sonuç olarak, bu farklı ihtiyaçları bloated olacak ve etkili bir şekilde bir tek yapılı uygulama veya tek yapılı hizmet oldukça benzer olabilir. Çok API ağ geçidi birden çok hizmet ya da birden çok daha küçük API ağ geçidi, istemci uygulaması form faktörü türü, her bir örneği için bölmeniz önerilir nedeni budur.

API ağ geçidi deseni uygularken dikkatli olmanız gerekir. Genellikle tek bir API uygulamanızın tüm iç mikro toplayarak ağ geçidi için iyi bir fikir değil. Bulursa, bir tek yapılı toplayıcısı veya orchestrator olarak davranır ve tüm mikro eşleyerek mikro hizmet otonomisi ihlal ediyor.

Bu nedenle, API ağ geçidi iş sınırları ve istemci uygulamaları ve değil act bağlı olarak tüm iç mikro hizmetler için tek bir toplayıcısı yinelenmeli.

Birincil bir Özet birden çok API ağ geçidi türleri tanımlarken olabilir ve böylece her istemci uygulaması gereksinimleri için farklı bir cephesi sahip birden çok istemci uygulamaları uygulamanız varsa, birden çok API ağ geçidi API ağ geçidi katmanı ayırma sırasında. Bu durumda "Arka uç için ön uç" adlı bir düzeni olduğunu ([BFF](http://samnewman.io/patterns/architectural/bff/)) her API ağ geçidi sağlayabilir burada büyük olasılıkla bile istemci form faktörünü belirli bağdaştırıcı uygulayarak göre her istemci uygulaması türü için uyarlanmış farklı bir API kod hangi underneath aşağıdaki görüntüde gösterildiği gibi birden çok dahili mikro çağırır:

![Birden çok özel API ağ geçidi gösteren diyagram](./media/image13.1.png)

**Şekil 4-13,1**. Birden çok özel API ağ geçidi kullanma

Önceki görüntüde birden çok hassas API ağ geçidi ile basitleştirilmiş bir mimari gösterilir. Bu durumda, her API ağ geçidi için tanımlanan sınırları tamamen "arka uç için ön uç üzerinde" temel alır ([BFF](http://samnewman.io/patterns/architectural/bff/)) deseni, bu nedenle yalnızca istemci uygulaması gereken API göre. Ancak büyük uygulamalarda ayrıca daha ve ek API iş sınırları ikinci bir tasarım Özet temel ağ geçidi oluşturun.

## <a name="main-features-in-the-api-gateway-pattern"></a>API ağ geçidi deseni temel özellikleri

Bir API ağ geçidi, birden çok özellik sunabilir. Ürün bağlı olarak daha zengin sağlayabilir veya basit özellikleri, Bununla birlikte, tüm API ağ geçidi için en önemli ve temel özellikleri aşağıdaki tasarım modeli şunlardır:

**Proxy veya ağ geçidi yönlendirme ters**. API ağ geçidi yeniden yönlendirme veya (katman 7, genellikle Http istekleri yönlendirme) istekleri iç mikro Uç noktalara yönlendirmek için ters proxy sunar. Ağ geçidi tek bir uç nokta veya URL için istemci uygulamaları sağlar ve istekleri iç mikro grubuna dahili olarak eşler. Bu yönlendirme özelliği mikro istemci uygulamalardan aynı şekilde yardımcı olur, ancak API ağ geçidi tek yapılı API ve istemci uygulamaları, daha sonra Between durduğunu tek yapılı bir API modernizing yeni API'leri yeni mikro eklediğinizde, ayrıca oldukça uygun olduğunu birçok mikro gelecekte bölünür kadar hala eski tek yapılı API kullanarak. API ağ geçidi nedeniyle istemci uygulamaları iç mikro veya tek yapılı bir API ve daha da önemlisi, ne zaman Gelişmekte olan ve tek yapılı API mikro yeniden düzenleme teşekkürler API yönlendirme ağ geçidi olarak kullanılan API'leri uygulanmışsa farkına , istemci uygulamaları olmaz etkilenebilir herhangi bir URI değişiklik ile.

Daha fazla bilgi için bkz: [ağ geçidi yönlendirme düzeni](https://docs.microsoft.com/azure/architecture/patterns/gateway-routing).

**İstekleri toplama**. Ağ geçidi desen bir parçası olarak tek bir istemci isteği birden çok dahili mikro hedefleme birden çok istemci isteklerini (genellikle Http isteklerini) toplayabilirsiniz. İstemci sayfa/ekran birkaç mikro bilgilerinden ihtiyacı olduğunda bu deseni özellikle kullanışlıdır. Bu yaklaşımda, istemci uygulaması iç mikro için çeşitli istekler gönderir ve ardından sonuçları toplar ve her şeyi istemci uygulamasına gönderir API ağ geçidi tek bir istek gönderir. Bu tasarım deseni amacı ve ana avantajı olan istemci uygulamaları ve API, arka uç arasında burada mikro, mobil uygulamaları veya SPA uygulamalardan gelen istekleri gibi canlı özellikle veri merkezi dışında uzak uygulamalar için önemlidir chattiness azaltmak için Uzak istemci tarayıcılarında JavaScript gelir. Normal web uygulamaları (örneğin, bir ASP.NET Core MVC web uygulaması) bir sunucu ortamında isteklerini gerçekleştirmek için bu deseni gecikme uzak istemci uygulamaları için çok daha küçük olduğu gibi çok önemli değil.

Kullandığınız API ağ geçidi ürün bağlı olarak, bu toplama gerçekleştirmek mümkün olabilir. Bununla birlikte, çoğu durumda, toplama mikro API ağ geçidi kapsamını altında oluşturmak için daha esnektir toplama (diğer bir deyişle, C# kodu) kodda tanımlamak için.

Daha fazla bilgi için bkz: [ağ geçidi toplama düzeni](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation).

**Çapraz kesme sorunları veya ağ geçidi boşaltma**. Her API ağ geçidi ürün tarafından sunulan özelliklerden bağlı olarak, tek tek mikro işlevinden bir katmanı arası kesme sorunları birleştirerek her mikro hizmet uygulaması basitleştirir ağ geçidine boşaltabilir. Bu, özellikle düzgün aşağıdaki işlevleri gibi iç her mikro hizmet uygulama karmaşık olabilir özel özellikler için uygundur:

- Kimlik doğrulama ve yetkilendirme
- Hizmet bulma tümleştirme
- Yanıt önbelleğe alma
- İlkeleri, devre kesici ve QoS yeniden deneyin
- Hız sınırı ve azaltma
- Yük Dengeleme
- Günlüğe kaydetme, izleme, bağıntı
- Üstbilgiler, sorgu dizeleri ve talep dönüştürme
- IP uygulamaları güvenilir listeye almayı

Daha fazla bilgi için bkz: [düzeni boşaltma ağ geçidi](https://docs.microsoft.com/azure/architecture/patterns/gateway-offloading).

## <a name="using-products-with-api-gateway-features"></a>Ürünleri ile API ağ geçidi özelliklerini kullanma

Her uygulama bağlı olarak API ağ geçitleri ürünleri sunduğu pek çok daha fazla arası kesme sorunları olabilir. Örneğin, [Azure API Management](https://azure.microsoft.com/services/api-management/) (Şekil 4-14'te gösterildiği gibi) yalnızca API ağ geçidi gereksinimlerinizi çözdü ancak API'Öngörüler toplama gibi özellikler sağlar. API yönetim çözümünü kullanıyorsanız, bir API ağ geçidi yalnızca bir bu tam API yönetimi çözümü içinde bileşenidir.

![API ağ geçidi ile Azure API Yönetimi mimarisi gösteren diyagram](./media/image14.png)

**Şekil 4-14**. API ağ geçidiniz için Azure API Management kullanma

Bu tür bir API ağ geçidi "ince" olduğundan Azure API Management, tek bir API ağ geçidi olabilir olgu gibi bir ürün kullanarak kadar riskli olmadığı durumlarda, bu durumda, bir tek yapılı gelişmesi özel C# kod uygulamaz anlamına gelir Bileşen.

API ağ geçidi ürünler genellikle giriş iletişimi, burada, ayrıca iç mikro API'lerden filtre yanı sıra bu tek katmandaki yayımlanan API'ler yetkilendirme uygulamak için ters proxy gibi davranır.

Bir API Management sistem Yardım'dan kullanılabilir bilgiler Apı'lerinizi nasıl kullanılacağı konusunda bilgi edinmek ve nasıl performans gösterdiğini. Gerçek zamanlı analiz raporları görüntülemenize izin vererek ve işinizin etkileyebilecek eğilimleri tanımlama bunu. Ayrıca, hakkında daha fazla çevrimiçi ve çevrimdışı analiz için istek ve yanıt etkinlik günlükleri olabilir.

Azure API Management ile bir anahtar, bir belirteç ve IP filtresini kullanarak Apı'lerinizi güvenliğini sağlayabilirsiniz. Bu özellikler, esnek ve hassas kotaları zorlamak ve oran sınırları, Şekil ve ilkelerini kullanarak Apı'lerinizi davranışını değiştirmek ve yanıt önbelleğe alma ile performansı sağlar.

Bu kılavuz ve başvuru örnek uygulaması (eShopOnContainers) mimarisi Azure API Management gibi PaaS ürünler kullanmadan düz kapsayıcılarında odaklanmak için daha basit ve özel yapılan kapsayıcılı mimarisi sınırlıdır. Ancak, Microsoft Azure'da dağıtılan büyük mikro hizmet tabanlı uygulamalar için üretim, API ağ geçitleri için Azure API Management temel olarak değerlendirmek için öneririz.

**Ocelot.** Daha basit yaklaşımlardan için hafif bir API ağ geçidi Ocelot gibi önerilir. [Ocelot](https://github.com/ThreeMammals/Ocelot) bir açık kaynak .NET Core tabanlı API ağ geçidi özellikle sistemlerine giriş birleşik noktalarına ihtiyaç mikro mimarisi için yapılır. Basit, hızlı ve ölçeklenebilir ve Yönlendirme ve diğer birçok özellik arasında kimlik doğrulaması sağlar.

Neden Ocelot kullanıldı içindeki ana nedeni [eShopOnContainers başvuru uygulama](https://github.com/dotnet-architecture/eShopOnContainers) Ocelot bir .NET Core basit API burada dağıtma aynı uygulama dağıtım ortamına dağıtabilirsiniz ağ geçidi olduğundan mikro/kapsayıcıları bir Docker ana bilgisayar, vb. Kubernetes, Service Fabric. Ve .NET Core üzerinde bağlı olduğundan, platformlar arası Linux veya Windows dağıtmanıza olanak kalır.

Özel API kapsayıcılarında çalıştıran ağ geçitleri gösteren önceki diyagramlarda tam olarak nasıl de Ocelot bir kapsayıcı ve mikro hizmet tabanlı uygulama çalıştırabilirsiniz var.

Ayrıca, Apigee, Kong, MuleSoft, WSO2, gibi API ağ geçitleri özellikleri sunan pazardaki diğer birçok ürün vardır ve giriş Denetleyicisi Özellikleri Linkerd ve Istio gibi diğer ürünleri için hizmet kafes.

İlk mimarisi ve desenler açıklama bölümleri sonra sonraki bölümlerde API ağ geçitleri ile uygulama açıklamaktadır [Ocelot](https://github.com/ThreeMammals/Ocelot).

## <a name="drawbacks-of-the-api-gateway-pattern"></a>API ağ geçidi düzeni eksileri

- En önemli dezavantajı, bir API ağ geçidi uyguladığınızda, iç mikro ile bu katmanı Kuplaj olmasıdır. Bu gibi bağlantı uygulamanız için ciddi sorunlar getirebilir. Vaster Clemens Azure Service Bus ekibine adresindeki Mimarı başvurduğu "Yeni ESB" olarak olası bu zorluk içinde "[Mesajlaşma ve mikro](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" GOTO 2016 oturumunda.

- Mikro API ağ geçidi kullanarak bir ek olası tek hata noktası oluşturur.

- Bir API ağ geçidi artan yanıt süresi ek ağ çağrısı nedeniyle ortaya çıkarabilir. Ancak, bu ek çağrı genellikle, arabirim, bir istemcinin doğrudan iç mikro çağırma çok chatty olandan daha az etkisi yoktur.

- Out düzgün ölçeklendirilmiş değil, API ağ geçidi bir ayak bağı olabilir.

- Özel mantık ve verileri toplama içeriyorsa, bir API ağ geçidi ek geliştirme maliyetini ve gelecekteki bakım gerektirir. Geliştiriciler API ağ geçidi her mikro 's uç noktalarını kullanıma sunmak için güncelleştirmeniz gerekir. Ayrıca, uygulama değişiklikleri iç mikro API ağ geçidi düzeyinde kod değişiklikleri neden olabilir. Ancak, API ağ geçidi yalnızca güvenlik, günlüğe kaydetme ve sürüm oluşturma uygulama varsa (as Azure API Management kullanırken), bu ek geliştirme maliyet geçerli.

- API ağ geçidi tek bir takım tarafından geliştirilen bir geliştirme performans sorunu olabilir. Birkaç fined düzey API farklı istemci ihtiyaçlarına yanıt veren ağ geçitleri için daha iyi bir yaklaşım neden olan başka bir neden de budur. Ayrıca API ağ geçidi dahili olarak birden çok alanları veya iç mikro üzerinde çalışan farklı ekip tarafından sahip olunan Katmanlar kurabilmeleri.

## <a name="additional-resources"></a>Ek kaynaklar

- **Charles Uludağ. Desen: API ağ geçidi / arka uç için ön uç** [*https://microservices.io/patterns/apigateway.html*](https://microservices.io/patterns/apigateway.html)

- **API ağ geçidi düzeni** [*https://docs.microsoft.com/azure/architecture/microservices/gateway*](https://docs.microsoft.com/azure/architecture/microservices/gateway)

- **Toplama ve birleşim deseni** [*http://microservices.io/patterns/data/api-composition.html*](http://microservices.io/patterns/data/api-composition.html)

- **Azure API Yönetimi** [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

- **UDI Dahan. Hizmet odaklı oluşturma**\
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

- **Clemens Vasters. Mesajlaşma ve mikro GOTO 2016 adresindeki** (video)   [*https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)

>[!div class="step-by-step"]
[Önceki] (tanımlamak-mikro hizmet-etki-model-boundaries.md) [sonraki] (iletişimi-içinde-mikro hizmet-architecture.md)
