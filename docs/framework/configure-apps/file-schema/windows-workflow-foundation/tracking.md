---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 79230c65d8eb8c15cef5dce73698448ca7b1e003
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947309"
---
# <a name="tracking"></a><span data-ttu-id="005ae-101">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="005ae-101">\<tracking></span></span>
<span data-ttu-id="005ae-102">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="005ae-102">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="005ae-103">İş akışı izleme ve yapılandırması hakkında daha fazla bilgi için bkz. iş akışı [izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme yapılandırma](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="005ae-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="005ae-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="005ae-104">\<system.serviceModel></span></span>  
<span data-ttu-id="005ae-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="005ae-105">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="005ae-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="005ae-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String" 
             profileName="String" 
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String" 
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
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
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="005ae-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="005ae-107">Attributes and Elements</span></span>  
 <span data-ttu-id="005ae-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="005ae-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="005ae-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="005ae-109">Attributes</span></span>  
 <span data-ttu-id="005ae-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="005ae-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="005ae-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="005ae-111">Child Elements</span></span>  
  
|<span data-ttu-id="005ae-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="005ae-112">Element</span></span>|<span data-ttu-id="005ae-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="005ae-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="005ae-114">\<Katılımcılar ></span><span class="sxs-lookup"><span data-stu-id="005ae-114">\<participants></span></span>](participants.md)|<span data-ttu-id="005ae-115">Kayıtları izlemeye abone olan katılımcıları tanımlayan bir yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="005ae-115">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="005ae-116">İzleme katılımcıları, izleme kayıtlarından yükü işlemeye yönelik mantığı içerir (örneğin, bir dosyaya yazmayı seçebilirler).</span><span class="sxs-lookup"><span data-stu-id="005ae-116">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="005ae-117">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="005ae-117">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="005ae-118">Bir iş akışı örneğinden yayılan izleme kayıtlarını filtrelemek için bir izleme profili.</span><span class="sxs-lookup"><span data-stu-id="005ae-118">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="005ae-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="005ae-119">Parent Elements</span></span>  
  
|<span data-ttu-id="005ae-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="005ae-120">Element</span></span>|<span data-ttu-id="005ae-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="005ae-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="005ae-122">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="005ae-122">system.ServiceModel</span></span>|<span data-ttu-id="005ae-123">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="005ae-123">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="005ae-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="005ae-124">Remarks</span></span>  
 <span data-ttu-id="005ae-125">İzleme, bir iş akışının yürütülmesini incelemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="005ae-125">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="005ae-126">İş akışı izleme altyapısı, yürütme sırasında önemli olayları yansıtan kayıtları göstermek için bir iş akışı araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="005ae-126">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="005ae-127">Örneğin, bir iş akışı örneği başlatıldığında ya da tamamlandığında izleme kayıtları yayınlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="005ae-127">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="005ae-128">İzleme, iş akışı değişkenleriyle ilişkili iş ile ilgili verileri de ayıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="005ae-128">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="005ae-129">Örneğin, iş akışı bir sipariş işleme sistemini temsil ediyorsa, sipariş kimliği izleme kaydıyla birlikte ayıklanabilir.</span><span class="sxs-lookup"><span data-stu-id="005ae-129">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="005ae-130">Genel olarak, WF izlemeyi etkinleştirmek, bir iş akışı yürütmesi üzerinde tanılamayı veya iş analizlerini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="005ae-130">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="005ae-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="005ae-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="005ae-132">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="005ae-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
