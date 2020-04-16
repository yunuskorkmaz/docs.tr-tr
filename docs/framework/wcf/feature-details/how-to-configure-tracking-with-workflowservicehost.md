---
title: 'Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 3f78b77849d6da7dfff3bdcba90bb4d5200186a7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464152"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="8e5fc-102">Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8e5fc-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="8e5fc-103">Bu konu, 'de [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırılan bir iş akışı için izlemeyi nasıl yapılandırılabildiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="8e5fc-104">Bir hizmet davranışı belirterek bir Web.config dosyası üzerinden yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="8e5fc-105">Yapılandırmada İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8e5fc-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="8e5fc-106">Aşağıdaki <xref:System.Activities.Tracking.EtwTrackingParticipant> örnekte `behavior` gösterildiği gibi, yapılandırma dosyasında <> öğesini kullanarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
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
    > <span data-ttu-id="8e5fc-107">Önceki yapılandırma örneği basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="8e5fc-108">Daha fazla bilgi için Bkz. [Basitleştirilmiş Yapılandırma.](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="8e5fc-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="8e5fc-109">Önceki yapılandırma örneği bir <xref:System.Activities.Tracking.EtwTrackingParticipant> izleme profili adı ekler ve belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="8e5fc-110">İzleme profilleri, <`trackingProfile` `tracking`> öğesi içinde <bir> öğesi nde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="8e5fc-111">İzleme profili, bir izleme katılımcısının çalışma zamanında iş akışı örneği durumu değiştiğinde yayılan iş akışı olaylarına abone olmasını sağlayan izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="8e5fc-112">Aşağıdaki örnekte, izleme profilinin nasıl oluşturuluşu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     <span data-ttu-id="8e5fc-113">İzleme profilleri hakkında daha fazla bilgi için Izleme [Profilleri'ne](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="8e5fc-114">Genel olarak izleme hakkında daha fazla bilgi için [İş Akışı İzleme ve İzleme'ye](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="8e5fc-115">Kodda İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8e5fc-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="8e5fc-116">Aşağıdaki <xref:System.Activities.Tracking.EtwTrackingParticipant> örnekte <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> gösterildiği gibi, koddaki davranışı kullanma ekleme.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="8e5fc-117">Önceki kod örneği a <xref:System.Activities.Tracking.EtwTrackingParticipant> ekler ve bir izleme profili adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="8e5fc-118">İzleme profilleri, önceki bölümde `trackingProfile` gösterildiği gibi `tracking` <> öğesi içindeki <bir> öğesinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="8e5fc-119">İzleme profilleri hakkında daha fazla bilgi için Izleme [Profilleri'ne](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="8e5fc-120">Genel olarak izleme hakkında daha fazla bilgi için [İş Akışı İzleme ve İzleme'ye](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="8e5fc-121">İzlemeyi yapılandırma örneği için [bkz.](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="8e5fc-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e5fc-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e5fc-122">See also</span></span>

- [<span data-ttu-id="8e5fc-123">WCF Hizmetleri için Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8e5fc-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="8e5fc-124">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="8e5fc-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="8e5fc-125">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="8e5fc-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
