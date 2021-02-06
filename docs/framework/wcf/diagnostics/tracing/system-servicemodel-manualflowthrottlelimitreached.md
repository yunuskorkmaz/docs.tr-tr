---
description: 'Şu konuda daha fazla bilgi edinin: System. ServiceModel. Manualflowthrottlelimitulaşıldı'
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: 90c911131259ea02023eb05a97793f00f3eb43fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99633341"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="456a3-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="456a3-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>

<span data-ttu-id="456a3-104">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="456a3-104">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="456a3-105">Description</span><span class="sxs-lookup"><span data-stu-id="456a3-105">Description</span></span>  

 <span data-ttu-id="456a3-106">Sistem ManualFlowControlLimit kısıtlaması için belirlenen sınıra ulaştı.</span><span class="sxs-lookup"><span data-stu-id="456a3-106">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="456a3-107">Kısıtlama değeri, varsa ServiceHost veya InstanceContext üzerindeki ManualFlowControlLimit özelliği değiştirilerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="456a3-107">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="456a3-108">Bu izleme, el ile akış denetim sınırı başlangıçta 0 ' a azaltılacağı zaman yayılır.</span><span class="sxs-lookup"><span data-stu-id="456a3-108">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="456a3-109">0 ' a yapılan sonraki değişiklikler izlenmez.</span><span class="sxs-lookup"><span data-stu-id="456a3-109">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="456a3-110">Örnek bağlamındaki akış denetim sınırı her bağlam için bir kez izleniyor.</span><span class="sxs-lookup"><span data-stu-id="456a3-110">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="456a3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="456a3-111">See also</span></span>

- [<span data-ttu-id="456a3-112">İzleme</span><span class="sxs-lookup"><span data-stu-id="456a3-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="456a3-113">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="456a3-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="456a3-114">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="456a3-114">Administration and Diagnostics</span></span>](../index.md)
