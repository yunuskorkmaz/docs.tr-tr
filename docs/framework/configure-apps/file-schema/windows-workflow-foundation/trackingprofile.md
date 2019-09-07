---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 3120d6f5d1bb5a5cf452567e96766231534f3f41
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398589"
---
# <a name="trackingprofile"></a><span data-ttu-id="de463-101">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="de463-101">\<trackingProfile></span></span>
<span data-ttu-id="de463-102">Bir izleme katılımcısı içindeki iş akışı izleme kayıtlarına abonelik oluşturmak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de463-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="de463-103">Bir izleme profili, bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="de463-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="de463-104">İzleme profili bölümü içinde tanımlanan sorgular, aboneliğin döndürdüğü olay türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="de463-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="de463-105">İş akışı izleme ve yapılandırma hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="de463-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="de463-106">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="de463-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="de463-107">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="de463-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="de463-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="de463-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="de463-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<trackingProfile >**</span><span class="sxs-lookup"><span data-stu-id="de463-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de463-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de463-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de463-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="de463-111">Attributes and Elements</span></span>  
 <span data-ttu-id="de463-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="de463-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de463-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="de463-113">Attributes</span></span>  
  
|<span data-ttu-id="de463-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="de463-114">Attribute</span></span>|<span data-ttu-id="de463-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de463-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de463-116">name</span><span class="sxs-lookup"><span data-stu-id="de463-116">name</span></span>|<span data-ttu-id="de463-117">İzleme profilinin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="de463-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de463-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="de463-118">Child Elements</span></span>  
  
|<span data-ttu-id="de463-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="de463-119">Element</span></span>|<span data-ttu-id="de463-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de463-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de463-121">\<Katılımcılar ></span><span class="sxs-lookup"><span data-stu-id="de463-121">\<participants></span></span>](participants.md)|<span data-ttu-id="de463-122">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="de463-122">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de463-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="de463-123">Parent Elements</span></span>  
  
|<span data-ttu-id="de463-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="de463-124">Element</span></span>|<span data-ttu-id="de463-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de463-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de463-126">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="de463-126">\<tracking></span></span>](tracking.md)|<span data-ttu-id="de463-127">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de463-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de463-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de463-128">Remarks</span></span>  
 <span data-ttu-id="de463-129">İzleme profilleri, bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="de463-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="de463-130">Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="de463-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="de463-131">Buna karşılık, daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok özel bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de463-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="de463-132">İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanızı sağlayan kayıtları izlemek için bildirim temelli abonelikler olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="de463-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="de463-133">Farklı <xref:System.Activities.Tracking.TrackingRecord> nesne sınıflarına abone olmanıza imkan tanıyan bir dizi sorgu türü vardır.</span><span class="sxs-lookup"><span data-stu-id="de463-133">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="de463-134">Sorguların tüm listesi için bkz [ \<. katılımcılar >](participants.md) ve [izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)..</span><span class="sxs-lookup"><span data-stu-id="de463-134">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="de463-135">Aşağıdaki örnek, bir yapılandırma dosyasında izleme katılımcısının `Started` ve `Completed` iş akışı olaylarına abone olmasına izin veren bir izleme profilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="de463-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="de463-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de463-136">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="de463-137">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="de463-137">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="de463-138">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="de463-138">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
