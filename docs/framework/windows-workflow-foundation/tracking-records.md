---
title: İzleme kayıtları
ms.date: 03/30/2017
ms.assetid: 51adbda3-bd8b-4892-a8ea-d343186472d2
ms.openlocfilehash: 2be8dbcdd740dee1c5cddd1121716058bfa5c175
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527045"
---
# <a name="tracking-records"></a>İzleme kayıtları
İş akışı çalışma zamanı, bir iş akışı örneği yürütülmesini izlemek için izleme kayıtları yaymak üzere işaretlendi.  
  
## <a name="tracking-records"></a>İzleme kayıtları  
 Aşağıdaki tabloda, iş akışı çalışma zamanı yayan izleme kayıtları ayrıntıları.  
  
|Kayıt izleme|Açıklama|  
|---------------------|-----------------|  
|İş akışı yaşam döngüsü kayıtları|İş akışı örneği yaşam döngüsü çeşitli aşamaları boyunca yayılır. Örneğin, iş akışı başlatıldığında veya tamamlanan bir kayıt yayılır.|  
|Etkinlik yaşam döngüsü kayıtları|Etkinlik yürütme ayrıntıları. Bu kayıtlar gibi bir etkinlik zamanlandığında etkinlik tamamlandığında veya bir hata oluştuğunda bir iş akışı etkinlik durumunu gösterir.|  
|Yer imi sürdürme kayıtları|Her bir iş akışı örneği içinde yer sürdürüldü yayılır.|  
|Özel izleme kayıtları|Bir iş akışı Yazar özel izleme kayıtları oluşturabilir ve bunları özel bir etkinlik içinde gösterin.|  
  
 WF çalışma zamanını şuradan yayılan izleme ile ilgili tüm kayıtları temel sınıfından türetilir <xref:System.Activities.Tracking.TrackingRecord>, ortak bir veri kümesini içerir. İzleme kayıtları için basit bir iş akışı yaşam döngüsünü gösterir. Her bir izleme kaydını gibi ilişkili izleme olayı ayrıntılarını içeren <xref:System.Activities.Tracking.TrackingRecord.InstanceId%2A>, <xref:System.Activities.Tracking.TrackingRecord.RecordNumber%2A>ve belirli kayıt türü için ek bilgiler.  
  
 Aşağıdaki türde <xref:System.Activities.Tracking.TrackingRecord> nesneleri iş akışı çalışma zamanı tarafından yayılan:  
  
-   **WorkflowInstanceRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> iş akışı örneği yaşam döngüsünü açıklar. Örneğin, iş akışı başlatır veya tamamlandığında ve iş akışı örneğinin durumunu içeren bir kayıt yayınlanır. Bu kaydın ayrıntılarını şu yolda bulunabilir: <xref:System.Activities.Tracking.WorkflowInstanceRecord>.  
  
-   **WorkflowInstanceAbortedRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> bir iş akışı örneği iptal ettiğinde yayılır. Kayıt iş akışı örneği durdurma nedeni içerir. Bu kaydın ayrıntılarını şu yolda bulunabilir: <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>.  
  
-   **WorkflowInstanceUnhandledExceptionRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> bir özel durum iş akışı örneği içinde oluşur ve herhangi bir etkinliği tarafından işlenmiyor yayılır. Kayıt, özel durum ayrıntıları içerir. Bu kaydın ayrıntılarını şu yolda bulunabilir: <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>.  
  
-   **WorkflowInstanceSuspendedRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> her bir iş akışı örneği askıya alındığında yayılır. Kayıt iş akışı örneği askıya alınmasını nedeni içerir. Bu kaydın ayrıntılarını şu yolda bulunabilir: <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>.  
  
-   **WorkflowInstanceTerminatedRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> her bir iş akışı örneği sonlandırıldı yayılır. Kayıt iş akışı örneği sonlandırılıyor nedeni içerir. Bu kaydın ayrıntılarını şu yolda bulunabilir: <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>.  
  
-   **ActivityStateRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> bir iş akışı içinde bir etkinlik yürütüldüğünde yayılır. Bu kayıtlar, iş akışı örneği içinde etkinlik durumunu gösterir. Bu kaydın ayrıntılarını şu yolda bulunabilir: <xref:System.Activities.Tracking.ActivityStateRecord>.  
  
-   **ActivityScheduledRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> bir etkinlik bir alt etkinlik zamanlarken yayılır. Bu kayıt (etkinlik zamanlama) üst etkinliği hem zamanlanmış bir alt etkinlik ayrıntılarını içerir. Bu kaydın ayrıntılarını şu yolda bulunabilir: <xref:System.Activities.Tracking.ActivityScheduledRecord>.  
  
-   **FaultPropagationRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> kaydında ele alınır kadar görünen her işleyici yayılır. İş akışı örneği içinde bir hata aldı yolunu belirtmek için kullanılır. Bu kaydın ayrıntılarını şu yolda bulunabilir: <xref:System.Activities.Tracking.FaultPropagationRecord>.  
  
-   **CancelRequestedRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> bir alt etkinlik iptal etmek bir etkinlik çalıştığında yayılır. Bu kayıt, üst etkinliği hem iptal ediliyor alt etkinlik ayrıntılarını içerir. Bu kaydın ayrıntılarını şu yolda bulunabilir: <xref:System.Activities.Tracking.CancelRequestedRecord>.  
  
-   **BookmarkResumptionRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> başarıyla sürdürüldü herhangi bir yer işareti izler. Bu kaydın ayrıntılarını şu yolda bulunabilir: <xref:System.Activities.Tracking.BookmarkResumptionRecord>.  
  
-   **CustomTrackingRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> oluşturulur ve bir özel iş akışı etkinlikleri içinden bir iş akışı yazar tarafından yayılan. Özel kayıtları izleme kayıtları ile birlikte yayılan verilerle doldurulabilir. Bu kaydın ayrıntılarını şu yolda bulunabilir: <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
 Örneğin, olabilir basit <xref:System.Activities.Statements.Sequence> içeren etkinlik bir <xref:System.Activities.Statements.WriteLine> kayıtları aşağıdaki sırayla yayılan izleme işlemi:  
  
1.  <xref:System.Activities.Tracking.WorkflowInstanceRecord> İş akışı başlanacağını gösterir.  
  
2.  <xref:System.Activities.Tracking.ActivityScheduledRecord> bir etkinlik zamanlandı gösterir. Bu durumda, bir <xref:System.Activities.Statements.Sequence> etkinlik.  
  
3.  <xref:System.Activities.Tracking.ActivityScheduledRecord> temsil eden <xref:System.Activities.Statements.WriteLine> etkinlik.  
  
4.  İki <xref:System.Activities.Tracking.ActivityStateRecord> Tamamlanıyor iki etkinliği temsil eden kaydeder.  
  
5.  <xref:System.Activities.Tracking.WorkflowInstanceRecord> İş akışı tamamlıyor gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Server App Fabric izleme](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [App Fabric ile uygulamaları izleme](https://go.microsoft.com/fwlink/?LinkId=201275)
