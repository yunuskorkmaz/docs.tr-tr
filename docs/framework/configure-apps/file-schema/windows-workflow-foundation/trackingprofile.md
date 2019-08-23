---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 8b8cfe95a646563642e7425fdb4b5257cafa466f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947296"
---
# <a name="trackingprofile"></a><span data-ttu-id="dba35-101">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="dba35-101">\<trackingProfile></span></span>
<span data-ttu-id="dba35-102">Bir izleme katılımcısı içindeki iş akışı izleme kayıtlarına abonelik oluşturmak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dba35-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="dba35-103">Bir izleme profili, bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="dba35-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="dba35-104">İzleme profili bölümü içinde tanımlanan sorgular, aboneliğin döndürdüğü olay türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dba35-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="dba35-105">İş akışı izleme ve yapılandırma hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="dba35-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="dba35-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dba35-106">\<system.serviceModel></span></span>  
<span data-ttu-id="dba35-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="dba35-107">\<tracking></span></span>  
<span data-ttu-id="dba35-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="dba35-108">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba35-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dba35-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dba35-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dba35-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dba35-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dba35-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dba35-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dba35-112">Attributes</span></span>  
  
|<span data-ttu-id="dba35-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dba35-113">Attribute</span></span>|<span data-ttu-id="dba35-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dba35-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dba35-115">name</span><span class="sxs-lookup"><span data-stu-id="dba35-115">name</span></span>|<span data-ttu-id="dba35-116">İzleme profilinin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="dba35-116">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dba35-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dba35-117">Child Elements</span></span>  
  
|<span data-ttu-id="dba35-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="dba35-118">Element</span></span>|<span data-ttu-id="dba35-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dba35-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dba35-120">\<Katılımcılar ></span><span class="sxs-lookup"><span data-stu-id="dba35-120">\<participants></span></span>](participants.md)|<span data-ttu-id="dba35-121">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="dba35-121">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dba35-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dba35-122">Parent Elements</span></span>  
  
|<span data-ttu-id="dba35-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="dba35-123">Element</span></span>|<span data-ttu-id="dba35-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dba35-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dba35-125">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="dba35-125">\<tracking></span></span>](tracking.md)|<span data-ttu-id="dba35-126">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dba35-126">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dba35-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dba35-127">Remarks</span></span>  
 <span data-ttu-id="dba35-128">İzleme profilleri, bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="dba35-128">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="dba35-129">Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="dba35-129">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="dba35-130">Buna karşılık, daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok özel bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dba35-130">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="dba35-131">İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanızı sağlayan kayıtları izlemek için bildirim temelli abonelikler olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="dba35-131">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="dba35-132">Farklı <xref:System.Activities.Tracking.TrackingRecord> nesne sınıflarına abone olmanıza imkan tanıyan bir dizi sorgu türü vardır.</span><span class="sxs-lookup"><span data-stu-id="dba35-132">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="dba35-133">Sorguların tüm listesi için bkz [ \<. katılımcılar >](participants.md) ve [izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)..</span><span class="sxs-lookup"><span data-stu-id="dba35-133">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="dba35-134">Aşağıdaki örnek, bir yapılandırma dosyasında izleme katılımcısının `Started` ve `Completed` iş akışı olaylarına abone olmasına izin veren bir izleme profilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dba35-134">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dba35-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dba35-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="dba35-136">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="dba35-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dba35-137">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="dba35-137">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
