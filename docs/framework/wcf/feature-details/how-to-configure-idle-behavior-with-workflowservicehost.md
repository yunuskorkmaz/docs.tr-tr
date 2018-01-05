---
title: "Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1a0d0d4a8b99a6c0536bba8371234f8d46bc1dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="d46e0-102">Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d46e0-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="d46e0-103">İş akışı örneği bir ileti kullanılarak teslim edilebilir beklenirken örneğin bazı dış stimulus tarafından sürdürüldü gerekir bir yer işareti karşılaştığınızda iş akışları boşta Git bir <xref:System.ServiceModel.Activities.Receive> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d46e0-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="d46e0-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>bir hizmet örneği boşta gittiğinde arasında ve örnek kalıcı ya da kaldırıldığında süreyi belirtmek üzere izin veren bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="d46e0-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="d46e0-105">Bu zaman aralıkları ayarlamanıza olanak tanır iki özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="d46e0-105">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="d46e0-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>bir iş akışı hizmeti örneği boşta gittiğinde ve ne zaman iş akışı hizmeti örneği kalıcı arasındaki zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d46e0-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="d46e0-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>ne zaman bir iş akışı hizmeti örneği arasında zaman aralığı boşta gider ve iş akışı hizmeti örneği kaldırıldığında, burada unload örnek deposuna örnek kalıcı bellekten kaldırılıyor anlamına gelir ve belirtir.</span><span class="sxs-lookup"><span data-stu-id="d46e0-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="d46e0-108">Bu konuda nasıl yapılandırılacağını açıklar <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="d46e0-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="d46e0-109">WorkflowIdleBehavior yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="d46e0-109">To configure WorkflowIdleBehavior</span></span>  
  
1.  <span data-ttu-id="d46e0-110">Ekleme bir <`workflowIdle`> öğesi <`behavior`> öğesi içinde <`serviceBehaviors`> Aşağıdaki örnekte gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="d46e0-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="d46e0-111">`timeToUnload` Özniteliği, bir iş akışı hizmeti örneği boşta gittiğinde ve iş akışı hizmeti kaldırılmış olduğunda arasındaki süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d46e0-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="d46e0-112">`timeToPersist` Özniteliği, bir iş akışı hizmeti örneği boşta gittiğinde ve ne zaman iş akışı hizmeti örneği kalıcı arasındaki süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d46e0-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="d46e0-113">İçin varsayılan değer `timeToUnload` 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="d46e0-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="d46e0-114">İçin varsayılan değer `timeToPersist` olan <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="d46e0-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="d46e0-115">Boşta örnekleri bellekte tut ancak bunları için sağlamlık kalıcı hale getirmek istiyorsanız, değerleri ayarlamak için `timeToPersist`  <  `timeToUnload`.</span><span class="sxs-lookup"><span data-stu-id="d46e0-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="d46e0-116">Boşta örnekleri bellekten kaldırılan engellemek istiyorsanız, Ayarla `timeToUnload` için <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="d46e0-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d46e0-117"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, bkz: [iş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="d46e0-117"> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d46e0-118">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="d46e0-118">The preceding configuration sample is using simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="d46e0-119">[Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d46e0-119"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="d46e0-120">Kodda boşta davranışı değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="d46e0-120">To change idle behavior in code</span></span>  
  
-   <span data-ttu-id="d46e0-121">Aşağıdaki örnek kalıcı yapma ve program aracılığıyla kaldırılması önce beklenecek süreyi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d46e0-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d46e0-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d46e0-122">See Also</span></span>  
 [<span data-ttu-id="d46e0-123">İş Akışı Hizmeti Konak Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="d46e0-123">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [<span data-ttu-id="d46e0-124">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d46e0-124">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="d46e0-125">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d46e0-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
