---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: 5205f9ab89297c0e55c3e5e0c03b9e3fef36963a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397574"
---
# <a name="workflow"></a><span data-ttu-id="ed281-101">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="ed281-101">\<workflow></span></span>
<span data-ttu-id="ed281-102">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ed281-102">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="ed281-103">İş akışı izleme ve yapılandırma hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ed281-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ed281-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed281-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ed281-105">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ed281-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="ed281-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="ed281-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="ed281-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="ed281-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="ed281-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<iş akışı >**</span><span class="sxs-lookup"><span data-stu-id="ed281-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflow>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed281-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed281-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed281-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed281-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ed281-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed281-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed281-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ed281-112">Attributes</span></span>  
  
|<span data-ttu-id="ed281-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ed281-113">Attribute</span></span>|<span data-ttu-id="ed281-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed281-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ed281-115">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="ed281-115">activityDefinitionId</span></span>|<span data-ttu-id="ed281-116">İzlenmekte olan iş akışının etkinlik tanımı KIMLIĞINI belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ed281-116">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed281-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed281-117">Child Elements</span></span>  
  
|<span data-ttu-id="ed281-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="ed281-118">Element</span></span>|<span data-ttu-id="ed281-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed281-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed281-120">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="ed281-120">\<activityScheduledQueries></span></span>](activityscheduledqueries.md)|<span data-ttu-id="ed281-121">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ed281-121">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="ed281-122">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ed281-122">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="ed281-123">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="ed281-123">\<activityStateQueries></span></span>](activitystatequeries.md)|<span data-ttu-id="ed281-124">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ed281-124">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="ed281-125">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed281-125">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="ed281-126">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ed281-126">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="ed281-127">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ed281-127">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="ed281-128">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="ed281-128">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="ed281-129">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ed281-129">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="ed281-130">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ed281-130">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="ed281-131">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="ed281-131">\<cancelRequestedQueries></span></span>](cancelrequestedqueries.md)|<span data-ttu-id="ed281-132">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ed281-132">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ed281-133">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ed281-133">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="ed281-134">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="ed281-134">\<customTrackingQueries></span></span>](customtrackingqueries.md)|<span data-ttu-id="ed281-135">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ed281-135">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ed281-136">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ed281-136">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="ed281-137">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="ed281-137">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="ed281-138">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ed281-138">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ed281-139">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="ed281-139">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="ed281-140">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed281-140">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="ed281-141">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ed281-141">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="ed281-142">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="ed281-142">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="ed281-143">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ed281-143">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ed281-144">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed281-144">Parent Elements</span></span>  
  
|<span data-ttu-id="ed281-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="ed281-145">Element</span></span>|<span data-ttu-id="ed281-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed281-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed281-147">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ed281-147">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="ed281-148">Bir izleme katılımcısı içindeki iş akışı izleme kayıtlarına abonelik oluşturmak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ed281-148">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="ed281-149">Bir izleme profili, bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="ed281-149">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="ed281-150">İzleme profili bölümü içinde tanımlanan sorgular, aboneliğin döndürdüğü olay türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ed281-150">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed281-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed281-151">Remarks</span></span>  
 <span data-ttu-id="ed281-152">İzleme profilleri, belirli bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="ed281-152">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="ed281-153">İzlenmekte olan iş akışı örneği bu yapılandırma öğesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ed281-153">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="ed281-154">Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="ed281-154">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="ed281-155">Buna karşılık, daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok özel bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed281-155">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="ed281-156">İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanızı sağlayan kayıtları izlemek için bildirim temelli abonelikler olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ed281-156">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="ed281-157">Farklı izleme kayıt sınıflarına abone olmanızı sağlayan bir dizi sorgu türü vardır.</span><span class="sxs-lookup"><span data-stu-id="ed281-157">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="ed281-158">Sorguların tüm listesi için, bu konunun alt öğe listesi ve [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)' ne bakın.</span><span class="sxs-lookup"><span data-stu-id="ed281-158">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="ed281-159">Aşağıdaki örnek, bir yapılandırma dosyasında izleme katılımcısının `Started` ve `Completed` iş akışı olaylarına abone olmasına izin veren bir izleme profilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed281-159">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ed281-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed281-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="ed281-161">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="ed281-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ed281-162">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="ed281-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
