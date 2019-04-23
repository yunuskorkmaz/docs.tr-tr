---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 747660df58604dd9384abefccb51ea665f97e2e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139678"
---
# <a name="trackingprofile"></a><span data-ttu-id="6dc38-101">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="6dc38-101">\<trackingProfile></span></span>
<span data-ttu-id="6dc38-102">İş akışı izleme katılımcı kayıtlarında izleme aboneliği oluşturmak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6dc38-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="6dc38-103">Bir izleme profili çalışma zamanında bir iş akışı örneği durumu değiştiğinde yayılan iş akışı olayları abone olmak için izleme katılımcı izin izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="6dc38-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="6dc38-104">Tanımlanan sorguları izleme profilinde bölümü abonelik tarafından döndürülen olayları tür tanımlamak.</span><span class="sxs-lookup"><span data-stu-id="6dc38-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="6dc38-105">İş akışı izleme ve kendi yapılandırmasını daha fazla bilgi için bkz: [takip ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6dc38-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="6dc38-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6dc38-106">\<system.serviceModel></span></span>  
<span data-ttu-id="6dc38-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="6dc38-107">\<tracking></span></span>  
<span data-ttu-id="6dc38-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="6dc38-108">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dc38-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6dc38-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6dc38-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6dc38-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6dc38-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6dc38-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6dc38-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6dc38-112">Attributes</span></span>  
  
|<span data-ttu-id="6dc38-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6dc38-113">Attribute</span></span>|<span data-ttu-id="6dc38-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6dc38-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6dc38-115">name</span><span class="sxs-lookup"><span data-stu-id="6dc38-115">name</span></span>|<span data-ttu-id="6dc38-116">İzleme profilinin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="6dc38-116">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6dc38-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6dc38-117">Child Elements</span></span>  
  
|<span data-ttu-id="6dc38-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="6dc38-118">Element</span></span>|<span data-ttu-id="6dc38-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6dc38-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6dc38-120">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="6dc38-120">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="6dc38-121">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6dc38-121">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6dc38-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6dc38-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6dc38-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="6dc38-123">Element</span></span>|<span data-ttu-id="6dc38-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6dc38-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6dc38-125">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="6dc38-125">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="6dc38-126">Bir iş akışı hizmeti için izleme ayarları tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6dc38-126">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dc38-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6dc38-127">Remarks</span></span>  
 <span data-ttu-id="6dc38-128">İzleme profilleri bir iş akışı örneğinin durumunu çalışma zamanında değiştiğinde yayılan iş akışı olayları abone olmak için izleme katılımcı izin izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="6dc38-128">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="6dc38-129">Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="6dc38-129">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="6dc38-130">Buna karşılık, elde edilen ayarlanmış olayları ayrıntılı yürütme akışı daha sonra yeniden oluşturmak için zengin bir çok özel profil oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="6dc38-130">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="6dc38-131">İzleme profilleri belirli izleme kayıtları için iş akışı çalışma zamanı sorgulamaya izin kayıtları izleme için bildirim abonelikleri olarak yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6dc38-131">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="6dc38-132">Birkaç farklı sınıfları için abone izin sorgu türleri vardır <xref:System.Activities.Tracking.TrackingRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6dc38-132">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="6dc38-133">Sorguları tam listesi için bkz. [ \<katılımcıları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) ve [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)...</span><span class="sxs-lookup"><span data-stu-id="6dc38-133">For a complete list of queries, see [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="6dc38-134">Aşağıdaki örnek, abone olmak izleme katılımcı izin veren bir yapılandırma dosyasında bir izleme profili gösterir. `Started` ve `Completed` iş akışı olayları.</span><span class="sxs-lookup"><span data-stu-id="6dc38-134">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>  
  <tracking>    
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
  
## <a name="see-also"></a><span data-ttu-id="6dc38-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6dc38-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="6dc38-136">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="6dc38-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6dc38-137">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="6dc38-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
