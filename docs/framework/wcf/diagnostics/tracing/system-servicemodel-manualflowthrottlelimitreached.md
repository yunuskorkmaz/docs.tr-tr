---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: 86d47ab0a83ff3e4a68bfa8ccf1349cf2b345b23
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597742"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="58ee8-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="58ee8-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="58ee8-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="58ee8-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="58ee8-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58ee8-104">Description</span></span>  
 <span data-ttu-id="58ee8-105">Sistem, ManualFlowControlLimit kısıtlama için ayarladığı sınırına ulaştı.</span><span class="sxs-lookup"><span data-stu-id="58ee8-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="58ee8-106">Kısıtlama değeri, geçerli olduğu ServiceHost veya InstanceContext, ManualFlowControlLimit özelliğini değiştirerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="58ee8-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="58ee8-107">Bu izleme, el ile akış denetimi sınırına 0 olarak başlangıçta azaltıldığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="58ee8-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="58ee8-108">0 sonraki değişiklikleri izlenen değil.</span><span class="sxs-lookup"><span data-stu-id="58ee8-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="58ee8-109">Akış denetimi sınırına örnek bağlamı, her bağlam için bir kez izlenen.</span><span class="sxs-lookup"><span data-stu-id="58ee8-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ee8-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58ee8-110">See also</span></span>
- [<span data-ttu-id="58ee8-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="58ee8-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="58ee8-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="58ee8-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="58ee8-113">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="58ee8-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
