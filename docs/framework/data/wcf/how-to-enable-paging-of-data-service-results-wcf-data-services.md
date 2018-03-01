---
title: "Nasıl yapılır: veri hizmeti sonuçları (WCF Veri Hizmetleri) ICollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b03dd234681d031361696108702a7bbb558065ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="31048-102">Nasıl yapılır: veri hizmeti sonuçları (WCF Veri Hizmetleri) ICollection</span><span class="sxs-lookup"><span data-stu-id="31048-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="31048-103">bir veri hizmeti sorgu tarafından döndürülen varlık sayısını sınırlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="31048-103"> enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="31048-104">Sayfa sınırlarını hizmeti başlatılır ve her varlık kümesi için ayrı ayrı ayarlanabilir çağrılan yöntem tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="31048-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="31048-105">Sayfalama etkin olduğunda, son girişi akıştaki verilerin bir sonraki sayfaya bir bağlantı içerir.</span><span class="sxs-lookup"><span data-stu-id="31048-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="31048-106">Daha fazla bilgi için bkz: [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="31048-106">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="31048-107">Bu konu, disk belleği etkinleştirmek için veri hizmeti değiştirmek nasıl gösterir döndürülen `Customers` ve `Orders` varlık kümeleri.</span><span class="sxs-lookup"><span data-stu-id="31048-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="31048-108">Bu konudaki örnek Northwind örnek veri hizmeti kullanır.</span><span class="sxs-lookup"><span data-stu-id="31048-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="31048-109">Bu hizmeti tamamladığınızda oluşturulan [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="31048-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="31048-110">Disk belleği döndürülen müşteriler ve siparişler varlık kümelerinin etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="31048-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
-   <span data-ttu-id="31048-111">Veri Hizmeti için kodda yer tutucu kodu `InitializeService` aşağıdaki işleviyle:</span><span class="sxs-lookup"><span data-stu-id="31048-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="31048-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31048-112">See Also</span></span>  
 [<span data-ttu-id="31048-113">Ertelenmiş İçerik Yükleme</span><span class="sxs-lookup"><span data-stu-id="31048-113">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [<span data-ttu-id="31048-114">Nasıl yapılır: Sayfalanmış Sonuçları Yükleme</span><span class="sxs-lookup"><span data-stu-id="31048-114">How to: Load Paged Results</span></span>](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
