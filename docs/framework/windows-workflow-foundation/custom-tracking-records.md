---
description: 'Daha fazla bilgi edinin: özel Izleme kayıtları'
title: Özel İzleme Kayıtları
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 9d6988465fa3afca4302c86e0c2cad2778f2beae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742699"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="96fdf-103">Özel İzleme Kayıtları</span><span class="sxs-lookup"><span data-stu-id="96fdf-103">Custom Tracking Records</span></span>

<span data-ttu-id="96fdf-104">Bu konu, özel izleme kayıtlarının nasıl oluşturulduğunu ve kayıtlarla birlikte oluşturulacak verilerle nasıl doldurulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="96fdf-104">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>

## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="96fdf-105">Özel Izleme kayıtlarını yayma</span><span class="sxs-lookup"><span data-stu-id="96fdf-105">Emitting Custom Tracking Records</span></span>

<span data-ttu-id="96fdf-106">Özel izleme kayıtları, aşağıdaki örnekte gösterildiği gibi bir kod etkinliğinden dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="96fdf-106">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<span data-ttu-id="96fdf-107"><xref:System.Activities.Tracking.CustomTrackingRecord> <xref:System.Activities.NativeActivityContext.Track%2A> ,, Üzerinde yöntemi çağırarak bir kod etkinliğine yayılır `ActivityContext` .</span><span class="sxs-lookup"><span data-stu-id="96fdf-107">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActivityContext`.</span></span>

## <a name="see-also"></a><span data-ttu-id="96fdf-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96fdf-108">See also</span></span>

- <span data-ttu-id="96fdf-109">[Windows Server App Fabric Izleme](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="96fdf-109">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="96fdf-110">[App Fabric ile uygulamaları izleme](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="96fdf-110">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
