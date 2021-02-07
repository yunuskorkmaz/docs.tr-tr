---
description: 'Daha fazla bilgi edinin: nasıl yapılır: WorkflowServiceHost ile Izlemeyi yapılandırma'
title: 'Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 11c48c3989ab9b788c1e6834d8cbfe53e2b8a53e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734834"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="62daf-103">Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="62daf-103">How to: Configure Tracking with WorkflowServiceHost</span></span>

<span data-ttu-id="62daf-104">Bu konu başlığında barındırılan bir iş akışı için izlemenin nasıl yapılandırılacağı açıklanmaktadır [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="62daf-104">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="62daf-105">Bir hizmet davranışı belirtilerek bir Web.config dosyası aracılığıyla yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="62daf-105">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="62daf-106">Yapılandırmada Izlemeyi Yapılandır</span><span class="sxs-lookup"><span data-stu-id="62daf-106">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="62daf-107"><xref:System.Activities.Tracking.EtwTrackingParticipant> `behavior` Aşağıdaki örnekte gösterildiği gibi, bir yapılandırma dosyasında <> öğesini kullanarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="62daf-107">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="62daf-108">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="62daf-108">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="62daf-109">Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="62daf-109">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="62daf-110">Önceki yapılandırma örneği bir ekler <xref:System.Activities.Tracking.EtwTrackingParticipant> ve bir izleme profili adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="62daf-110">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="62daf-111">İzleme profilleri, bir `trackingProfile` <> öğesi içindeki bir <> öğesinde oluşturulur `tracking` .</span><span class="sxs-lookup"><span data-stu-id="62daf-111">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="62daf-112">İzleme profili, çalışma zamanında bir iş akışı örneği durumu değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="62daf-112">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="62daf-113">Aşağıdaki örnek, bir izleme profilinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="62daf-113">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     <span data-ttu-id="62daf-114">İzleme profilleri hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="62daf-114">For more information about tracking profiles, see [Tracking Profiles](../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="62daf-115">Genel olarak izleme hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="62daf-115">For more information about tracking in general, see [Workflow Tracking and Tracing](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="62daf-116">Kodda Izlemeyi Yapılandır</span><span class="sxs-lookup"><span data-stu-id="62daf-116">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="62daf-117"><xref:System.Activities.Tracking.EtwTrackingParticipant> <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> Aşağıdaki örnekte gösterildiği gibi, koddaki davranışı kullanarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="62daf-117">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="62daf-118">Önceki kod örneği bir ekler <xref:System.Activities.Tracking.EtwTrackingParticipant> ve bir izleme profili adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="62daf-118">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="62daf-119">İzleme profilleri, `trackingProfile` `tracking` önceki bölümde gösterildiği gibi bir <> öğesi içindeki bir <> öğesinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="62daf-119">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="62daf-120">İzleme profilleri hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="62daf-120">For more information about tracking profiles, see [Tracking Profiles](../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="62daf-121">Genel olarak izleme hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="62daf-121">For more information about tracking in general, see [Workflow Tracking and Tracing](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="62daf-122">Program aracılığıyla izlemeyi yapılandırmaya yönelik bir örnek için bkz. [bir Iş akışı Için Izlemeyi yapılandırma](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="62daf-122">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62daf-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62daf-123">See also</span></span>

- [<span data-ttu-id="62daf-124">WCF Hizmetleri için Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="62daf-124">Simplified Configuration for WCF Services</span></span>](../samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="62daf-125">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="62daf-125">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="62daf-126">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="62daf-126">Tracking Profiles</span></span>](../../windows-workflow-foundation/tracking-profiles.md)
