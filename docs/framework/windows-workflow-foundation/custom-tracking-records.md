---
title: Özel İzleme Kayıtları
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: e0bbb9d57290b072d834f0b8bc0815dfe265e72a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543907"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="e0a1a-102">Özel İzleme Kayıtları</span><span class="sxs-lookup"><span data-stu-id="e0a1a-102">Custom Tracking Records</span></span>

<span data-ttu-id="e0a1a-103">Bu konu, özel izleme kayıtlarının nasıl oluşturulduğunu ve kayıtlarla birlikte oluşturulacak verilerle nasıl doldurulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0a1a-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>

## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="e0a1a-104">Özel Izleme kayıtlarını yayma</span><span class="sxs-lookup"><span data-stu-id="e0a1a-104">Emitting Custom Tracking Records</span></span>

<span data-ttu-id="e0a1a-105">Özel izleme kayıtları, aşağıdaki örnekte gösterildiği gibi bir kod etkinliğinden dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="e0a1a-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<span data-ttu-id="e0a1a-106"><xref:System.Activities.Tracking.CustomTrackingRecord> <xref:System.Activities.NativeActivityContext.Track%2A> ,, Üzerinde yöntemi çağırarak bir kod etkinliğine yayılır `ActivityContext` .</span><span class="sxs-lookup"><span data-stu-id="e0a1a-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActivityContext`.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0a1a-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0a1a-107">See also</span></span>

- <span data-ttu-id="e0a1a-108">[Windows Server App Fabric Izleme](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e0a1a-108">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="e0a1a-109">[App Fabric ile uygulamaları izleme](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e0a1a-109">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
