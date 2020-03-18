---
title: API ağ geçidi deseni, doğrudan istemciden mikrohizmete iletişime karşı
description: API ağ geçidi deseninin ve doğrudan istemciden mikrohizmete iletişimin farklılıklarını ve kullanımlarını anlayın.
ms.date: 01/07/2019
ms.openlocfilehash: 47e9a383c1fcb6c9fec38cb376b60a4ab839077d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401727"
---
# <a name="the-api-gateway-pattern-versus-the-direct-client-to-microservice-communication"></a>Doğrudan istemciden mikrohizmete iletişime karşı API ağ geçidi deseni

Microservices mimarisinde, her microservice bir dizi (genellikle) ince taneli uç noktaları ortaya çıkarır. Bu durum, bu bölümde açıklandığı gibi, istemci-mikrohizmet iletişimetkileyebilir.

## <a name="direct-client-to-microservice-communication"></a>Doğrudan istemciden mikrohizmete iletişim

Olası bir yaklaşım, doğrudan istemciden mikrohizmete iletişim mimarisi kullanmaktır. Bu yaklaşımda, bir istemci uygulaması Şekil 4-12'de gösterildiği gibi, bazı mikro hizmetlere doğrudan istekte bulunabilir.

![İstemciden mikrohizmete iletişim mimarisini gösteren diyagram.](./media/direct-client-to-microservice-communication.png)

**Şekil 4-12**. Doğrudan istemciden mikrohizmete iletişim mimarisini kullanma

Bu yaklaşımda, her microservice'in ortak bir bitiş noktası vardır, bazen her microservice için farklı bir TCP bağlantı noktasına sahiptir. Belirli bir hizmetin URL'si, Azure'da aşağıdaki URL olabilir:

`http://eshoponcontainers.westus.cloudapp.azure.com:88/`

Bir kümeyi temel alan bir üretim ortamında, bu URL kümede kullanılan yük dengeleyicisine eşlenir ve bu da istekleri mikro hizmetlere dağıtır. Üretim ortamlarında, mikro hizmetleriniz ve Internet arasında [Azure Uygulama Ağ Geçidi](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) gibi bir Uygulama Teslim Denetleyicisi (ADC) olabilir. Bu, yalnızca yük dengeleme sataşma gerçekleştirmenin yanı sıra SSL sonlandırma sunarak hizmetlerinizi güvence altına alan saydam bir katman görevi görür. Bu, CPU yoğun SSL sonlandırma ve diğer yönlendirme görevlerini Azure Uygulama Ağ Geçidi'ne boşaltarak ev sahiplerinizin yükünü artırır. Her durumda, bir yük dengeleyici ve ADC bakış mantıksal uygulama mimarisi açısından saydamdır.

Doğrudan istemciden mikrohizmete iletişim mimarisi, özellikle istemci uygulaması ASP.NET bir MVC uygulaması gibi sunucu tarafında ki bir web uygulamasıysa, küçük bir mikrohizmet tabanlı uygulama için yeterince iyi olabilir. Ancak, büyük ve karmaşık mikrohizmet tabanlı uygulamalar oluşturduğunuzda (örneğin, düzinelerce mikro hizmet türünü işlerken) ve özellikle istemci uygulamalar uzak mobil uygulamalar veya SPA web uygulamaları olduğunda, bu yaklaşım birkaç sorunla karşı karşıya kalır.

Mikro hizmetlere dayalı büyük bir uygulama geliştirirken aşağıdaki soruları göz önünde bulundurun:

- *İstemci uygulamaları arka uçtaki istek sayısını nasıl en aza indirebilir ve geveze iletişimi birden çok mikro hizmete indirgeyebilir?*

Tek bir UI ekranı oluşturmak için birden çok mikro hizmetle etkileşim kurmak, Internet'te gidiş-dönüş seyahat sayısını artırır. Bu, UI tarafında gecikme ve karmaşıklığı artırır. İdeal olarak, yanıtlar sunucu tarafında verimli bir şekilde toplanmalıdır. Birden çok veri parçası paralel olarak geri geldiğinden ve bazı UI'ler hazır olur olmaz verileri gösterebildiği için bu gecikme süresini azaltır.

- *Yetkilendirme, veri dönüşümleri ve dinamik istek gönderme gibi çapraz kesme yle nasıl başa çıkabilirsiniz?*

Her mikro hizmette güvenlik ve yetkilendirme gibi güvenlik ve çapraz kesme kaygılarının uygulanması önemli geliştirme çabası gerektirebilir. Olası bir yaklaşım, bu hizmetlerin Docker ana bilgisayar veya dahili küme içinde dışarıdan doğrudan erişimi kısıtlamak ve api ağ geçidi gibi merkezi bir yerde bu çapraz kesme endişelerini uygulamaktır.

- *İstemci uygulamaları, Internet dostu olmayan protokoller kullanan hizmetlerle nasıl iletişim kurabilir?*

Sunucu tarafında kullanılan protokoller (AMQP veya ikili protokoller gibi) genellikle istemci uygulamalarında desteklenmez. Bu nedenle, istekler HTTP/HTTPS gibi protokoller aracılığıyla gerçekleştirilmeli ve daha sonra diğer protokollere çevrilmelidir. *Ortadaki adam* yaklaşımı bu durumda yardımcı olabilir.

- *Özellikle mobil uygulamalar için yapılmış bir cepheyi nasıl şekillendirebilirsiniz?*

Birden çok mikro hizmetin API'si farklı istemci uygulamalarının gereksinimleri için iyi tasarlanamayabilir. Örneğin, bir mobil uygulamanın gereksinimleri bir web uygulamasının gereksinimlerinden farklı olabilir. Mobil uygulamalar için, veri yanıtları daha verimli olması için daha da optimize etmek gerekebilir. Bunu, birden çok mikro hizmetten veri toplayarak ve tek bir veri kümesini döndürerek ve bazen mobil uygulamanın ihtiyaç daşmayan yanıtındaki verileri ortadan kaldırarak yapabilirsiniz. Ve, tabii ki, bu verileri sıkıştırabilirsiniz. Yine, mobil uygulama ve mikro hizmetler arasında bir cephe veya API bu senaryo için uygun olabilir.

## <a name="why-consider-api-gateways-instead-of-direct-client-to-microservice-communication"></a>Neden doğrudan istemciden mikrohizmete iletişim yerine API Ağ Geçitleri'ni göz önünde bulundurun?

Bir microservices mimarisinde, istemci uygulamalarının genellikle birden fazla microservice işlevselliğini tüketmek gerekir. Bu tüketim doğrudan gerçekleştirilirse, istemcinin mikrohizmet uç noktalarına birden çok çağrı yı işlemesi gerekir. Uygulama geliştiğinde ve yeni mikro hizmetler sunulduğunda veya mevcut mikro hizmetler güncellendiğinde ne olur? Uygulamanızda çok sayıda mikro hizmet varsa, istemci uygulamalarından bu kadar çok uç nokta yı işlemek bir kabus olabilir. İstemci uygulaması bu dahili uç noktalarla birleştiğinden, gelecekte mikro hizmetlerin gelişmesi istemci uygulamaları üzerinde yüksek etkiye neden olabilir.

Bu nedenle, bir ara düzey veya indirection katmanı (Ağ Geçidi) olması mikro hizmet tabanlı uygulamalar için çok uygun olabilir. API Ağ Geçitleriniz yoksa, istemci uygulamalarının istekleri doğrudan mikro hizmetlere göndermesi gerekir ve bu da aşağıdaki sorunlar gibi sorunlara yol açar:

- **Kaplin**: API Ağ Geçidi deseni olmadan, istemci uygulamaları dahili mikro hizmetlerle birleştiğinde. İstemci uygulamaları, uygulamanın birden fazla alanının mikro hizmetlerde nasıl ayrıştırDığını bilmek gerekir. Dahili mikro hizmetleri geliştirip yeniden düzenleme yaparken, bu eylemler, istemci uygulamalarından gelen dahili mikro hizmetlere doğrudan başvuru nedeniyle istemci uygulamalarında kırılmalara neden oldukları için bakımı oldukça kötü etkiler. İstemci uygulamalarının sık sık güncellenmesi gerekir, bu da çözümün daha da gelişmesini sağlar.

- **Çok fazla gidiş-dönüş seyahat**: İstemci uygulamasındaki tek bir sayfa/ekran birden çok hizmete birden fazla çağrı gerektirebilir. Bu, istemci ve sunucu arasında birden çok ağ turu turuna neden olabilir ve önemli bir gecikme sonu ekleyebilir. Ara düzeyde işlenen toplama, istemci uygulamasının performansını ve kullanıcı deneyimini artırabilir.

- **Güvenlik sorunları**: Ağ geçidi olmadan, tüm mikro hizmetler "dış dünyaya" maruz kalmalıdır ve bu da saldırı yüzeyini istemci uygulamaları tarafından doğrudan kullanılmayan dahili mikro hizmetleri gizlemenize göre daha büyük hale getirmelidir. Saldırı yüzeyi ne kadar küçükse, uygulamanız o kadar güvenli olabilir.

- **Çapraz kesme endişeleri**: Kamuya açık her mikro hizmet, yetkilendirme, SSL, vb. gibi endişeleri ele almalıdır. Birçok durumda, bu endişeler tek bir katmanda ele alınabilir, böylece dahili mikro hizmetler basitleştirilir.

## <a name="what-is-the-api-gateway-pattern"></a>API Ağ Geçidi deseni nedir?

Birden çok istemci uygulamasıyla büyük veya karmaşık mikrohizmet tabanlı uygulamalar tasarlayıp oluşturduğunuzda, dikkate alınması gereken iyi bir yaklaşım [api ağ geçidi](https://microservices.io/patterns/apigateway.html)olabilir. Bu, belirli mikro hizmet grupları için tek giriş noktası sağlayan bir hizmettir. Nesne yönelimli tasarımdaki [Cephe desenine](https://en.wikipedia.org/wiki/Facade_pattern) benzer, ama bu durumda, dağıtılmış bir sistemin parçası. API Ağ Geçidi deseni bazen "ön uç için arka uç"[(BFF)](https://samnewman.io/patterns/architectural/bff/)olarak da bilinir, çünkü istemci uygulamasının gereksinimlerini düşünürken bunu oluşturursunuz.

Bu nedenle, API ağ geçidi istemci uygulamaları ve mikro hizmetler arasında yer alıyor. İstemlerden hizmetlere istekleri yönlendirme, ters proxy olarak görür. Ayrıca kimlik doğrulama, SSL sonlandırma ve önbellek gibi ek çapraz kesme özellikleri de sağlayabilir.

Şekil 4-13, özel bir API Ağ Geçidi'nin yalnızca birkaç mikro hizmetle basitleştirilmiş mikrohizmet tabanlı bir mimariye nasıl sığabileceğini gösterir.

![Özel hizmet olarak uygulanan bir API Ağ Geçidi'ni gösteren diyagram.](./media/direct-client-to-microservice-communication-versus-the-API-Gateway-pattern/custom-service-api-gateway.png)

**Şekil 4-13**. Özel hizmet olarak uygulanan bir API Ağ Geçidi kullanma

Uygulamalar, istekleri tek tek mikro hizmetlere iletmek üzere yapılandırılan tek bir uç nokta olan API Ağ Geçidi'ne bağlanır. Bu örnekte, API Ağ Geçidi, kapsayıcı olarak çalışan özel bir ASP.NET Core WebHost hizmeti olarak uygulanır.

Bu diyagramda birden çok ve farklı istemci uygulamasına bakan tek bir özel API Ağ Geçidi hizmeti kullandığınızı vurgulamak önemlidir. API Ağ Geçidi hizmetiniz istemci uygulamalarından gelen birçok farklı gereksinime bağlı olarak büyüyeceği ve gelişeceği için bu durum önemli bir risk olabilir. Sonunda, bu farklı ihtiyaçları nedeniyle şişirilmiş olacak ve etkili bir monolitik uygulama veya monolitik hizmet oldukça benzer olabilir. Bu nedenle, API Ağ Geçidi'ni örneğin istemci uygulama form faktörü türü başına bir olmak üzere birden çok hizmete veya birden çok küçük API Ağ Geçidine bölmenize çok yöneliktır.

API Ağ Geçidi deseni uygularken dikkatli olmanız gerekir. Genellikle uygulamanızın tüm dahili microservices toplama tek bir API Ağ Geçidi olması iyi bir fikir değildir. Eğer varsa, yekpare bir toplayıcı veya orkestratör olarak hareket eder ve tüm microservices birikerek microservice özerkliğini ihlal eder.

Bu nedenle, API Ağ Geçitleri iş sınırlarına ve istemci uygulamalarına göre ayrı tutulmalıdır ve tüm dahili mikro hizmetler için tek bir toplayıcı olarak hareket etmemelidir.

API Ağ Geçidi katmanını birden çok API Ağ Geçidi'ne bölerken, uygulamanızda birden çok istemci uygulaması varsa, birden çok API Ağ Geçidi türünü tanımlarken birincil pivot olabilir, böylece her istemci uygulamasının gereksinimleri için farklı bir cepheye sahip olabilirsiniz. Bu durum, her API Ağ Geçidi'nin her istemci uygulama türü için özel leştirilmiş farklı bir API sağlayabileceği ve hatta aşağıdaki resimde gösterildiği gibi birden çok dahili mikro hizmeti çağıran belirli bağdaştırıcı kodu uygulayarak istemci form faktörüne göre uyarlanmış farklı bir API sağlayabileceği "Frontend için Backend" ([BFF)](https://samnewman.io/patterns/architectural/bff/)adlı bir desendir:

![Birden çok özel API Ağ Geçidi ni gösteren diyagram.](./media/direct-client-to-microservice-communication-versus-the-API-Gateway-pattern/multiple-custom-api-gateways.png)

**Şekil 4-13.1**. Birden çok özel API Ağ Geçidi kullanma

Şekil 4-13.1, istemci türüne göre ayrılmış API Ağ geçitlerini gösterir; biri mobil istemciler ve diğeri de web istemcileri için. Geleneksel bir web uygulaması, web API Ağ Geçidi'ni kullanan bir MVC microservice'e bağlanır. Örnekte, birden çok ince taneli API Ağ Geçidi içeren basitleştirilmiş bir mimari gösterilmiştir. Bu durumda, her API Ağ Geçidi için tanımlanan sınırlar tamamen "Frontend için Backend"[(BFF)](https://samnewman.io/patterns/architectural/bff/)desenine dayanır, bu nedenle yalnızca istemci uygulaması başına gereken API'ye dayanır. Ancak daha büyük uygulamalarda da daha ileri gitmeli ve ikinci bir tasarım pivotolarak iş sınırlarına dayalı ek API Ağ Geçitleri oluşturmalısınız.

## <a name="main-features-in-the-api-gateway-pattern"></a>API Ağ Geçidi modelindeki ana özellikler

BIR API Ağ Geçidi birden çok özellik sunabilir. Ürüne bağlı olarak daha zengin veya daha basit özellikler sunabilir, ancak herhangi bir API Ağ Geçidi için en önemli ve temel özellikler aşağıdaki tasarım desenleridir:

**Proxy veya ağ geçidi yönlendirmesi ters.** API Ağ Geçidi, istekleri (katman 7 yönlendirme, genellikle HTTP istekleri) dahili mikro hizmetlerin uç noktalarına yönlendirmek veya yönlendirmek için ters proxy sunar. Ağ geçidi, istemci uygulamaları için tek bir bitiş noktası veya URL sağlar ve ardından istekleri dahili olarak bir grup dahili mikro hizmetle eşler. Bu yönlendirme özelliği, istemci uygulamalarını mikro hizmetlerden ayırmaya yardımcı olur, ancak api ağ geçidini yekpare API ile istemci uygulamaları arasında oturtarak yekpare bir API'yi modernize ederken de oldukça kullanışlıdır, ardından yeni mikro hizmetler olarak yeni API'ler ekleyebilirsiniz gelecekte birçok mikro hizmetlere bölünene kadar eski yekpare API'yi kullanmaya devam edin. API Ağ Geçidi sayesinde, kullanılan API'lerin dahili mikro hizmetler veya yekpare API olarak uygulanıp uygulanmadığını ve daha da önemlisi, API Ağ Geçidi yönlendirmesi sayesinde monolitik API'yi mikro hizmetlere dönüştürürken ve yeniden düzenlemede istemci uygulamaları fark etmez. , istemci uygulamaları herhangi bir URI değişikliğinden etkilenmez.

Daha fazla bilgi için [ağ geçidi yönlendirme deseni'ne](https://docs.microsoft.com/azure/architecture/patterns/gateway-routing)bakın.

**Toplama istekleri.** Ağ geçidi deseninin bir parçası olarak, birden çok dahili mikro hizmeti hedefleyen birden çok istemci isteğini (genellikle HTTP istekleri) tek bir istemci isteğine toplayabilirsiniz. Bu desen, özellikle bir istemci sayfasının/ekranının çeşitli mikro hizmetlerden gelen bilgilere ihtiyacı olduğunda kullanışlıdır. Bu yaklaşımla, istemci uygulaması API Ağ Geçidi'ne tek bir istek gönderir ve bu istekler dahili mikro hizmetlere gönderilir ve ardından sonuçları toplar ve her şeyi istemci uygulamasına geri gönderir. Bu tasarım deseninin temel yararı ve amacı, mobil uygulamalar veya SPA uygulamalarından gelen istekler gibi mikro hizmetlerin yaşadığı veri merkezinin dışında, özellikle uzak uygulamalar için önemli olan istemci uygulamaları ve arka uç API'si arasındaki gevezeliği azaltmaktır. istemci uzak tarayıcılarda Javascript geliyor. Sunucu ortamında istekleri gerçekleştiren normal web uygulamaları için (ASP.NET Core MVC web uygulaması gibi), gecikme gecikmesi uzak istemci uygulamalarına göre çok daha küçük olduğu için bu desen o kadar önemli değildir.

Kullandığınız API Ağ Geçidi ürününe bağlı olarak, bu toplama yı gerçekleştirebilir. Ancak, çoğu durumda API Ağ Geçidi kapsamında toplama mikrohizmetleri oluşturmak daha esnektir, bu nedenle kümelenmeyi kodda tanımlarsınız (c# kodu):

Daha fazla bilgi için [ağ geçidi toplama deseni'ne](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation)bakın.

**Çapraz kesme endişeleri veya ağ geçidi boşaltma.** Her API Ağ Geçidi ürünü tarafından sunulan özelliklere bağlı olarak, işlevselliği tek tek mikro hizmetlerden ağ geçidine boşaltarak, çapraz kesme endişelerini tek bir katmanda birleştirerek her bir mikro hizmetin uygulanmasını kolaylaştırabilirsiniz. Bu, özellikle aşağıdaki işlevler gibi her dahili mikro hizmette düzgün bir şekilde uygulanması karmaşık olabilecek özel leştirilmiş özellikler için uygundur:

- Kimlik doğrulama ve yetkilendirme
- Hizmet bulma tümleştirmesi
- Yanıtları Önbelleğe Alma
- Yeniden deneme politikaları, devre kesici ve QoS
- Hız sınırlama ve azaltma
- Yük dengeleme
- Günlük, izleme, korelasyon
- Üstbilgi, sorgu dizeleri ve talepleri dönüştürme
- IP beyaz liste

Daha fazla bilgi için [bkz.](https://docs.microsoft.com/azure/architecture/patterns/gateway-offloading)

## <a name="using-products-with-api-gateway-features"></a>API Ağ Geçidi özelliklerine sahip ürünleri kullanma

Her uygulamaya bağlı olarak API Ağ Geçitleri ürünleri tarafından sunulan çok daha fazla çapraz kesme endişeleri olabilir. Burada keşfedeceğiz:

- [Azure API Management](https://azure.microsoft.com/services/api-management/)
- [Ocelot](https://github.com/ThreeMammals/Ocelot)

### <a name="azure-api-management"></a>Azure API Management

[Azure API Yönetimi](https://azure.microsoft.com/services/api-management/) (Şekil 4-14'te gösterildiği gibi) yalnızca API Ağ Geçidi ihtiyaçlarınızı çözmekle kalmıyor, aynı zamanda API'lerinizden öngörüler toplama gibi özellikler de sağlar. Bir API yönetimi çözümü kullanıyorsanız, API Ağ Geçidi yalnızca tam API yönetimi çözümü içinde bir bileşendir.

![API ağ geçidiniz olarak Azure API Yönetimi'nin nasıl kullanılacağını gösteren diyagram.](./media/direct-client-to-microservice-communication-versus-the-API-Gateway-pattern/api-gateway-azure-api-management.png)

**Şekil 4-14**. API Ağ Geçidiniz için Azure API Yönetimini kullanma

Azure API Yönetimi hem API Ağ Geçidi nizi hem de günlük, güvenlik, ölçüm, vb. gibi Yönetim gereksinimlerinizi çözer. Bu durumda, Azure API Yönetimi gibi bir ürünü kullanırken, bu tür API Ağ geçitleri "daha ince" olduğundan, tek bir API Ağ Geçidi'ne sahip olabileceğiniz gerçeği o kadar da riskli değildir, yani yekpare bir bileşene dönüşebilecek özel C# kodu uygulamazsınız.

API Ağ Geçidi ürünleri genellikle giriş iletişimi için ters proxy gibi davranır, burada api'leri dahili mikro hizmetlerden filtreleyebilir ve bu tek katmanda yayınlanan API'lere yetkilendirme uygulayabilirsiniz.

API Yönetim sisteminden edinilebilen bilgiler, API'lerinizin nasıl kullanıldığını ve nasıl performans gösterdiğini anlamanıza yardımcı olur. Bunu, yakın gerçek zamanlı analiz raporlarını görüntülemenize ve işletmenizi etkileyebilecek eğilimleri belirleyerek yaparlar. Ayrıca, daha fazla çevrimiçi ve çevrimdışı çözümleme için istek ve yanıt etkinliği yle ilgili günlüklere sahip olabilirsiniz.

Azure API Yönetimi ile API'lerinizi bir anahtar, bir belirteç ve IP filtreleme kullanarak güvenebilirsiniz. Bu özellikler, esnek ve ince taneli kotaları ve oran sınırlarını zorlamanıza, ilkeleri kullanarak API'lerinizin şeklini ve davranışını değiştirmenize ve yanıt önbelleğe alma yla performansı artırmanıza izin verir.

Bu kılavuzda ve başvuru örneği uygulamasında (eShopOnContainers), azure API Yönetimi gibi PaaS ürünlerini kullanmadan düz kaplara odaklanmak için mimari daha basit ve özel yapım kapsayıcı mimarisiyle sınırlıdır. Ancak Microsoft Azure'da dağıtılan büyük mikro hizmet tabanlı uygulamalar için, üretimdeki API Ağ geçitlerinizin temeli olarak Azure API Yönetimini değerlendirmenizi öneririz.

### <a name="ocelot"></a>Ocelot

[Ocelot](https://github.com/ThreeMammals/Ocelot) hafif bir API Ağ Geçidi, basit yaklaşımlar için önerilir. Ocelot, özellikle kendi sistemine birleşik giriş noktaları gerektiren mikro hizmetler mimarisi için yapılmış bir Açık Kaynak .NET Core tabanlı API Ağ Geçididir. Hafif, hızlı, ölçeklenebilir ve diğer birçok özellik arasında yönlendirme ve kimlik doğrulama sağlar.

[eShopOnContainers başvuru uygulaması](https://github.com/dotnet-architecture/eShopOnContainers) için Ocelot'u seçmenizin temel nedeni, Ocelot'un Docker Host, Kubernetes gibi mikro hizmetleri/kapsayıcılarınızı dağıttığınız aynı uygulama dağıtım ortamına dağıtabileceğiniz bir .NET Core hafif API Ağ Geçidi olmasıdır. Ve .NET Core'a dayandığı için, Linux veya Windows'da dağıtım alabildiğiniz çapraz platformdur.

Kapsayıcılarda çalışan özel API Ağ geçitlerini gösteren önceki diyagramlar, Ocelot'u bir kapsayıcıda ve mikro hizmet tabanlı uygulamada nasıl çalıştırabileceğinizdir.

Buna ek olarak, apigee, Kong, MuleSoft, WSO2 ve linkerd ve Istio gibi diğer ürünler servis örgü denetleyici özellikleri için API Ağ Geçitleri özellikleri sunan piyasada birçok ürün vardır.

İlk mimari ve desenler açıklama bölümlerinden sonra, sonraki bölümlerde [Ocelot](https://github.com/ThreeMammals/Ocelot)ile API Ağ Geçitleri nasıl uygulanacağını açıklar.

## <a name="drawbacks-of-the-api-gateway-pattern"></a>API Ağ Geçidi deseni sakıncaları

- En önemli dezavantajı, bir API Ağ Geçidi uyguladığınız zaman, bu katmanı dahili mikro hizmetlerle birarada tutabiliyor olmasıdır. Bu gibi kaplin uygulamanız için ciddi zorluklara neden olabilir. Azure Servis Veri Servisi ekibinin mimarı Clemens Vaster, goto 2016'daki "[Mesajlaşma ve MikroHizmetler](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" oturumunda bu olası zorluğu "yeni ESB" olarak tanımlıyor.

- Mikro hizmetler API Ağ Geçidi kullanmak, olası tek bir hata noktası oluşturur.

- Bir API Ağ Geçidi, ek ağ çağrısı nedeniyle daha fazla yanıt süresi başlatabilir. Ancak, bu ekstra arama genellikle doğrudan dahili mikro hizmetleri arayan çok geveze bir istemci arabirimine sahip daha az etkisi vardır.

- Düzgün ölçeklendirilemezse, API Ağ Geçidi bir darboğaza dönüşebilir.

- Bir API Ağ Geçidi, özel mantık ve veri toplama içeriyorsa ek geliştirme maliyeti ve gelecekteki bakım gerektirir. Geliştiriciler, her mikro hizmetin uç noktalarını ortaya çıkarmak için API Ağ Geçidi'ni güncelleştirmelidir. Ayrıca, dahili mikro hizmetlerdeki uygulama değişiklikleri API Ağ Geçidi düzeyinde kod değişikliklerine neden olabilir. Ancak, API Ağ Geçidi yalnızca güvenlik, günlüğe kaydetme ve sürüm uygulaması (Azure API Yönetimi'ni kullanırken olduğu gibi) uyguluyorsa, bu ek geliştirme maliyeti geçerli olmayabilir.

- API Ağ Geçidi tek bir ekip tarafından geliştirilirse, bir geliştirme darboğaz olabilir. Bu, daha iyi bir yaklaşımın farklı istemci gereksinimlerine yanıt veren birkaç para cezası kesilen API Ağ Geçidine sahip olmasının başka bir nedenidir. Ayrıca, API Ağ Geçidi'ni dahili olarak, dahili mikro hizmetler üzerinde çalışan farklı ekiplerin sahip olduğu birden çok alana veya katmana ayırabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

- **Chris Richardson' ı. Desen: API Ağ Geçidi / Ön Uç için Arka Uç** \
  <https://microservices.io/patterns/apigateway.html>

- **API Ağ Geçidi deseni** \
  <https://docs.microsoft.com/azure/architecture/microservices/gateway>

- **Toplama ve kompozisyon deseni** \
  <https://microservices.io/patterns/data/api-composition.html>

- **Azure API Yönetimi** \
  <https://azure.microsoft.com/services/api-management/>

- **Udi Dahan. Hizmet Odaklı Kompozisyon** \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

- **Clemens Vasters' ı. GOTO 2016'da Mesajlaşma ve MikroHizmetler (video)** \
  <https://www.youtube.com/watch?v=rXi5CLjIQ9k>

- **Özetle API Ağ Geçidi** (Core API Ağ Geçidi Öğretici Serisi ASP.net) \
  <https://www.pogsdotnet.com/2018/08/api-gateway-in-nutshell.html>

>[!div class="step-by-step"]
>[Önceki](identify-microservice-domain-model-boundaries.md)
>[Sonraki](communication-in-microservice-architecture.md)
