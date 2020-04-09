---
title: Ön uç istemci iletişimi
description: Ön uç istemcilerin bulut tabanlı sistemlerle nasıl iletişim kurduğunu öğrenin
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: af26873381509df7807db6ecb37a7d73669adb37
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989083"
---
# <a name="front-end-client-communication"></a>Ön uç istemci iletişimi

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bulut ait bir sistemde, ön uç istemciler (mobil, web ve masaüstü uygulamaları) bağımsız arka uç mikro hizmetlerle etkileşim kurmak için bir iletişim kanalı gerektirir.  

Seçenekler nelerdir?

İşleri basit tutmak için, ön uç istemcisi Şekil 4-2'de gösterilen arka uç mikro hizmetlerle *doğrudan iletişim kurabilir.*

![Hizmet iletişimine doğrudan istemci](./media/direct-client-to-service-communication.png)

**Şekil 4-2.** Hizmet iletişimine doğrudan istemci

Bu yaklaşımla, her microservice ön uç istemcileri tarafından erişilebilir bir ortak bitiş noktası vardır. Üretim ortamında, trafiği orantılı olarak yönlendirme, mikro hizmetlerin önüne bir yük dengeleyicisi yerleştirilecek.

Uygulanması basit olsa da, doğrudan istemci iletişimi sadece basit microservice uygulamaları için kabul edilebilir olacaktır. Bu desen sıkıca çekirdek arka uç hizmetleri için ön uç müşterileri çiftler, dahil olmak üzere bir dizi sorun için kapıyı açarak:

- Müşteri arka uç hizmet refactoring için duyarlılık.
- Çekirdek arka uç hizmetleri doğrudan maruz olarak daha geniş bir saldırı yüzeyi.
- Her mikro hizmet te çapraz kesme endişelerinin çoğaltılması.
- Aşırı karmaşık istemci kodu - istemciler birden çok uç noktayı izlemeli ve hataları esnek bir şekilde işlemelidir.

Bunun yerine, yaygın olarak kabul edilen bulut tasarım deseni, ön uç uygulamaları ve arka uç hizmetleri arasında bir [API Ağ Geçidi Hizmeti](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) uygulamaktır. Desen Şekil 4-3'te gösterilmiştir.

![API Ağ Geçidi Deseni](./media/api-gateway-pattern.png)

**Şekil 4-3.** API ağ geçidi deseni

Önceki şekilde, API Ağ Geçidi hizmetinin arka uç çekirdek mikro hizmetlerini nasıl özetlediğime dikkat edin. Bir web API olarak uygulanan, bir *ters proxy*olarak hareket eder , iç mikrohizmetler için gelen trafik yönlendirme.

Ağ geçidi, istemciyi dahili hizmet bölümleme ve yeniden düzenlemeden yalıtıyor. Bir arka uç hizmetini değiştirirseniz, istemciyi bozmadan ağ geçidinde barındırırsınız. Ayrıca kimlik, önbelleğe alma, esneklik, ölçüm leme ve azaltma gibi çapraz kesme endişeleri için ilk savunma hattıdır. Bu çapraz kesme kaygılarının çoğu arka uç temel servislerinden ağ geçidine yüklenebilir ve arka uç hizmetlerini basitleştirebilir.

API Ağ Geçidi'ni basit ve hızlı tutmaya özen gerekir. Genellikle, iş mantığı ağ geçidi dışında tutulur. Karmaşık bir ağ geçidi bir darboğaz ve sonunda bir monolit kendisi olma riskleri. Daha büyük sistemler genellikle istemci türüne (mobil, web, masaüstü) veya arka uç işlevlerine göre bölümlenmiş birden çok API Ağ Geçidi ni ortaya çıkarır. Frontends deseni [için Backend,](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) birden çok ağ geçidi uygulamak için yön sağlar. Desen Şekil 4-4'te gösterilmiştir.

![API Ağ Geçidi Deseni](./media/backend-for-frontend-pattern.png)

**Şekil 4-4.** Ön uç deseni için arka uç

Önceki şekilde gelen trafiğin belirli bir API ağ geçidine nasıl gönderildiğini not edin - istemci türüne göre: web, mobil veya masaüstü uygulaması. Her aygıtın yetenekleri form faktörü, performans ve görüntü sınırlamaları arasında önemli ölçüde farklılık gösterdiğinden, bu yaklaşım anlamlıdır. Genellikle mobil uygulamalar tarayıcı veya masaüstü uygulamalarından daha az işlevsellik ortaya çıkarır. Her ağ geçidi, ilgili aygıtın özellikleri ve işlevleriyle eşleşecek şekilde optimize edilebilir.

Başlangıç olarak, kendi API Ağ Geçidi hizmetinizi oluşturabilirsiniz. GitHub hızlı bir arama birçok örnek verecektir. Ancak, çeşitli çerçeveler ve ticari ağ geçidi ürünleri mevcuttur.

## <a name="ocelot-gateway"></a>Ocelot Ağ Geçidi

Basit .NET bulut tabanlı uygulamalar için [Ocelot Ağ Geçidi'ni](https://github.com/ThreeMammals/Ocelot)düşünebilirsiniz. Ocelot, .NET mikro hizmetleri için oluşturulan ve sisteme birleşik bir giriş noktası gerektiren bir Açık Kaynak API Ağ Geçididir. Hafif, hızlı, ölçeklenebilir.

Herhangi bir API Ağ Geçidi gibi, birincil işlevi gelen HTTP isteklerini aşağı akış hizmetlerine iletmektir. Ayrıca, bir .NET Core ara yazılım ardışık boru hattında yapılandırılabilir yetenekleri geniş bir yelpazede destekler. Özellik kümesi aşağıdaki tabloda sunulur.

|Ocelot Özellikleri  | |
| :-------- | :-------- |
| Yönlendirme | Kimlik Doğrulaması |
| İstek Toplama | Yetkilendirme |
| Hizmet Bulma (Konsolos ve Eureka ile) | Azaltma |
| Yük Dengeleme | Günlük, İzleme |
| Önbelleğe alma | Üstbilgi/Sorgu Dize Dönüşümü |
| Korelasyon Geçişi | Özel Middleware |
| Hizmet Kalitesi | Yeniden İlkeler |

Her Ocelot ağ geçidi, json yapılandırma dosyasında yukarı ve aşağı akışları adreslerini ve yapılandırılabilir özellikleri belirtir. İstemci Ocelot ağ geçidine bir HTTP isteği gönderir. Ocelot, alındıktan sonra HttpRequest nesnesini, yapılandırmasında belirtilen duruma yönlendirerek ardışık kaynaktan geçirir. Boru hattının sonunda, Ocelot yeni bir HTTPResponseObject oluşturur ve alt hizmete geçirir. Yanıt için, Ocelot yanıtı istemciye geri göndererek ardışık hattı tersine çevirir.

Ocelot NuGet paketi olarak mevcuttur. NET Standart 2.0'ı hedefler ve hem .NET Core 2.0+ hem de .NET Framework 4.6.1+ çalışma süreleri ile uyumlu hale getirir. Ocelot, HTTP konuşan ve .NET Core'un desteklediği platformlarda çalışan her şeyle bütünleşir: Linux, macOS ve Windows. Ocelot genişletilebilir ve Docker kapsayıcıları, Azure Kubernetes Hizmetleri veya diğer genel bulutlar dahil olmak üzere birçok modern platformu destekler.  Ocelot [Konsolos](https://www.consul.io)gibi açık kaynak paketleri ile entegre , [GraphQL](https://graphql.org), ve Netflix's [Eureka](https://github.com/Netflix/eureka).

Ticari API ağ geçidinin zengin özellik kümesini gerektirmeyen basit bulut tabanlı uygulamalar için Ocelot'u düşünün.

## <a name="azure-application-gateway"></a>Azure Application Gateway

Basit ağ geçidi gereksinimleri için [Azure Uygulama Ağ Geçidi'ni](https://docs.microsoft.com/azure/application-gateway/overview)düşünebilirsiniz. Azure [PaaS hizmeti](https://azure.microsoft.com/overview/what-is-paas/)olarak kullanılabilir, URL yönlendirme, SSL sonlandırma ve Web Uygulaması Güvenlik Duvarı gibi temel ağ geçidi özelliklerini içerir. Hizmet [Katman-7 yük dengeleme](https://www.nginx.com/resources/glossary/layer-7-load-balancing/) özelliklerini destekler. Katman 7 ile, istekleri yalnızca düşük düzeyli TCP ağ paketlerinin değil, bir HTTP iletisinin gerçek içeriğine göre yönlendirebilirsiniz.

Bu kitap boyunca, [Biz Kubernetes](https://www.infoworld.com/article/3268073/what-is-kubernetes-your-next-application-platform.html)bulut-yerli sistemleri barındırma evangelize. Bir konteyner orkestratörü olan Kubernetes, konteynerleştirilmiş iş yüklerinin dağıtımını, ölçeklemesini ve operasyonel endişelerini otomatikleştirir. Azure Uygulama Ağ Geçidi, [Azure Kubernetes Hizmet](https://azure.microsoft.com/services/kubernetes-service/) kümesi için bir API ağ geçidi olarak yapılandırılabilir.

[Uygulama Ağ Geçidi Giriş Denetleyicisi,](https://azure.github.io/application-gateway-kubernetes-ingress/) Azure Uygulama Ağ Geçidi'nin doğrudan Azure [Kubernetes Hizmeti](https://azure.microsoft.com/services/kubernetes-service/)ile çalışmasını sağlar. Şekil 4.5 mimarisini gösterir.

![Application Gateway Giriş Denetleyicisi](./media/application-gateway-ingress-controller.png)

**Şekil 4-5.** Application Gateway Giriş Denetleyicisi

Kubernetes, [HTTP](https://kubernetes.io/docs/concepts/services-networking/ingress/)(Düzey 7) yük dengelemeyi destekleyen yerleşik bir özellik içerir. Giriş, AKS içindeki mikrohizmet örneklerinin dış dünyaya nasıl maruz kalına açıklanabildiği ne kadar kurallar tanımlar. Önceki resimde, giriş denetleyicisi küme için yapılandırılan giriş kurallarını yorumlar ve Azure Uygulama Ağ Geçidi'ni otomatik olarak yapılandırır. Bu kurallara göre, Uygulama Ağ Geçidi trafiği AKS içinde çalışan mikro hizmetlere yönlendirir. Giriş denetleyicisi giriş kurallarındaki değişiklikleri dinler ve Azure Uygulama Ağ Geçidi'nde uygun değişiklikleri yapar.

## <a name="azure-api-management"></a>Azure API Management

Orta ve büyük ölçekli bulut tabanlı sistemler için [Azure API Yönetimi'ni](https://azure.microsoft.com/services/api-management/)düşünebilirsiniz. Bu, yalnızca API Ağ Geçidi ihtiyaçlarınızı çözmekle kalmıyor, aynı zamanda tam özellikli bir geliştirici ve yönetim deneyimi de sağlayan bulut tabanlı bir hizmet. API Yönetimi Şekil 4-6'da gösterilmiştir.

![Azure API Management](./media/azure-api-management.png)

**Şekil 4-6.** Azure API Management

Başlatmak için, API Yönetimi, yapılandırılabilir kurallar ayarı ve ilkelerine dayalı arka uç hizmetlerine kontrollü erişim sağlayan bir ağ geçidi sunucusu ortaya çıkarır. Bu hizmetler Azure bulutu, ön hazırlık veri merkezinizde veya diğer genel bulutlarda olabilir. API anahtarları ve JWT belirteçleri kimin ne yapabileceğini belirler. Tüm trafik analitik amaçlarla günlüğe kaydedilir.

Geliştiriciler için API Management, hizmetlere, belgelere ve bunları çağırmak için örnek kodlara erişim sağlayan bir geliştirici portalı sunar. Geliştiriciler, hizmet bitiş noktalarını incelemek ve kullanımlarını analiz etmek için Swagger/Open API'yi kullanabilir. Hizmet, büyük geliştirme platformlarında çalışır: .NET, Java, Golang ve daha fazlası.

Yayımcı portalı, yöneticilerin API'leri ortaya çıkardığı ve davranışlarını yönettiği bir yönetim panosu ortaya çıkarır. Hizmet erişimi verilebilir, hizmet sağlığı izlenebilir ve hizmet telemetrisi toplanabilir. Yöneticiler, davranışı etkilemek için her uç noktaya *ilkeler* uygular. İlkeler, her hizmet çağrısı için sırayla yürüten önceden oluşturulmuş [deyimlerdir.](https://docs.microsoft.com/azure/api-management/api-management-howto-policies)  İlkeler, gelen arama, giden çağrı veya bir hata üzerine çağrılmak üzere yapılandırılır. İlkeler, ilkeleri birleştirirken deterministic sıralamayı etkinleştirmek için farklı hizmet kapsamlarında uygulanabilir. Önceden inşa [politikaları](https://docs.microsoft.com/azure/api-management/api-management-policies)çok sayıda ürün gemileri.

İlkelerin bulut ayarı olan hizmetlerinizin davranışını nasıl etkileyebileceğine örnekler aşağıda verilmiştir:  

- Hizmet erişimini kısıtlayın.
- Kimlik doğrulamasını zorla.  
- Gerekirse tek bir kaynaktan gelen gaz çağrıları.
- Önbelleğe alma'yı etkinleştirin.
- Belirli IP adreslerinden gelen aramaları engelleyin.
- Hizmet akışını kontrol edin.
- İstekleri SOAP'dan REST'e veya XML'den JSON'a gibi farklı veri biçimleri arasında dönüştürün.

Azure API Yönetimi, bulutta veya veri merkezinizde her yerde barındırılan arka uç hizmetlerini ortaya çıkarabilir. Bulut tabanlı sistemlerinizde ortaya çıkarabileceğiniz eski hizmetler için hem REST hem de SOAP API'lerini destekler. Diğer Azure hizmetleri bile API Yönetimi aracılığıyla ortaya çıkabilir. Azure [Hizmet Veri Veri Tos'u](https://azure.microsoft.com/services/service-bus/) veya Azure Mantıksal [Uygulamaları](https://azure.microsoft.com/services/logic-apps/)gibi bir Azure destek hizmetinin üzerine yönetilen bir API yerleştirebilirsiniz. Azure API Yönetimi yerleşik yük dengeleme desteğini içermez ve bir yük dengeleme hizmetiyle birlikte kullanılmalıdır.

Azure API Yönetimi [dört farklı katmanda](https://azure.microsoft.com/pricing/details/api-management/)kullanılabilir:

- Geliştirici
- Temel
- Standart
- Premium

Geliştirici katmanı, üretim dışı iş yükleri ve değerlendirme içindir. Diğer katmanlar giderek daha fazla güç, özellik ve daha yüksek hizmet düzeyi anlaşmaları (SLA'lar) sunar. Premium katman [Azure Sanal Ağ](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) ve [çok bölgeli destek](https://docs.microsoft.com/azure/api-management/api-management-howto-deploy-multi-region)sağlar. Tüm katmanlar saat başına sabit bir fiyata sahiptir.

Son zamanlarda Microsoft, Azure API Yönetimi için [bir API Yönetimi sunucusuz katmanı](https://azure.microsoft.com/blog/announcing-azure-api-management-for-serverless-architectures/) duyurdu. Tüketim fiyatlandırma *katmanı*olarak adlandırılan hizmet, sunucusuz bilgi işlem modeli etrafında tasarlanmış API Yönetimi'nin bir çeşididir. Daha önce gösterilen "önceden tahsis edilmiş" fiyatlandırma katmanlarının aksine, tüketim katmanı anında sağlama ve eylem başına ödeme fiyatlandırması sağlar.

Aşağıdaki kullanım örnekleri için API Ağ Geçidi özelliklerini sağlar:

- [Azure İşlevler](https://docs.microsoft.com/azure/azure-functions/functions-overview) ve [Azure Mantık Uygulamaları](https://azure.microsoft.com/services/logic-apps/)gibi sunucusuz teknolojiler kullanılarak uygulanan microservices.
- Hizmet Veri Mes'i kuyrukları ve konuları, Azure depolama ve diğerleri gibi Azure destek hizmet kaynaklarını destekler.
- Trafiğin zaman zaman büyük ani olduğu ancak çoğu zaman düşük kaldığı mikro hizmetler.

Tüketim katmanı aynı temel hizmet API Yönetimi bileşenlerini kullanır, ancak dinamik olarak ayrılan kaynaklara dayalı tamamen farklı bir mimari kullanır. Sunucusuz bilgi işlem modeliyle mükemmel bir şekilde uyumluhale getirir:

- Yönetecek altyapı yok.
- Boşta kapasite yok.
- Yüksek kullanılabilirlik.
- Otomatik ölçekleme.
- Maliyet, fiili kullanıma bağlıdır.
  
Yeni tüketim katmanı, sunucusuz kaynakları API'ler olarak ortaya çıkaran bulut tabanlı sistemler için mükemmel bir seçimdir.

> Yazma sırasında, tüketim katmanı Azure bulutunda önizlemededir.

## <a name="real-time-communication"></a>Gerçek zamanlı iletişim

Gerçek zamanlı veya itme, iletişim, https://yassı sistemlerle HTTP üzerinden iletişim sağlayan ön uç uygulamalar için başka bir seçenektir. Finansal işaretlemeler, çevrimiçi eğitim, oyun oynama ve iş ilerleme güncellemeleri gibi uygulamalar, arka uçtan anında, gerçek zamanlı yanıtlar gerektirir. Normal HTTP iletişimi sayesinde, istemcinin yeni verilerin ne zaman kullanılabildığını bilmesi ne zaman mümkündür. İstemci sürekli *olarak yoklama* veya sunucuya istek göndermek gerekir. *Gerçek zamanlı* iletişim sayesinde, sunucu istediği zaman istemciye yeni veriler itebilir.

Gerçek zamanlı sistemler genellikle yüksek frekanslı veri akışları ve çok sayıda eşzamanlı istemci bağlantısı ile karakterize edilir. Gerçek zamanlı bağlantının el ile uygulanması, bağlı istemcilere ölçeklenebilirlik ve güvenilir mesajlaşma sağlamak için önemsiz olmayan altyapı gerektiren, hızlı bir şekilde karmaşık hale gelebilir. Kendinizi Azure Redis Önbelleği'nin bir örneğini ve istemci yakınlığı için yapışkan oturumlarla yapılandırılan bir dizi yük dengeleyicisini yönetirken bulabilirsiniz.

[Azure SignalR Hizmeti,](https://azure.microsoft.com/services/signalr-service/) bulut ayarı uygulamalarınız için gerçek zamanlı iletişimi kolaylaştıran tam olarak yönetilen bir Azure hizmetidir. Kapasite sağlama, ölçekleme ve kalıcı bağlantılar gibi teknik uygulama ayrıntıları soyutlanır. %99.9 hizmet seviyesi anlaşmasıyla sizin için halledilirler. Altyapı tesisatı değil, uygulama özelliklerine odaklanırsınız.

Bulut tabanlı bir HTTP hizmeti etkinleştirildiğinde, içerik güncelleştirmelerini tarayıcı, mobil ve masaüstü uygulamaları da dahil olmak üzere doğrudan bağlı istemcilere iletebilir. İstemciler sunucuyu yoklamaya gerek kalmadan güncelleştirilir. Azure SignalR, Web Sockets, Sunucu Tarafı Etkinlikleri ve Uzun Yoklama gibi gerçek zamanlı bağlantı oluşturan aktarım teknolojilerini özetler. Geliştiriciler, bağlı istemcilerin tümüne veya belirli alt kümelerine ileti göndermeye odaklanır.

Şekil 4-7, Azure SignalR etkinleştirilmiş bulut tabanlı bir uygulamaya bağlanan bir TÜR İstemci kümesini gösterir.

![Azure SignalR](./media/azure-signalr-service.png)

**Şekil 4-7.** Azure SignalR

Azure SignalR Hizmetinin bir diğer avantajı da Serverless bulut ayarı hizmetlerinin uygulanmasıyla birlikte gelir. Belki de kodunuz Azure Fonksiyonları tetikleyicileri ile isteğe bağlı olarak yürütülür. Kodunuz istemcilerle uzun bağlantılar sağlamadığından, bu senaryo zor olabilir. Azure SignalR Hizmeti, bağlantıları zaten yönettiği için bu durumu sizin yerinize çözebilir.

Azure SignalR Hizmeti, Azure SQL Veritabanı, Hizmet Veri Cemi veya Redis Önbelleği gibi diğer Azure hizmetleriyle yakından tümleşince bulut ayarı uygulamalarınız için birçok olasılık açar.

>[!div class="step-by-step"]
>[Önceki](communication-patterns.md)
>[Sonraki](service-to-service-communication.md)
