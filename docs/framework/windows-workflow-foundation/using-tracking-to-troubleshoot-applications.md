---
title: Uygulamalarda Sorun Giderme için İzleme Kullanma
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: fc9427d0c06ed67ea69669cab2aae64f39f7c10c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551294"
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Uygulamalarda Sorun Giderme için İzleme Kullanma
Windows Workflow Foundation (WF), bir Windows Workflow Foundation uygulamasının veya hizmetin yürütülmesine ilişkin ayrıntılar vermek için iş akışı ile ilgili bilgileri izlemenize olanak sağlar. Windows Workflow Foundation Konakları, bir iş akışı örneğinin yürütülmesi sırasında iş akışı olaylarını yakalayabilir. İş akışınız hata veya özel durumlar oluşturursa, işleme sorunlarını gidermek için Windows Workflow Foundation izleme ayrıntılarını kullanabilirsiniz.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>WF Izlemeyi kullanarak WF sorunlarını giderme  
 Windows Workflow Foundation etkinliğinin işlenmesi içindeki hataları algılamak için, hata durumunu hatalı bir şekilde sorgulayan bir izleme profiliyle izlemeyi etkinleştirebilirsiniz <xref:System.Activities.Tracking.ActivityStateRecord> . Karşılık gelen sorgu aşağıdaki kodda belirtilir.  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 Hata işleyicide bir hata yayılmışsa ve işlenirse (örneğin, bir <xref:System.Activities.Statements.TryCatch> etkinlik) Bu, kullanılarak algılanabilir <xref:System.Activities.Tracking.FaultPropagationRecord> . , Hatanın <xref:System.Activities.Tracking.FaultPropagationRecord> kaynak etkinliğini ve hata işleyicisinin adını gösterir. <xref:System.Activities.Tracking.FaultPropagationRecord>Hatanın özel durum yığını formundaki hata ayrıntılarını içerir. Bir için abone olunacak sorgu <xref:System.Activities.Tracking.FaultPropagationRecord> Aşağıdaki örnekte gösterilmiştir.  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 Bir hata iş akışı içinde işlenmezse, iş akışı örneğinde işlenmemiş bir özel duruma neden olur ve iş akışı örneği iptal edilir. İşlenmeyen özel durumun ayrıntılarını anlamak için, izleme profilinin `state name="UnhandledException"` Aşağıdaki örnekte belirtilen şekilde iş akışı örneği kaydını sorgulaması gerekir.  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 Bir iş akışı örneği işlenmeyen bir özel durumla karşılaştığında, <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> Windows Workflow Foundation izleme etkinleştirildiyse bir nesne yayınlanır.  
  
 Bu izleme kaydı, özel durum yığını formundaki hata ayrıntılarını içerir. Hatanın kaynağının ayrıntılarını (örneğin, etkinlik) hata verdi ve işlenmemiş özel durumla sonuçlandı. Bir Windows Workflow Foundation hata olaylarına abone olmak için izleme katılımcısı ekleyerek izlemeyi etkinleştirin. Bu katılımcıyı,, ve için sorgulayan bir izleme profiliyle `ActivityStateQuery (state="Faulted")` yapılandırın <xref:System.Activities.Tracking.FaultPropagationRecord> `WorkflowInstanceQuery (state="UnhandledException")` .  
  
 İzleme, ETW izleme katılımcısı kullanılarak etkinleştirilmişse, hata olayları bir ETW oturumuna dağıtılır. Olaylar Olay Görüntüleyicisi Olay Görüntüleyicisi kullanılarak görüntülenebilir. Bu, düğüm **Olay Görüntüleyicisi->uygulamalar ve hizmetler günlükleri->Microsoft->Windows->uygulama sunucusu-** çözümleme kanalında uygulamalar altında bulunabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Fabric Izleme](/previous-versions/appfabric/ee677251(v=azure.10))
- [App Fabric ile uygulamaları izleme](/previous-versions/appfabric/ee677276(v=azure.10))
