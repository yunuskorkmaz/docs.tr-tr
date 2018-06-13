---
title: İzleme kayıtları
ms.date: 03/30/2017
ms.assetid: 51adbda3-bd8b-4892-a8ea-d343186472d2
ms.openlocfilehash: b07175943f85b61024030c1e0251e24d1eb35c86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520285"
---
# <a name="tracking-records"></a>İzleme kayıtları
İş akışı çalışma zamanı, bir iş akışı örneğini yürütmeyi izlemek için izleme kayıtları yaymak üzere işaretlenir.  
  
## <a name="tracking-records"></a>İzleme kayıtları  
 Aşağıdaki tabloda, iş akışı çalışma zamanı yayar izleme kayıtları ayrıntıları verilmektedir.  
  
|İzleme kaydı|Açıklama|  
|---------------------|-----------------|  
|İş akışı yaşam döngüsü kayıtları|İş akışı örneği yaşam döngüsünü çeşitli aşamalarında yayılan. Örneğin, iş akışı başlatıldığında veya tamamlandıktan bir kayıt yayınlanır.|  
|Etkinlik yaşam döngüsü kayıtları|Ayrıntılar Etkinlik yürütme. Bu kayıtları gibi bir etkinlik zamanlandığı etkinlik tamamlandığında veya bir hata oluştuğunda bir iş akışı etkinlik durumunu belirtir.|  
|Yer işareti sürdürme kayıtları|Bir iş akışı örneği yer işareti sürdürüldü her yayılan.|  
|Özel izleme kayıtları|Bir iş akışı yazarı özel izleme kayıtları oluşturun ve özel bir aktivite içinde yayma.|  
  
 Tüm izleme ile ilgili kayıtları WF çalışma zamanını şuradan yayılan temel sınıfından türetilir <xref:System.Activities.Tracking.TrackingRecord>, ortak veri kümesini içerir. İzleme kayıtları basit bir iş akışı için yaşam döngüsünü gösterir. Her izleme kaydı gibi ilişkili izleme olayı ayrıntılarını içeren <xref:System.Activities.Tracking.TrackingRecord.InstanceId%2A>, <xref:System.Activities.Tracking.TrackingRecord.RecordNumber%2A>ve kayıt izleme türüne özgü ek bilgileri.  
  
 Aşağıdaki türden <xref:System.Activities.Tracking.TrackingRecord> nesneleri iş akışı çalışma zamanı tarafından gösterilen:  
  
-   **WorkflowInstanceRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> iş akışı örneği yaşam döngüsünü açıklar. Örneğin, iş akışını başlatır veya tamamlandığında ve iş akışı örneği durumunu içeren bir kayıt yayınlanır. Bu kayıt ayrıntılarını bulunabilir <xref:System.Activities.Tracking.WorkflowInstanceRecord>.  
  
-   **WorkflowInstanceAbortedRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> bir iş akışı örneği iptal ettiğinde yayınlanır. Durdurulan iş akışı örneği nedeni kayıt içeriyor. Bu kayıt ayrıntılarını bulunabilir <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>.  
  
-   **WorkflowInstanceUnhandledExceptionRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> bir özel durum iş akışı örneği oluşur ve herhangi bir etkinlik tarafından işlenmemiş yayınlanır. Kayıt özel durum ayrıntıları içerir. Bu kayıt ayrıntılarını bulunabilir <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>.  
  
-   **WorkflowInstanceSuspendedRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> her bir iş akışı örneği askıya alındığında yayınlanır. Kayıt askıya alınmasını iş akışı örneği nedeni içeriyor. Bu kayıt ayrıntılarını bulunabilir <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>.  
  
-   **WorkflowInstanceTerminatedRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> bir iş akışı örneği sonlandırıldı her yayınlanır. Kayıt sonlandırılıyor iş akışı örneği nedeni içeriyor. Bu kayıt ayrıntılarını bulunabilir <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>.  
  
-   **ActivityStateRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> bir iş akışı içinde bir etkinlik yürüttüğünde yayınlanır. Bu kayıtları iş akışı örneği içinde etkinlik durumunu belirtir. Bu kayıt ayrıntılarını bulunabilir <xref:System.Activities.Tracking.ActivityStateRecord>.  
  
-   **ActivityScheduledRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> bir etkinlik bir alt etkinlik zamanlarken yayınlanır. Bu kayıt (etkinlik planlama) üst etkinlik ve zamanlanmış alt etkinliğin ayrıntılarını içerir. Bu kayıt ayrıntılarını bulunabilir <xref:System.Activities.Tracking.ActivityScheduledRecord>.  
  
-   **FaultPropagationRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> kaydında ele alınır kadar görünen her işleyicisi yayınlanır. İş akışı örneği içinde bir hata aldı yolunu belirtmek için kullanılır. Bu kayıt ayrıntılarını bulunabilir <xref:System.Activities.Tracking.FaultPropagationRecord>.  
  
-   **CancelRequestedRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> bir alt etkinlik iptal etmek bir etkinlik çalıştığında yayınlanır. Bu kayıt üst etkinlik ve iptal ediliyor alt etkinliği ayrıntılarını içerir. Bu kayıt ayrıntılarını bulunabilir <xref:System.Activities.Tracking.CancelRequestedRecord>.  
  
-   **BookmarkResumptionRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> başarıyla sürdürüldü herhangi bir yer işareti izler. Bu kayıt ayrıntılarını bulunabilir <xref:System.Activities.Tracking.BookmarkResumptionRecord>.  
  
-   **CustomTrackingRecord** - bu <xref:System.Activities.Tracking.TrackingRecord> oluşturulur ve bir özel iş akışı etkinlik iş akışı yazarı tarafından gösterilen. Kayıtları İzleme özel yanı sıra kayıtların yayınlaması verilerle doldurulabilir. Bu kayıt ayrıntılarını bulunabilir <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
 Örneğin, olabilir basit bir <xref:System.Activities.Statements.Sequence> içeren etkinliği bir <xref:System.Activities.Statements.WriteLine> aşağıdaki sırayla yayılan kayıtları izleme işlemi:  
  
1.  <xref:System.Activities.Tracking.WorkflowInstanceRecord> İş akışı başlayarak olduğunu gösterir.  
  
2.  <xref:System.Activities.Tracking.ActivityScheduledRecord> bir etkinlik zamanlandı gösterir. Bu durumda olduğu bir <xref:System.Activities.Statements.Sequence> etkinlik.  
  
3.  <xref:System.Activities.Tracking.ActivityScheduledRecord> temsil eden <xref:System.Activities.Statements.WriteLine> etkinlik.  
  
4.  Var olan iki <xref:System.Activities.Tracking.ActivityStateRecord> Tamamlanıyor iki etkinlik temsil kaydeder.  
  
5.  <xref:System.Activities.Tracking.WorkflowInstanceRecord> İş akışı üzeredir gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Server App Fabric izleme](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [App Fabric ile uygulamaları izleme](http://go.microsoft.com/fwlink/?LinkId=201275)
