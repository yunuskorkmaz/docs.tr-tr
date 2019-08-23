---
title: 'Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 5781878270272f5ef894c68dc23b9433029e1d41
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968501"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="5f2a0-102">Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5f2a0-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="5f2a0-103">Bu konu başlığında [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırılan bir iş akışı için izlemenin nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="5f2a0-104">Bir hizmet davranışı belirtilerek bir Web. config dosyası aracılığıyla yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="5f2a0-105">Yapılandırmada Izlemeyi Yapılandır</span><span class="sxs-lookup"><span data-stu-id="5f2a0-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="5f2a0-106">Aşağıdaki örnekte gösterildiği gibi,`behavior`bir yapılandırma dosyasında < > öğesini kullanarakekleyin.<xref:System.Activities.Tracking.EtwTrackingParticipant></span><span class="sxs-lookup"><span data-stu-id="5f2a0-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>              
       </serviceBehaviors>  
    <behaviors>  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="5f2a0-107">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="5f2a0-108">Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="5f2a0-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="5f2a0-109">Önceki yapılandırma örneği bir <xref:System.Activities.Tracking.EtwTrackingParticipant> ekler ve bir izleme profili adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="5f2a0-110">İzleme profilleri, bir <`trackingProfile``tracking`> öğesi içindeki bir < > öğesinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="5f2a0-111">İzleme profili, çalışma zamanında bir iş akışı örneği durumu değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="5f2a0-112">Aşağıdaki örnek, bir izleme profilinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-112">The following example shows how to create a tracking profile.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <tracking>   
         <trackingProfile name="Sample Tracking Profile">  
            <workflow activityDefinitionId="*">  
               <workflowInstanceQueries>  
                 <workflowInstanceQuery>  
                    <states>  
                       <state name="Started"/>  
                       <state name="Completed"/>  
                    </states>  
                </workflowInstanceQuery>  
             </workflowInstanceQueries>  
           </workflow>  
         </trackingProfile>   
       </tracking>  
    </system.serviceModel>  
    ```  
  
     <span data-ttu-id="5f2a0-113">İzleme profilleri hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5f2a0-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="5f2a0-114">Genel olarak izleme hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="5f2a0-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="5f2a0-115">Kodda Izlemeyi Yapılandır</span><span class="sxs-lookup"><span data-stu-id="5f2a0-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="5f2a0-116">Aşağıdaki örnekte gösterildiği gibi <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> , koddaki davranışı kullanarakekleyin.<xref:System.Activities.Tracking.EtwTrackingParticipant></span><span class="sxs-lookup"><span data-stu-id="5f2a0-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="5f2a0-117">Önceki kod örneği bir <xref:System.Activities.Tracking.EtwTrackingParticipant> ekler ve bir izleme profili adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="5f2a0-118">İzleme profilleri, önceki bölümde gösterildiği gibi`trackingProfile`bir <`tracking`> öğesi içindeki bir < > öğesinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="5f2a0-119">İzleme profilleri hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5f2a0-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="5f2a0-120">Genel olarak izleme hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="5f2a0-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="5f2a0-121">Program aracılığıyla izlemeyi yapılandırmaya yönelik bir örnek için bkz. [bir Iş akışı Için Izlemeyi yapılandırma](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="5f2a0-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f2a0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f2a0-122">See also</span></span>

- [<span data-ttu-id="5f2a0-123">WCF Hizmetleri için Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5f2a0-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="5f2a0-124">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="5f2a0-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="5f2a0-125">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="5f2a0-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
