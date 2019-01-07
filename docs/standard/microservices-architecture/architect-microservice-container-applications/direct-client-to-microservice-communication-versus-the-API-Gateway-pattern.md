---
title: Doğrudan istemci-mikro hizmet iletişimi ile API ağ geçidi düzeni
description: Farklar ve API ağ geçidi düzeni ve doğrudan istemci-mikro hizmet iletişimi kullanımlarını anlayın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: eebbfa6579de4cd24f58371ed1c7ab9a5f2e1c00
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54030548"
---
# <a name="the-api-gateway-pattern-versus-the-direct-client-to-microservice-communication"></a>Doğrudan istemci-mikro hizmet iletişimi ile API ağ geçidi düzeni

Bir mikro hizmet mimarisinde her mikro hizmet (genellikle) ayrıntılı uç noktalar kümesi sunar. Bu durum, bu bölümde açıklandığı gibi istemci mikro hizmet iletişimi etkileyebilir.

## <a name="direct-client-to-microservice-communication"></a>Doğrudan istemci-mikro hizmet iletişimi

Olası bir yaklaşım, doğrudan istemci-mikro hizmet iletişimi mimarisi kullanmaktır. Bu yaklaşımda, bir istemci uygulaması mikro hizmetler, doğrudan bazıları için Şekil 4-12'de gösterildiği gibi isteğinde bulunabilir.

![Burada her uygulama doğrudan bireysel mikro hizmetler ile iletişim kuran gösteren doğrudan istemci-mikro hizmet iletişimi mimari diyagramı.](./media/image12.png)

**Şekil 4-12**. Doğrudan istemci-mikro hizmet iletişimi mimari kullanarak

Bu yaklaşımda, her bir mikro hizmetin her mikro hizmet için farklı bir TCP bağlantı noktası ile bazen genel bir uç nokta vardır. Belirli bir hizmet için bir URL örneği azure'da aşağıdaki URL'yi olabilir:

<http://eshoponcontainers.westus.cloudapp.azure.com:88/>

URL kümede kullanılan yük dengeleyici eşlemek bir küme, temel bir üretim ortamında hangi sırayla istekleri mikro hizmetler arasında dağıtır. Üretim ortamlarında gibi uygulama teslim denetleyicisi (ADC) olabilir. [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) mikro hizmetlerin ve Internet arasında. Bu, yalnızca Yük Dengeleme gerçekleştirir, ancak SSL sonlandırma sunarak hizmetlerinizin güvenliğini sağlar ve saydam bir katman olarak görev yapar. Bu, CPU yoğunluklu SSL sonlandırma ve diğer yönlendirme görevlerini Azure Application gateway'e boşaltarak konaklarınız yükünü artırır. Herhangi bir durumda, bir yük dengeleyici ve ADC bir mantıksal uygulama mimarisi açısından saydam.

Doğrudan istemci-mikro hizmet iletişimi mimari, özellikle bir ASP.NET MVC uygulaması gibi bir sunucu tarafı web uygulaması istemci uygulaması ise, bir küçük mikro hizmet tabanlı uygulama için yeterince iyi olabilir. Ancak, büyük ve karmaşık mikro hizmet tabanlı uygulamalar (örneğin, mikro hizmet türleri onlarca işlerken) oluşturduğunuzda ve özellikle istemci uygulamaları uzak mobil uygulamalarından veya SPA web uygulamaları olduğunda bu yaklaşımı birkaç sorun yüzler.

Mikro hizmetler üzerinde alan büyük bir uygulama geliştirirken aşağıdaki soruları göz önünde bulundurun:

- *Nasıl istemci uygulamaları istekleri arka ucuna sayısını en aza indirmek ve birden fazla mikro hizmetlere geveze iletişimi azaltmak?*

Tek bir kullanıcı Arabirimi ekranı oluşturmak için birden fazla mikro Hizmetleri ile etkileşim kurma Internet üzerinden gidiş dönüş sayısı artar. Bu, gecikme süresi ve UI tarafında karmaşıklığı artırır. İdeal olarak, yanıtları sunucu tarafı verimli bir şekilde toplanması. Bu gecikme, paralel olarak birden çok veri parçasını dönün ve hazır duruma geldiği bazı kullanıcı Arabirimi veri gösterebilirsiniz azaltır.

- *Yetkilendirme, veri dönüştürme seçenekleri ve dinamik istek gönderme gibi çapraz kesme konuları nasıl işleyebilirsiniz?*

Güvenlik ve her bir mikro hizmet yetkilendirme önemli geliştirme çalışma gerektirebilir gibi güvenlik ve geniş kapsamlı kritik konular uygulama. Docker konağı veya iç küme dışarıdan kendisine doğrudan erişimi kısıtlamak için ve bir API ağ geçidi gibi merkezi bir yerde bu geniş kapsamlı kritik konular uygulamak için bu hizmetleri olası bir yaklaşımdır.

- *İstemci uygulamalarını Internet kolay protokolleri kullanan hizmetler ile nasıl iletişim kurabilir?*

Sunucu tarafında (örneğin, AMQP veya ikili protokolleri) kullanılan protokoller, genellikle istemci uygulamalarında desteklenmez. Bu nedenle, istekleri gibi HTTP/HTTPS protokolleri üzerinden gerçekleştirilen ve gerekir için diğer protokolleri sonradan çevrilir. A *adam-de-ADAM* yaklaşımı, bu durumda yardımcı olabilir.

- *Nasıl mobil uygulamalar için özellikle yapılan bir cephe şekillendirebileceğinize?*

Birden çok mikro hizmetler API'si için farklı istemci uygulamalarının ihtiyaçlarını da tasarlanmamış olabilir. Örneğin, bir mobil uygulama ihtiyaçlarını bir web uygulaması ihtiyaçlarını farklı olabilir. Mobil uygulamalarda, veri yanıtları daha verimli olabilir, böylece daha da iyileştirmek gerekebilir. Birden fazla mikro hizmetin veri toplama ve tek bir veri kümesi döndüren ve bazen herhangi bir veri gerek yoktur, mobil uygulama tarafından bir yanıt ortadan bunu yapabilirsiniz. Ve Elbette, bu verileri sıkıştırmak. Tekrar bir cephe veya mobil uygulamayı ve mikro hizmetler arası API bu senaryo için kullanışlı olabilir.

## <a name="why-consider-api-gateways-instead-of-direct-client-to-microservice-communication"></a>API ağ geçitleri yerine doğrudan istemci-mikro hizmet iletişimi neden düşünün

Bir mikro hizmet mimarisinde birden fazla mikro hizmet işlevlerini kullanmak istemci uygulamaları genellikle gerekir. Bu tüketim doğrudan gerçekleştirilirse, mikro hizmet uç noktaları için birden çok çağrıları işlemek istemcinin gerekir. Uygulama geliştikçe yeni mikro hizmetler sunulan ve var olan bir mikro hizmetler güncelleştirilir ne olur? İstemci uygulamalardan gelen çok fazla uç işleme, birçok mikro hizmetler, uygulamanızın varsa bir onarımı kabus olabilir. İstemci uygulaması iç uç sıkı bağlı olduğundan, mikro hizmetlerin gelecekteki gelişen istemci uygulamaları için yüksek etkili neden olabilir.

Bu nedenle, bir Orta düzeye veya yöneltme (ağ geçidi) katmanı sorun mikro hizmet tabanlı uygulamalar için kullanışlı olabilir. API ağ geçitleri yoksa, istemci uygulamaları istekleri doğrudan mikro hizmetler göndermeniz gerekir ve aşağıdaki sorunlar gibi sorunlar oluşturan:

- **Eşlenmesiyle**: API ağ geçidi desenini istemci uygulamaları için iç mikro Hizmetleri bağlı. İstemci uygulamaları, uygulamanın birden fazla alana mikro hizmetleri nasıl ayrılmış bilmeniz gerekir. Gelişen ve iç mikro hizmetler yeniden düzenleme, bu eylemlerin etkisi, bakım yapıyorsak hatalı, bozucu değişiklikleri nedeniyle istemci doğrudan başvurudan iç mikro Hizmetleri için istemci uygulamaları için uygulamaları nedeni. Çözüm geliştirilebilen daha zor hale sık güncelleştirilmesi istemci uygulamaları gerekir.

- **Çok fazla gidiş dönüş**: Tek bir sayfa/ekran istemci uygulamasında, birden çok hizmeti çeşitli çağrılar gerektirebilir. Birden çok ağ sonucunda gelişlerin önemli bir gecikme ekleme, sunucu ile istemci arasında yuvarlayabilirsiniz. Bir ara düzeyinde ele toplama performansı ve kullanıcı deneyimi için istemci uygulaması geliştirebilirsiniz.

- **Güvenlik sorunları**: Bir ağ geçidi "saldırı yüzeyini istemci uygulamalar tarafından doğrudan kullanılmayan iç mikro hizmetler gizlerseniz daha büyük hale dış dünya" için tüm mikro Hizmetleri sunulmalıdır. Daha küçük saldırı yüzeyini, uygulamanızı daha güvenli olabilir.

- **Geniş kapsamlı kritik konular**: Genel olarak yayımlanan her mikro hizmet sorunları işlemesi yetkilendirme gibi SSL vs. İç mikro hizmetler basitleştirilmiştir böylece çoğu durumda, bu sorunları tek bir katmanda işlenmesi.

## <a name="what-is-the-api-gateway-pattern"></a>API ağ geçidi düzeni nedir?

Tasarım ve büyük veya karmaşık mikro hizmet tabanlı uygulamaları birden çok istemci uygulamaları oluşturmak, dikkate almanız iyi bir yaklaşım olabilir bir [API ağ geçidi](https://microservices.io/patterns/apigateway.html). Bu tek giriş noktası belirli grupları mikro hizmetler sağlayan bir hizmettir. Benzer [görünüm düzeni](https://en.wikipedia.org/wiki/Facade_pattern) nesne yönelimli Tasarım'dan ancak bu durumda, bu kullanıcının dağıtılmış bir sistemin parçası. API ağ geçidi desenini bazen "arka uç için ön uç" olarak bilinen ([BFF](https://samnewman.io/patterns/architectural/bff/)) istemci uygulamasının gereksinimlerini düşünmek sırasında derleme nedeni.

API ağ geçidi, bu nedenle, istemci uygulamalar ve mikro hizmetler arasında bulunur. Ters Ara sunucu, istemcilerden gelen yönlendirme isteklerini hizmetlerine görür. Ayrıca, kimlik doğrulaması, SSL sonlandırma ve önbellek gibi ek çapraz özellikler de sağlayabilirsiniz.

Şekil 4-13 basitleştirilmiş bir mikro hizmet tabanlı mimari ile yalnızca birkaç mikro hizmetler halinde nasıl özel bir API ağ geçidi uygun gösterir.

![Uygulamaları tek bir uç API istekleri iletmek üzere her bir mikro hizmetin yapılandırılmış ağ geçidine bağlanmak için bir API ağ geçidi özel bir hizmet olarak uygulanan gösteren diyagram.](./media/image13.png)

**Şekil 4-13**. Özel bir hizmet olarak uygulanan bir API ağ geçidi kullanma

Bu örnekte, bir kapsayıcı olarak çalışan özel bir ASP.NET Core Web barındırma hizmeti olarak API ağ geçidi uygulanması.

Bu diyagramda vurgulamak önemlidir, birden çok'e yönelik tek bir özel API ağ geçidi hizmeti kullanılarak ve farklı istemci uygulamaları. API ağ geçidi hizmetiniz büyütmeye ve gelişen çünkü olgu önemli bir risk olabilir istemci uygulamalardan gelen çok sayıda farklı gereksinimlerine göre. Sonuç olarak, bu farklı gereksinimleri nedeniyle bloated olacaktır ve etkili bir şekilde bir tek parçalı bir uygulama veya hizmet tek parçalı oldukça benzer olabilir. İşte bu çok birden çok hizmeti veya birden çok daha küçük API ağ geçitleri, istemci uygulama form faktörü türü, her bir API ağ geçidi örneği için bölmek için önerilir.

API ağ geçidi desenini uygulama oluştururken dikkatli olmanız gerekir. Genellikle tek bir API tüm iç mikro hizmetler, uygulamanızın toplama ağ geçidi için iyi bir fikir değildir. Varsa, tek parçalı bir Toplayıcı veya orchestrator olarak görev yapar ve mikro hizmet otonomi tüm mikro Hizmetleri eşlenmesiyle tarafından ihlal ediyor.

Bu nedenle, API ağ geçitleri iş sınırları ve istemci uygulamaları ve değil Yasası göre tek bir Toplayıcı iç tüm mikro hizmetlere yönelik olarak ayrılmış.

Böylece her bir istemci uygulama ihtiyaçlarını için farklı bir cephe olabilir API ağ geçidi katmanı birden çok API ağ geçitleri bölünürken, uygulamanızın birden çok istemci uygulamalar varsa, birincil bir Özet birden çok API ağ geçitleri türleri tanımlamak için kullanıldığında olabilir. Bu durumda "Arka uç için ön uç" adlı bir desendir ([BFF](https://samnewman.io/patterns/architectural/bff/)) her bir API ağ geçidi sağlayabilir burada büyük olasılıkla bile istemci form faktörünün belirli bağdaştırıcı uygulayarak göre her istemci uygulaması türü için uyarlanmış farklı bir API kod, underneath birden çok iç mikro hizmetler, aşağıdaki görüntüde gösterildiği gibi çağırır:

![Birden çok özel API API ağ geçitleri istemci türüne göre nerede arkadaşlarından ağ geçitleri, gösteren diyagram; bir mobil istemciler, biri web istemcileri. Geleneksel web uygulaması, web API ağ geçidi kullanan bir MVC mikro hizmet bağlanır.](./media/image13.1.png)

**Şekil 4-13.1**. Birden çok özel API ağ geçidi kullanma

Önceki görüntüde birden çok ayrıntılı API ağ geçitleri ile basitleştirilmiş bir mimari gösterilmektedir. Bu durumda, her API ağ geçidi için tanımlanan sınırları tamamen "arka uç için ön uç üzerinde" dayalı ([BFF](https://samnewman.io/patterns/architectural/bff/)) deseni, bu nedenle yalnızca istemci uygulaması gerekli API göre. Ancak daha büyük uygulamalarında ayrıca daha da İleri gidin ve ek API ikinci bir tasarım Özet iş sınırlarına göre ağ geçitleri oluşturma.

## <a name="main-features-in-the-api-gateway-pattern"></a>API ağ geçidi desenini temel özellikleri

Bir API ağ geçidi, birden çok özellikler sunabilir. Ürün bağlı olarak daha zengin sağlayabilir veya basit özellikleri, ancak herhangi bir API ağ geçidi için en önemli ve temel özellikleri aşağıdaki tasarım modeli şunlardır:

**Ters proxy ya da ağ geçidi yönlendirme olabilir.** API ağ geçidi yönlendirme veya iç mikro hizmet uç noktaları için istek (katman 7 yönlendirmeyi, genellikle HTTP isteklerini) yönlendirmek için ters Ara sunucu sunar. Ağ geçidi tek bir uç nokta veya URL istemci uygulamalar sağlar ve istekleri iç mikro hizmetler grubuna dahili olarak eşler. Yönlendirme bu özellik mikro Hizmetleri istemci uygulamalardan ayırmanıza yardımcı olur. ancak, tek parçalı bir API, API ağ geçidi arasında tek parça API ve istemci uygulamaları olduktan sonra durduğunu modernleştirme yeni API'ler yeni mikro hizmetler ekleyebilirsiniz da oldukça uygun olan Gelecekte birçok mikro hizmetler halinde bölme kadar süre hala eski tek yapılı API kullanarak. API ağ geçidi nedeniyle istemci uygulamalarını iç mikro hizmetler veya tek parça bir API ve daha da önemlisi, gelişen ve tek parça API mikro hizmetler halinde yeniden düzenleme teşekkürler API ağ geçidi yönlendirme için kullanılan API'ler uygulanmışsa fark olmaz , istemci uygulamaları olmaz etkilenebilir herhangi bir URI değişiklik ile.

Daha fazla bilgi için [ağ geçidi yönlendirme düzeni](https://docs.microsoft.com/azure/architecture/patterns/gateway-routing).

**İstekleri toplama.** Ağ geçidi desenini bir parçası olarak birden çok iç mikro hizmetler tek bir istemci isteği hedefleyen birden çok istemci istekleri (genellikle, HTTP isteklerini) toplayabilirsiniz. İstemci sayfa/ekran birden fazla mikro hizmetler bilgilerinden gerektiğinde bu özellikle kullanışlı bir desendir. Bu yaklaşımda, istemci uygulaması iç mikro hizmetler için çeşitli istekler gönderir ve sonra sonuçları toplar ve her şeyi istemci uygulamasına gönderir API ağ geçidi tek bir istek gönderir. Bu tasarım deseni amacı ve ana avantajı olduğu yere mikro hizmetler, mobil uygulamalar veya SPA uygulamalardan gelen istekleri gibi canlı veri merkezi dışında uzak uygulamalar için özellikle önemli olan arasındaki iletişim yoğunluğunu istemci uygulamaları ve arka uç API'si, azaltmak için Uzak istemci tarayıcılarında JavaScript gelir. Bu düzen (örneğin, bir ASP.NET Core MVC web uygulaması) bir sunucu ortamında istekler gerçekleştiren normal web apps için gecikme süresi için Uzak istemci uygulamalarını çok daha küçük olduğu gibi önemli değildir.

Kullandığınız API ağ geçidi ürün bağlı olarak, bu toplama gerçekleştirmek mümkün olabilir. Ancak, çoğu durumda, kodun içinde toplama tanımlamak için API ağ geçidi kapsamı altında toplama mikro hizmetler oluşturmak için daha esnektir (diğer bir deyişle, C# kod):

Daha fazla bilgi için [ağ geçidi toplama düzeni](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation).

**Geniş kapsamlı kritik konular veya ağ geçidi boşaltma.** Her bir API ağ geçidi ürün tarafından sunulan özelliklerin bağlı olarak, her bir mikro hizmetin işlevinden bir katmana geniş kapsamlı kritik konular birleştirerek her mikro hizmet uygulaması basitleştirir ağ geçidine boşaltabilirsiniz. Bu, özellikle aşağıdaki işlevleri gibi iç her mikro hizmet içinde düzgün bir şekilde uygulamak için karmaşık olabilir özelleştirilmiş bir özellik için kullanışlıdır:

- Kimlik doğrulama ve yetkilendirme
- Hizmet bulma tümleştirmesi
- Yanıtları Önbelleğe Alma
- Yeniden deneme ilkeleri, devre kesici ve hizmet kalitesi
- Oran sınırlandırma ve azaltma
- Yük Dengeleme
- Günlüğe kaydetme, izleme, bağıntı
- Üstbilgiler, sorgu dizeleri ve talep dönüştürme
- IP beyaz listesi

Daha fazla bilgi için [ağ geçidi boşaltma düzeni](https://docs.microsoft.com/azure/architecture/patterns/gateway-offloading).

## <a name="using-products-with-api-gateway-features"></a>API ağ geçidi özellikleri ile ürünleri kullanma

Her uygulama bağlı olarak API ağ geçitleri ürünleri tarafından sunulan çok sayıda daha geniş kapsamlı kritik konular olabilir. Biz burada keşfedeceğiz:

- [Azure API Management](https://azure.microsoft.com/services/api-management/)
- [Ocelot](https://github.com/ThreeMammals/Ocelot)

### <a name="azure-api-management"></a>Azure API Management

[Azure API Management](https://azure.microsoft.com/services/api-management/) (Şekil 4-14'te gösterildiği gibi) değil yalnızca API ağ geçidi gereksinimlerinizi çözer ancak öngörüleri, API'lerinden toplama gibi özellikler sağlar. API Yönetimi çözümünü kullanıyorsanız, bir API ağ geçidi, tam API yönetimi çözümü içinde yalnızca bir bileşen ' dir.

![Azure API Management, her iki API ağ geçidi ve yönetim gereksinimlerinizi günlüğe kaydetme, güvenlik, kullanım ölçümü, vb. çözer.](./media/image14.png)

**Şekil 4-14**. API ağ geçidinizin Azure API Yönetimi'ni kullanma

Bu tür bir API ağ geçitleri "ince" olduğu gibi Azure API Management, tek bir API ağ geçidi olabilir olgusu bir ürünü kullanmaya riskli olmadığı durumlarda, bu durumda, doğru tek parça gelişmek özel C# kod uygulamayıp anlamı bileşeni. Bu ürünler, burada da iç mikro hizmetler API'lerinden filtreleyebilir ve yayımlanan API'leri tek bu katmandaki yetkilendirme uygulamak giriş iletişim için ters Ara sunucu gibi davranır.

API ağ geçidi ürünler genellikle burada, ayrıca iç mikro hizmetler API'lerinden filtre yanı sıra bu tek katmanda yayımlanan API'leri için yetkilendirme uygulama giriş iletişim için ters proxy gibi davranır.

Bir API Management sistemi Yardım öngörüleri Apı'lerinizin nasıl kullanılacağı konusunda bilgi almak ve nasıl gerçekleştiriyorsunuz. Süreniz neredeyse gerçek zamanlı analiz raporları görüntüleyin ve işinizi etkileyebilecek eğilimleri belirleyerek bunu. Ayrıca, hakkında daha fazla çevrimiçi ve çevrimdışı analiz için istek ve yanıt etkinlik günlükleri olabilir.

Azure API Management, bir anahtar, belirteç ve IP filtreleme kullanarak Apı'lerinizi güvenli hale getirebilirsiniz. Bu özellikler, esnek ve ayrıntılı kotalar zorlamak ve oran sınırları, Şekil ve ilkeleri kullanarak Apı'lerinizi davranışını değiştirmek ve yanıt önbelleğe alma ile performansı sağlar.

Bu kılavuz ve referans örnek uygulaması (hizmetine), Azure API Management gibi PaaS ürünleri kullanmadan düz kapsayıcılarında odaklanabilmek için daha basit ve özel bir kapsayıcı mimarisi için sınırlı mimaridir. Ancak, Microsoft Azure'a dağıtılan büyük mikro hizmet tabanlı uygulamalar için Azure API Management temel olarak üretim ortamında, bir API ağ geçitleri için değerlendirilecek geçirmenizi öneririz.

### <a name="ocelot"></a>Ocelot

[Ocelot](https://github.com/ThreeMammals/Ocelot) bir basit API daha basit bir yaklaşım için önerilen, ağ geçididir. Ocelot tabanlı API ağ geçidi özellikle sistemlerine giriş birleşik noktalarına ihtiyaç mikro hizmet mimarisi için yapılan açık bir kaynak .NET Core ' dir. Bu basit, hızlı ve ölçeklenebilir ve Yönlendirme ve diğer birçok özelliği arasında kimlik doğrulaması sağlar.

Temel nedeni için Ocelot seçin [hizmetine başvuru uygulaması](https://github.com/dotnet-architecture/eShopOnContainers) Ocelot bir .NET Core basit API, burada dağıtma aynı uygulama dağıtım ortamına dağıtabilirsiniz ağ geçidi olduğundan mikro hizmetler/kapsayıcıları, Docker konağı, Kubernetes, Service Fabric, vb. gibi. Ve .NET Core üzerine dayalı olduğundan, platformlar arası, Linux veya Windows üzerinde dağıtmanızı sağlar.

Özel API kapsayıcılarda çalıştırılan ağ geçitleri gösteren önceki diyagramlarda tam olarak ne de Ocelot bir kapsayıcı ve mikro hizmet tabanlı uygulama çalıştırabilirsiniz olan.

Ayrıca, Apigee, Kong, MuleSoft, WSO2, API ağ geçitleri özellikleri sunan pazardaki diğer pek çok ürünlerin vardır ve giriş Denetleyicisi Özellikleri Linkerd ve Istio gibi diğer ürünleri için hizmet kafes.

İlk mimarisi ve desenleri açıklama bölümleri sonra sonraki bölümlerde, nasıl API ağ geçitleri ile gerçekleştirilebileceğini açıklamak. [Ocelot](https://github.com/ThreeMammals/Ocelot).

## <a name="drawbacks-of-the-api-gateway-pattern"></a>API ağ geçidi desenini dezavantajları

- En önemli dezavantajı, bir API ağ geçidi uyguladığınızda, iç mikro hizmetlerin söz konusu katman eşlenmesiyle olmasıdır. Böyle bağlantısından uygulamanız için ciddi sorunlar yapabilecek. Azure Service Bus ekibine Mimarı Clemens Vaster başvurduğu olası bu güçlük "Yeni ESB" olarak "[Mesajlaşma ve mikro Hizmetler](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" Git 2016 oturumunda.

- Mikro hizmetler API ağ geçidi kullanarak bir ek olası tek hata noktası oluşturur.

- Bir API ağ geçidi ek ağ çağrısı nedeniyle yüksek yanıt süresi ortaya çıkarabilir. Ancak bu ek çağrı genellikle iç mikro Hizmetleri doğrudan çağırma çok sık iletişim kuran bir istemci arabirimi olması daha az bir etkisi yoktur.

- API ağ geçidi, düzgün bir şekilde ölçeği değil, bir performans sorunu haline gelebilir.

- Özel mantığı ve veri toplama içeriyorsa, bir API ağ geçidi ek geliştirme maliyetini ve gelecekte bakım yapılmasını gerektiriyor. Geliştiriciler, her bir mikro hizmetin ait uç noktalarını kullanıma için API ağ geçidi güncelleştirmeniz gerekir. Ayrıca, iç mikro Hizmetler uygulaması değişiklikleri API ağ geçidi düzeyde kod değişiklikleri neden olabilir. Ancak, API ağ geçidi, yalnızca güvenlik, günlüğe kaydetme ve sürüm oluşturma uyguluyor varsa (as Azure API Management'ı kullanırken), bu ek geliştirme maliyetini geçerli.

- API ağ geçidi tek bir ekip tarafından geliştirilmişse geliştirme performans sorunu olabilir. Neden daha iyi bir yaklaşım birkaç fined şirketlerinde API için farklı istemci ihtiyaçları yanıt ağ geçitleri için başka bir nedeni budur. Siz de API ağ geçidi dahili olarak birden çok alanlar veya iç mikro hizmetleri üzerinde çalışan farklı ekipler tarafından sahip olunan katmanları ayırabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

- **Charles Uludağ. Desen: API ağ geçidi / arka uç için ön uç** \
  [*https://microservices.io/patterns/apigateway.html*](https://microservices.io/patterns/apigateway.html)

- **API ağ geçidi düzeni** \
  [*https://docs.microsoft.com/azure/architecture/microservices/gateway*](https://docs.microsoft.com/azure/architecture/microservices/gateway)

- **Toplama ve birleştirme deseni** \
  [*https://microservices.io/patterns/data/api-composition.html*](https://microservices.io/patterns/data/api-composition.html)

- **Azure API Management** \
  [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

- **UDI Dahan. Hizmet yönelimli oluşturma** \
  [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

- **Clemens Vasters. Mesajlaşma ve mikro hizmetler, GOTO 2016 (video)** \
  [*https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)

- **API ağ geçidi kısaca** (ASP.net Core API ağ geçidi öğretici serisi) \
  [*https://www.pogsdotnet.com/2018/08/api-gateway-in-nutshell.html*](https://www.pogsdotnet.com/2018/08/api-gateway-in-nutshell.html)

>[!div class="step-by-step"]
>[Önceki](identify-microservice-domain-model-boundaries.md)
>[İleri](communication-in-microservice-architecture.md)