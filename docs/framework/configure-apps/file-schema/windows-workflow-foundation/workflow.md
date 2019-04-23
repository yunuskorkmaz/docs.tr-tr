---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: d6c23bb0b819b5f22367a93db0dec64787449664
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136191"
---
# <a name="workflow"></a><span data-ttu-id="a7e35-101">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="a7e35-101">\<workflow></span></span>
<span data-ttu-id="a7e35-102">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a7e35-102">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="a7e35-103">İş akışı izleme ve kendi yapılandırmasını daha fazla bilgi için bkz: [takip ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a7e35-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a7e35-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a7e35-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a7e35-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="a7e35-105">\<tracking></span></span>  
<span data-ttu-id="a7e35-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a7e35-106">\<trackingProfile></span></span>  
<span data-ttu-id="a7e35-107">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="a7e35-107">\<workflow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e35-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7e35-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7e35-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7e35-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a7e35-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a7e35-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7e35-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a7e35-111">Attributes</span></span>  
  
|<span data-ttu-id="a7e35-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a7e35-112">Attribute</span></span>|<span data-ttu-id="a7e35-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7e35-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7e35-114">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="a7e35-114">activityDefinitionId</span></span>|<span data-ttu-id="a7e35-115">İzlenen iş akışı etkinlik tanımı kimliği belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a7e35-115">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7e35-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7e35-116">Child Elements</span></span>  
  
|<span data-ttu-id="a7e35-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7e35-117">Element</span></span>|<span data-ttu-id="a7e35-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7e35-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7e35-119">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="a7e35-119">\<activityScheduledQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledqueries.md)|<span data-ttu-id="a7e35-120">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a7e35-120">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="a7e35-121">Sorgu zamanlanmış etkinlik kayıtlarına abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a7e35-121">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="a7e35-122">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="a7e35-122">\<activityStateQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequeries.md)|<span data-ttu-id="a7e35-123">Yaşam döngüsü değişiklikleri bir iş akışı örneği oluşturan etkinliklerinin izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a7e35-123">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="a7e35-124">Örneğin, "E-posta Gönder" etkinlik içinde bir iş akışı örneği tamamlanan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7e35-124">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="a7e35-125">Bu sorgu, etkinlik durumu kayıt nesnelerine abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a7e35-125">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="a7e35-126">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a7e35-126">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="a7e35-127">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="a7e35-127">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="a7e35-128">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a7e35-128">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="a7e35-129">Sorgu için yer imi sürdürme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a7e35-129">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="a7e35-130">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="a7e35-130">\<cancelRequestedQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedqueries.md)|<span data-ttu-id="a7e35-131">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a7e35-131">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a7e35-132">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a7e35-132">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="a7e35-133">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="a7e35-133">\<customTrackingQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingqueries.md)|<span data-ttu-id="a7e35-134">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a7e35-134">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="a7e35-135">Sorgu özel izleme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a7e35-135">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="a7e35-136">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="a7e35-136">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="a7e35-137">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a7e35-137">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a7e35-138">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="a7e35-138">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="a7e35-139">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7e35-139">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="a7e35-140">Sorgu hata yayma kayıtlara abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a7e35-140">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="a7e35-141">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="a7e35-141">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="a7e35-142">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleme yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a7e35-142">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7e35-143">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7e35-143">Parent Elements</span></span>  
  
|<span data-ttu-id="a7e35-144">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7e35-144">Element</span></span>|<span data-ttu-id="a7e35-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7e35-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7e35-146">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="a7e35-146">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="a7e35-147">İş akışı izleme katılımcı kayıtlarında izleme aboneliği oluşturmak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a7e35-147">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="a7e35-148">Bir izleme profili çalışma zamanında bir iş akışı örneği durumu değiştiğinde yayılan iş akışı olayları abone olmak için izleme katılımcı izin izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="a7e35-148">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="a7e35-149">Tanımlanan sorguları izleme profilinde bölümü abonelik tarafından döndürülen olayları tür tanımlamak.</span><span class="sxs-lookup"><span data-stu-id="a7e35-149">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7e35-150">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7e35-150">Remarks</span></span>  
 <span data-ttu-id="a7e35-151">İzleme profilleri belirli bir iş akışı örneğinin durumunu çalışma zamanında değiştiğinde yayılan iş akışı olayları abone olmak için izleme katılımcı izin izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="a7e35-151">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="a7e35-152">İzlenen iş akışı örneği bu yapılandırma öğesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a7e35-152">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="a7e35-153">Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="a7e35-153">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="a7e35-154">Buna karşılık, elde edilen ayarlanmış olayları ayrıntılı yürütme akışı daha sonra yeniden oluşturmak için zengin bir çok özel profil oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="a7e35-154">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="a7e35-155">İzleme profilleri belirli izleme kayıtları için iş akışı çalışma zamanı sorgulamaya izin kayıtları izleme için bildirim abonelikleri olarak yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a7e35-155">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="a7e35-156">Birkaç kayıtları izleme farklı sınıfları için abone izin sorgu türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="a7e35-156">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="a7e35-157">Bu konu alt öğe listesi sorguları tam listesi için bkz ve [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a7e35-157">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="a7e35-158">Aşağıdaki örnek, abone olmak izleme katılımcı izin veren bir yapılandırma dosyasında bir izleme profili gösterir. `Started` ve `Completed` iş akışı olayları.</span><span class="sxs-lookup"><span data-stu-id="a7e35-158">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a7e35-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7e35-159">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="a7e35-160">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a7e35-160">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a7e35-161">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a7e35-161">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
