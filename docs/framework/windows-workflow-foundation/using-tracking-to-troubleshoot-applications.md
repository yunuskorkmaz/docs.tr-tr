---
title: Uygulamalarda Sorun Giderme için İzleme Kullanma
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: 62c46ca36c89c023bfc775eb76ba454c9a4162c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004594"
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Uygulamalarda Sorun Giderme için İzleme Kullanma
Windows Workflow Foundation (WF), Windows Workflow Foundation uygulama veya hizmet yürütülmesini ayrıntı vermek için iş akışı ile ilgili bilgileri izlemenize olanak sağlar. Bir iş akışı örneği yürütülürken iş akışı olaylarını yakalamak Windows Workflow Foundation konakları gösterebilmektedir. İş akışınızı hataları veya özel durum oluşturursa, Windows Workflow Foundation ayrıntıları işlemesi sorun giderme için izleme kullanabilirsiniz.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>İzleme WF kullanarak bir WF sorunlarını giderme  
 İçinde Windows Workflow Foundation'da etkinlik işlenmesini hataları algılamak için izleme için sorgular bir izleme profili ile etkinleştirebilirsiniz. bir <xref:System.Activities.Tracking.ActivityStateRecord> Faulted durumunda. Karşılık gelen sorgu, aşağıdaki kodda belirtilir.  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 Bir hata yayılır ve içinde bir hata işleyicisi işlenen varsa (gibi bir <xref:System.Activities.Statements.TryCatch> etkinliği) bu kullanılarak algılanabilir bir <xref:System.Activities.Tracking.FaultPropagationRecord>. <xref:System.Activities.Tracking.FaultPropagationRecord> Kaynak etkinliği hata ve hata işleyicisi adını belirtir. <xref:System.Activities.Tracking.FaultPropagationRecord> Özel yığının hata formunda hata ayrıntılarını içerir. Sorgu için abone olmak için bir <xref:System.Activities.Tracking.FaultPropagationRecord> aşağıdaki örnekte gösterilmiştir.  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 İş akışı iş akışı örneği ve iş akışı örneği işlenmeyen bir özel durum ile sonuçlanır, içinde bir hata işlenmiyorsa iptal edildi. İşlenmeyen özel durumun ayrıntılarını anlamak için izleme profili ile iş akışı örneği kaydının sorgu `state name="UnhandledException"` aşağıdaki örnekte belirtildiği gibi.  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 Bir iş akışı örneği işlenmeyen bir özel durum karşılaştığında bir <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> nesne Windows Workflow Foundation izleme etkinleştirilirse yayılır.  
  
 Bu izleme kayıt formunda özel yığının hata ayrıntılarını içerir. Hata kaynağı olan hatalı ve içinde işlenmeyen bir özel yol (örneğin, etkinliği) ayrıntılarını var. Windows Workflow Foundation hata olaylarına abone olmak için izleme katılımcı ekleyerek izlemeyi etkinleştirin. Sorgular bir izleme profili ile bu katılımcı yapılandırın `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, ve `WorkflowInstanceQuery (state="UnhandledException")`.  
  
 ETW İzleme katılımcı kullanarak izleme etkinse bir ETW oturumu hata olaylar gönderilir. Olaylar, Olay Görüntüleyicisi'ni Olay Görüntüleyicisi'ni kullanarak görüntülenebilir. Bu düğümü altında bulunabilir **Olay Görüntüleyicisi -> uygulamalar ve hizmet günlükleri -> Microsoft -> Windows -> Uygulama uygulamalarının** analitik kanal.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Fabric izleme](https://go.microsoft.com/fwlink/?LinkId=201273)
- [App Fabric ile uygulamaları izleme](https://go.microsoft.com/fwlink/?LinkId=201275)
