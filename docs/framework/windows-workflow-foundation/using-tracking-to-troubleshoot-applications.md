---
title: Uygulamalarda Sorun Giderme için İzleme Kullanma
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: b07e850810734082568ddca9776a72575c986094
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837564"
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Uygulamalarda Sorun Giderme için İzleme Kullanma
Windows Workflow Foundation (WF), bir Windows Workflow Foundation uygulamasının veya hizmetin yürütülmesine ilişkin ayrıntılar vermek için iş akışı ile ilgili bilgileri izlemenize olanak sağlar. Windows Workflow Foundation Konakları, bir iş akışı örneğinin yürütülmesi sırasında iş akışı olaylarını yakalayabilir. İş akışınız hata veya özel durumlar oluşturursa, işleme sorunlarını gidermek için Windows Workflow Foundation izleme ayrıntılarını kullanabilirsiniz.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>WF Izlemeyi kullanarak WF sorunlarını giderme  
 Windows Workflow Foundation etkinliğinin işlenmesi içindeki hataları algılamak için, hata durumu ile bir <xref:System.Activities.Tracking.ActivityStateRecord> sorgulayan bir izleme profiliyle izlemeyi etkinleştirebilirsiniz. Karşılık gelen sorgu aşağıdaki kodda belirtilir.  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 Bir hata işleyicide bir hata yayılmışsa ve işlenirse (<xref:System.Activities.Statements.TryCatch> etkinliği gibi) Bu, <xref:System.Activities.Tracking.FaultPropagationRecord>kullanılarak algılanabilir. <xref:System.Activities.Tracking.FaultPropagationRecord>, hatanın kaynak etkinliğini ve hata işleyicisinin adını gösterir. <xref:System.Activities.Tracking.FaultPropagationRecord> hata için özel durum yığını biçiminde hata ayrıntılarını içerir. Bir <xref:System.Activities.Tracking.FaultPropagationRecord> Abone olunacak sorgu aşağıdaki örnekte gösterilmiştir.  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 Bir hata iş akışı içinde işlenmezse, iş akışı örneğinde işlenmemiş bir özel duruma neden olur ve iş akışı örneği iptal edilir. İşlenmemiş özel durumun ayrıntılarını anlamak için, izleme profilinin aşağıdaki örnekte belirtildiği gibi `state name="UnhandledException"` iş akışı örneği kaydını sorgulaması gerekir.  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 Bir iş akışı örneği işlenmeyen bir özel durumla karşılaştığında, Windows Workflow Foundation izleme etkinleştirildiyse <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> nesne yayınlanır.  
  
 Bu izleme kaydı, özel durum yığını formundaki hata ayrıntılarını içerir. Hatanın kaynağının ayrıntılarını (örneğin, etkinlik) hata verdi ve işlenmemiş özel durumla sonuçlandı. Bir Windows Workflow Foundation hata olaylarına abone olmak için izleme katılımcısı ekleyerek izlemeyi etkinleştirin. Bu katılımcıyı `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>ve `WorkflowInstanceQuery (state="UnhandledException")`sorgulayan bir izleme profiliyle yapılandırın.  
  
 İzleme, ETW izleme katılımcısı kullanılarak etkinleştirilmişse, hata olayları bir ETW oturumuna dağıtılır. Olaylar Olay Görüntüleyicisi Olay Görüntüleyicisi kullanılarak görüntülenebilir. Bu, düğüm **Olay Görüntüleyicisi-> uygulamalar ve hizmetler günlükleri-> Microsoft-> Windows-> uygulama sunucusu-** çözümleme kanalında uygulamalar altında bulunabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Fabric Izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [App Fabric ile uygulamaları izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
