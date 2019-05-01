---
title: Özel İzleme Kayıtları
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: d4733b4ffc0d866cf90fd5a5e7d649de261c45fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945840"
---
# <a name="custom-tracking-records"></a>Özel İzleme Kayıtları

Bu konu, özel izleme kayıtları oluşturmak ve bunları birlikte kayıtları yayılan verilerle doldurabilirsiniz gösterilmektedir.

## <a name="emitting-custom-tracking-records"></a>Özel izleme kayıtları yayma

Özel izleme kayıtları, aşağıdaki örnekte gösterildiği gibi bir kod etkinliği yayılabilir.

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

A <xref:System.Activities.Tracking.CustomTrackingRecord> çağırarak bir kod etkinliği yayılan <xref:System.Activities.NativeActivityContext.Track%2A> metodunda `ActivityContext`.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Fabric izleme](https://go.microsoft.com/fwlink/?LinkId=201273)
- [App Fabric ile uygulamaları izleme](https://go.microsoft.com/fwlink/?LinkId=201275)
