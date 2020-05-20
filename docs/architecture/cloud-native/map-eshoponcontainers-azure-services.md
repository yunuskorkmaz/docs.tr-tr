---
title: eShopOnContainers'ı Azure Hizmetlerine eşleme
description: EShopOnContainers 'ı Azure Kubernetes hizmeti, API Gateway ve Azure Service Bus gibi Azure hizmetleriyle eşleme.
ms.date: 05/13/2020
ms.openlocfilehash: 271707404f7fb51aec59c6f682ddaefd0bac82cc
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613843"
---
# <a name="mapping-eshoponcontainers-to-azure-services"></a>eShopOnContainers'ı Azure Hizmetlerine eşleme

Gerekli olmasa da, proje bulutta yerel bir uygulama olarak oluşturulduğundan, Azure eShopOnContainers 'ı desteklemeye uygundur. Uygulama .NET Core ile oluşturulmuştur, bu nedenle Docker konağına bağlı olarak Linux veya Windows kapsayıcıları üzerinde çalışabilir. Uygulama, her biri kendi verileri olan birden çok otonom mikro hizmetten oluşur. Farklı mikro hizmetler, basit CRUD işlemlerinden daha karmaşık DDD ve CQRS desenlerine kadar farklı yaklaşımlar gösterimi. Mikro hizmetler, HTTP üzerinden ve ileti tabanlı iletişim aracılığıyla bir diğeri ile istemcilerle iletişim kurar. Uygulama, HTTP 'yi standart iletişim protokolü olarak benimsediğinden ve Android, iOS ve Windows platformlarında çalışan ASP.NET Core ve Xamarin mobil uygulamaları içerdiğinden, istemciler için birden çok platformu destekler.

Uygulamanın mimarisi Şekil 2-5 ' de gösterilmiştir. Sol tarafta, mobil, geleneksel web ve Web tek sayfalı uygulama (SPA) türleri ile ayrılmış olan istemci uygulamalar vardır. Sağ tarafta, her biri Docker kapsayıcılarında ve Kubernetes kümelerinde barındırılabilen sistem oluşturan sunucu tarafı bileşenleridir. Geleneksel Web uygulaması, sarı renkle gösterilen ASP.NET Core MVC uygulaması tarafından desteklenir. Bu uygulama ve mobil ve Web SPA uygulamaları, tek tek mikro hizmetlerle bir veya daha fazla API ağ geçidi üzerinden iletişim kurar. API ağ geçitleri, her bir ağ geçidinin belirli bir ön uç istemcisini destekleyecek şekilde tasarlandığı anlamına gelen "ön uçlar için arka uçlar" (BFF) düzenine uyar. Tek tek mikro hizmetler, API ağ geçitlerinin sağında listelenir ve hem iş mantığını hem de bazı kalıcılık deposu türlerini içerir. Farklı hizmetler SQL Server veritabanları, Redsıs Cache örnekleri ve MongoDB/CosmosDB mağazalarını kullanır. En sağdaki, mikro hizmetler arasında iletişim kurmak için kullanılan sistemin olay veri yolu.

![eShopOnContainers mimari ](./media/eshoponcontainers-architecture.png)
 **Şekil 2-5**. EShopOnContainers mimarisi.

Bu mimarinin sunucu tarafı bileşenleri, Azure hizmetlerine kolayca eşlenir.

## <a name="container-orchestration-and-clustering"></a>Kapsayıcı düzenlemesi ve Kümelemesi

Azure Kubernetes Service (AKS) ile ASP.NET Core MVC uygulamalarından bağımsız olarak Katalog ve sıralama mikro hizmetleri olan uygulama kapsayıcısı barındırılan Hizmetleri, barındırılabilecek ve yönetilebilir. Uygulama Docker ve Kubernetes 'te yerel olarak çalışabilir ve aynı kapsayıcılar, AKS içinde barındırılan hazırlama ve üretim ortamlarına dağıtılabilir. Sonraki bölümde görüyoruz, bu işlem otomatikleştirilebilir.

AKS, bağımsız kapsayıcı kümeleri için yönetim hizmetleri sağlar. Uygulama, yukarıdaki mimari diyagramında gösterilen her mikro hizmet için ayrı AKS kümeleri dağıtır. Bu yaklaşım, her bir hizmetin, kaynak taleplerine göre bağımsız olarak ölçeklendirilmesine olanak tanır. Her mikro hizmet de bağımsız olarak dağıtılabilir ve ideal olarak bu tür dağıtımlar sıfır sistem kapalı kalma süresine neden olur.

## <a name="api-gateway"></a>API Ağ Geçidi

EShopOnContainers uygulamasının birden çok ön uç istemcisi ve birden çok farklı arka uç hizmeti vardır. İstemci uygulamaları ve bunları destekleyen mikro hizmetler arasında bire bir yazışmalar yoktur. Böyle bir senaryoda, istemci yazılımını, çeşitli arka uç hizmetleriyle güvenli bir şekilde arabirimine yazarken harika bir karmaşıklık olabilir. Her istemcinin bu karmaşıklığı kendi kendine ele almanız gerekir. bunun sonucunda, yineleme ve hizmet olarak güncelleştirmelerin değiştirileceği veya yeni ilkelerin uygulandığı birçok yer vardır.

Azure API Management (APıM), kuruluşların API 'Leri tutarlı, yönetilebilir bir biçimde yayımlamasına yardımcı olur. APıM üç bileşenden oluşur: API ağ geçidi ve yönetim portalı (Azure portal) ve bir geliştirici portalı.

API ağ geçidi, API çağrılarını kabul eder ve bunları uygun arka uç API 'sine yönlendirir. Ayrıca, kod değişiklikleri olmadan (örneğin, eski bir arabirim bekleyen istemcilere uyum sağlamak için) API anahtarlarını veya JWT belirteçlerini ve API dönüşümünü doğrulama gibi ek hizmetler de sağlayabilir.

Azure portal, API şemasını tanımladığınız ve farklı API 'Leri ürünlere paketettiğiniz yerdir. Ayrıca, Kullanıcı erişimini yapılandırır, raporları görüntüleyebilir ve Kotalar ya da dönüşümler için ilkeleri yapılandırabilirsiniz.

Geliştirici portalı, geliştiriciler için ana kaynak görevi görür. Geliştiricilere API belgeleri, etkileşimli bir test konsolu ve kendi kullanımlarıyla ilgili raporlar sağlar. Geliştiriciler ayrıca, abonelik ve API anahtarı desteği dahil olmak üzere kendi hesaplarını oluşturup yönetmek için portalını kullanır.

APıM kullanarak uygulamalar, her biri belirli bir ön uç istemcisi için arka uç sağlayan birkaç farklı hizmet grubunu kullanıma sunabilir. Karmaşık senaryolar için APıM önerilir. Daha basit gereksinimler için, hafif API ağ geçidi Ocelot kullanılabilir. EShopOnContainers uygulaması, basitliği nedeniyle ve uygulamanın kendisi ile aynı uygulama ortamına dağıtılabileceği için Ocelot kullanır. [EShopOnContainers, APıM ve Ocelot hakkında daha fazla bilgi edinin.](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern#azure-api-management)

Uygulamanız AKS kullanıyorsa diğer bir seçenek de, Azure Gateway giriş denetleyicisi 'ni AKS kümeniz içinde Pod olarak dağıtmaktır. Bu, kümenizin bir Azure Application Gateway ile tümleşmesini sağlayarak ağ geçidinin trafiği AKS pods 'ye yükünü dengelemeye olanak tanır. [AKS Için Azure Gateway giriş denetleyicisi hakkında daha fazla bilgi edinin](https://github.com/Azure/application-gateway-kubernetes-ingress).

## <a name="data"></a>Veriler

EShopOnContainers tarafından kullanılan çeşitli arka uç Hizmetleri farklı depolama gereksinimlerine sahiptir. Birkaç mikro hizmet SQL Server veritabanlarını kullanır. Sepet mikro hizmeti, kalıcılığı için bir Redsıs önbelleği kullanır. Konumlar mikro hizmeti, verileri için bir MongoDB API 'SI bekler. Azure, bu veri biçimlerinin her birini destekler.

Azure SQL Server veritabanı desteği için, tek veritabanlarından gelen ve yüksek düzeyde ölçeklenebilir SQL veritabanı elastik havuzlarına kadar her şeye yönelik ürünleri vardır. Tek tek mikro hizmetler, kendi bireysel SQL Server veritabanlarıyla hızla ve kolayca iletişim kuracak şekilde yapılandırılabilir. Bu veritabanları, ihtiyaçlarına göre her ayrı mikro hizmeti desteklemek için gereken şekilde ölçeklendirilebilir.

EShopOnContainers uygulaması, kullanıcının güncel alışveriş sepetini istekler arasında depolar. Bu, verileri Redsıs önbelleğinde depolayan sepet mikro hizmeti tarafından yönetilir. Geliştirme aşamasında, bu önbellek bir kapsayıcıda dağıtılabilir ve üretim sırasında Redsıs için Azure Cache kullanabilir. Redsıs için Azure önbelleği, Redsıs örnekleri veya kapsayıcılarını kendi kendinize dağıtmanıza ve yönetmeye gerek kalmadan yüksek performans ve güvenilirlik sunan tam olarak yönetilen bir hizmettir.

Konumlar mikro hizmeti, sürekliliği için bir MongoDB NoSQL veritabanı kullanır. Geliştirme sırasında, veritabanı kendi kapsayıcısına dağıtılabilir ve üretimde, hizmet [Azure Cosmos DB MongoDB için API 'sini](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)kullanabilir. Azure Cosmos DB avantajlarından biri, bir SQL API 'SI ve MongoDB, Cassandra, Gremlin ve Azure Tablo depolama dahil yaygın NoSQL API 'Leri dahil olmak üzere birden çok farklı iletişim protokollerinden faydalanabilir. Azure Cosmos DB, kendisini kullanan hizmetlerin ihtiyaçlarını karşılamak üzere ölçeklenebilen bir hizmet olarak tam olarak yönetilen ve genel olarak dağıtılmış bir veritabanı sunmaktadır.

Bulutta yerel uygulamalardaki dağıtılmış veriler, [Bölüm 5](distributed-data.md)' te daha ayrıntılı bir şekilde ele alınmıştır.

## <a name="event-bus"></a>Olay veri yolu

Uygulama, farklı hizmetler arasındaki değişiklikleri iletmek için olayları kullanır. Bu işlevsellik çeşitli uygulamalarla uygulanabilir ve yerel olarak eShopOnContainers uygulaması [Kbbitmq](https://www.rabbitmq.com/)kullanır. Azure 'da barındırıldığı zaman, uygulama kendi mesajlaşmasından [Azure Service Bus](https://docs.microsoft.com/azure/service-bus/) faydalanır. Azure Service Bus, uygulamaların ve hizmetlerin ayrılmış, güvenilir ve zaman uyumsuz bir şekilde birbirleriyle iletişim kurmasına olanak sağlayan, tam olarak yönetilen bir tümleştirme ileti aracısıdır. Azure Service Bus, Yayımcı-abone senaryolarını desteklemek üzere ayrı ayrı kuyrukları ve ayrı *konuları* destekler. EShopOnContainers uygulaması, bir mikro hizmetten gelen iletilerin belirli bir iletiye tepki vermek için gereken diğer mikro hizmetlere dağıtılmasını desteklemek üzere Azure Service Bus ile ilgili konuların faydalanır.

## <a name="resiliency"></a>Dayanıklılık

Üretim ortamına dağıtıldıktan sonra, eShopOnContainers uygulaması, dayanıklılığını artırmak için kullanılabilen çeşitli Azure hizmetlerinden yararlanabilir. Uygulama, uygulamanın kullanılabilirliğine göre raporlama ve uyarılar sağlamak üzere Application Insights ile tümleştirilebilen sistem durumu denetimleri yayımlar. Azure kaynakları, hataları ve performans sorunlarını belirlemek ve düzeltmek için kullanılabilecek tanılama günlükleri de sağlar. Kaynak günlükleri, uygulama tarafından farklı Azure kaynaklarının ne zaman ve nasıl kullanıldığı hakkında ayrıntılı bilgi sağlar. [Bölüm 6](resiliency.md)' da bulutta yerel dayanıklılık özellikleri hakkında daha fazla bilgi edineceksiniz.

>[!div class="step-by-step"]
>[Önceki](introduce-eshoponcontainers-reference-app.md) 
> [Sonraki](deploy-eshoponcontainers-azure.md)
