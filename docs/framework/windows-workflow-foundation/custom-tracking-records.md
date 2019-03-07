---
title: Özel izleme kayıtları
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: d4733b4ffc0d866cf90fd5a5e7d649de261c45fb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499127"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="5ec0b-102">Özel izleme kayıtları</span><span class="sxs-lookup"><span data-stu-id="5ec0b-102">Custom Tracking Records</span></span>

<span data-ttu-id="5ec0b-103">Bu konu, özel izleme kayıtları oluşturmak ve bunları birlikte kayıtları yayılan verilerle doldurabilirsiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5ec0b-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>

## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="5ec0b-104">Özel izleme kayıtları yayma</span><span class="sxs-lookup"><span data-stu-id="5ec0b-104">Emitting Custom Tracking Records</span></span>

<span data-ttu-id="5ec0b-105">Özel izleme kayıtları, aşağıdaki örnekte gösterildiği gibi bir kod etkinliği yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ec0b-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<span data-ttu-id="5ec0b-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> çağırarak bir kod etkinliği yayılan <xref:System.Activities.NativeActivityContext.Track%2A> metodunda `ActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="5ec0b-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActivityContext`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ec0b-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ec0b-107">See also</span></span>

- [<span data-ttu-id="5ec0b-108">Windows Server App Fabric izleme</span><span class="sxs-lookup"><span data-stu-id="5ec0b-108">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="5ec0b-109">App Fabric ile uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="5ec0b-109">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
