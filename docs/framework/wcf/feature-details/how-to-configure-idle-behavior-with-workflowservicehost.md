---
title: 'Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: a676f03b4e6f9dd210b843a6f3bf00c735889500
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330161"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="9bbdc-102">Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9bbdc-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="9bbdc-103">İş akışı örneği kullanarak teslim edilecek bir ileti için beklediği sırada örneğin dış bazı stimulus tarafından sürdürülmesini bir yer işareti karşılaştıkları olduğunda iş akışları boş Git bir <xref:System.ServiceModel.Activities.Receive> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> <span data-ttu-id="9bbdc-104">bir hizmet örneği boşta gittiğinde arasında ve örneği kalıcı ya da kaldırıldığında zaman belirtmenizi sağlar bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-104">is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="9bbdc-105">Bu, bu zaman aralıkları ayarlamanıza olanak tanır, iki özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-105">It contains two properties that enable you to set these time spans.</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> <span data-ttu-id="9bbdc-106">bir iş akışı hizmet örneği boşta gittiğinde ve ne zaman iş akışı hizmet örneği kalıcıdır arasındaki zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-106">specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> <span data-ttu-id="9bbdc-107">İş akışı hizmet örneği kaldırıldığında, burada kaldırma örnek deposuna örneği kalıcı ve bellekten kaldırılıyor anlamına gelir ve ne zaman bir iş akışı hizmet örneği arasındaki zaman aralığını boşta giden belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-107">specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="9bbdc-108">Bu konu nasıl yapılandırılacağını açıklar <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="9bbdc-109">WorkflowIdleBehavior yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="9bbdc-109">To configure WorkflowIdleBehavior</span></span>  
  
1. <span data-ttu-id="9bbdc-110">Ekleme bir <`workflowIdle`> öğesi <`behavior`> öğesi içinde <`serviceBehaviors`> Aşağıdaki örnekte gösterildiği gibi bir öğe.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="9bbdc-111">`timeToUnload` Özniteliği, bir iş akışı hizmet örneği boşta gittiğinde ve iş akışı hizmeti yüklenmemiş olduğunda arasındaki süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="9bbdc-112">`timeToPersist` Özniteliği, bir iş akışı hizmet örneği boşta gittiğinde ve ne zaman iş akışı hizmet örneği kalıcıdır arasındaki süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="9bbdc-113">İçin varsayılan değer `timeToUnload` 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="9bbdc-114">İçin varsayılan değer `timeToPersist` olduğu <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="9bbdc-115">Boşta örnekleri bellekte tut ancak sağlamlık için kalıcı hale getirmek istiyorsanız, değerleri ayarlamak için `timeToPersist`  <  `timeToUnload`.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="9bbdc-116">Öğesinden kaldırılıyor boşta örnekleri önlemek istiyorsanız `timeToUnload` için <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="9bbdc-117">Hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, bkz: [iş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="9bbdc-117">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bbdc-118">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="9bbdc-119">Daha fazla bilgi için [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="9bbdc-119">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="9bbdc-120">Kodda boşta davranışı değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="9bbdc-120">To change idle behavior in code</span></span>  
  
-   <span data-ttu-id="9bbdc-121">Aşağıdaki örnekte, program aracılığıyla kaldırma ve devam ettirmeden önce beklenecek süreyi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9bbdc-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bbdc-122">See also</span></span>

- [<span data-ttu-id="9bbdc-123">İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="9bbdc-123">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="9bbdc-124">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9bbdc-124">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="9bbdc-125">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="9bbdc-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
