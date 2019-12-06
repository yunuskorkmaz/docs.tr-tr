---
title: İzleme Kayıtları
ms.date: 03/30/2017
ms.assetid: 51adbda3-bd8b-4892-a8ea-d343186472d2
ms.openlocfilehash: d59db7e4c90b3cffe523c89de093f58f3e520bde
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837616"
---
# <a name="tracking-records"></a>İzleme Kayıtları
İş akışı çalışma zamanı, izleme kayıtlarını izlemek için bir iş akışı örneğinin yürütülmesini izlemek üzere işaretlenir.  
  
## <a name="tracking-records"></a>İzleme Kayıtları  
 Aşağıdaki tabloda iş akışı çalışma zamanının yaydığı izleme kayıtlarının ayrıntıları verilmiştir.  
  
|İzleme kaydı|Açıklama|  
|---------------------|-----------------|  
|İş akışı yaşam döngüsü kayıtları|İş akışı örneği yaşam döngüsünün çeşitli aşamaları sırasında yayınlanır. Örneğin, iş akışı başladığında veya tamamlandığında bir kayıt yayınlanır.|  
|Etkinlik yaşam döngüsü kayıtları|Ayrıntıları etkinlik yürütmesi. Bu kayıtlar, bir etkinliğin ne zaman zamanlandığı, etkinlik tamamlandığında veya bir hata oluştuğunda olduğu gibi bir iş akışı etkinliğinin durumunu gösterir.|  
|Yer işareti sürdürme kayıtları|Bir iş akışı örneği içindeki bir yer işareti kaldığı zaman yayınlanır.|  
|Özel izleme kayıtları|Bir iş akışı yazarı özel izleme kayıtları oluşturabilir ve bunları özel bir etkinlik içinde yayabilir.|  
  
 WF çalışma zamanından yayılan tüm izleme ile ilgili kayıtlar, ortak veri kümesini içeren <xref:System.Activities.Tracking.TrackingRecord>temel sınıfından türetilir. Kayıtları izleme basit bir iş akışının yaşam döngüsünü gösterir. Her izleme kaydı, <xref:System.Activities.Tracking.TrackingRecord.InstanceId%2A>, <xref:System.Activities.Tracking.TrackingRecord.RecordNumber%2A>ve izleme kaydı türüne özgü ek bilgiler gibi ilişkili izleme olayı hakkındaki ayrıntıları içerir.  
  
 Aşağıdaki <xref:System.Activities.Tracking.TrackingRecord> nesne türleri iş akışı çalışma zamanı tarafından yayılır:  
  
- **Workflowcerecord** -bu <xref:System.Activities.Tracking.TrackingRecord> iş akışı örneğinin yaşam döngüsünü açıklar. Örneğin, iş akışı başladığında veya tamamlandığında bir kayıt yayınlanır ve iş akışı örneğinin durumunu içerir. Bu kaydın ayrıntıları <xref:System.Activities.Tracking.WorkflowInstanceRecord>' de bulunabilir.  
  
- **WorkflowInstanceAbortedRecord** -bu <xref:System.Activities.Tracking.TrackingRecord>, bir iş akışı örneği iptal edildiğinde yayınlanır. Kayıt, iş akışı örneğinin durdurulduğu nedeni içerir. Bu kaydın ayrıntıları <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>' de bulunabilir.  
  
- **WorkflowInstanceUnhandledExceptionRecord** -iş akışı örneğinde bir özel durum oluşursa ve herhangi bir etkinlik tarafından işlenmediğinde bu <xref:System.Activities.Tracking.TrackingRecord> yayınlanır. Kayıt, özel durum ayrıntılarını içerir. Bu kaydın ayrıntıları <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>' de bulunabilir.  
  
- **Workflowcesuspendedrecord** -bu <xref:System.Activities.Tracking.TrackingRecord>, her bir iş akışı örneği askıya alındığında yayınlanır. Kayıt, iş akışı örneğinin askıya alınma nedenini içerir. Bu kaydın ayrıntıları <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>' de bulunabilir.  
  
- **Workflowınstancesonlandırılanmış kayıt** -bu <xref:System.Activities.Tracking.TrackingRecord>, bir iş akışı örneği her sonlandırıldığında yayınlanır. Kayıt, iş akışı örneğinin sonlandırılmasının nedenini içerir. Bu kaydın ayrıntıları <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>' de bulunabilir.  
  
- **ActivityStateRecord** -iş akışı içindeki bir etkinlik yürütüldüğünde bu <xref:System.Activities.Tracking.TrackingRecord> yayınlanır. Bu kayıtlar, iş akışı örneği içindeki etkinliğin durumunu gösterir. Bu kaydın ayrıntıları <xref:System.Activities.Tracking.ActivityStateRecord>' de bulunabilir.  
  
- **ActivityScheduledRecord** -bu <xref:System.Activities.Tracking.TrackingRecord>, bir etkinlik bir alt etkinliği zamanlamalarına göre yayınlanır. Bu kayıt, hem üst etkinliğin (zamanlama etkinliğinin) hem de zamanlanan alt etkinliğin ayrıntılarını içerir. Bu kaydın ayrıntıları <xref:System.Activities.Tracking.ActivityScheduledRecord>' de bulunabilir.  
  
- **FaultPropagationRecord** -bu <xref:System.Activities.Tracking.TrackingRecord>, işleme işlenene kadar kayda baktığı her işleyici için yayılır. Bir hata, iş akışı örneği içinde geçen yolu belirtmek için kullanılır. Bu kaydın ayrıntıları <xref:System.Activities.Tracking.FaultPropagationRecord>' de bulunabilir.  
  
- **CancelRequestedRecord** -bu <xref:System.Activities.Tracking.TrackingRecord>, bir etkinlik her bir alt etkinliği iptal etmeye çalıştığında yayınlanır. Bu kayıt, hem üst etkinliğin hem de iptal edilmekte olan alt etkinliğin ayrıntılarını içerir. Bu kaydın ayrıntıları <xref:System.Activities.Tracking.CancelRequestedRecord>' de bulunabilir.  
  
- **BookmarkResumptionRecord** -bu <xref:System.Activities.Tracking.TrackingRecord> başarıyla devam eden yer imlerini izler. Bu kaydın ayrıntıları <xref:System.Activities.Tracking.BookmarkResumptionRecord>' de bulunabilir.  
  
- **CustomTrackingRecord** -bu <xref:System.Activities.Tracking.TrackingRecord>, özel bir iş akışı etkinliği içindeki bir iş akışı yazarı tarafından oluşturulur ve yayınlanır. Özel izleme kayıtları kayıtlarla birlikte yayınlanmek üzere verilerle doldurulabilir. Bu kaydın ayrıntıları <xref:System.Activities.Tracking.CustomTrackingRecord>' de bulunabilir.  
  
 Örneğin, aşağıdaki sırayla sıralanmış kayıtları izleme ile <xref:System.Activities.Statements.WriteLine> bir işlem içeren basit bir <xref:System.Activities.Statements.Sequence> etkinlik olabilir:  
  
1. <xref:System.Activities.Tracking.WorkflowInstanceRecord>, iş akışının başladığını gösterir.  
  
2. <xref:System.Activities.Tracking.ActivityScheduledRecord>, bir etkinliğin zamanlandığını gösterir. Bu durumda, <xref:System.Activities.Statements.Sequence> bir etkinliktir.  
  
3. <xref:System.Activities.Tracking.ActivityScheduledRecord>, <xref:System.Activities.Statements.WriteLine> etkinliğini temsil eder.  
  
4. İki etkinliğin tamamlanmasını temsil eden iki <xref:System.Activities.Tracking.ActivityStateRecord> kaydı vardır.  
  
5. <xref:System.Activities.Tracking.WorkflowInstanceRecord>, iş akışının tamamlandığını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Fabric Izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [App Fabric ile uygulamaları izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
