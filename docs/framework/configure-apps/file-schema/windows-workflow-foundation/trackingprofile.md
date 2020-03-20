---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 8985da7e1223ac117cf1b68227140634f9c85d3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151895"
---
# <a name="trackingprofile"></a><span data-ttu-id="91c84-101">\<izlemeProfil></span><span class="sxs-lookup"><span data-stu-id="91c84-101">\<trackingProfile></span></span>
<span data-ttu-id="91c84-102">İzleme katılımcısında iş akışı izleme kayıtlarına abonelik oluşturmak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="91c84-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="91c84-103">İzleme profili, bir izleme katılımcısının çalışma zamanında iş akışı örneği durumu değiştiğinde yayılan iş akışı olaylarına abone olmasını sağlayan izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="91c84-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="91c84-104">İzleme profili bölümünde tanımlanan sorgular, abonelik tarafından döndürülen olay türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="91c84-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="91c84-105">İş akışı izleme ve yapılandırmasında daha fazla bilgi için [İş Akışı İzleme ve İzleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve İzleme [Profilleri'ne](../../../windows-workflow-foundation/tracking-profiles.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="91c84-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="91c84-106">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="91c84-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="91c84-107">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="91c84-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="91c84-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="91c84-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="91c84-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<izlemeProfil>**</span><span class="sxs-lookup"><span data-stu-id="91c84-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91c84-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91c84-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91c84-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="91c84-111">Attributes and Elements</span></span>  
 <span data-ttu-id="91c84-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="91c84-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91c84-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="91c84-113">Attributes</span></span>  
  
|<span data-ttu-id="91c84-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="91c84-114">Attribute</span></span>|<span data-ttu-id="91c84-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91c84-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="91c84-116">ad</span><span class="sxs-lookup"><span data-stu-id="91c84-116">name</span></span>|<span data-ttu-id="91c84-117">İzleme profilinin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="91c84-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91c84-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="91c84-118">Child Elements</span></span>  
  
|<span data-ttu-id="91c84-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="91c84-119">Element</span></span>|<span data-ttu-id="91c84-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91c84-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91c84-121">\<katılımcılar></span><span class="sxs-lookup"><span data-stu-id="91c84-121">\<participants></span></span>](participants.md)|<span data-ttu-id="91c84-122">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="91c84-122">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91c84-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="91c84-123">Parent Elements</span></span>  
  
|<span data-ttu-id="91c84-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="91c84-124">Element</span></span>|<span data-ttu-id="91c84-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91c84-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91c84-126">\<izleme></span><span class="sxs-lookup"><span data-stu-id="91c84-126">\<tracking></span></span>](tracking.md)|<span data-ttu-id="91c84-127">İş akışı hizmeti için izleme ayarlarını tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="91c84-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91c84-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91c84-128">Remarks</span></span>  
 <span data-ttu-id="91c84-129">İzleme profilleri, bir izleme katılımcısının çalışma zamanında iş akışı örneği durumu değiştiğinde yayılan iş akışı olaylarına abone olmasını sağlayan izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="91c84-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="91c84-130">Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="91c84-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="91c84-131">Tersine, ortaya çıkan olaylar daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok özel bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91c84-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="91c84-132">İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanıza olanak tanıyan kayıtları izlemek için bildirimsel abonelikler olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="91c84-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="91c84-133">Farklı <xref:System.Activities.Tracking.TrackingRecord> nesne sınıflarına abone olsanız neden olan bir avuç sorgu türü vardır.</span><span class="sxs-lookup"><span data-stu-id="91c84-133">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="91c84-134">Sorguların tam listesi için [ \<katılımcılar>](participants.md) ve [İzleme Profilleri'ne](../../../windows-workflow-foundation/tracking-profiles.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="91c84-134">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="91c84-135">Aşağıdaki örnek, bir yapılandırma dosyasındaki bir izleme katılımcısının iş `Started` `Completed` akışı olaylarına abone olmasını sağlayan bir izleme profilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="91c84-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91c84-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91c84-136">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="91c84-137">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="91c84-137">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="91c84-138">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="91c84-138">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
