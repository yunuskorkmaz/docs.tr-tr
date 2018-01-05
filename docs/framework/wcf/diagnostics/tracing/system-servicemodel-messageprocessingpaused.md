---
title: System.ServiceModel.MessageProcessingPaused
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f767165486ac2dc6ce4ee5b3e0825eceef0c249
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="fed0d-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="fed0d-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="fed0d-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="fed0d-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="fed0d-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fed0d-104">Description</span></span>  
 <span data-ttu-id="fed0d-105">İş parçacığı bir ileti işlenirken anahtarlı.</span><span class="sxs-lookup"><span data-stu-id="fed0d-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="fed0d-106">İleti işleme tarafından aşağıdaki nedenlerden duraklatılabilir:</span><span class="sxs-lookup"><span data-stu-id="fed0d-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="fed0d-107">ConcurrencyMode tek ya da desteklemeyeceğini ve başka bir ileti işleme hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="fed0d-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="fed0d-108">İşlem etkindir ve başka bir işlem işleme hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="fed0d-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="fed0d-109">Eşitleme bağlamı geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="fed0d-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fed0d-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fed0d-110">See Also</span></span>  
 [<span data-ttu-id="fed0d-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="fed0d-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="fed0d-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="fed0d-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="fed0d-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="fed0d-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
