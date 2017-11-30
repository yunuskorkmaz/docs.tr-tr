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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a459e6df0e030f4e17bb73461d8fa790a61787e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
