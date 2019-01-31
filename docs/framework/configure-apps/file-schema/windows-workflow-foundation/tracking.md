---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: fa96cb374204ffbdb4c0fcd353c70b6e27ef7481
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263816"
---
# <a name="tracking"></a><span data-ttu-id="53285-101">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="53285-101">\<tracking></span></span>
<span data-ttu-id="53285-102">Bir iş akışı hizmeti için izleme ayarları tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="53285-102">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="53285-103">İş akışı izleme ve kendi yapılandırmasını daha fazla bilgi için bkz: [takip ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [yapılandırma izleme için bir iş akışı](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="53285-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="53285-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="53285-104">\<system.serviceModel></span></span>  
<span data-ttu-id="53285-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="53285-105">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53285-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53285-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53285-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="53285-107">Attributes and Elements</span></span>  
 <span data-ttu-id="53285-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="53285-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53285-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="53285-109">Attributes</span></span>  
 <span data-ttu-id="53285-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="53285-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="53285-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="53285-111">Child Elements</span></span>  
  
|<span data-ttu-id="53285-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="53285-112">Element</span></span>|<span data-ttu-id="53285-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53285-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53285-114">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="53285-114">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="53285-115">Kayıtları İzleme için abone katılımcıları tanımlama yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="53285-115">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="53285-116">İzleme katılımcıları izleme kayıtları yükü işlemek için mantığı içerir (örneğin, bunlar bir dosyaya yazmak seçebilir).</span><span class="sxs-lookup"><span data-stu-id="53285-116">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="53285-117">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="53285-117">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="53285-118">Bir iş akışı örneğinden yayılan filtre izleme kayıtları için izleme profili.</span><span class="sxs-lookup"><span data-stu-id="53285-118">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="53285-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="53285-119">Parent Elements</span></span>  
  
|<span data-ttu-id="53285-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="53285-120">Element</span></span>|<span data-ttu-id="53285-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53285-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53285-122">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="53285-122">system.ServiceModel</span></span>|<span data-ttu-id="53285-123">Tüm iş akışı yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="53285-123">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53285-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53285-124">Remarks</span></span>  
 <span data-ttu-id="53285-125">İzleme bir iş akışı yürütülmesini inceleyin olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="53285-125">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="53285-126">İş akışı izleme altyapısı yürütme sırasında anahtar olayları yansıtan kayıtları yaymak için bir iş akışı Instruments.</span><span class="sxs-lookup"><span data-stu-id="53285-126">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="53285-127">Örneğin, bir iş akışı örneği başlatıldığında veya tamamlanan izleme kayıtları yayılan.</span><span class="sxs-lookup"><span data-stu-id="53285-127">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="53285-128">İzleme, iş akışı değişkenleri ile ilişkili iş ilgili verileri de ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53285-128">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="53285-129">Örneğin, iş akışı sistem işleme bir sırayı temsil ediyorsa sırası kimliği birlikte izleme kayıt ayıklanabileceği.</span><span class="sxs-lookup"><span data-stu-id="53285-129">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="53285-130">Genel olarak, izleme WF etkinleştirme Tanılama veya İş analizi bir iş akışı yürütme kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="53285-130">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53285-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53285-131">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="53285-132">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="53285-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
