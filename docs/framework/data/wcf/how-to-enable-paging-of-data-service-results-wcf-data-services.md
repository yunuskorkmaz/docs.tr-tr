---
title: 'Nasıl yapılır: (WCF Veri Hizmetleri) veri hizmeti sonuçlarını sayfalamayı etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: edc150d118153849dd84eb40f1443d842c7d346d
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517848"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="b4b5a-102">Nasıl yapılır: (WCF Veri Hizmetleri) veri hizmeti sonuçlarını sayfalamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b4b5a-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="b4b5a-103">bir veri hizmeti sorgu tarafından döndürülen varlık sayısını sınırlamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4b5a-103">enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="b4b5a-104">Sayfa sınırlarını hizmeti başlatılır ve ayrı olarak her varlık kümesi için ayarlanabilir çağrılan yöntem tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b4b5a-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="b4b5a-105">Sayfalama etkin olduğunda, son girişi akıştaki verilerin bir sonraki sayfaya bir bağlantı içerir.</span><span class="sxs-lookup"><span data-stu-id="b4b5a-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="b4b5a-106">Daha fazla bilgi için [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="b4b5a-106">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="b4b5a-107">Bu konuda, disk belleğini etkinleştirmek için bir veri hizmeti değiştirme işlemi gösterilmektedir döndürülen `Customers` ve `Orders` varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="b4b5a-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="b4b5a-108">Bu konudaki örnek Northwind örnek veri hizmeti kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4b5a-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="b4b5a-109">Bu hizmet, tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="b4b5a-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="b4b5a-110">Döndürülen müşteriler ve siparişler varlık kümeleri sayfalamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b4b5a-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
-   <span data-ttu-id="b4b5a-111">Veri Hizmeti için kodda yer tutucusunu değiştirin `InitializeService` işlevi aşağıdaki:</span><span class="sxs-lookup"><span data-stu-id="b4b5a-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="b4b5a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4b5a-112">See also</span></span>

- [<span data-ttu-id="b4b5a-113">Ertelenmiş İçerik Yükleme</span><span class="sxs-lookup"><span data-stu-id="b4b5a-113">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)
- [<span data-ttu-id="b4b5a-114">Nasıl yapılır: Disk belleği sonuçları</span><span class="sxs-lookup"><span data-stu-id="b4b5a-114">How to: Load Paged Results</span></span>](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
