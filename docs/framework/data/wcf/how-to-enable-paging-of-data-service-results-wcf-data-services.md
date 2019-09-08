---
title: 'Nasıl yapılır: Veri hizmeti sonuçlarının Sayfalamayı Etkinleştir (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 82b4d0fd3531778ab494d6526a56b092edf9481a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780047"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="ee9cd-102">Nasıl yapılır: Veri hizmeti sonuçlarının Sayfalamayı Etkinleştir (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="ee9cd-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="ee9cd-103">bir veri hizmeti sorgusu tarafından döndürülen varlıkların sayısını sınırlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee9cd-103">enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="ee9cd-104">Sayfa sınırları, hizmet başlatıldığında çağrılan yönteminde tanımlanır ve her bir varlık kümesi için ayrı ayrı ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ee9cd-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="ee9cd-105">Sayfalama etkinleştirildiğinde akıştaki son giriş, bir sonraki veri sayfasına bir bağlantı içerir.</span><span class="sxs-lookup"><span data-stu-id="ee9cd-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="ee9cd-106">Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="ee9cd-106">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="ee9cd-107">Bu konuda, döndürülen `Customers` ve `Orders` varlık kümelerinin sayfalama özelliğini etkinleştirmek için bir veri hizmetinin nasıl değiştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ee9cd-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="ee9cd-108">Bu konudaki örnek, Northwind örnek veri hizmetini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ee9cd-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="ee9cd-109">Bu hizmet, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ee9cd-109">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="ee9cd-110">Döndürülen müşterilerin ve sipariş varlık kümelerinin sayfalama özelliğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="ee9cd-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
- <span data-ttu-id="ee9cd-111">Veri Hizmeti kodunda, `InitializeService` işlevdeki yer tutucu kodunu aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="ee9cd-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="ee9cd-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee9cd-112">See also</span></span>

- [<span data-ttu-id="ee9cd-113">Ertelenmiş İçerik Yükleme</span><span class="sxs-lookup"><span data-stu-id="ee9cd-113">Loading Deferred Content</span></span>](loading-deferred-content-wcf-data-services.md)
- [<span data-ttu-id="ee9cd-114">Nasıl yapılır: Disk belleğine alınmış sonuçları yükle</span><span class="sxs-lookup"><span data-stu-id="ee9cd-114">How to: Load Paged Results</span></span>](how-to-load-paged-results-wcf-data-services.md)
