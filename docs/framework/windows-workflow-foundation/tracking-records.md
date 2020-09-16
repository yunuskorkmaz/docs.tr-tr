---
title: İzleme Kayıtları
ms.date: 03/30/2017
ms.assetid: 51adbda3-bd8b-4892-a8ea-d343186472d2
ms.openlocfilehash: 498d62fb1d3cc1386ea3bf57de431c57b18b7dda
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551307"
---
# <a name="tracking-records"></a>İzleme Kayıtları
İş akışı çalışma zamanı, izleme kayıtlarını izlemek için bir iş akışı örneğinin yürütülmesini izlemek üzere işaretlenir.  
  
## <a name="tracking-records"></a>İzleme Kayıtları  
 Aşağıdaki tabloda iş akışı çalışma zamanının yaydığı izleme kayıtlarının ayrıntıları verilmiştir.  
  
|İzleme kaydı|Description|  
|---------------------|-----------------|  
|İş akışı yaşam döngüsü kayıtları|İş akışı örneği yaşam döngüsünün çeşitli aşamaları sırasında yayınlanır. Örneğin, iş akışı başladığında veya tamamlandığında bir kayıt yayınlanır.|  
|Etkinlik yaşam döngüsü kayıtları|Ayrıntıları etkinlik yürütmesi. Bu kayıtlar, bir etkinliğin ne zaman zamanlandığı, etkinlik tamamlandığında veya bir hata oluştuğunda olduğu gibi bir iş akışı etkinliğinin durumunu gösterir.|  
|Yer işareti sürdürme kayıtları|Bir iş akışı örneği içindeki bir yer işareti kaldığı zaman yayınlanır.|  
|Özel izleme kayıtları|Bir iş akışı yazarı özel izleme kayıtları oluşturabilir ve bunları özel bir etkinlik içinde yayabilir.|  
  
 WF çalışma zamanından yayılan tüm izleme ile ilgili kayıtlar <xref:System.Activities.Tracking.TrackingRecord> , ortak veri kümesini içeren temel sınıftan türetilir. Kayıtları izleme basit bir iş akışının yaşam döngüsünü gösterir. Her izleme kaydı,,, <xref:System.Activities.Tracking.TrackingRecord.InstanceId%2A> <xref:System.Activities.Tracking.TrackingRecord.RecordNumber%2A> ve izleme kaydı türüne özgü ek bilgiler gibi ilişkili izleme olayı hakkındaki ayrıntıları içerir.  
  
 Aşağıdaki <xref:System.Activities.Tracking.TrackingRecord> nesne türleri iş akışı çalışma zamanı tarafından yayılır:  
  
- **Workflowcerecord** -bu <xref:System.Activities.Tracking.TrackingRecord> , iş akışı örneğinin yaşam döngüsünü açıklar. Örneğin, iş akışı başladığında veya tamamlandığında bir kayıt yayınlanır ve iş akışı örneğinin durumunu içerir. Bu kaydın ayrıntıları adresinde bulunabilir <xref:System.Activities.Tracking.WorkflowInstanceRecord> .  
  
- **WorkflowInstanceAbortedRecord** -bu <xref:System.Activities.Tracking.TrackingRecord> , bir iş akışı örneği iptal edildiğinde yayınlanır. Kayıt, iş akışı örneğinin durdurulduğu nedeni içerir. Bu kaydın ayrıntıları adresinde bulunabilir <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord> .  
  
- **WorkflowInstanceUnhandledExceptionRecord** - <xref:System.Activities.Tracking.TrackingRecord> iş akışı örneğinde bir özel durum oluşursa ve herhangi bir etkinlik tarafından işlenmediğinde bu yayılır. Kayıt, özel durum ayrıntılarını içerir. Bu kaydın ayrıntıları adresinde bulunabilir <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> .  
  
- **Workflowcesuspendedrecord** -bu <xref:System.Activities.Tracking.TrackingRecord> , bir iş akışı örneği askıya alındığında yayınlanır. Kayıt, iş akışı örneğinin askıya alınma nedenini içerir. Bu kaydın ayrıntıları adresinde bulunabilir <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord> .  
  
- **Workflowınstancesonlandırılanmış kayıt** -bu <xref:System.Activities.Tracking.TrackingRecord> , bir iş akışı örneği sonlandırıldığı zaman yayılır. Kayıt, iş akışı örneğinin sonlandırılmasının nedenini içerir. Bu kaydın ayrıntıları adresinde bulunabilir <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord> .  
  
- **ActivityStateRecord** - <xref:System.Activities.Tracking.TrackingRecord> iş akışı içindeki bir etkinlik yürütüldüğünde bu durum yayınlanır. Bu kayıtlar, iş akışı örneği içindeki etkinliğin durumunu gösterir. Bu kaydın ayrıntıları adresinde bulunabilir <xref:System.Activities.Tracking.ActivityStateRecord> .  
  
- **ActivityScheduledRecord** -bu <xref:System.Activities.Tracking.TrackingRecord> , bir etkinlik bir alt etkinliği zamanlıyor olduğunda yayınlanır. Bu kayıt, hem üst etkinliğin (zamanlama etkinliğinin) hem de zamanlanan alt etkinliğin ayrıntılarını içerir. Bu kaydın ayrıntıları adresinde bulunabilir <xref:System.Activities.Tracking.ActivityScheduledRecord> .  
  
- **FaultPropagationRecord** -bu, <xref:System.Activities.Tracking.TrackingRecord> işleme işlenene kadar kayda baktığı her işleyici için yayılır. Bir hata, iş akışı örneği içinde geçen yolu belirtmek için kullanılır. Bu kaydın ayrıntıları adresinde bulunabilir <xref:System.Activities.Tracking.FaultPropagationRecord> .  
  
- **CancelRequestedRecord** -bu <xref:System.Activities.Tracking.TrackingRecord> , bir etkinlik her bir alt etkinliği iptal etmeye çalıştığında yayılır. Bu kayıt, hem üst etkinliğin hem de iptal edilmekte olan alt etkinliğin ayrıntılarını içerir. Bu kaydın ayrıntıları adresinde bulunabilir <xref:System.Activities.Tracking.CancelRequestedRecord> .  
  
- **BookmarkResumptionRecord** -bu <xref:System.Activities.Tracking.TrackingRecord> , başarıyla devam eden tüm yer imlerini izler. Bu kaydın ayrıntıları adresinde bulunabilir <xref:System.Activities.Tracking.BookmarkResumptionRecord> .  
  
- **CustomTrackingRecord** -bu <xref:System.Activities.Tracking.TrackingRecord> , özel bir iş akışı etkinliği içinde bir iş akışı yazarı tarafından oluşturulur ve yayılır. Özel izleme kayıtları kayıtlarla birlikte yayınlanmek üzere verilerle doldurulabilir. Bu kaydın ayrıntıları adresinde bulunabilir <xref:System.Activities.Tracking.CustomTrackingRecord> .  
  
 Örneğin, <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.WriteLine> aşağıdaki sırayla sıralanmış kayıtları izleyen bir işlem içeren basit bir etkinlik olabilir:  
  
1. <xref:System.Activities.Tracking.WorkflowInstanceRecord> iş akışının başladığını gösterir.  
  
2. <xref:System.Activities.Tracking.ActivityScheduledRecord> bir etkinliğin zamanlandığını gösterir. Bu durumda, bir <xref:System.Activities.Statements.Sequence> etkinliktir.  
  
3. <xref:System.Activities.Tracking.ActivityScheduledRecord> etkinliği temsil eder <xref:System.Activities.Statements.WriteLine> .  
  
4. <xref:System.Activities.Tracking.ActivityStateRecord>İki etkinliğin tamamlanmasını temsil eden iki kayıt vardır.  
  
5. <xref:System.Activities.Tracking.WorkflowInstanceRecord> iş akışının tamamlandığını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Fabric Izleme](/previous-versions/appfabric/ee677251(v=azure.10))
- [App Fabric ile uygulamaları izleme](/previous-versions/appfabric/ee677276(v=azure.10))
