---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 556afe035697ee35d7ba86185b5b768a645c32c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="e48f4-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="e48f4-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="e48f4-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="e48f4-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="e48f4-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e48f4-104">Description</span></span>  
 <span data-ttu-id="e48f4-105">Sistem ManualFlowControlLimit kısıtlama için ayarladığı sınırına ulaştı.</span><span class="sxs-lookup"><span data-stu-id="e48f4-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="e48f4-106">Kısıtlama değeri, geçerli olarak ServiceHost ya da InstanceContext, ManualFlowControlLimit özelliğini değiştirerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e48f4-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="e48f4-107">Bu izleme, el ile akış denetimi sınırına başlangıçta 0 olarak azaltıldığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="e48f4-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="e48f4-108">0 sonraki değişiklikleri izlenen değil.</span><span class="sxs-lookup"><span data-stu-id="e48f4-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="e48f4-109">Akış denetimi sınırı örnek bağlamı her bağlam için bir kez izlenen.</span><span class="sxs-lookup"><span data-stu-id="e48f4-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e48f4-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e48f4-110">See Also</span></span>  
 [<span data-ttu-id="e48f4-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="e48f4-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e48f4-112">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="e48f4-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e48f4-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="e48f4-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
