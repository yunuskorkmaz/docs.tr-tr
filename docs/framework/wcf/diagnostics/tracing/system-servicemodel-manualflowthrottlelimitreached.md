---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: fb69c3c737a0e77b05e08ab8d8282069feb069bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095691"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="b0105-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="b0105-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="b0105-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="b0105-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="b0105-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0105-104">Description</span></span>  
 <span data-ttu-id="b0105-105">Sistem, ManualFlowControlLimit kısıtlama için ayarladığı sınırına ulaştı.</span><span class="sxs-lookup"><span data-stu-id="b0105-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="b0105-106">Kısıtlama değeri, geçerli olduğu ServiceHost veya InstanceContext, ManualFlowControlLimit özelliğini değiştirerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b0105-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="b0105-107">Bu izleme, el ile akış denetimi sınırına 0 olarak başlangıçta azaltıldığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="b0105-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="b0105-108">0 sonraki değişiklikleri izlenen değil.</span><span class="sxs-lookup"><span data-stu-id="b0105-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="b0105-109">Akış denetimi sınırına örnek bağlamı, her bağlam için bir kez izlenen.</span><span class="sxs-lookup"><span data-stu-id="b0105-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0105-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0105-110">See also</span></span>

- [<span data-ttu-id="b0105-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="b0105-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="b0105-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="b0105-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b0105-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="b0105-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
