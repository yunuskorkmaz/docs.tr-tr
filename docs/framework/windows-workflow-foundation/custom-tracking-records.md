---
title: Özel İzleme Kayıtları
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 986f0350c24414d0ff960474445adf6ac3f39734
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802628"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="a7be2-102">Özel İzleme Kayıtları</span><span class="sxs-lookup"><span data-stu-id="a7be2-102">Custom Tracking Records</span></span>

<span data-ttu-id="a7be2-103">Bu konu, özel izleme kayıtlarının nasıl oluşturulduğunu ve kayıtlarla birlikte oluşturulacak verilerle nasıl doldurulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7be2-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>

## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="a7be2-104">Özel Izleme kayıtlarını yayma</span><span class="sxs-lookup"><span data-stu-id="a7be2-104">Emitting Custom Tracking Records</span></span>

<span data-ttu-id="a7be2-105">Özel izleme kayıtları, aşağıdaki örnekte gösterildiği gibi bir kod etkinliğinden dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="a7be2-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<span data-ttu-id="a7be2-106"><xref:System.Activities.Tracking.CustomTrackingRecord>, `ActivityContext`<xref:System.Activities.NativeActivityContext.Track%2A> yöntemi çağrılarak kod etkinliğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="a7be2-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActivityContext`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7be2-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7be2-107">See also</span></span>

- <span data-ttu-id="a7be2-108">[Windows Server App Fabric Izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a7be2-108">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="a7be2-109">[App Fabric ile uygulamaları izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a7be2-109">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
