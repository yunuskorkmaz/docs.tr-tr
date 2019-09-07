---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 28d73bb74c4a49052589040adc26194b1300668c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397599"
---
# <a name="tracking"></a><span data-ttu-id="d9f1b-101">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="d9f1b-101">\<tracking></span></span>
<span data-ttu-id="d9f1b-102">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d9f1b-102">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="d9f1b-103">İş akışı izleme ve yapılandırması hakkında daha fazla bilgi için bkz. iş akışı [izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme yapılandırma](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="d9f1b-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="d9f1b-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d9f1b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d9f1b-105">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d9f1b-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="d9f1b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<İzleme >**</span><span class="sxs-lookup"><span data-stu-id="d9f1b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9f1b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9f1b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9f1b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9f1b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d9f1b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d9f1b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9f1b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d9f1b-110">Attributes</span></span>  
 <span data-ttu-id="d9f1b-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="d9f1b-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d9f1b-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9f1b-112">Child Elements</span></span>  
  
|<span data-ttu-id="d9f1b-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9f1b-113">Element</span></span>|<span data-ttu-id="d9f1b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9f1b-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9f1b-115">\<Katılımcılar ></span><span class="sxs-lookup"><span data-stu-id="d9f1b-115">\<participants></span></span>](participants.md)|<span data-ttu-id="d9f1b-116">Kayıtları izlemeye abone olan katılımcıları tanımlayan bir yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d9f1b-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="d9f1b-117">İzleme katılımcıları, izleme kayıtlarından yükü işlemeye yönelik mantığı içerir (örneğin, bir dosyaya yazmayı seçebilirler).</span><span class="sxs-lookup"><span data-stu-id="d9f1b-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="d9f1b-118">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="d9f1b-118">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="d9f1b-119">Bir iş akışı örneğinden yayılan izleme kayıtlarını filtrelemek için bir izleme profili.</span><span class="sxs-lookup"><span data-stu-id="d9f1b-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9f1b-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9f1b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d9f1b-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9f1b-121">Element</span></span>|<span data-ttu-id="d9f1b-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9f1b-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9f1b-123">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d9f1b-123">system.ServiceModel</span></span>|<span data-ttu-id="d9f1b-124">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d9f1b-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9f1b-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9f1b-125">Remarks</span></span>  
 <span data-ttu-id="d9f1b-126">İzleme, bir iş akışının yürütülmesini incelemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9f1b-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="d9f1b-127">İş akışı izleme altyapısı, yürütme sırasında önemli olayları yansıtan kayıtları göstermek için bir iş akışı araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9f1b-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="d9f1b-128">Örneğin, bir iş akışı örneği başlatıldığında ya da tamamlandığında izleme kayıtları yayınlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d9f1b-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="d9f1b-129">İzleme, iş akışı değişkenleriyle ilişkili iş ile ilgili verileri de ayıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="d9f1b-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="d9f1b-130">Örneğin, iş akışı bir sipariş işleme sistemini temsil ediyorsa, sipariş kimliği izleme kaydıyla birlikte ayıklanabilir.</span><span class="sxs-lookup"><span data-stu-id="d9f1b-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="d9f1b-131">Genel olarak, WF izlemeyi etkinleştirmek, bir iş akışı yürütmesi üzerinde tanılamayı veya iş analizlerini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d9f1b-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9f1b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9f1b-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="d9f1b-133">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="d9f1b-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
