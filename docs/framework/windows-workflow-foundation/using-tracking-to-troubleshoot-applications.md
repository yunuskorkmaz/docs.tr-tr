---
title: Uygulamalarda sorun giderme için izleme kullanma
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: 1ed95a26f682fcdb609b410251fdb3f8b647016a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734428"
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="57d42-102">Uygulamalarda sorun giderme için izleme kullanma</span><span class="sxs-lookup"><span data-stu-id="57d42-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="57d42-103">Windows Workflow Foundation (WF), Windows Workflow Foundation uygulama veya hizmet yürütülmesini ayrıntı vermek için iş akışı ile ilgili bilgileri izlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="57d42-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="57d42-104">Bir iş akışı örneği yürütülürken iş akışı olaylarını yakalamak Windows Workflow Foundation konakları gösterebilmektedir.</span><span class="sxs-lookup"><span data-stu-id="57d42-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="57d42-105">İş akışınızı hataları veya özel durum oluşturursa, Windows Workflow Foundation ayrıntıları işlemesi sorun giderme için izleme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57d42-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="57d42-106">İzleme WF kullanarak bir WF sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="57d42-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="57d42-107">İçinde Windows Workflow Foundation'da etkinlik işlenmesini hataları algılamak için izleme için sorgular bir izleme profili ile etkinleştirebilirsiniz. bir <xref:System.Activities.Tracking.ActivityStateRecord> Faulted durumunda.</span><span class="sxs-lookup"><span data-stu-id="57d42-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="57d42-108">Karşılık gelen sorgu, aşağıdaki kodda belirtilir.</span><span class="sxs-lookup"><span data-stu-id="57d42-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="57d42-109">Bir hata yayılır ve içinde bir hata işleyicisi işlenen varsa (gibi bir <xref:System.Activities.Statements.TryCatch> etkinliği) bu kullanılarak algılanabilir bir <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="57d42-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="57d42-110"><xref:System.Activities.Tracking.FaultPropagationRecord> Kaynak etkinliği hata ve hata işleyicisi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="57d42-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="57d42-111"><xref:System.Activities.Tracking.FaultPropagationRecord> Özel yığının hata formunda hata ayrıntılarını içerir. Sorgu için abone olmak için bir <xref:System.Activities.Tracking.FaultPropagationRecord> aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="57d42-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="57d42-112">İş akışı iş akışı örneği ve iş akışı örneği işlenmeyen bir özel durum ile sonuçlanır, içinde bir hata işlenmiyorsa iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="57d42-112">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="57d42-113">İşlenmeyen özel durumun ayrıntılarını anlamak için izleme profili ile iş akışı örneği kaydının sorgu `state name="UnhandledException"` aşağıdaki örnekte belirtildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="57d42-113">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="57d42-114">Bir iş akışı örneği işlenmeyen bir özel durum karşılaştığında bir <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> nesne Windows Workflow Foundation izleme etkinleştirilirse yayılır.</span><span class="sxs-lookup"><span data-stu-id="57d42-114">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="57d42-115">Bu izleme kayıt formunda özel yığının hata ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="57d42-115">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="57d42-116">Hata kaynağı olan hatalı ve içinde işlenmeyen bir özel yol (örneğin, etkinliği) ayrıntılarını var. Windows Workflow Foundation hata olaylarına abone olmak için izleme katılımcı ekleyerek izlemeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="57d42-116">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="57d42-117">Sorgular bir izleme profili ile bu katılımcı yapılandırın `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, ve `WorkflowInstanceQuery (state="UnhandledException")`.</span><span class="sxs-lookup"><span data-stu-id="57d42-117">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="57d42-118">ETW İzleme katılımcı kullanarak izleme etkinse bir ETW oturumu hata olaylar gönderilir.</span><span class="sxs-lookup"><span data-stu-id="57d42-118">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="57d42-119">Olaylar, Olay Görüntüleyicisi'ni Olay Görüntüleyicisi'ni kullanarak görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="57d42-119">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="57d42-120">Bu düğümü altında bulunabilir **Olay Görüntüleyicisi -> uygulamalar ve hizmet günlükleri -> Microsoft -> Windows -> Uygulama uygulamalarının** analitik kanal.</span><span class="sxs-lookup"><span data-stu-id="57d42-120">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57d42-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57d42-121">See also</span></span>
- [<span data-ttu-id="57d42-122">Windows Server App Fabric izleme</span><span class="sxs-lookup"><span data-stu-id="57d42-122">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="57d42-123">App Fabric ile uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="57d42-123">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
