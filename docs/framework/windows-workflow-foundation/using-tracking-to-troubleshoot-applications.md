---
title: "Uygulamalarla ilgili sorunları gidermek için izleme kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52a599d9cba2e68fdb74d364dad562d2547ca020
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Uygulamalarla ilgili sorunları gidermek için izleme kullanma
[!INCLUDE[wf](../../../includes/wf-md.md)]Ayrıntılar yürütülmesi vermek için iş akışı ile ilgili bilgileri izlemenize olanak sağlayan bir [!INCLUDE[wf2](../../../includes/wf2-md.md)] uygulama veya hizmet. [!INCLUDE[wf2](../../../includes/wf2-md.md)]ana bilgisayarlar bir iş akışı örneği yürütülürken iş akışı olaylarını yakalamak kullanabilirsiniz. İş akışınızı arıza ya da özel durum oluşturursa, kullanabileceğiniz [!INCLUDE[wf2](../../../includes/wf2-md.md)] ayrıntıları işlemesi sorun giderme için izleme.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>WF izleme kullanılarak WF sorunlarını giderme  
 Hatalarının işlenmesini içinde algılamak için bir [!INCLUDE[wf2](../../../includes/wf2-md.md)] etkinlik, izleme için sorgular bir izleme profiliyle etkinleştirebilir bir <xref:System.Activities.Tracking.ActivityStateRecord> Faulted durumunda. Karşılık gelen sorgu aşağıdaki kodu belirtilmedi.  
  
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
  
 Bir iş akışı örneği işlenmeyen bir özel durum karşılaştığında bir <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> nesne varsa yayılan [!INCLUDE[wf2](../../../includes/wf2-md.md)] izleme etkinleştirildi.  
  
 Bu izleme kaydı özel durum yığını formunda hata ayrıntıları içerir. Hatalı ve içinde işlenmeyen bir özel sonuçlandı hataya (örneğin, etkinlik) kaynak ayrıntılarını sahiptir. Hata olayları abone olmak için bir [!INCLUDE[wf2](../../../includes/wf2-md.md)], izleme katılımcı ekleyerek izlemeyi etkinleştir. Bu katılımcı için sorgular bir izleme profili yapılandırmak `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, ve `WorkflowInstanceQuery (state="UnhandledException")`.  
  
 ETW İzleme katılımcı kullanarak izleme etkinleştirilirse, hata olayları ETW oturumuna gösterilen. Olaylar, Olay Görüntüleyicisi'ni Olay Görüntüleyicisi'ni kullanarak görüntülenebilir. Bu düğümü altında bulunabilir **Olay Görüntüleyicisi -> uygulamalar ve hizmet günlükleri -> Microsoft -> Windows -> Uygulama uygulamalarının** analitik kanal.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Server App Fabric izleme](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [App Fabric ile uygulamaları izleme](http://go.microsoft.com/fwlink/?LinkId=201275)
