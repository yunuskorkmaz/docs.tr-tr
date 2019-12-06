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
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="b896d-102">Uygulamalarda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="b896d-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="b896d-103">Windows Workflow Foundation (WF), bir Windows Workflow Foundation uygulamasının veya hizmetin yürütülmesine ilişkin ayrıntılar vermek için iş akışı ile ilgili bilgileri izlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b896d-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="b896d-104">Windows Workflow Foundation Konakları, bir iş akışı örneğinin yürütülmesi sırasında iş akışı olaylarını yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="b896d-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="b896d-105">İş akışınız hata veya özel durumlar oluşturursa, işleme sorunlarını gidermek için Windows Workflow Foundation izleme ayrıntılarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b896d-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="b896d-106">WF Izlemeyi kullanarak WF sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="b896d-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="b896d-107">Windows Workflow Foundation etkinliğinin işlenmesi içindeki hataları algılamak için, hata durumu ile bir <xref:System.Activities.Tracking.ActivityStateRecord> sorgulayan bir izleme profiliyle izlemeyi etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b896d-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="b896d-108">Karşılık gelen sorgu aşağıdaki kodda belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b896d-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="b896d-109">Bir hata işleyicide bir hata yayılmışsa ve işlenirse (<xref:System.Activities.Statements.TryCatch> etkinliği gibi) Bu, <xref:System.Activities.Tracking.FaultPropagationRecord>kullanılarak algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="b896d-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="b896d-110"><xref:System.Activities.Tracking.FaultPropagationRecord>, hatanın kaynak etkinliğini ve hata işleyicisinin adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b896d-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="b896d-111"><xref:System.Activities.Tracking.FaultPropagationRecord> hata için özel durum yığını biçiminde hata ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b896d-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.</span></span> <span data-ttu-id="b896d-112">Bir <xref:System.Activities.Tracking.FaultPropagationRecord> Abone olunacak sorgu aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b896d-112">The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="b896d-113">Bir hata iş akışı içinde işlenmezse, iş akışı örneğinde işlenmemiş bir özel duruma neden olur ve iş akışı örneği iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="b896d-113">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="b896d-114">İşlenmemiş özel durumun ayrıntılarını anlamak için, izleme profilinin aşağıdaki örnekte belirtildiği gibi `state name="UnhandledException"` iş akışı örneği kaydını sorgulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b896d-114">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="b896d-115">Bir iş akışı örneği işlenmeyen bir özel durumla karşılaştığında, Windows Workflow Foundation izleme etkinleştirildiyse <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> nesne yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="b896d-115">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="b896d-116">Bu izleme kaydı, özel durum yığını formundaki hata ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b896d-116">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="b896d-117">Hatanın kaynağının ayrıntılarını (örneğin, etkinlik) hata verdi ve işlenmemiş özel durumla sonuçlandı. Bir Windows Workflow Foundation hata olaylarına abone olmak için izleme katılımcısı ekleyerek izlemeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="b896d-117">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="b896d-118">Bu katılımcıyı `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>ve `WorkflowInstanceQuery (state="UnhandledException")`sorgulayan bir izleme profiliyle yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="b896d-118">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="b896d-119">İzleme, ETW izleme katılımcısı kullanılarak etkinleştirilmişse, hata olayları bir ETW oturumuna dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="b896d-119">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="b896d-120">Olaylar Olay Görüntüleyicisi Olay Görüntüleyicisi kullanılarak görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="b896d-120">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="b896d-121">Bu, düğüm **Olay Görüntüleyicisi-> uygulamalar ve hizmetler günlükleri-> Microsoft-> Windows-> uygulama sunucusu-** çözümleme kanalında uygulamalar altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b896d-121">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b896d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b896d-122">See also</span></span>

- <span data-ttu-id="b896d-123">[Windows Server App Fabric Izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b896d-123">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="b896d-124">[App Fabric ile uygulamaları izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b896d-124">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
