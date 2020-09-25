---
title: <tracking> WCF
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: 223a30cd79d346d6ae36ca64fa887a683e6bfc8d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201440"
---
# <a name="tracking-of-wcf"></a><span data-ttu-id="cee97-102">\<tracking> WCF</span><span class="sxs-lookup"><span data-stu-id="cee97-102">\<tracking> of WCF</span></span>

<span data-ttu-id="cee97-103">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cee97-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="cee97-104">İş akışı izleme ve yapılandırması hakkında daha fazla bilgi için bkz. iş akışı [izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme yapılandırma](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="cee97-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**  
  
## <a name="syntax"></a><span data-ttu-id="cee97-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cee97-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <participants>
      <add name="String"
           profileName="String"
           type="String" />
    </participants>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String"/>
            </arguments>
            <states>
              <state name="String"/>
            </states>
            <variables>
              <variable name="String"/>
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String"
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String"
                                   faultHandlerActivityName="String"/>
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cee97-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cee97-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cee97-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cee97-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cee97-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cee97-108">Attributes</span></span>  

 <span data-ttu-id="cee97-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="cee97-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cee97-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cee97-110">Child Elements</span></span>  
  
|<span data-ttu-id="cee97-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="cee97-111">Element</span></span>|<span data-ttu-id="cee97-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cee97-112">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="cee97-113">Kayıtları izlemeye abone olan katılımcıları tanımlayan bir yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="cee97-113">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="cee97-114">İzleme katılımcıları, izleme kayıtlarından yükü işlemeye yönelik mantığı içerir (örneğin, bir dosyaya yazmayı seçebilirler).</span><span class="sxs-lookup"><span data-stu-id="cee97-114">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[\<trackingProfile>](../windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="cee97-115">Bir iş akışı örneğinden yayılan izleme kayıtlarını filtrelemek için bir izleme profili.</span><span class="sxs-lookup"><span data-stu-id="cee97-115">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cee97-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cee97-116">Parent Elements</span></span>  
  
|<span data-ttu-id="cee97-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="cee97-117">Element</span></span>|<span data-ttu-id="cee97-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cee97-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cee97-119">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cee97-119">system.ServiceModel</span></span>|<span data-ttu-id="cee97-120">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="cee97-120">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cee97-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cee97-121">Remarks</span></span>  

 <span data-ttu-id="cee97-122">İzleme, bir iş akışının yürütülmesini incelemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cee97-122">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="cee97-123">İş akışı izleme altyapısı, yürütme sırasında önemli olayları yansıtan kayıtları göstermek için bir iş akışı araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="cee97-123">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="cee97-124">Örneğin, bir iş akışı örneği başlatıldığında ya da tamamlandığında izleme kayıtları yayınlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cee97-124">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="cee97-125">İzleme, iş akışı değişkenleriyle ilişkili iş ile ilgili verileri de ayıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="cee97-125">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="cee97-126">Örneğin, iş akışı bir sipariş işleme sistemini temsil ediyorsa, sipariş kimliği izleme kaydıyla birlikte ayıklanabilir.</span><span class="sxs-lookup"><span data-stu-id="cee97-126">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="cee97-127">Genel olarak, WF izlemeyi etkinleştirmek, bir iş akışı yürütmesi üzerinde tanılamayı veya iş analizlerini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="cee97-127">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cee97-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cee97-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="cee97-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="cee97-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
