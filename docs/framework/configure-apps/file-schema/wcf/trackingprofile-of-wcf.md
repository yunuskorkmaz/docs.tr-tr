---
title: <trackingProfile>WCF
ms.date: 10/08/2018
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: c5df03d63653e658a23a36e8943c06f156d2ae00
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854945"
---
# <a name="trackingprofile-of-wcf"></a><span data-ttu-id="f2de9-102">\<WCF > trackingProfile</span><span class="sxs-lookup"><span data-stu-id="f2de9-102">\<trackingProfile> of WCF</span></span>
<span data-ttu-id="f2de9-103">Bir izleme katılımcısı içindeki iş akışı izleme kayıtlarına abonelik oluşturmak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2de9-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="f2de9-104">Bir izleme profili, bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="f2de9-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="f2de9-105">İzleme profili bölümü içinde tanımlanan sorgular, aboneliğin döndürdüğü olay türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2de9-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
<span data-ttu-id="f2de9-106">İş akışı izleme ve yapılandırma hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f2de9-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="f2de9-107">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2de9-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f2de9-108">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f2de9-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f2de9-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="f2de9-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="f2de9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="f2de9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="f2de9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<trackingProfile >**</span><span class="sxs-lookup"><span data-stu-id="f2de9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2de9-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2de9-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2de9-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2de9-113">Attributes and Elements</span></span>  

<span data-ttu-id="f2de9-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2de9-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2de9-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2de9-115">Attributes</span></span>  
  
|<span data-ttu-id="f2de9-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f2de9-116">Attribute</span></span>|<span data-ttu-id="f2de9-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2de9-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2de9-118">name</span><span class="sxs-lookup"><span data-stu-id="f2de9-118">name</span></span>|<span data-ttu-id="f2de9-119">İzleme profilinin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f2de9-119">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2de9-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2de9-120">Child Elements</span></span>  
  
|<span data-ttu-id="f2de9-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2de9-121">Element</span></span>|<span data-ttu-id="f2de9-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2de9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2de9-123">\<Katılımcılar ></span><span class="sxs-lookup"><span data-stu-id="f2de9-123">\<participants></span></span>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="f2de9-124">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f2de9-124">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2de9-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2de9-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f2de9-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2de9-126">Element</span></span>|<span data-ttu-id="f2de9-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2de9-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2de9-128">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="f2de9-128">\<tracking></span></span>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="f2de9-129">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2de9-129">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2de9-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2de9-130">Remarks</span></span>  
 <span data-ttu-id="f2de9-131">İzleme profilleri, bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="f2de9-131">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="f2de9-132">Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="f2de9-132">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="f2de9-133">Buna karşılık, daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok özel bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2de9-133">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="f2de9-134">İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanızı sağlayan kayıtları izlemek için bildirim temelli abonelikler olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="f2de9-134">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="f2de9-135">Farklı <xref:System.Activities.Tracking.TrackingRecord> nesne sınıflarına abone olmanıza imkan tanıyan bir dizi sorgu türü vardır.</span><span class="sxs-lookup"><span data-stu-id="f2de9-135">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="f2de9-136">Sorguların tüm listesi için bkz [ \<. katılımcılar >](../windows-workflow-foundation/participants.md) ve [izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f2de9-136">For a complete list of queries, see [\<participants>](../windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="f2de9-137">Aşağıdaki örnek, bir yapılandırma dosyasında izleme katılımcısının `Started` ve `Completed` iş akışı olaylarına abone olmasına izin veren bir izleme profilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2de9-137">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2de9-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2de9-138">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="f2de9-139">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f2de9-139">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f2de9-140">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f2de9-140">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
