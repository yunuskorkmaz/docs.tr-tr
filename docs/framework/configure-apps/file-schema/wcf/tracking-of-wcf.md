---
title: <tracking>WCF
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: ad4f85139ff0a0f587bc47f63334fe97e25440b0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932370"
---
# <a name="tracking-of-wcf"></a><span data-ttu-id="d6cf9-102">\<WCF > izleme</span><span class="sxs-lookup"><span data-stu-id="d6cf9-102">\<tracking> of WCF</span></span>
<span data-ttu-id="d6cf9-103">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6cf9-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="d6cf9-104">İş akışı izleme ve yapılandırması hakkında daha fazla bilgi için bkz. iş akışı [izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme yapılandırma](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="d6cf9-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
 <span data-ttu-id="d6cf9-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d6cf9-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d6cf9-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="d6cf9-106">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6cf9-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6cf9-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6cf9-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6cf9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d6cf9-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d6cf9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6cf9-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d6cf9-110">Attributes</span></span>  
 <span data-ttu-id="d6cf9-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="d6cf9-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d6cf9-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6cf9-112">Child Elements</span></span>  
  
|<span data-ttu-id="d6cf9-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="d6cf9-113">Element</span></span>|<span data-ttu-id="d6cf9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6cf9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6cf9-115">\<Katılımcılar ></span><span class="sxs-lookup"><span data-stu-id="d6cf9-115">\<participants></span></span>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="d6cf9-116">Kayıtları izlemeye abone olan katılımcıları tanımlayan bir yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d6cf9-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="d6cf9-117">İzleme katılımcıları, izleme kayıtlarından yükü işlemeye yönelik mantığı içerir (örneğin, bir dosyaya yazmayı seçebilirler).</span><span class="sxs-lookup"><span data-stu-id="d6cf9-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="d6cf9-118">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="d6cf9-118">\<trackingProfile></span></span>](../windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="d6cf9-119">Bir iş akışı örneğinden yayılan izleme kayıtlarını filtrelemek için bir izleme profili.</span><span class="sxs-lookup"><span data-stu-id="d6cf9-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6cf9-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6cf9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d6cf9-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="d6cf9-121">Element</span></span>|<span data-ttu-id="d6cf9-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6cf9-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6cf9-123">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d6cf9-123">system.ServiceModel</span></span>|<span data-ttu-id="d6cf9-124">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d6cf9-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6cf9-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6cf9-125">Remarks</span></span>  
 <span data-ttu-id="d6cf9-126">İzleme, bir iş akışının yürütülmesini incelemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6cf9-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="d6cf9-127">İş akışı izleme altyapısı, yürütme sırasında önemli olayları yansıtan kayıtları göstermek için bir iş akışı araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6cf9-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="d6cf9-128">Örneğin, bir iş akışı örneği başlatıldığında ya da tamamlandığında izleme kayıtları yayınlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d6cf9-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="d6cf9-129">İzleme, iş akışı değişkenleriyle ilişkili iş ile ilgili verileri de ayıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="d6cf9-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="d6cf9-130">Örneğin, iş akışı bir sipariş işleme sistemini temsil ediyorsa, sipariş kimliği izleme kaydıyla birlikte ayıklanabilir.</span><span class="sxs-lookup"><span data-stu-id="d6cf9-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="d6cf9-131">Genel olarak, WF izlemeyi etkinleştirmek, bir iş akışı yürütmesi üzerinde tanılamayı veya iş analizlerini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d6cf9-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6cf9-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6cf9-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="d6cf9-133">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="d6cf9-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
