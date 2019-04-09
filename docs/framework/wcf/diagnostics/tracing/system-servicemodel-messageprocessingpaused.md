---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: ac1dacef94d6446aa407e4a390b9561d033af1bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087487"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="29355-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="29355-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="29355-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="29355-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="29355-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29355-104">Description</span></span>  
 <span data-ttu-id="29355-105">İş parçacığı, bir ileti işlenirken anahtarlı.</span><span class="sxs-lookup"><span data-stu-id="29355-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="29355-106">İleti işleme, aşağıdaki nedenlerden duraklatılabilir:</span><span class="sxs-lookup"><span data-stu-id="29355-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="29355-107">ConcurrencyMode tek ya da desteklemeyeceğini ve başka bir ileti işleme hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="29355-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="29355-108">İşlem etkindir ve başka bir işlem işleme hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="29355-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="29355-109">Eşitleme bağlamı geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="29355-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29355-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29355-110">See also</span></span>

- [<span data-ttu-id="29355-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="29355-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="29355-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="29355-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="29355-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="29355-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
