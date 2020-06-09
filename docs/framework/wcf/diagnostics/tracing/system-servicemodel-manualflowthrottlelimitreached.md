---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: bffa6361df5a50748f45aa3004f7a307ad516d7b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84580495"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="091e3-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="091e3-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="091e3-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="091e3-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="091e3-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="091e3-104">Description</span></span>  
 <span data-ttu-id="091e3-105">Sistem ManualFlowControlLimit kısıtlaması için belirlenen sınıra ulaştı.</span><span class="sxs-lookup"><span data-stu-id="091e3-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="091e3-106">Kısıtlama değeri, varsa ServiceHost veya InstanceContext üzerindeki ManualFlowControlLimit özelliği değiştirilerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="091e3-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="091e3-107">Bu izleme, el ile akış denetim sınırı başlangıçta 0 ' a azaltılacağı zaman yayılır.</span><span class="sxs-lookup"><span data-stu-id="091e3-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="091e3-108">0 ' a yapılan sonraki değişiklikler izlenmez.</span><span class="sxs-lookup"><span data-stu-id="091e3-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="091e3-109">Örnek bağlamındaki akış denetim sınırı her bağlam için bir kez izleniyor.</span><span class="sxs-lookup"><span data-stu-id="091e3-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="091e3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="091e3-110">See also</span></span>

- [<span data-ttu-id="091e3-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="091e3-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="091e3-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="091e3-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="091e3-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="091e3-113">Administration and Diagnostics</span></span>](../index.md)
