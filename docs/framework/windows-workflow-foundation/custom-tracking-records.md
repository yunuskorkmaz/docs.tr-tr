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
# <a name="custom-tracking-records"></a>Özel İzleme Kayıtları

Bu konu, özel izleme kayıtlarının nasıl oluşturulduğunu ve kayıtlarla birlikte oluşturulacak verilerle nasıl doldurulacağını gösterir.

## <a name="emitting-custom-tracking-records"></a>Özel Izleme kayıtlarını yayma

Özel izleme kayıtları, aşağıdaki örnekte gösterildiği gibi bir kod etkinliğinden dağıtılabilir.

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<xref:System.Activities.Tracking.CustomTrackingRecord> <xref:System.Activities.NativeActivityContext.Track%2A> ,, Üzerinde yöntemi çağırarak bir kod etkinliğine yayılır `ActivityContext` .

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Fabric Izleme](/previous-versions/appfabric/ee677251(v=azure.10))
- [App Fabric ile uygulamaları izleme](/previous-versions/appfabric/ee677276(v=azure.10))
