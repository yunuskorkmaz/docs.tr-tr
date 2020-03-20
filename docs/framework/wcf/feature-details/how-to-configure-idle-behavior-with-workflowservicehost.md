---
title: 'Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 67be47f97e57792e2f1e14505d3cd121729db33b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185076"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="04f44-102">Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04f44-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="04f44-103">İş akışları, örneğin iş akışı örneği bir <xref:System.ServiceModel.Activities.Receive> etkinlik kullanılarak iletinin teslim edilmesini beklerken, bazı dış uyaranlar tarafından başlatılması gereken bir yer işaretiyle karşılaştıklarında boşta kalır.</span><span class="sxs-lookup"><span data-stu-id="04f44-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="04f44-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>bir hizmet örneğinin boşta kalma süresi ile örneğin kalıcı veya boşaltılan saat arasındaki süreyi belirtmenize olanak tanıyan bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="04f44-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="04f44-105">Bu zaman aralıklarını ayarlamanızı sağlayan iki özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="04f44-105">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="04f44-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span><span class="sxs-lookup"><span data-stu-id="04f44-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="04f44-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>bir iş akışı hizmeti örneğinin boşta kaldığı zaman ile iş akışı hizmeti örneğinin boşaltılması arasındaki zaman aralığını belirtir, burada boşaltma örneği örnek deposuna devam etmek ve bellekten kaldırmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="04f44-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="04f44-108">Bu konu, yapılandırma dosyasında nasıl yapılandırılabildiğini <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> açıklar.</span><span class="sxs-lookup"><span data-stu-id="04f44-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="04f44-109">İş akışını yapılandırmak içinIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="04f44-109">To configure WorkflowIdleBehavior</span></span>  
  
1. <span data-ttu-id="04f44-110">Aşağıdaki örnekte gösterildiği gibi `behavior` <`serviceBehaviors`> öğesi içinde <> öğesine <`workflowIdle` bir> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="04f44-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="04f44-111">Öznitelik, `timeToUnload` iş akışı hizmeti örneğinin boşta yatması ile iş akışı hizmetinin boşaltılması arasındaki süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="04f44-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="04f44-112">Öznitelik, `timeToPersist` iş akışı hizmeti örneğinin boşta yatması ile iş akışı hizmeti örneğinin kalıcı olması arasındaki süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="04f44-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="04f44-113">Varsayılan değer `timeToUnload` 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="04f44-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="04f44-114">Varsayılan <xref:System.TimeSpan.MaxValue>değer. `timeToPersist`</span><span class="sxs-lookup"><span data-stu-id="04f44-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="04f44-115">Boşta kalan örnekleri bellekte tutmak, ancak sağlamlık için devam `timeToPersist`  <  `timeToUnload`ettirmek istiyorsanız, değerleri şu şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="04f44-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="04f44-116">Boşta kalan örneklerin yüklenmesini önlemek istiyorsanız, <xref:System.TimeSpan.MaxValue>'' olarak ayarlayın `timeToUnload`</span><span class="sxs-lookup"><span data-stu-id="04f44-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="04f44-117">Hakkında <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>daha fazla bilgi için Bkz. [İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="04f44-117">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="04f44-118">Önceki yapılandırma örneği basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="04f44-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="04f44-119">Daha fazla bilgi için Bkz. [Basitleştirilmiş Yapılandırma.](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="04f44-119">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="04f44-120">Koddaki boşta davranışı değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="04f44-120">To change idle behavior in code</span></span>  
  
- <span data-ttu-id="04f44-121">Aşağıdaki örnek, kalıcı olarak bekletmeden ve programlı olarak boşaltmadan önce bekleme süresini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="04f44-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="04f44-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04f44-122">See also</span></span>

- [<span data-ttu-id="04f44-123">İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="04f44-123">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="04f44-124">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04f44-124">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="04f44-125">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="04f44-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
