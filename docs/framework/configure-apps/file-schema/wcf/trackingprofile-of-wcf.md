---
title: <trackingProfile>WCF
ms.date: 10/08/2018
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: 79326322eeed1f6b73729da675eb02fe6de670df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932344"
---
# <a name="trackingprofile-of-wcf"></a><span data-ttu-id="26c7d-102">\<WCF > trackingProfile</span><span class="sxs-lookup"><span data-stu-id="26c7d-102">\<trackingProfile> of WCF</span></span>
<span data-ttu-id="26c7d-103">Bir izleme katılımcısı içindeki iş akışı izleme kayıtlarına abonelik oluşturmak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="26c7d-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="26c7d-104">Bir izleme profili, bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="26c7d-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="26c7d-105">İzleme profili bölümü içinde tanımlanan sorgular, aboneliğin döndürdüğü olay türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="26c7d-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="26c7d-106">İş akışı izleme ve yapılandırma hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="26c7d-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="26c7d-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="26c7d-107">\<system.serviceModel></span></span>  
<span data-ttu-id="26c7d-108">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="26c7d-108">\<tracking></span></span>  
<span data-ttu-id="26c7d-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="26c7d-109">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26c7d-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26c7d-110">Syntax</span></span>  
  
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
                <argument name="String" />
              </arguments>
              <states>
                <state name="String" />
              </states>
              <variables>
                <variable name="String" />
              </variables>
            </activityStateQuery>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestedQueries>
            <cancelRequestedQuery activityName="String"
                                  childActivityName="String" />
          </cancelRequestedQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String" />
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery faultSourceActivityName="String"
                                   faultHandlerActivityName="String" />
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26c7d-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="26c7d-111">Attributes and Elements</span></span>  

<span data-ttu-id="26c7d-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="26c7d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26c7d-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="26c7d-113">Attributes</span></span>  
  
|<span data-ttu-id="26c7d-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="26c7d-114">Attribute</span></span>|<span data-ttu-id="26c7d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26c7d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26c7d-116">name</span><span class="sxs-lookup"><span data-stu-id="26c7d-116">name</span></span>|<span data-ttu-id="26c7d-117">İzleme profilinin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="26c7d-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26c7d-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="26c7d-118">Child Elements</span></span>  
  
|<span data-ttu-id="26c7d-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="26c7d-119">Element</span></span>|<span data-ttu-id="26c7d-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26c7d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26c7d-121">\<Katılımcılar ></span><span class="sxs-lookup"><span data-stu-id="26c7d-121">\<participants></span></span>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="26c7d-122">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="26c7d-122">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="26c7d-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="26c7d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="26c7d-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="26c7d-124">Element</span></span>|<span data-ttu-id="26c7d-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26c7d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26c7d-126">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="26c7d-126">\<tracking></span></span>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="26c7d-127">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="26c7d-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26c7d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26c7d-128">Remarks</span></span>  
 <span data-ttu-id="26c7d-129">İzleme profilleri, bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="26c7d-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="26c7d-130">Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="26c7d-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="26c7d-131">Buna karşılık, daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok özel bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26c7d-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="26c7d-132">İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanızı sağlayan kayıtları izlemek için bildirim temelli abonelikler olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="26c7d-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="26c7d-133">Farklı <xref:System.Activities.Tracking.TrackingRecord> nesne sınıflarına abone olmanıza imkan tanıyan bir dizi sorgu türü vardır.</span><span class="sxs-lookup"><span data-stu-id="26c7d-133">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="26c7d-134">Sorguların tüm listesi için bkz [ \<. katılımcılar >](../windows-workflow-foundation/participants.md) ve [izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="26c7d-134">For a complete list of queries, see [\<participants>](../windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="26c7d-135">Aşağıdaki örnek, bir yapılandırma dosyasında izleme katılımcısının `Started` ve `Completed` iş akışı olaylarına abone olmasına izin veren bir izleme profilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="26c7d-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started" />
                <state name="Completed" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="26c7d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26c7d-136">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="26c7d-137">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="26c7d-137">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="26c7d-138">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="26c7d-138">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
