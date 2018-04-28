---
title: Uygulamalarla ilgili sorunları gidermek için izleme kullanma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: adc9a159b8887b0198cf19891f73fdee2a48437b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="f3601-102">Uygulamalarla ilgili sorunları gidermek için izleme kullanma</span><span class="sxs-lookup"><span data-stu-id="f3601-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="f3601-103">Windows Workflow Foundation (WF), bir Windows Workflow Foundation uygulaması veya hizmeti yürütülmesi ayrıntıları vermek için iş akışı ile ilgili bilgileri izlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3601-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="f3601-104">Windows Workflow Foundation ana iş akışı olayları bir iş akışı örneği yürütülürken yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="f3601-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="f3601-105">İş akışınızı arıza ya da özel durum oluşturursa, Windows Workflow Foundation ayrıntıları işlemesi sorun giderme için izleme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3601-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="f3601-106">WF izleme kullanılarak WF sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="f3601-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="f3601-107">Windows Workflow Foundation etkinliği işlenmesini içinde hataları algılamak için izleme için sorgular bir izleme profiliyle etkinleştirebilirsiniz bir <xref:System.Activities.Tracking.ActivityStateRecord> Faulted durumunda.</span><span class="sxs-lookup"><span data-stu-id="f3601-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="f3601-108">Karşılık gelen sorgu aşağıdaki kodu belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="f3601-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="f3601-109">Bir arıza yayılan ve bir arıza işleyici içinde ele varsa (gibi bir <xref:System.Activities.Statements.TryCatch> etkinlik) bu kullanılarak algılanabilir bir <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="f3601-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="f3601-110"><xref:System.Activities.Tracking.FaultPropagationRecord> Hataya kaynak etkinliğini ve hata işleyici adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3601-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="f3601-111"><xref:System.Activities.Tracking.FaultPropagationRecord> Hatası için özel durum yığını formunda hata ayrıntıları içerir. Sorgu için abone olmak için bir <xref:System.Activities.Tracking.FaultPropagationRecord> aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f3601-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="f3601-112">İçinde bir arıza işlenmemiş, işlenmeyen bir özel durum iş akışı örneği ve iş akışı örneği sonuçlanır iş akışı iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="f3601-112">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="f3601-113">İşlenmeyen özel durum ayrıntılarını anlamak için izleme profili iş akışı örneği kaydıyla sorgu `state name="UnhandledException"` aşağıdaki örnekte belirtildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f3601-113">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="f3601-114">Bir iş akışı örneği işlenmeyen bir özel durum karşılaştığında bir <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> nesnesi Windows Workflow Foundation izleme etkinleştirilirse yayılan.</span><span class="sxs-lookup"><span data-stu-id="f3601-114">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="f3601-115">Bu izleme kaydı özel durum yığını formunda hata ayrıntıları içerir.</span><span class="sxs-lookup"><span data-stu-id="f3601-115">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="f3601-116">Hatalı ve içinde işlenmeyen bir özel sonuçlandı hataya (örneğin, etkinlik) kaynak ayrıntılarını sahiptir. Windows Workflow Foundation hata olaylarına abone olmak için izleme katılımcı ekleyerek izlemeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f3601-116">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="f3601-117">Bu katılımcı için sorgular bir izleme profili yapılandırmak `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, ve `WorkflowInstanceQuery (state="UnhandledException")`.</span><span class="sxs-lookup"><span data-stu-id="f3601-117">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="f3601-118">ETW İzleme katılımcı kullanarak izleme etkinleştirilirse, hata olayları ETW oturumuna gösterilen.</span><span class="sxs-lookup"><span data-stu-id="f3601-118">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="f3601-119">Olaylar, Olay Görüntüleyicisi'ni Olay Görüntüleyicisi'ni kullanarak görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="f3601-119">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="f3601-120">Bu düğümü altında bulunabilir **Olay Görüntüleyicisi -> uygulamalar ve hizmet günlükleri -> Microsoft -> Windows -> Uygulama uygulamalarının** analitik kanal.</span><span class="sxs-lookup"><span data-stu-id="f3601-120">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3601-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3601-121">See Also</span></span>  
 [<span data-ttu-id="f3601-122">Windows Server App Fabric izleme</span><span class="sxs-lookup"><span data-stu-id="f3601-122">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="f3601-123">App Fabric ile uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="f3601-123">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
