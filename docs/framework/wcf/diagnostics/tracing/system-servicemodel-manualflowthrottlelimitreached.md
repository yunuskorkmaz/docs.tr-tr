---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: fb69c3c737a0e77b05e08ab8d8282069feb069bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761526"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="ea45c-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="ea45c-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="ea45c-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="ea45c-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="ea45c-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea45c-104">Description</span></span>  
 <span data-ttu-id="ea45c-105">Sistem, ManualFlowControlLimit kısıtlama için ayarladığı sınırına ulaştı.</span><span class="sxs-lookup"><span data-stu-id="ea45c-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="ea45c-106">Kısıtlama değeri, geçerli olduğu ServiceHost veya InstanceContext, ManualFlowControlLimit özelliğini değiştirerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ea45c-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="ea45c-107">Bu izleme, el ile akış denetimi sınırına 0 olarak başlangıçta azaltıldığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="ea45c-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="ea45c-108">0 sonraki değişiklikleri izlenen değil.</span><span class="sxs-lookup"><span data-stu-id="ea45c-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="ea45c-109">Akış denetimi sınırına örnek bağlamı, her bağlam için bir kez izlenen.</span><span class="sxs-lookup"><span data-stu-id="ea45c-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea45c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea45c-110">See also</span></span>

- [<span data-ttu-id="ea45c-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="ea45c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="ea45c-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="ea45c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="ea45c-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="ea45c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
