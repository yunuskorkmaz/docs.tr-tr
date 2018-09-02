---
title: Özel izleme kayıtları
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: ef3c20890f33f3ffd07a9c88de863e1ebe24851f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401257"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="ae443-102">Özel izleme kayıtları</span><span class="sxs-lookup"><span data-stu-id="ae443-102">Custom Tracking Records</span></span>
<span data-ttu-id="ae443-103">Bu konu, özel izleme kayıtları oluşturmak ve bunları birlikte kayıtları yayılan verilerle doldurabilirsiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ae443-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>  
  
## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="ae443-104">Özel izleme kayıtları yayma</span><span class="sxs-lookup"><span data-stu-id="ae443-104">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="ae443-105">Özel izleme kayıtları, aşağıdaki örnekte gösterildiği gibi bir kod etkinliği yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae443-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 <span data-ttu-id="ae443-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> çağırarak bir kod etkinliği yayılan <xref:System.Activities.NativeActivityContext.Track%2A> metodunda `ActvityContext`.</span><span class="sxs-lookup"><span data-stu-id="ae443-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActvityContext`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae443-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae443-107">See Also</span></span>  
 [<span data-ttu-id="ae443-108">Windows Server App Fabric izleme</span><span class="sxs-lookup"><span data-stu-id="ae443-108">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="ae443-109">App Fabric ile uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="ae443-109">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
