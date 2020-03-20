---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: e2df5d83375b2daa2e39ba1ee990c47a6a04f6fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151864"
---
# <a name="workflow"></a><span data-ttu-id="f8bc0-101">\<iş akışı></span><span class="sxs-lookup"><span data-stu-id="f8bc0-101">\<workflow></span></span>
<span data-ttu-id="f8bc0-102">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-102">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="f8bc0-103">İş akışı izleme ve yapılandırmasında daha fazla bilgi için [İş Akışı İzleme ve İzleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve İzleme [Profilleri'ne](../../../windows-workflow-foundation/tracking-profiles.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="f8bc0-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f8bc0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f8bc0-105">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f8bc0-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="f8bc0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="f8bc0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="f8bc0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<izlemeProfil>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="f8bc0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="f8bc0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<iş akışı>**</span><span class="sxs-lookup"><span data-stu-id="f8bc0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflow>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8bc0-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f8bc0-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8bc0-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f8bc0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f8bc0-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8bc0-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f8bc0-112">Attributes</span></span>  
  
|<span data-ttu-id="f8bc0-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f8bc0-113">Attribute</span></span>|<span data-ttu-id="f8bc0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8bc0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f8bc0-115">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="f8bc0-115">activityDefinitionId</span></span>|<span data-ttu-id="f8bc0-116">İzlenen iş akışının etkinlik tanım kimliğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-116">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8bc0-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f8bc0-117">Child Elements</span></span>  
  
|<span data-ttu-id="f8bc0-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="f8bc0-118">Element</span></span>|<span data-ttu-id="f8bc0-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8bc0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8bc0-120">\<etkinlikPlanlanmışSorgular></span><span class="sxs-lookup"><span data-stu-id="f8bc0-120">\<activityScheduledQueries></span></span>](activityscheduledqueries.md)|<span data-ttu-id="f8bc0-121">Bir üst etkinlik tarafından yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgukoleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-121">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="f8bc0-122">Sorgu, bir izleme katılımcısının etkinlik zamanlanan kayıtlara abone olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-122">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="f8bc0-123">\<etkinlikStateQueries></span><span class="sxs-lookup"><span data-stu-id="f8bc0-123">\<activityStateQueries></span></span>](activitystatequeries.md)|<span data-ttu-id="f8bc0-124">İş akışı örneğini oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-124">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="f8bc0-125">Örneğin, "E-Posta Gönder" etkinliği bir iş akışı örneği içinde her tamamlandığında izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-125">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="f8bc0-126">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesneleri abone olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-126">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="f8bc0-127">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-127">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="f8bc0-128">\<yer imiDevamıSorgular></span><span class="sxs-lookup"><span data-stu-id="f8bc0-128">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="f8bc0-129">İş akışı örneği içinde yer işaretinin yeniden başlatılmasını izlemek için kullanılan sorgukoleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-129">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="f8bc0-130">Sorgu, bir izleme katılımcısının devam kayıtlarını yer imine abone olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-130">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="f8bc0-131">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="f8bc0-131">\<cancelRequestedQueries></span></span>](cancelrequestedqueries.md)|<span data-ttu-id="f8bc0-132">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek için kullanılan sorgukoleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-132">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="f8bc0-133">Sorgu, bir izleme katılımcısının istek kayıt nesnelerini iptal etmek için abone olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-133">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="f8bc0-134">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="f8bc0-134">\<customTrackingQueries></span></span>](customtrackingqueries.md)|<span data-ttu-id="f8bc0-135">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-135">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="f8bc0-136">Sorgu, bir izleme katılımcısının özel izleme kayıtlarına abone olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-136">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="f8bc0-137">\<hata YayılımSorgular></span><span class="sxs-lookup"><span data-stu-id="f8bc0-137">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="f8bc0-138">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan sorgukoleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-138">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f8bc0-139">Bu olay, bir Hata Handler bir hatayı her işlerde oluşur.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-139">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="f8bc0-140">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için bu tür sorguyu kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-140">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="f8bc0-141">Sorgu, bir izleme katılımcısının hata yayma kayıtlarına abone olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-141">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="f8bc0-142">\<iş akışıInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="f8bc0-142">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="f8bc0-143">Başlatılan veya tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğeleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-143">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f8bc0-144">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f8bc0-144">Parent Elements</span></span>  
  
|<span data-ttu-id="f8bc0-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="f8bc0-145">Element</span></span>|<span data-ttu-id="f8bc0-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8bc0-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8bc0-147">\<izlemeProfil></span><span class="sxs-lookup"><span data-stu-id="f8bc0-147">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="f8bc0-148">İzleme katılımcısında iş akışı izleme kayıtlarına abonelik oluşturmak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-148">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="f8bc0-149">İzleme profili, bir izleme katılımcısının çalışma zamanında iş akışı örneği durumu değiştiğinde yayılan iş akışı olaylarına abone olmasını sağlayan izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-149">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="f8bc0-150">İzleme profili bölümünde tanımlanan sorgular, abonelik tarafından döndürülen olay türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-150">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8bc0-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8bc0-151">Remarks</span></span>  
 <span data-ttu-id="f8bc0-152">İzleme profilleri, belirli bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayılan iş akışı olaylarına abone olmak için izleme katılımcısının izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-152">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="f8bc0-153">İzlenen iş akışı örneği bu yapılandırma öğesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-153">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="f8bc0-154">Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-154">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="f8bc0-155">Tersine, ortaya çıkan olaylar daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok özel bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-155">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="f8bc0-156">İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanıza olanak tanıyan kayıtları izlemek için bildirimsel abonelikler olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-156">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="f8bc0-157">Farklı izleme kayıtları sınıflarına abone olsanız sağlayan bir avuç sorgu türü vardır.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-157">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="f8bc0-158">Sorguların tam listesi için, bu konunun alt öğe öğesi listesine ve [İzleme Profilleri'ne](../../../windows-workflow-foundation/tracking-profiles.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-158">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="f8bc0-159">Aşağıdaki örnek, bir yapılandırma dosyasındaki bir izleme katılımcısının iş `Started` `Completed` akışı olaylarına abone olmasını sağlayan bir izleme profilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-159">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8bc0-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8bc0-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="f8bc0-161">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f8bc0-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f8bc0-162">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f8bc0-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
