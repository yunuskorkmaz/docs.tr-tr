---
title: Ön uç istemci iletişimi
description: Ön uç istemcilerinin, bulutta yerel sistemlerle nasıl iletişim kuracağını öğrenin
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: a488337b48e30b99bfcc9894a780350f32af864f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087454"
---
# <a name="front-end-client-communication"></a>Ön uç istemci iletişimi

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bulutta yerel bir sistemde, ön uç istemcileri (mobil, Web ve Masaüstü uygulamaları) bağımsız arka uç mikro hizmetleriyle etkileşim kurmak için bir iletişim kanalı gerektirir.  

Seçenekler nelerdir?

İşleri basit tutmak için bir ön uç istemci, Şekil 4-2 ' de gösterilen arka uç mikro hizmetleriyle *doğrudan iletişim kurabilir* .

![İstemcisini hizmet iletişimine yönlendirin](./media/direct-client-to-service-communication.png)

**Şekil 4-2.** İstemcisini hizmet iletişimine yönlendirin

Bu yaklaşımda, her mikro hizmetin ön uç istemcilerle erişilebilen genel bir uç noktası vardır. Bir üretim ortamında, mikro hizmetlerin önüne bir yük dengeleyici yerleştirirsiniz, yönlendirme trafiği orantılı olarak yapılır.

Basit bir uygulama olarak, doğrudan istemci iletişimi yalnızca basit mikro hizmet uygulamaları için kabul edilebilir. Bu model, ön uç istemcilerini çekirdek arka uç hizmetlerine sıkı bir şekilde bağlıarak, bir dizi sorunun kapısını açarak aşağıdakiler de dahildir:

- Arka uç hizmeti yeniden düzenleme için istemci geçirtibilirliği.
- Çekirdek arka uç hizmetleri olarak daha geniş bir saldırı yüzeyi doğrudan kullanıma sunulur.
- Her mikro hizmette çapraz kesme sorunlarının çoğaltılması.
- Aşırı karmaşık istemci kodu-istemciler birden çok bitiş noktasını takip etmelidir ve hataların dayanıklı bir şekilde işlenmesi gerekir.

Bunun yerine, yaygın olarak kabul edilen bir bulut tasarım deseninin ön uç uygulamaları ve arka uç hizmetleri arasında bir [API ağ geçidi hizmeti](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) uygulaması vardır. Model Şekil 4-3 ' de gösterilmiştir.

![API ağ geçidi kalıbı](./media/api-gateway-pattern.png)

**Şekil 4-3.** API ağ geçidi kalıbı

Önceki şekilde, API ağ geçidi hizmetinin arka uç çekirdek mikro hizmetlerini nasıl soyutlamasını aklınızda bir yere göz önüne alın. Bir Web API 'SI olarak uygulanan, iç mikro hizmetlere gelen trafiği yönlendiren bir *ters proxy*işlevi görür.

Ağ Geçidi, iç hizmet bölümlendirme ve yeniden düzenleme işleminden istemciyi yalıtılmış olarak düzenler. Bir arka uç hizmetini değiştirirseniz, istemciyi bozmadan ağ geçidinde buna uyum sağlayabilirsiniz. Ayrıca, kimlik, önbelleğe alma, dayanıklılık, ölçüm ve azaltma gibi çapraz savunma sorunları için ilk savunma hattınızdır. Bu çapraz kesme sorunlarının birçoğu arka uç çekirdek hizmetlerinden ağ geçidine yüklenebilir ve arka uç hizmetleri basitleştirir.

API ağ geçidini basit ve hızlı tutmak için dikkatli olunmalıdır. Genellikle, iş mantığı ağ geçidinin dışında tutulur. Karmaşık bir ağ geçidi riski soruna neden oluyor ve sonunda tek bir. Daha büyük sistemler genellikle istemci türüne (mobil, Web, masaüstü) veya arka uç işlevselliğine göre bölünmüş birden çok API ağ geçidi sunar. Ön [uçlar Için arka uç](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) , birden çok ağ geçidi uygulamaya yönelik bir yön sağlar. Model Şekil 4-4 ' de gösterilmiştir.

![API ağ geçidi kalıbı](./media/backend-for-frontend-pattern.png)

**Şekil 4-4.** Ön uç deseninin arka ucu

Önceki şekilde, gelen trafiğin istemci türüne göre belirli bir API Gateway 'e gönderilme şekli: Web, mobil veya masaüstü uygulaması. Bu yaklaşım, her bir cihazın özellikleri, form faktörü, performansı ve görüntüleme sınırlamaları arasında önemli ölçüde farklılık gösterir. Genellikle mobil uygulamalar tarayıcıdan veya Masaüstü uygulamalarından daha az işlevsellik sunar. Her ağ geçidi, ilgili cihazın özellikleri ve işlevselliğiyle eşleşecek şekilde iyileştirilebilir.

Başlamak için kendi API Gateway hizmetinizi oluşturabilirsiniz. GitHub ' da hızlı bir arama birçok örnek sağlayacaktır. Ancak, çeşitli çerçeveler ve ticari ağ geçidi ürünleri mevcuttur.

## <a name="ocelot-gateway"></a>Ocelot ağ geçidi

Basit .NET bulutu yerel uygulamaları için [Ocelot ağ geçidini](https://github.com/ThreeMammals/Ocelot)göz önünde bulundurmayabilirsiniz. Ocelot, sistemlerinde Birleşik bir giriş noktası gerektiren .NET mikro hizmetleri için oluşturulan açık kaynaklı bir API ağ geçididir. Hafif, hızlı, ölçeklenebilir.

API ağ geçitlerine benzer şekilde, birincil işlevselliği gelen HTTP isteklerini aşağı akış hizmetlerine iletmektir. Ayrıca, bir .NET Core ara yazılım ardışık düzeninde yapılandırılabilir çok çeşitli özellikleri destekler. Özellik kümesi, aşağıdaki tabloda sunulmuştur.

|Ocelot özellikleri  | |
| :-------- | :-------- |
| Yönlendirme | Kimlik doğrulaması |
| İstek toplama | Yetkilendirme |
| Hizmet bulma (Tüketil ve Eureka ile) | Sınırlama |
| YükDengeleme | Günlüğe kaydetme, Izleme |
| Önbelleğe Alma | Üstbilgiler/sorgu dizesi dönüştürmesi |
| Bağıntı geçişi | Özel ara yazılım |
| Hizmet Kalitesi | Yeniden deneme Ilkeleri |

Her Ocelot Gateway, bir JSON yapılandırma dosyasında yukarı akış ve aşağı akış adreslerini ve yapılandırılabilir özellikleri belirtir. İstemci Ocelot ağ geçidine bir HTTP isteği gönderir. Bir kez alındıktan sonra, Ocelot, kendi işlem hattı aracılığıyla, kendi yapılandırması tarafından belirtilen duruma geçen HttpRequest nesnesini geçirir. İşlem hattının sonunda, Ocelot yeni bir HTTPResponseObject oluşturur ve bunu aşağı akış hizmetine geçirir. Yanıt için Ocelot, yanıtı istemciye geri göndererek işlem hattını tersine çevirir.

Ocelot, bir NuGet paketi olarak kullanılabilir. NET Standard 2,0 ' i hedefler ve hem .NET Core 2.0 + hem de .NET Framework 4.6.1 + çalışma zamanları ile uyumlu hale getirir. Ocelot, HTTP ve .NET Core 'un desteklediği platformlarda çalışan, Linux, macOS ve Windows ile tümleşen her şeyi tümleştirir. Ocelot genişletilebilir ve Docker kapsayıcıları, Azure Kubernetes Hizmetleri veya diğer genel bulutlar dahil olmak üzere birçok modern platformu destekler.  Ocelot, [Tüketil](https://www.consul.io), [Graphql](https://graphql.org)ve Netflix 'in [Eureka](https://github.com/Netflix/eureka)gibi açık kaynaklı paketlerle tümleştirilir.

Ticari bir API ağ geçidinin zengin özellik kümesini gerektirmeyen basit bulutta yerel uygulamalar için Ocelot ' i düşünün.

## <a name="azure-application-gateway"></a>Azure Application Gateway

Basit ağ geçidi gereksinimleri için [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/overview)göz önüne alabilirsiniz. Azure [PaaS hizmeti](https://azure.microsoft.com/overview/what-is-paas/)olarak KULLANILABILIR, URL YÖNLENDIRME, SSL sonlandırma ve bir Web uygulaması güvenlik duvarı gibi temel ağ geçidi özelliklerini içerir. Hizmet, [katman 7 Yük Dengeleme](https://www.nginx.com/resources/glossary/layer-7-load-balancing/) özelliklerini destekler. Katman 7 ile, yalnızca düşük düzeyde TCP ağ paketleri yerine bir HTTP iletisinin gerçek içeriğine göre istekleri yönlendirebilirsiniz.

Bu kitapta, [Kubernetes](https://www.infoworld.com/article/3268073/what-is-kubernetes-your-next-application-platform.html)'te bulutta yerel sistemleri barındırıyoruz endişe. Bir kapsayıcı Orchestrator, Kubernetes Kapsayıcılı iş yüklerinin dağıtım, ölçeklendirme ve operasyonel sorunlarını otomatikleştirir. Azure Application Gateway, [Azure Kubernetes hizmet](https://azure.microsoft.com/services/kubernetes-service/) kümesi IÇIN bir API ağ geçidi olarak yapılandırılabilir.

[Application Gateway giriş denetleyicisi](https://azure.github.io/application-gateway-kubernetes-ingress/) , Azure Application Gateway 'In doğrudan [Azure Kubernetes hizmeti](https://azure.microsoft.com/services/kubernetes-service/)ile çalışmasını sağlar. Şekil 4,5, mimariyi gösterir.

![Application Gateway giriş denetleyicisi](./media/application-gateway-ingress-controller.png)

**Şekil 4-5.** Application Gateway giriş denetleyicisi

Kubernetes, [giriş ADLı http](https://kubernetes.io/docs/concepts/services-networking/ingress/)(düzey 7) yük dengelemeyi destekleyen yerleşik bir özellik içerir. Giriş, mikro hizmet örneklerinin dışarıdaki dünyaya nasıl sunulabileceğini gösteren bir kurallar kümesi tanımlar. Önceki görüntüde, giriş denetleyicisi küme için yapılandırılmış giriş kurallarını yorumlar ve Azure Application Gateway otomatik olarak yapılandırır. Bu kurallara göre Application Gateway trafiği AKS içinde çalışan mikro hizmetlere yönlendirir. Giriş denetleyicisi, giriş kurallarında yapılan değişiklikleri dinler ve Azure Application Gateway uygun değişiklikleri yapar.

## <a name="azure-api-management"></a>Azure API Management

Orta ve büyük ölçekli bulut Yerel sistemleri için [Azure API Management](https://azure.microsoft.com/services/api-management/)göz önünde bulundurmanız gerekebilir. Yalnızca API ağ geçidi ihtiyaçlarınızı çözme, ancak tam özellikli bir geliştirici ve yönetim deneyimi sağlayan bulut tabanlı bir hizmettir. API Management Şekil 4-6 ' de gösterilir.

![Azure API Management](./media/azure-api-management.png)

**Şekil 4-6.** Azure API Management

Başlamak için API Management, yapılandırılabilir kurallara ve ilkelere bağlı olarak arka uç hizmetlerine denetimli erişime izin veren bir ağ geçidi sunucusu kullanıma sunar. Bu hizmetler Azure bulutta, şirket içi veri merkezinizde veya diğer genel bulutlarda olabilir. API anahtarları ve JWT belirteçleri neleri yapabileceğini tespit edebilir. Tüm trafik analitik amaçlar için günlüğe kaydedilir.

Geliştiriciler için API Management Hizmetleri, belgeleri ve bunları çağırmaya yönelik örnek koda erişim sağlayan bir geliştirici portalı sunmaktadır. Geliştiriciler, hizmet uç noktalarını incelemek ve kullanımlarını çözümlemek için Swagger/Open API 'sini kullanabilir. Hizmet, .NET, Java, Golang ve daha fazlası için büyük geliştirme platformları genelinde çalışmaktadır.

Yayımcı portalı, yöneticilerin API 'Leri kullanıma sunduğu ve davranışlarını yönetebilen bir Yönetim Panosu sunar. Hizmet erişimi verilebilir, hizmet durumu izlenir ve hizmet telemetri toplanır. Yöneticiler, davranışı etkilemek için her bir uç noktaya *ilke* uygular. [İlkeler](https://docs.microsoft.com/azure/api-management/api-management-howto-policies) , her hizmet çağrısı için sırayla yürütülen önceden oluşturulmuş deyimlerdir.  İlkeler bir gelen çağrı, giden çağrı için yapılandırılır veya bir hata olduğunda çağrılır. İlkeler, ilke birleştirilirken belirleyici sıralamayı etkinleştirmek üzere farklı hizmet kapsamlarına uygulanabilir. Ürün, çok sayıda önceden oluşturulmuş [ilke](https://docs.microsoft.com/azure/api-management/api-management-policies)ile birlikte gelir.

İlkelerin bulut Yerel hizmetlerinizin davranışını nasıl etkileyebileceğini gösteren örnekler aşağıda verilmiştir:  

- Hizmet erişimini kısıtlayın.
- Kimlik doğrulamasını zorunlu tutun.  
- Gerekirse, tek bir kaynaktaki çağrıları kısıtlama.
- Önbelleğe almayı etkinleştirin.
- Belirli IP adreslerinden gelen çağrıları engelleyin.
- Hizmetin akışını denetleyin.
- İstekleri SOAP 'dan REST 'e veya XML gibi farklı veri biçimleri arasında dönüştürme.

Azure API Management, bulutta veya veri merkezinizde herhangi bir yerde barındırılan arka uç hizmetlerini kullanıma sunabilir. Bulut Yerel sistemlerinizde kullanıma sunabileceğiniz eski hizmetler için hem REST hem de SOAP API 'Lerini destekler. Diğer Azure hizmetleri de API Management aracılığıyla görüntülenebilir. Yönetilen bir API 'yi [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) veya [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/)gibi bir Azure yedekleme hizmetinin üzerine yerleştirebilirsiniz. Azure API Management, yerleşik yük dengeleme desteği içermez ve bir Yük Dengeleme hizmeti ile birlikte kullanılmalıdır.

Azure API Management [dört farklı katmanda](https://azure.microsoft.com/pricing/details/api-management/)kullanılabilir:

- Geliştirici
- Temel
- Stand
- Premium

Geliştirici katmanı, üretim dışı iş yükleri ve değerlendirme için tasarlanmıştır. Diğer katmanlar, giderek daha fazla güç, özellik ve daha yüksek hizmet düzeyi sözleşmeleri (SLA 'Lar) sunar. Premium katmanı, [Azure sanal ağı](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) ve [çok bölgeli destek](https://docs.microsoft.com/azure/api-management/api-management-howto-deploy-multi-region)sağlar. Tüm katmanların saat başına sabit bir fiyatı vardır.

Son olarak Microsoft, Azure API Management için [API Management sunucusuz bir katman](https://azure.microsoft.com/blog/announcing-azure-api-management-for-serverless-architectures/) duyurmuştur. *Tüketim fiyatlandırma katmanı*olarak adlandırılan hizmet, sunucusuz bilgi işlem modeli etrafında tasarlanan API Management bir değişkendir. Daha önce gösterilen "önceden ayrılmış" fiyatlandırma katmanlarının aksine, tüketim katmanı hızlı sağlama ve eylem başına ödeme fiyatlandırması sağlar.

Aşağıdaki kullanım örnekleri için API Gateway özelliklerini sunar:

- Mikro hizmetler, [Azure işlevleri](https://docs.microsoft.com/azure/azure-functions/functions-overview) ve [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/)gibi sunucusuz teknolojiler kullanılarak uygulanır.
- Azure yedekleme hizmeti kaynakları, Service Bus kuyrukları ve konuları, Azure depolama ve diğerleri.
- Trafiğin zaman zaman büyük ani artışlar olduğu halde mikro hizmetler, sürenin büyük bölümü azalmış kalır.

Tüketim katmanı, aynı temel hizmet API Management bileşenlerini kullanır, ancak dinamik olarak ayrılan kaynaklara göre tamamen farklı bir mimari kullanır. Sunucusuz bilgi işlem modeliyle mükemmel bir şekilde hizalanır:

- Yönetilecek altyapı yok.
- Boş kapasite yok.
- Yüksek kullanılabilirlik.
- Otomatik ölçeklendirme.
- Maliyet, gerçek kullanıma göre belirlenir.
  
Yeni tüketim katmanı, sunucusuz kaynakları API olarak sunan, bulutta yerel sistemler için harika bir seçimdir.

> Yazma sırasında, tüketim katmanı Azure bulutu 'nda önizlemededir.

## <a name="real-time-communication"></a>Gerçek zamanlı iletişim

Gerçek zamanlı veya gönderim, iletişim, ön uç uygulamalar için HTTP üzerinden arka uç bulut Yerel sistemleriyle iletişim kuran başka bir seçenektir. Finansal-ticiler, çevrimiçi eğitim, oyun ve iş ilerlemesi güncelleştirmeleri gibi uygulamalar, arka uçta anlık ve gerçek zamanlı yanıtlar gerektirir. Normal HTTP iletişimi sayesinde, istemcinin yeni verilerin ne zaman kullanılabilir olduğunu öğrenme yöntemi yoktur. İstemci sürekli olarak *yoklama* veya sunucuya istek gönderiyor olmalıdır. *Gerçek* zamanlı iletişimle, sunucu istediğiniz zaman istemciye yeni verileri gönderebilir.

Gerçek zamanlı sistemler genellikle yüksek frekanslı veri akışları ve çok sayıda eşzamanlı istemci bağlantısı tarafından belirlenir. Gerçek zamanlı bağlantının el ile uygulanması, bağlantılı istemcilere ölçeklenebilirlik ve güvenilir mesajlaşma sağlamak için önemsiz olmayan bir altyapı gerektiren hızlı bir şekilde karmaşık hale gelebilir. Bir Azure Redis Cache örneğini ve istemci benzeşimi için yapışkan oturumlarla yapılandırılmış yük dengeleyiciler kümesini yönetme hakkında bilgi edinebilirsiniz.

[Azure SignalR hizmeti](https://azure.microsoft.com/services/signalr-service/) , bulutta yerel uygulamalarınızın gerçek zamanlı iletişimini kolaylaştıran, tam olarak yönetilen bir Azure hizmetidir. Kapasite sağlama, ölçekleme ve kalıcı bağlantılar gibi teknik uygulama ayrıntıları soyutlanmıştır. Bunlar sizin için 99,9% bir hizmet düzeyi sözleşmesi ile işlenirler. Altyapı sıhhi tesisat değil uygulama özelliklerine odaklanırsınız.

Bulut tabanlı bir HTTP hizmeti etkinleştirildikten sonra, tarayıcı, mobil ve Masaüstü uygulamaları dahil olmak üzere doğrudan bağlı istemcilere içerik güncelleştirmeleri gönderebilir. İstemciler, sunucuyu yoklamaya gerek kalmadan güncelleştirilir. Azure SignalR, WebSockets, sunucu tarafı olayları ve uzun yoklama dahil gerçek zamanlı bağlantı oluşturan aktarım teknolojilerini soyutlar. Geliştiriciler bağlı istemcilerin tamamına veya belirli alt kümelerine ileti göndermeye odaklanmaktadır.

Şekil 4-7, Azure SignalR özellikli bir bulutta yerel uygulamaya bağlanan bir HTTP Istemcileri kümesini gösterir.

![Azure SignalR](./media/azure-signalr-service.png)

**Şekil 4-7.** Azure SignalR

Azure SignalR hizmeti 'nin başka bir avantajı da sunucusuz bulut Yerel Hizmetleri uygulama ile birlikte gelir. Belki de kodunuz Azure Işlevleri tetikleyicilerine göre isteğe bağlı olarak yürütülür. Bu senaryo, kodunuz istemcilerle uzun bağlantıları korumadığından karmaşık olabilir. Azure SignalR hizmeti, hizmet bağlantıları zaten sizin için yönettiğinden bu durumu işleyebilir.

Azure SignalR hizmeti, Azure SQL veritabanı, Service Bus veya Redis Cache gibi diğer Azure hizmetleriyle yakından tümleştirilir, bulutta yerel uygulamalarınız için birçok olasılıktan fazlasını açıyor.

>[!div class="step-by-step"]
>[Önceki](communication-patterns.md)
>[İleri](service-to-service-communication.md)
