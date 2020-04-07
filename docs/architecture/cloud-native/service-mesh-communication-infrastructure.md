---
title: Service Mesh iletişim altyapısı
description: Hizmet örgü teknolojilerinin bulut ayarı mikro hizmet iletişimini nasıl kolaylaştırdığını öğrenin
author: robvet
ms.date: 03/03/2020
ms.openlocfilehash: 8bb57e990dbf1baf8c246fe4aacfbb2904a251e6
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805756"
---
# <a name="service-mesh-communication-infrastructure"></a>Service Mesh iletişim altyapısı

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bu bölüm boyunca, mikrohizmet iletişiminin zorluklarını araştırdık. Geliştirme ekiplerinin arka uç servisin birbiriyle nasıl iletişim kurduğu konusunda duyarlı olması gerektiğini söyledik. İdeal olarak, daha az hizmet arası iletişim, daha iyi. Ancak, arka uç hizmetleri işlemleri tamamlamak için genellikle birbirlerine güvendiğinden kaçınma her zaman mümkün değildir.

Senkron HTTP iletişimi ve eşzamanlı mesajlaşmayı uygulamak için farklı yaklaşımları araştırdık. Her durumda, geliştirici iletişim kodu uygulama ile yüklenir. İletişim kodu karmaşık ve zaman yoğundur. Yanlış kararlar önemli performans sorunlarına yol açabilir.

*Hizmet Mesh*başlıklı yeni ve hızla gelişen teknoloji etrafında mikrohizmet iletişim merkezleri için daha modern bir yaklaşım. [Hizmet örgü,](https://www.nginx.com/blog/what-is-a-service-mesh/) hizmete hizmet iletişimi, esneklik ve birçok çapraz kesme kaygısını işlemek için yerleşik özelliklere sahip yapılandırılabilir bir altyapı katmanıdır. Bu endişelerin sorumluluğunu mikro hizmetlerden çıkarıp servis örgü katmanına taşır. İletişim, mikro hizmetlerinizden soyutlanır.

Hizmet kafesinin önemli bir bileşeni proxy'dir. Bulut ait bir uygulamada, proxy örneği genellikle her microservice ile birlikte konumlanır. Ayrı işlemlerde yürütülürken, ikisi birbirine yakından bağlıdır ve aynı yaşam döngüsünü paylaşır. [Sidecar deseni](https://docs.microsoft.com/azure/architecture/patterns/sidecar)olarak bilinen bu desen Şekil 4-24'te gösterilmiştir.

![Yan araba ile servis örgü](./media/service-mesh-with-side-car.png)

**Şekil 4-24**. Yan araba ile servis örgü

Önceki şekilde iletilerin her microservice ile birlikte çalışan bir proxy tarafından nasıl ele geçirildiğine dikkat edin. Her proxy, mikro hizmete özgü trafik kurallarıyla yapılandırılabilir. İletileri anlar ve bunları hizmetlerinize ve dış dünyaya yönlendirebilir.

Service Mesh, hizmetten hizmete iletişimi yönetmenin yanı sıra hizmet bulma ve yük dengeleme desteği sağlar.

Bir kez yapılandırıldıktan sonra, bir hizmet örgüson derece işlevseldir. Kafes, bir hizmet bulma bitiş noktasından karşılık gelen bir örnek havuzunu alır. Belirli bir hizmet örneğine, sonucun gecikme sebebini ve yanıt türünü kaydederek bir istek gönderir. Son istekler için gözlenen gecikme sonu da dahil olmak üzere farklı etkenlere göre hızlı yanıt verme olasılığı en yüksek örneği seçer.

Servis kafesi, uygulama düzeyinde trafik, iletişim ve ağ la ilgili endişeleri yönetir. İletileri ve istekleri anlar. Servis örgüsi genellikle bir kapsayıcı orkestratörle bütünleşir. Kubernetes, bir hizmet örgüsü eklenebilir genişletilebilir bir mimari destekler.

Bölüm 6'da, mimarisi ve mevcut açık kaynak uygulamaları üzerine bir tartışma da dahil olmak üzere Service Mesh teknolojilerine derinlemesine daldık.

## <a name="summary"></a>Özet

Bu bölümde bulut-yerel iletişim kalıplarını tartıştık. Ön uç müşterilerinin arka uç mikro hizmetlerle nasıl iletişim kurduklarını inceleyerek başladık. Yol boyunca, API Gateway platformları ve gerçek zamanlı iletişim hakkında konuştuk. Daha sonra mikro hizmetlerin diğer arka uç servislerle nasıl iletişim kurduğuna baktık. Hem senkron HTTP iletişimine hem de hizmetler arasında eşzamanlı mesajlaşmaya baktık. Bulut-yerli dünyada yeni bir teknoloji olan gRPC'yi ele aldık. Son olarak, mikro hizmet iletişimini kolaylaştırabilen Service Mesh adlı yeni ve hızla gelişen bir teknoloji sunduk.

Bulut ayarı olan sistemlerde iletişimin uygulanmasına yardımcı olabilecek yönetilen Azure hizmetlerine özel önem verildi:

- [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/overview)
- [Azure API Management](https://azure.microsoft.com/services/api-management/)
- [Azure SignalR Service](https://azure.microsoft.com/services/signalr-service/)
- [Azure Depolama Kuyrukları](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure Event Hub](https://azure.microsoft.com/services/event-hubs/)

Daha sonra bulut ayarı sistemlerde dağıtılmış verilere ve sunduğu avantajlara ve zorluklara geçiyoruz.

### <a name="references"></a>Başvurular

- [.NET Microservices: Containerized .NET uygulamaları için mimari](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Mikro hizmetler için Servisler Arası İletişim Tasarımı](https://docs.microsoft.com/azure/architecture/microservices/design/interservice-communication)

- [Azure SignalR Hizmeti, gerçek zamanlı işlevsellik eklemek için tam olarak yönetilen bir hizmettir](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [Azure API Ağ Geçidi Giriş Denetleyicisi](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [Azure Kubernetes Hizmetinde Giriş Hakkında (AKS)](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [gRPC Dokümantasyon](https://grpc.io/docs/guides/)

- [WCF Geliştiricileri için gRPC](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/)

- [gRPC Hizmetlerinin HTTP API'leri ile karşılaştırılması](https://docs.microsoft.com/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

- [.NET video ile gRPC Hizmetleri Oluşturma](https://channel9.msdn.com/Shows/The-Cloud-Native-Show/Building-Microservices-with-gRPC-and-NET)

>[!div class="step-by-step"]
>[Önceki](grpc.md)
>[Sonraki](database-per-microservice.md)
