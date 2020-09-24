---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: fdfaf234b5dda5703da7fc1ca1fe4554d57405f5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148691"
---
# \<workflow>

<span data-ttu-id="30c4e-101">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="30c4e-101">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="30c4e-102">İş akışı izleme ve yapılandırma hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="30c4e-102">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflow>**  
  
## <a name="syntax"></a><span data-ttu-id="30c4e-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="30c4e-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30c4e-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="30c4e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="30c4e-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30c4e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30c4e-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="30c4e-106">Attributes</span></span>  
  
|<span data-ttu-id="30c4e-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="30c4e-107">Attribute</span></span>|<span data-ttu-id="30c4e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30c4e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30c4e-109">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="30c4e-109">activityDefinitionId</span></span>|<span data-ttu-id="30c4e-110">İzlenmekte olan iş akışının etkinlik tanımı KIMLIĞINI belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="30c4e-110">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30c4e-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="30c4e-111">Child Elements</span></span>  
  
|<span data-ttu-id="30c4e-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="30c4e-112">Element</span></span>|<span data-ttu-id="30c4e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30c4e-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries.md)|<span data-ttu-id="30c4e-114">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="30c4e-114">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="30c4e-115">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="30c4e-115">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[\<activityStateQueries>](activitystatequeries.md)|<span data-ttu-id="30c4e-116">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="30c4e-116">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="30c4e-117">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30c4e-117">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="30c4e-118">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="30c4e-118">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="30c4e-119">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="30c4e-119">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="30c4e-120">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="30c4e-120">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="30c4e-121">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="30c4e-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[\<cancelRequestedQueries>](cancelrequestedqueries.md)|<span data-ttu-id="30c4e-122">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="30c4e-122">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="30c4e-123">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="30c4e-123">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[\<customTrackingQueries>](customtrackingqueries.md)|<span data-ttu-id="30c4e-124">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="30c4e-124">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="30c4e-125">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="30c4e-125">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[\<faultPropagationQueries>](faultpropagationqueries.md)|<span data-ttu-id="30c4e-126">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="30c4e-126">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="30c4e-127">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="30c4e-127">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="30c4e-128">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="30c4e-128">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="30c4e-129">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="30c4e-129">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[\<workflowInstanceQueries>](workflowinstancequeries.md)|<span data-ttu-id="30c4e-130">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="30c4e-130">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30c4e-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="30c4e-131">Parent Elements</span></span>  
  
|<span data-ttu-id="30c4e-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="30c4e-132">Element</span></span>|<span data-ttu-id="30c4e-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30c4e-133">Description</span></span>|  
|-------------|-----------------|  
|[\<trackingProfile>](trackingprofile.md)|<span data-ttu-id="30c4e-134">Bir izleme katılımcısı içindeki iş akışı izleme kayıtlarına abonelik oluşturmak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="30c4e-134">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="30c4e-135">Bir izleme profili, bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="30c4e-135">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="30c4e-136">İzleme profili bölümü içinde tanımlanan sorgular, aboneliğin döndürdüğü olay türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="30c4e-136">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30c4e-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30c4e-137">Remarks</span></span>  

 <span data-ttu-id="30c4e-138">İzleme profilleri, belirli bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="30c4e-138">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="30c4e-139">İzlenmekte olan iş akışı örneği bu yapılandırma öğesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="30c4e-139">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="30c4e-140">Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="30c4e-140">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="30c4e-141">Buna karşılık, daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok özel bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30c4e-141">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="30c4e-142">İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanızı sağlayan kayıtları izlemek için bildirim temelli abonelikler olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="30c4e-142">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="30c4e-143">Farklı izleme kayıt sınıflarına abone olmanızı sağlayan bir dizi sorgu türü vardır.</span><span class="sxs-lookup"><span data-stu-id="30c4e-143">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="30c4e-144">Sorguların tüm listesi için, bu konunun alt öğe listesi ve [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)' ne bakın.</span><span class="sxs-lookup"><span data-stu-id="30c4e-144">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="30c4e-145">Aşağıdaki örnek, bir yapılandırma dosyasında izleme katılımcısının `Started` ve iş akışı olaylarına abone olmasına izin veren bir izleme profilini gösterir `Completed` .</span><span class="sxs-lookup"><span data-stu-id="30c4e-145">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30c4e-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30c4e-146">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="30c4e-147">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="30c4e-147">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="30c4e-148">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="30c4e-148">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
