---
title: "Özel izleme kayıtları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5202f69ac3f5408091d73f2ae39f92659a991740
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-tracking-records"></a><span data-ttu-id="4eae9-102">Özel izleme kayıtları</span><span class="sxs-lookup"><span data-stu-id="4eae9-102">Custom Tracking Records</span></span>
<span data-ttu-id="4eae9-103">Bu konu, özel izleme kayıtları oluşturmak ve bunları yanı sıra kayıtların yayınlaması verilerle doldurmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4eae9-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>  
  
## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="4eae9-104">Özel izleme kayıtları yayma</span><span class="sxs-lookup"><span data-stu-id="4eae9-104">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="4eae9-105">Kayıtları İzleme özel kod etkinliğinden aşağıdaki örnekte gösterildiği gibi yayılan.</span><span class="sxs-lookup"><span data-stu-id="4eae9-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 <span data-ttu-id="4eae9-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> çağırarak bir kod etkinliklerinizi yayılan <xref:System.Activities.NativeActivityContext.Track%2A> yöntemi `ActvityContext`.</span><span class="sxs-lookup"><span data-stu-id="4eae9-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActvityContext`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eae9-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4eae9-107">See Also</span></span>  
 [<span data-ttu-id="4eae9-108">Windows Server App Fabric izleme</span><span class="sxs-lookup"><span data-stu-id="4eae9-108">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="4eae9-109">App Fabric ile uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="4eae9-109">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
