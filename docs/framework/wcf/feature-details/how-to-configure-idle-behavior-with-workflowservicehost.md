---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: WorkflowServiceHost ile boşta davranışı yapılandırma'
title: 'Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 530ab1833f3f8bb91d39b19161070bc75c45f11a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780056"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="f6f56-103">Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f6f56-103">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>

<span data-ttu-id="f6f56-104">İş akışları, bazı dış Camulus tarafından devam edilmesi gereken bir yer işaretiyle karşılaştıklarında boşta kalır, örneğin, iş akışı örneği bir etkinliği kullanarak bir ileti teslim edilmesini bekliyorsa <xref:System.ServiceModel.Activities.Receive> .</span><span class="sxs-lookup"><span data-stu-id="f6f56-104">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="f6f56-105"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> , bir hizmet örneğinin boşta kaldığı ve örneğin kalıcı veya kaldırılmış olduğu zaman arasındaki süreyi belirtmenize olanak tanıyan bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="f6f56-105"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="f6f56-106">Bu zaman yayılmalarını ayarlamanıza olanak tanıyan iki özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="f6f56-106">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="f6f56-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> bir iş akışı hizmet örneğinin boşta kaldığı ve iş akışı hizmet örneğinin kalıcı olduğu zaman arasındaki süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6f56-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="f6f56-108"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> bir iş akışı hizmet örneğinin boşta kaldığı ve iş akışı hizmeti örneğinin ne zaman kaldırılabileceği arasındaki süreyi belirtir. burada, kaldırma işlemi örneği örnek deposuna kalıcı hale getiren ve bellekten kaldıran anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f6f56-108"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="f6f56-109">Bu konu, <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> bir yapılandırma dosyasında ' nin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f6f56-109">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="f6f56-110">WorkflowIdleBehavior yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="f6f56-110">To configure WorkflowIdleBehavior</span></span>  
  
1. <span data-ttu-id="f6f56-111">`workflowIdle` `behavior` `serviceBehaviors` Aşağıdaki örnekte gösterildiği gibi, <> öğesi içindeki <> öğesine bir <> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6f56-111">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="f6f56-112">`timeToUnload`Öznitelik, bir iş akışı hizmeti örneğinin boşta kalma süresi ve iş akışı hizmeti kaldırıldığında arasındaki süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6f56-112">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="f6f56-113">`timeToPersist`Öznitelik, bir iş akışı hizmet örneğinin boşta kaldığı ve iş akışı hizmet örneğinin kalıcı olduğu zaman arasındaki süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6f56-113">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="f6f56-114">İçin varsayılan değer `timeToUnload` 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="f6f56-114">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="f6f56-115">İçin varsayılan değer `timeToPersist` <xref:System.TimeSpan.MaxValue> .</span><span class="sxs-lookup"><span data-stu-id="f6f56-115">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="f6f56-116">Boştaki örnekleri bellekte tutmak, ancak bunları sağlamlık için kalıcı hale getirmek istiyorsanız değerlerini ayarlayın `timeToPersist`  <  `timeToUnload` .</span><span class="sxs-lookup"><span data-stu-id="f6f56-116">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="f6f56-117">Boş örneklerin bellekten kaldırılmasını engellemek istiyorsanız, `timeToUnload` olarak ayarlayın <xref:System.TimeSpan.MaxValue> .</span><span class="sxs-lookup"><span data-stu-id="f6f56-117">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="f6f56-118">Hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> bkz. [Iş akışı hizmeti konak genişletilebilirliği](workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="f6f56-118">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f6f56-119">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="f6f56-119">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="f6f56-120">Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="f6f56-120">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="f6f56-121">Koddaki boşta davranışını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="f6f56-121">To change idle behavior in code</span></span>  
  
- <span data-ttu-id="f6f56-122">Aşağıdaki örnek, programlı bir şekilde kalıcı ve kaldırmadan önce beklenecek süreyi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f6f56-122">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f6f56-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6f56-123">See also</span></span>

- [<span data-ttu-id="f6f56-124">İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="f6f56-124">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)
- [<span data-ttu-id="f6f56-125">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f6f56-125">Simplified Configuration</span></span>](../simplified-configuration.md)
- [<span data-ttu-id="f6f56-126">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="f6f56-126">Workflow Services</span></span>](workflow-services.md)
