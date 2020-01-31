---
title: Service Mesh iletişim altyapısı
description: Hizmet ağı teknolojilerinin bulut Yerel mikro hizmet iletişimini nasıl kolaylaştırması hakkında bilgi edinin
author: robvet
ms.date: 09/10/2019
ms.openlocfilehash: 66bc69580cc56efe725683c16a047aeb07e7e840
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76780929"
---
# <a name="service-mesh-communication-infrastructure"></a>Service Mesh iletişim altyapısı

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bu bölümde, mikro hizmet iletişiminin sorunlarını araştırdık. Geliştirme ekiplerinin, arka uç hizmetlerinin birbirleriyle iletişim kurmasına duyarlı olmaları gerektiğini belirledik. İdeal olarak, hizmet içi iletişim, daha iyi. Ancak, arka uç hizmetleri genellikle işlemleri tamamlamaya yönelik bir diğerine bağlı olduğu için engelleme her zaman mümkün değildir.

Zaman uyumlu HTTP iletişimini ve zaman uyumsuz mesajlaşma uygulamak için farklı yaklaşımlar araştırdık. Her bir durumda, geliştirici iletişim kodu uygulamayla birlikte kullanıma açıldı. İletişim kodu karmaşıktır ve zaman yoğunluğu vardır. Yanlış kararlar önemli performans sorunlarına neden olabilir.

*Hizmet ağı*ile yeni ve hızlı gelişen bir teknolojinin etrafında mikro hizmet iletişim merkezlerine daha modern bir yaklaşım. [Hizmet ağı](https://www.nginx.com/blog/what-is-a-service-mesh/) , Service-to-Service iletişimini, dayanıklılığı ve birçok çapraz kesme ile ilgili sorunları ele almak için yerleşik yeteneklere sahip yapılandırılabilir bir altyapı katmanıdır. Bu sorunlar için sorumluluğu mikro hizmetlerden ve hizmet kafes katmanının dışına taşımıştır. İletişim, mikro hizmetlerinizin dışında soyutlanmıştır.

Bir hizmet ağı 'nın anahtar bileşeni bir ara sunucu. Bulutta yerel bir uygulamada, bir ara sunucu örneği genellikle her bir mikro hizmetle birlikte bulunur. Ayrı işlemlerde yürütme yaparken, ikisi de yakından bağlantılıdır ve aynı yaşam döngüsünü paylaşır. Bu model, [sepet](https://docs.microsoft.com/azure/architecture/patterns/sidecar)olarak bilinen ve Şekil 4-23 ' de gösterilmiştir.

![Yan otomobil ile hizmet ağı](./media/service-mesh-with-side-car.png)

**Şekil 4-23**. Yan otomobil ile hizmet ağı

Önceki şekilde, iletilerin her mikro hizmet ile birlikte çalışan bir ara sunucu tarafından nasıl yakalandığını unutmayın. Her proxy, mikro hizmete özel trafik kurallarıyla yapılandırılabilir. İletileri anlamıştır ve bunları hizmetlerinize ve dış dünyaya yönlendirebilir.

Hizmet ağı, hizmetten hizmete iletişimin yönetilmesine birlikte hizmet bulma ve yük dengeleme için destek sağlar.

Bir hizmet ağı yapılandırıldıktan sonra oldukça işlevseldir. Ağ hizmeti bulma uç noktasından karşılık gelen bir örnek havuzu alır. Belirli bir hizmet örneğine bir istek gönderir ve sonucun gecikme süresini ve yanıt türünü kaydetme. Son istekler için gözlemlenen gecikme süresi dahil olmak üzere, farklı faktörlere bağlı olarak hızlı bir yanıt döndürmesinin en olası örneğini seçer.

Hizmet ağı, uygulama düzeyinde trafik, iletişim ve ağ sorunlarını yönetir. İletileri ve istekleri anlamıştır. Hizmet ağı genellikle bir kapsayıcı Orchestrator ile tümleşir. Kubernetes, hizmet kafesinin eklenebileceği genişletilebilir bir mimariyi destekler.

Bölüm 6 ' da, mimarisi ve kullanılabilir açık kaynaklı uygulamalarla ilgili bir tartışma dahil olmak üzere hizmet ağı teknolojilerini yakından inceleyeceğiz.

## <a name="summary"></a>Özet

Bu bölümde, bulutta yerel iletişim desenleri tartışıyoruz. Ön uç istemcilerinin arka uç mikro hizmetleriyle nasıl iletişim kurduğunu inceleyerek başladık. Bu şekilde, API Gateway platformları ve gerçek zamanlı iletişim hakkında konuşuyoruz. Daha sonra mikro hizmetlerin diğer arka uç hizmetleriyle nasıl iletişim kuracağını inceledik. Hem zaman uyumlu HTTP iletişimini hem de hizmetler genelinde zaman uyumsuz mesajlaşmayı inceledik. Bulutta yerel dünyada yakında sunulacak bir teknoloji olan gRPC 'yi kapsadık. Son olarak, hizmet ağı ile mikro hizmet iletişimini kolaylaştırmaya yönelik yeni ve hızlı bir şekilde gelişen bir teknoloji tanıtıldık.

Bulutta yerel sistemlerde iletişimin sağlanmasına yardımcı olabilecek, yönetilen Azure hizmetlerinde özel bir vurgu yapıldı:

- [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/overview)
- [Azure API Management](https://azure.microsoft.com/services/api-management/)
- [Azure SignalR Hizmeti](https://azure.microsoft.com/services/signalr-service/)
- [Azure depolama kuyrukları](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure Olay Hub 'ı](https://azure.microsoft.com/services/event-hubs/)

Daha sonra bulut Yerel sistemlerdeki dağıtılmış verilere ve sunmakta olduğu avantajlara ve güçlüklere geçeceğiz.

### <a name="references"></a>Referanslar

- [.NET mikro hizmetleri: Kapsayıcılı .NET uygulamaları için mimari](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Mikro hizmetler için Interservice Iletişimi tasarlama](https://docs.microsoft.com/azure/architecture/microservices/design/interservice-communication)

- [Gerçek zamanlı işlevselliği eklemek için tam olarak yönetilen bir hizmet olan Azure SignalR hizmeti](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [Azure API ağ geçidi giriş denetleyicisi](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [Azure Kubernetes Service (AKS) içindeki giriş hakkında](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [Pratik gRPC](https://www.worldcat.org/title/practical-grpc/oclc/1042342319)

- [gRPC belgeleri](https://grpc.io/docs/guides/)

- [WCF geliştiricileri Için GRPC](https://bing.com) [Mark GRPC book]

- [GRPC hizmetlerini HTTP API 'Leri ile karşılaştırma](https://docs.microsoft.com/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

>[!div class="step-by-step"]
>[Önceki](rest-grpc.md)
>[İleri](Database-per-microservice.md)
