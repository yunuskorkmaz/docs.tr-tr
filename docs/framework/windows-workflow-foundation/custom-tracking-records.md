---
title: Özel izleme kayıtları
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 6c68c08e5beacee30b517bf0c2bad3e83785409b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="custom-tracking-records"></a>Özel izleme kayıtları
Bu konu, özel izleme kayıtları oluşturmak ve bunları yanı sıra kayıtların yayınlaması verilerle doldurmak gösterilmiştir.  
  
## <a name="emitting-custom-tracking-records"></a>Özel izleme kayıtları yayma  
 Kayıtları İzleme özel kod etkinliğinden aşağıdaki örnekte gösterildiği gibi yayılan.  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 A <xref:System.Activities.Tracking.CustomTrackingRecord> çağırarak bir kod etkinliklerinizi yayılan <xref:System.Activities.NativeActivityContext.Track%2A> yöntemi `ActvityContext`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Server App Fabric izleme](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [App Fabric ile uygulamaları izleme](http://go.microsoft.com/fwlink/?LinkId=201275)
