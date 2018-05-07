---
title: Uygulamalarla ilgili sorunları gidermek için izleme kullanma
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: ee9aaaae80f213f026a222ac1754ae8b4fdf2d37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Uygulamalarla ilgili sorunları gidermek için izleme kullanma
Windows Workflow Foundation (WF), bir Windows Workflow Foundation uygulaması veya hizmeti yürütülmesi ayrıntıları vermek için iş akışı ile ilgili bilgileri izlemenize olanak sağlar. Windows Workflow Foundation ana iş akışı olayları bir iş akışı örneği yürütülürken yakalayabilir. İş akışınızı arıza ya da özel durum oluşturursa, Windows Workflow Foundation ayrıntıları işlemesi sorun giderme için izleme kullanabilirsiniz.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>WF izleme kullanılarak WF sorunlarını giderme  
 Windows Workflow Foundation etkinliği işlenmesini içinde hataları algılamak için izleme için sorgular bir izleme profiliyle etkinleştirebilirsiniz bir <xref:System.Activities.Tracking.ActivityStateRecord> Faulted durumunda. Karşılık gelen sorgu aşağıdaki kodu belirtilmedi.  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 Bir arıza yayılan ve bir arıza işleyici içinde ele varsa (gibi bir <xref:System.Activities.Statements.TryCatch> etkinlik) bu kullanılarak algılanabilir bir <xref:System.Activities.Tracking.FaultPropagationRecord>. <xref:System.Activities.Tracking.FaultPropagationRecord> Hataya kaynak etkinliğini ve hata işleyici adını gösterir. <xref:System.Activities.Tracking.FaultPropagationRecord> Hatası için özel durum yığını formunda hata ayrıntıları içerir. Sorgu için abone olmak için bir <xref:System.Activities.Tracking.FaultPropagationRecord> aşağıdaki örnekte gösterilir.  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 İçinde bir arıza işlenmemiş, işlenmeyen bir özel durum iş akışı örneği ve iş akışı örneği sonuçlanır iş akışı iptal edilir. İşlenmeyen özel durum ayrıntılarını anlamak için izleme profili iş akışı örneği kaydıyla sorgu `state name="UnhandledException"` aşağıdaki örnekte belirtildiği gibi.  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 Bir iş akışı örneği işlenmeyen bir özel durum karşılaştığında bir <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> nesnesi Windows Workflow Foundation izleme etkinleştirilirse yayılan.  
  
 Bu izleme kaydı özel durum yığını formunda hata ayrıntıları içerir. Hatalı ve içinde işlenmeyen bir özel sonuçlandı hataya (örneğin, etkinlik) kaynak ayrıntılarını sahiptir. Windows Workflow Foundation hata olaylarına abone olmak için izleme katılımcı ekleyerek izlemeyi etkinleştirin. Bu katılımcı için sorgular bir izleme profili yapılandırmak `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, ve `WorkflowInstanceQuery (state="UnhandledException")`.  
  
 ETW İzleme katılımcı kullanarak izleme etkinleştirilirse, hata olayları ETW oturumuna gösterilen. Olaylar, Olay Görüntüleyicisi'ni Olay Görüntüleyicisi'ni kullanarak görüntülenebilir. Bu düğümü altında bulunabilir **Olay Görüntüleyicisi -> uygulamalar ve hizmet günlükleri -> Microsoft -> Windows -> Uygulama uygulamalarının** analitik kanal.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Server App Fabric izleme](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [App Fabric ile uygulamaları izleme](http://go.microsoft.com/fwlink/?LinkId=201275)
