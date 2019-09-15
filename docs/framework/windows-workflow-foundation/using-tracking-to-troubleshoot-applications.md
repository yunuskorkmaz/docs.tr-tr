---
title: Uygulamalarda Sorun Giderme için İzleme Kullanma
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: b64b92de9cb36807a2bf1eb7ff57f9f6e1a07156
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988927"
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Uygulamalarda Sorun Giderme için İzleme Kullanma
Windows Workflow Foundation (WF), bir Windows Workflow Foundation uygulamasının veya hizmetin yürütülmesine ilişkin ayrıntılar vermek için iş akışı ile ilgili bilgileri izlemenize olanak sağlar. Windows Workflow Foundation Konakları, bir iş akışı örneğinin yürütülmesi sırasında iş akışı olaylarını yakalayabilir. İş akışınız hata veya özel durumlar oluşturursa, işleme sorunlarını gidermek için Windows Workflow Foundation izleme ayrıntılarını kullanabilirsiniz.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>WF Izlemeyi kullanarak WF sorunlarını giderme  
 Windows Workflow Foundation etkinliğinin işlenmesi içindeki hataları algılamak için, hata durumunu hatalı bir <xref:System.Activities.Tracking.ActivityStateRecord> şekilde sorgulayan bir izleme profiliyle izlemeyi etkinleştirebilirsiniz. Karşılık gelen sorgu aşağıdaki kodda belirtilir.  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 Hata işleyicide bir hata yayılmışsa ve işlenirse (örneğin <xref:System.Activities.Statements.TryCatch> , bir etkinlik) Bu, <xref:System.Activities.Tracking.FaultPropagationRecord>kullanılarak algılanabilir. , <xref:System.Activities.Tracking.FaultPropagationRecord> Hatanın kaynak etkinliğini ve hata işleyicisinin adını gösterir. Hatanın özel durum yığını formundaki hata ayrıntılarını içerir.<xref:System.Activities.Tracking.FaultPropagationRecord> Bir <xref:System.Activities.Tracking.FaultPropagationRecord> için abone olunacak sorgu aşağıdaki örnekte gösterilmiştir.  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 Bir hata iş akışı içinde işlenmezse, iş akışı örneğinde işlenmemiş bir özel duruma neden olur ve iş akışı örneği iptal edilir. İşlenmeyen özel durumun ayrıntılarını anlamak için, izleme profilinin aşağıdaki örnekte belirtilen `state name="UnhandledException"` şekilde iş akışı örneği kaydını sorgulaması gerekir.  
  
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
  
 Bu izleme kaydı, özel durum yığını formundaki hata ayrıntılarını içerir. Hatanın kaynağının ayrıntılarını (örneğin, etkinlik) hata verdi ve işlenmemiş özel durumla sonuçlandı. Bir Windows Workflow Foundation hata olaylarına abone olmak için izleme katılımcısı ekleyerek izlemeyi etkinleştirin. Bu katılımcıyı, `ActivityStateQuery (state="Faulted")` <xref:System.Activities.Tracking.FaultPropagationRecord>, ve `WorkflowInstanceQuery (state="UnhandledException")`için sorgulayan bir izleme profiliyle yapılandırın.  
  
 İzleme, ETW izleme katılımcısı kullanılarak etkinleştirilmişse, hata olayları bir ETW oturumuna dağıtılır. Olaylar Olay Görüntüleyicisi Olay Görüntüleyicisi kullanılarak görüntülenebilir. Bu, düğüm **Olay Görüntüleyicisi-> uygulamalar ve hizmetler günlükleri-> Microsoft-> Windows-> uygulama sunucusu-** çözümleme kanalında uygulamalar altında bulunabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Fabric Izleme](https://go.microsoft.com/fwlink/?LinkId=201273)
- [App Fabric ile uygulamaları izleme](https://go.microsoft.com/fwlink/?LinkId=201275)
