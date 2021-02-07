---
description: 'Hakkında daha fazla bilgi edinin: <tracking>'
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 6301d3c6e472010e3ab78f7d85193f17adb15a1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739748"
---
# \<tracking>

<span data-ttu-id="3b37e-102">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3b37e-102">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="3b37e-103">İş akışı izleme ve yapılandırması hakkında daha fazla bilgi için bkz. iş akışı [izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme yapılandırma](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="3b37e-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**  
  
## <a name="syntax"></a><span data-ttu-id="3b37e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3b37e-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b37e-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b37e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3b37e-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b37e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b37e-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3b37e-107">Attributes</span></span>  

 <span data-ttu-id="3b37e-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="3b37e-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3b37e-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b37e-109">Child Elements</span></span>  
  
|<span data-ttu-id="3b37e-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="3b37e-110">Element</span></span>|<span data-ttu-id="3b37e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b37e-111">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](participants.md)|<span data-ttu-id="3b37e-112">Kayıtları izlemeye abone olan katılımcıları tanımlayan bir yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3b37e-112">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="3b37e-113">İzleme katılımcıları, izleme kayıtlarından yükü işlemeye yönelik mantığı içerir (örneğin, bir dosyaya yazmayı seçebilirler).</span><span class="sxs-lookup"><span data-stu-id="3b37e-113">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[\<trackingProfile>](trackingprofile.md)|<span data-ttu-id="3b37e-114">Bir iş akışı örneğinden yayılan izleme kayıtlarını filtrelemek için bir izleme profili.</span><span class="sxs-lookup"><span data-stu-id="3b37e-114">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3b37e-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b37e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="3b37e-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="3b37e-116">Element</span></span>|<span data-ttu-id="3b37e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b37e-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3b37e-118">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3b37e-118">system.ServiceModel</span></span>|<span data-ttu-id="3b37e-119">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3b37e-119">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b37e-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b37e-120">Remarks</span></span>  

 <span data-ttu-id="3b37e-121">İzleme, bir iş akışının yürütülmesini incelemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b37e-121">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="3b37e-122">İş akışı izleme altyapısı, yürütme sırasında önemli olayları yansıtan kayıtları göstermek için bir iş akışı araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b37e-122">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="3b37e-123">Örneğin, bir iş akışı örneği başlatıldığında ya da tamamlandığında izleme kayıtları yayınlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b37e-123">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="3b37e-124">İzleme, iş akışı değişkenleriyle ilişkili iş ile ilgili verileri de ayıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="3b37e-124">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="3b37e-125">Örneğin, iş akışı bir sipariş işleme sistemini temsil ediyorsa, sipariş kimliği izleme kaydıyla birlikte ayıklanabilir.</span><span class="sxs-lookup"><span data-stu-id="3b37e-125">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="3b37e-126">Genel olarak, WF izlemeyi etkinleştirmek, bir iş akışı yürütmesi üzerinde tanılamayı veya iş analizlerini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3b37e-126">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b37e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b37e-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="3b37e-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="3b37e-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
