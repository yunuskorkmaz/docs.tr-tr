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
