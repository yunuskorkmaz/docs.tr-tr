---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: 180a06efc94acba40806e1f5d661553127549596
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248493"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="0329d-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="0329d-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>

<span data-ttu-id="0329d-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="0329d-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="0329d-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0329d-104">Description</span></span>  

 <span data-ttu-id="0329d-105">Sistem ManualFlowControlLimit kısıtlaması için belirlenen sınıra ulaştı.</span><span class="sxs-lookup"><span data-stu-id="0329d-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="0329d-106">Kısıtlama değeri, varsa ServiceHost veya InstanceContext üzerindeki ManualFlowControlLimit özelliği değiştirilerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0329d-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="0329d-107">Bu izleme, el ile akış denetim sınırı başlangıçta 0 ' a azaltılacağı zaman yayılır.</span><span class="sxs-lookup"><span data-stu-id="0329d-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="0329d-108">0 ' a yapılan sonraki değişiklikler izlenmez.</span><span class="sxs-lookup"><span data-stu-id="0329d-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="0329d-109">Örnek bağlamındaki akış denetim sınırı her bağlam için bir kez izleniyor.</span><span class="sxs-lookup"><span data-stu-id="0329d-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0329d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0329d-110">See also</span></span>

- [<span data-ttu-id="0329d-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="0329d-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="0329d-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="0329d-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0329d-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="0329d-113">Administration and Diagnostics</span></span>](../index.md)
