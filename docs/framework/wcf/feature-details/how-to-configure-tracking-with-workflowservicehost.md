---
title: 'Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e1de3349bb9766beeee95b9934fc1ca11fc7006f
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="aa1a3-102">Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aa1a3-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="aa1a3-103">Bu konuda, izleme için yapılandırmak açıklanmaktadır bir [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] iş akışı içinde barındırılan <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="aa1a3-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="aa1a3-104">Bir hizmet davranışı belirterek, bir Web.config dosyası aracılığıyla yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="aa1a3-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="aa1a3-105">İzleme yapılandırmasını</span><span class="sxs-lookup"><span data-stu-id="aa1a3-105">Configure Tracking in Configuration</span></span>  
  
1.  <span data-ttu-id="aa1a3-106">Ekleme <xref:System.Activities.Tracking.EtwTrackingParticipant> kullanarak <`behavior`> öğesi aşağıdaki örnekte gösterildiği gibi bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="aa1a3-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
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
    >  <span data-ttu-id="aa1a3-107">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="aa1a3-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="aa1a3-108">Daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="aa1a3-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="aa1a3-109">Önceki yapılandırma örneği ekler bir <xref:System.Activities.Tracking.EtwTrackingParticipant> ve bir izleme belirtir profil adı.</span><span class="sxs-lookup"><span data-stu-id="aa1a3-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="aa1a3-110">İzleme profilleri oluşturulan bir <`trackingProfile`> öğesinde bir <`tracking`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="aa1a3-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="aa1a3-111">İzleme profili çalışma zamanında bir iş akışı örneğinin durumu değiştiğinde, gösterilen iş akışı olayları abone olmak için izleme katılımcı izin izleme sorgularını içerir.</span><span class="sxs-lookup"><span data-stu-id="aa1a3-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="aa1a3-112">Aşağıdaki örnekte bir izleme profilinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa1a3-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     <span data-ttu-id="aa1a3-113">Profilleri izleme hakkında daha fazla bilgi için bkz: [izleme profilleri](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="aa1a3-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="aa1a3-114">Genel olarak izleme hakkında daha fazla bilgi için bkz: [izleme ve izleme iş akışı](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="aa1a3-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="aa1a3-115">İzleme Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aa1a3-115">Configure Tracking in Code</span></span>  
  
1.  <span data-ttu-id="aa1a3-116">Ekleme <xref:System.Activities.Tracking.EtwTrackingParticipant> kullanarak <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> kodda, aşağıdaki örnekte gösterildiği gibi davranış.</span><span class="sxs-lookup"><span data-stu-id="aa1a3-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="aa1a3-117">Yukarıdaki kod örneğinde ekler bir <xref:System.Activities.Tracking.EtwTrackingParticipant> ve bir izleme belirtir profil adı.</span><span class="sxs-lookup"><span data-stu-id="aa1a3-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="aa1a3-118">İzleme profilleri oluşturulan bir <`trackingProfile`> öğesinde bir <`tracking`> önceki bölümde gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="aa1a3-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="aa1a3-119">Profilleri izleme hakkında daha fazla bilgi için bkz: [izleme profilleri](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="aa1a3-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="aa1a3-120">Genel olarak izleme hakkında daha fazla bilgi için bkz: [izleme ve izleme iş akışı](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="aa1a3-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="aa1a3-121">Program aracılığıyla izleme yapılandırma örneği için bkz: [yapılandırma izleme iş akışı için](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="aa1a3-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa1a3-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa1a3-122">See Also</span></span>  
 [<span data-ttu-id="aa1a3-123">WCF Hizmetleri için Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aa1a3-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)  
 [<span data-ttu-id="aa1a3-124">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="aa1a3-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="aa1a3-125">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="aa1a3-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
