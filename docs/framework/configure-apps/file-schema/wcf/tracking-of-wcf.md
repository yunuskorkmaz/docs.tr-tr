---
title: <tracking>WCF
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: e8f74d635299a965b754536234e6be28e4e7a104
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399426"
---
# <a name="tracking-of-wcf"></a><span data-ttu-id="f7076-102">\<WCF > izleme</span><span class="sxs-lookup"><span data-stu-id="f7076-102">\<tracking> of WCF</span></span>
<span data-ttu-id="f7076-103">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f7076-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="f7076-104">İş akışı izleme ve yapılandırması hakkında daha fazla bilgi için bkz. iş akışı [izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme yapılandırma](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="f7076-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="f7076-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f7076-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f7076-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f7076-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f7076-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<İzleme >**</span><span class="sxs-lookup"><span data-stu-id="f7076-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7076-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7076-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7076-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7076-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f7076-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f7076-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7076-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f7076-111">Attributes</span></span>  
 <span data-ttu-id="f7076-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="f7076-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f7076-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7076-113">Child Elements</span></span>  
  
|<span data-ttu-id="f7076-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="f7076-114">Element</span></span>|<span data-ttu-id="f7076-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7076-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7076-116">\<Katılımcılar ></span><span class="sxs-lookup"><span data-stu-id="f7076-116">\<participants></span></span>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="f7076-117">Kayıtları izlemeye abone olan katılımcıları tanımlayan bir yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f7076-117">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="f7076-118">İzleme katılımcıları, izleme kayıtlarından yükü işlemeye yönelik mantığı içerir (örneğin, bir dosyaya yazmayı seçebilirler).</span><span class="sxs-lookup"><span data-stu-id="f7076-118">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="f7076-119">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f7076-119">\<trackingProfile></span></span>](../windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="f7076-120">Bir iş akışı örneğinden yayılan izleme kayıtlarını filtrelemek için bir izleme profili.</span><span class="sxs-lookup"><span data-stu-id="f7076-120">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f7076-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7076-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f7076-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="f7076-122">Element</span></span>|<span data-ttu-id="f7076-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7076-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7076-124">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f7076-124">system.ServiceModel</span></span>|<span data-ttu-id="f7076-125">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f7076-125">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7076-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7076-126">Remarks</span></span>  
 <span data-ttu-id="f7076-127">İzleme, bir iş akışının yürütülmesini incelemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7076-127">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="f7076-128">İş akışı izleme altyapısı, yürütme sırasında önemli olayları yansıtan kayıtları göstermek için bir iş akışı araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7076-128">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="f7076-129">Örneğin, bir iş akışı örneği başlatıldığında ya da tamamlandığında izleme kayıtları yayınlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f7076-129">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="f7076-130">İzleme, iş akışı değişkenleriyle ilişkili iş ile ilgili verileri de ayıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="f7076-130">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="f7076-131">Örneğin, iş akışı bir sipariş işleme sistemini temsil ediyorsa, sipariş kimliği izleme kaydıyla birlikte ayıklanabilir.</span><span class="sxs-lookup"><span data-stu-id="f7076-131">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="f7076-132">Genel olarak, WF izlemeyi etkinleştirmek, bir iş akışı yürütmesi üzerinde tanılamayı veya iş analizlerini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="f7076-132">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7076-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7076-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="f7076-134">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f7076-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
