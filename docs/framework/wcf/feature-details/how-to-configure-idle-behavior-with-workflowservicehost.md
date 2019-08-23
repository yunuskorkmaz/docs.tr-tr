---
title: 'Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 57a9e0487ff605e99adc22471b02f5a288fc4a2b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912150"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="042fe-102">Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="042fe-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="042fe-103">İş akışları, bazı dış Camulus tarafından devam edilmesi gereken bir yer işaretiyle karşılaştıklarında boşta kalır, örneğin, iş akışı örneği bir <xref:System.ServiceModel.Activities.Receive> etkinliği kullanarak bir ileti teslim edilmesini bekliyorsa.</span><span class="sxs-lookup"><span data-stu-id="042fe-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="042fe-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, bir hizmet örneğinin boşta kaldığı ve örneğin kalıcı veya kaldırılmış olduğu zaman arasındaki süreyi belirtmenize olanak tanıyan bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="042fe-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="042fe-105">Bu zaman yayılmalarını ayarlamanıza olanak tanıyan iki özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="042fe-105">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="042fe-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>bir iş akışı hizmet örneğinin boşta kaldığı ve iş akışı hizmet örneğinin kalıcı olduğu zaman arasındaki süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="042fe-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="042fe-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>bir iş akışı hizmet örneğinin boşta kaldığı ve iş akışı hizmeti örneğinin ne zaman kaldırılabileceği arasındaki süreyi belirtir. burada, kaldırma işlemi örneği örnek deposuna kalıcı hale getiren ve bellekten kaldıran anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="042fe-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="042fe-108">Bu konu, <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> bir yapılandırma dosyasında ' nin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="042fe-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="042fe-109">WorkflowIdleBehavior yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="042fe-109">To configure WorkflowIdleBehavior</span></span>  
  
1. <span data-ttu-id="042fe-110">Aşağıdaki örnekte gösterildiği`workflowIdle`gibi, <`serviceBehaviors`> öğesi`behavior`içindeki < > öğesine bir < > öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="042fe-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="042fe-111">`timeToUnload` Öznitelik, bir iş akışı hizmeti örneğinin boşta kalma süresi ve iş akışı hizmeti kaldırıldığında arasındaki süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="042fe-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="042fe-112">`timeToPersist` Öznitelik, bir iş akışı hizmet örneğinin boşta kaldığı ve iş akışı hizmet örneğinin kalıcı olduğu zaman arasındaki süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="042fe-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="042fe-113">İçin `timeToUnload` varsayılan değer 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="042fe-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="042fe-114">`timeToPersist` İçin<xref:System.TimeSpan.MaxValue>varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="042fe-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="042fe-115">Boştaki örnekleri bellekte tutmak, ancak bunları sağlamlık için kalıcı hale getirmek istiyorsanız değerlerini `timeToPersist`  <  `timeToUnload`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="042fe-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="042fe-116">Boş örneklerin bellekten kaldırılmasını engellemek istiyorsanız, olarak `timeToUnload` <xref:System.TimeSpan.MaxValue>ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="042fe-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="042fe-117">Hakkında <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>daha fazla bilgi için bkz. [iş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="042fe-117">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="042fe-118">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="042fe-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="042fe-119">Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="042fe-119">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="042fe-120">Koddaki boşta davranışını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="042fe-120">To change idle behavior in code</span></span>  
  
- <span data-ttu-id="042fe-121">Aşağıdaki örnek, programlı bir şekilde kalıcı ve kaldırmadan önce beklenecek süreyi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="042fe-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="042fe-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="042fe-122">See also</span></span>

- [<span data-ttu-id="042fe-123">İş Akışı Hizmeti Konak Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="042fe-123">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="042fe-124">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="042fe-124">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="042fe-125">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="042fe-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
