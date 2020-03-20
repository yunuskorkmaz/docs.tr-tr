---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 968cfa8e5402458afd6f13545ed999a472adf2e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151916"
---
# <a name="tracking"></a><span data-ttu-id="8c680-101">\<izleme></span><span class="sxs-lookup"><span data-stu-id="8c680-101">\<tracking></span></span>
<span data-ttu-id="8c680-102">İş akışı hizmeti için izleme ayarlarını tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8c680-102">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="8c680-103">İş akışı izleme ve yapılandırmasında daha fazla bilgi için [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md) [bkz.](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="8c680-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="8c680-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8c680-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8c680-105">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="8c680-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="8c680-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<izleme>**</span><span class="sxs-lookup"><span data-stu-id="8c680-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c680-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c680-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c680-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8c680-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8c680-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8c680-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c680-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8c680-110">Attributes</span></span>  
 <span data-ttu-id="8c680-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="8c680-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8c680-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8c680-112">Child Elements</span></span>  
  
|<span data-ttu-id="8c680-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="8c680-113">Element</span></span>|<span data-ttu-id="8c680-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c680-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c680-115">\<katılımcılar></span><span class="sxs-lookup"><span data-stu-id="8c680-115">\<participants></span></span>](participants.md)|<span data-ttu-id="8c680-116">İzleme kayıtlarına abone olan katılımcıları tanımlayan yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8c680-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="8c680-117">İzleme katılımcıları, izleme kayıtlarından yükü işlemek için gereken mantığı içerir (örneğin, bir dosyaya yazmayı seçebilirler).</span><span class="sxs-lookup"><span data-stu-id="8c680-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="8c680-118">\<izlemeProfil></span><span class="sxs-lookup"><span data-stu-id="8c680-118">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="8c680-119">İş akışı örneğinden yayılan izleme kayıtlarını filtrelemek için izleme profili.</span><span class="sxs-lookup"><span data-stu-id="8c680-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8c680-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8c680-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8c680-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="8c680-121">Element</span></span>|<span data-ttu-id="8c680-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c680-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c680-123">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8c680-123">system.ServiceModel</span></span>|<span data-ttu-id="8c680-124">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="8c680-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c680-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c680-125">Remarks</span></span>  
 <span data-ttu-id="8c680-126">İzleme, iş akışının yürütülmesini inceleme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c680-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="8c680-127">İş akışı izleme altyapısı, yürütme sırasında ki önemli olayları yansıtan kayıtları yayacak bir iş akışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c680-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="8c680-128">Örneğin, bir iş akışı örneği başlatıldığında veya izleme kayıtlarını tamamladığında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="8c680-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="8c680-129">İzleme, iş akışı değişkenleriyle ilişkili iş ile ilgili verileri de ayıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="8c680-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="8c680-130">Örneğin, iş akışı bir sipariş işleme sistemini temsil ediyorsa, sipariş kimliği izleme kaydıyla birlikte ayıklanabilir.</span><span class="sxs-lookup"><span data-stu-id="8c680-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="8c680-131">Genel olarak, WF izlemeyi etkinleştirmek, iş akışı yürütmesi üzerinden tanılamayı veya iş analitiğini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="8c680-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c680-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c680-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="8c680-133">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="8c680-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
