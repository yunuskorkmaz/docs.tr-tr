---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: 89f9d0e7c57f6e66b9fdffd148d9dcae5a189fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947230"
---
# <a name="workflow"></a><span data-ttu-id="b8be1-101">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="b8be1-101">\<workflow></span></span>
<span data-ttu-id="b8be1-102">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b8be1-102">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="b8be1-103">İş akışı izleme ve yapılandırma hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b8be1-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b8be1-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b8be1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b8be1-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="b8be1-105">\<tracking></span></span>  
<span data-ttu-id="b8be1-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b8be1-106">\<trackingProfile></span></span>  
<span data-ttu-id="b8be1-107">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="b8be1-107">\<workflow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8be1-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8be1-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8be1-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8be1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b8be1-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b8be1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8be1-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b8be1-111">Attributes</span></span>  
  
|<span data-ttu-id="b8be1-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b8be1-112">Attribute</span></span>|<span data-ttu-id="b8be1-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8be1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8be1-114">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="b8be1-114">activityDefinitionId</span></span>|<span data-ttu-id="b8be1-115">İzlenmekte olan iş akışının etkinlik tanımı KIMLIĞINI belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="b8be1-115">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8be1-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8be1-116">Child Elements</span></span>  
  
|<span data-ttu-id="b8be1-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8be1-117">Element</span></span>|<span data-ttu-id="b8be1-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8be1-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8be1-119">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="b8be1-119">\<activityScheduledQueries></span></span>](activityscheduledqueries.md)|<span data-ttu-id="b8be1-120">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8be1-120">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="b8be1-121">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b8be1-121">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="b8be1-122">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="b8be1-122">\<activityStateQueries></span></span>](activitystatequeries.md)|<span data-ttu-id="b8be1-123">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8be1-123">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="b8be1-124">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8be1-124">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="b8be1-125">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b8be1-125">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="b8be1-126">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b8be1-126">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="b8be1-127">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="b8be1-127">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="b8be1-128">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8be1-128">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="b8be1-129">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b8be1-129">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="b8be1-130">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="b8be1-130">\<cancelRequestedQueries></span></span>](cancelrequestedqueries.md)|<span data-ttu-id="b8be1-131">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8be1-131">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b8be1-132">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b8be1-132">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="b8be1-133">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="b8be1-133">\<customTrackingQueries></span></span>](customtrackingqueries.md)|<span data-ttu-id="b8be1-134">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8be1-134">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="b8be1-135">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b8be1-135">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="b8be1-136">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="b8be1-136">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="b8be1-137">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8be1-137">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b8be1-138">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="b8be1-138">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="b8be1-139">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8be1-139">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="b8be1-140">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b8be1-140">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="b8be1-141">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="b8be1-141">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="b8be1-142">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8be1-142">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8be1-143">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8be1-143">Parent Elements</span></span>  
  
|<span data-ttu-id="b8be1-144">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8be1-144">Element</span></span>|<span data-ttu-id="b8be1-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8be1-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8be1-146">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b8be1-146">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="b8be1-147">Bir izleme katılımcısı içindeki iş akışı izleme kayıtlarına abonelik oluşturmak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8be1-147">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="b8be1-148">Bir izleme profili, bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="b8be1-148">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="b8be1-149">İzleme profili bölümü içinde tanımlanan sorgular, aboneliğin döndürdüğü olay türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b8be1-149">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8be1-150">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8be1-150">Remarks</span></span>  
 <span data-ttu-id="b8be1-151">İzleme profilleri, belirli bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="b8be1-151">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="b8be1-152">İzlenmekte olan iş akışı örneği bu yapılandırma öğesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b8be1-152">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="b8be1-153">Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="b8be1-153">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="b8be1-154">Buna karşılık, daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok özel bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8be1-154">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="b8be1-155">İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanızı sağlayan kayıtları izlemek için bildirim temelli abonelikler olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="b8be1-155">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="b8be1-156">Farklı izleme kayıt sınıflarına abone olmanızı sağlayan bir dizi sorgu türü vardır.</span><span class="sxs-lookup"><span data-stu-id="b8be1-156">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="b8be1-157">Sorguların tüm listesi için, bu konunun alt öğe listesi ve [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)' ne bakın.</span><span class="sxs-lookup"><span data-stu-id="b8be1-157">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="b8be1-158">Aşağıdaki örnek, bir yapılandırma dosyasında izleme katılımcısının `Started` ve `Completed` iş akışı olaylarına abone olmasına izin veren bir izleme profilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8be1-158">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b8be1-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8be1-159">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="b8be1-160">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="b8be1-160">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b8be1-161">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="b8be1-161">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
