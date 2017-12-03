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
ms.openlocfilehash: 33d05eaa94ec0efdf6d18d03d9d38bda6f0c9eb7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="b5181-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="b5181-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="b5181-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="b5181-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="b5181-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5181-104">Description</span></span>  
 <span data-ttu-id="b5181-105">İş parçacığı bir ileti işlenirken anahtarlı.</span><span class="sxs-lookup"><span data-stu-id="b5181-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="b5181-106">İleti işleme tarafından aşağıdaki nedenlerden duraklatılabilir:</span><span class="sxs-lookup"><span data-stu-id="b5181-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="b5181-107">ConcurrencyMode tek ya da desteklemeyeceğini ve başka bir ileti işleme hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="b5181-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="b5181-108">İşlem etkindir ve başka bir işlem işleme hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="b5181-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="b5181-109">Eşitleme bağlamı geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b5181-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5181-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5181-110">See Also</span></span>  
 [<span data-ttu-id="b5181-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="b5181-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="b5181-112">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="b5181-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="b5181-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="b5181-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
