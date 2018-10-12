---
title: WFC &lt;trackingProfile&gt;
ms.date: 10/08/2018
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: a11086ef07a2a605f3889bc4077d25e0b7748e5e
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49120927"
---
# <a name="lttrackingprofilegt-of-wcf"></a><span data-ttu-id="719e7-102">WFC &lt;trackingProfile&gt;</span><span class="sxs-lookup"><span data-stu-id="719e7-102">&lt;trackingProfile&gt; of WCF</span></span>
<span data-ttu-id="719e7-103">İş akışı izleme katılımcı kayıtlarında izleme aboneliği oluşturmak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="719e7-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="719e7-104">Bir izleme profili çalışma zamanında bir iş akışı örneği durumu değiştiğinde yayılan iş akışı olayları abone olmak için izleme katılımcı izin izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="719e7-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="719e7-105">Tanımlanan sorguları izleme profilinde bölümü abonelik tarafından döndürülen olayları tür tanımlamak.</span><span class="sxs-lookup"><span data-stu-id="719e7-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="719e7-106">İş akışı izleme ve kendi yapılandırmasını daha fazla bilgi için bkz: [takip ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="719e7-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="719e7-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="719e7-107">\<system.serviceModel></span></span>  
<span data-ttu-id="719e7-108">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="719e7-108">\<tracking></span></span>  
<span data-ttu-id="719e7-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="719e7-109">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="719e7-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="719e7-110">Syntax</span></span>  
  
```xml
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String" 
                                    childActivityName="String" />
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String">
              <arguments>
                <argument name="String"/>
              </arguments>
              <states>
                <state name="String"/>
              </states>
              <variables>
                <variable name="String"/>
              </variables>
            </activityStateQuery>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestedQueries>
            <cancelRequestedQuery activityName="String" 
                                childActivityName="String"/>
          </cancelRequestedQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String" 
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery faultSourceActivityName="String" 
                                   faultHandlerActivityName="String"/>
          </faultPropagationQueries>
          <stateMachineStateQueries>
            <stateMachineStateQuery activityName="String" />
          </stateMachineStateQueries>
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="719e7-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="719e7-111">Attributes and Elements</span></span>  

<span data-ttu-id="719e7-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="719e7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="719e7-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="719e7-113">Attributes</span></span>  
  
|<span data-ttu-id="719e7-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="719e7-114">Attribute</span></span>|<span data-ttu-id="719e7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="719e7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="719e7-116">name</span><span class="sxs-lookup"><span data-stu-id="719e7-116">name</span></span>|<span data-ttu-id="719e7-117">İzleme profilinin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="719e7-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="719e7-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="719e7-118">Child Elements</span></span>  
  
|<span data-ttu-id="719e7-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="719e7-119">Element</span></span>|<span data-ttu-id="719e7-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="719e7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="719e7-121">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="719e7-121">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="719e7-122">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="719e7-122">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="719e7-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="719e7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="719e7-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="719e7-124">Element</span></span>|<span data-ttu-id="719e7-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="719e7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="719e7-126">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="719e7-126">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="719e7-127">Bir iş akışı hizmeti için izleme ayarları tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="719e7-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="719e7-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="719e7-128">Remarks</span></span>  
 <span data-ttu-id="719e7-129">İzleme profilleri bir iş akışı örneğinin durumunu çalışma zamanında değiştiğinde yayılan iş akışı olayları abone olmak için izleme katılımcı izin izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="719e7-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="719e7-130">Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="719e7-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="719e7-131">Buna karşılık, elde edilen ayarlanmış olayları ayrıntılı yürütme akışı daha sonra yeniden oluşturmak için zengin bir çok özel profil oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="719e7-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="719e7-132">İzleme profilleri belirli izleme kayıtları için iş akışı çalışma zamanı sorgulamaya izin kayıtları izleme için bildirim abonelikleri olarak yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="719e7-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="719e7-133">Birkaç farklı sınıfları için abone izin sorgu türleri vardır <xref:System.Activities.Tracking.TrackingRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="719e7-133">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="719e7-134">Sorguları tam listesi için bkz. [ \<katılımcıları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) ve [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="719e7-134">For a complete list of queries, see [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="719e7-135">Aşağıdaki örnek, abone olmak izleme katılımcı izin veren bir yapılandırma dosyasında bir izleme profili gösterir. `Started` ve `Completed` iş akışı olayları.</span><span class="sxs-lookup"><span data-stu-id="719e7-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started"/>
                <state name="Completed"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="719e7-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="719e7-136">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>  
- <xref:System.Activities.Tracking.TrackingProfile>  
- [<span data-ttu-id="719e7-137">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="719e7-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="719e7-138">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="719e7-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
