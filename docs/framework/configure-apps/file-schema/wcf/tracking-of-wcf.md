---
title: WCF &lt;izleme&gt;
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: e033b569502bba795b5dcd1abdf9f68a726fac21
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121314"
---
# <a name="lttrackinggt-of-wcf"></a><span data-ttu-id="3c9b6-102">WCF &lt;izleme&gt;</span><span class="sxs-lookup"><span data-stu-id="3c9b6-102">&lt;tracking&gt; of WCF</span></span>
<span data-ttu-id="3c9b6-103">Bir iş akışı hizmeti için izleme ayarları tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3c9b6-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="3c9b6-104">İş akışı izleme ve kendi yapılandırmasını daha fazla bilgi için bkz: [takip ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [yapılandırma izleme için bir iş akışı](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="3c9b6-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
 <span data-ttu-id="3c9b6-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3c9b6-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3c9b6-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="3c9b6-106">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c9b6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c9b6-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c9b6-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c9b6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3c9b6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3c9b6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c9b6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3c9b6-110">Attributes</span></span>  
 <span data-ttu-id="3c9b6-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="3c9b6-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3c9b6-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c9b6-112">Child Elements</span></span>  
  
|<span data-ttu-id="3c9b6-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="3c9b6-113">Element</span></span>|<span data-ttu-id="3c9b6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c9b6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c9b6-115">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="3c9b6-115">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="3c9b6-116">Kayıtları İzleme için abone katılımcıları tanımlama yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3c9b6-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="3c9b6-117">İzleme katılımcıları izleme kayıtları yükü işlemek için mantığı içerir (örneğin, bunlar bir dosyaya yazmak seçebilir).</span><span class="sxs-lookup"><span data-stu-id="3c9b6-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="3c9b6-118">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="3c9b6-118">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="3c9b6-119">Bir iş akışı örneğinden yayılan filtre izleme kayıtları için izleme profili.</span><span class="sxs-lookup"><span data-stu-id="3c9b6-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3c9b6-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c9b6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3c9b6-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="3c9b6-121">Element</span></span>|<span data-ttu-id="3c9b6-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c9b6-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c9b6-123">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3c9b6-123">system.ServiceModel</span></span>|<span data-ttu-id="3c9b6-124">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3c9b6-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c9b6-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c9b6-125">Remarks</span></span>  
 <span data-ttu-id="3c9b6-126">İzleme bir iş akışı yürütülmesini inceleyin olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c9b6-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="3c9b6-127">İş akışı izleme altyapısı yürütme sırasında anahtar olayları yansıtan kayıtları yaymak için bir iş akışı Instruments.</span><span class="sxs-lookup"><span data-stu-id="3c9b6-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="3c9b6-128">Örneğin, bir iş akışı örneği başlatıldığında veya tamamlanan izleme kayıtları yayılan.</span><span class="sxs-lookup"><span data-stu-id="3c9b6-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="3c9b6-129">İzleme, iş akışı değişkenleri ile ilişkili iş ilgili verileri de ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c9b6-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="3c9b6-130">Örneğin, iş akışı sistem işleme bir sırayı temsil ediyorsa sırası kimliği birlikte izleme kayıt ayıklanabileceği.</span><span class="sxs-lookup"><span data-stu-id="3c9b6-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="3c9b6-131">Genel olarak, izleme WF etkinleştirme Tanılama veya İş analizi bir iş akışı yürütme kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3c9b6-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c9b6-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c9b6-132">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>       
 [<span data-ttu-id="3c9b6-133">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="3c9b6-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
