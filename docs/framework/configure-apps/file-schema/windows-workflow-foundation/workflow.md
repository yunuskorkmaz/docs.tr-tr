---
title: '&lt;İş akışı&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: dc7c693fb2d8b47c0b968eb51cc59327fe43bcc0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltworkflowgt"></a><span data-ttu-id="3ddde-102">&lt;İş akışı&gt;</span><span class="sxs-lookup"><span data-stu-id="3ddde-102">&lt;workflow&gt;</span></span>
<span data-ttu-id="3ddde-103">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **bir HYPERLINK "http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="3ddde-103">A configuration element that contains all queries for a specific workflow identified by the **a HYPERLINK "http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId** property.</span></span>  
  
 <span data-ttu-id="3ddde-104">İş akışı izleme ve yapılandırmasını daha fazla bilgi için bkz: [izleme ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="3ddde-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="3ddde-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3ddde-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3ddde-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="3ddde-106">\<tracking></span></span>  
<span data-ttu-id="3ddde-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3ddde-107">\<trackingProfile></span></span>  
<span data-ttu-id="3ddde-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="3ddde-108">\<workflow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ddde-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ddde-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ddde-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ddde-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3ddde-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3ddde-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ddde-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3ddde-112">Attributes</span></span>  
  
|<span data-ttu-id="3ddde-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3ddde-113">Attribute</span></span>|<span data-ttu-id="3ddde-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ddde-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ddde-115">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="3ddde-115">activityDefinitionId</span></span>|<span data-ttu-id="3ddde-116">İzlenmekte olan iş akışı etkinlik tanımı Kimliğini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3ddde-116">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ddde-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ddde-117">Child Elements</span></span>  
  
|<span data-ttu-id="3ddde-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="3ddde-118">Element</span></span>|<span data-ttu-id="3ddde-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ddde-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ddde-120">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="3ddde-120">\<activityScheduledQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledqueries.md)|<span data-ttu-id="3ddde-121">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ddde-121">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="3ddde-122">Sorgu için zamanlanan etkinlik kayıtlarını abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3ddde-122">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="3ddde-123">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="3ddde-123">\<activityStateQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequeries.md)|<span data-ttu-id="3ddde-124">Bir iş akışı örneği olun etkinliklerin ömrünü değişiklikleri izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ddde-124">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="3ddde-125">Örneğin, bir iş akışı örneği içinde "E-posta Gönder" etkinlik tamamlandıktan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ddde-125">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="3ddde-126">Bu sorgu, etkinlik durumu kaydı nesnelere abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3ddde-126">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="3ddde-127">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="3ddde-127">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="3ddde-128">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="3ddde-128">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="3ddde-129">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ddde-129">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="3ddde-130">Sorgu yer işareti sürdürme kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3ddde-130">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="3ddde-131">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="3ddde-131">\<cancelRequestedQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedqueries.md)|<span data-ttu-id="3ddde-132">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ddde-132">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="3ddde-133">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3ddde-133">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="3ddde-134">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="3ddde-134">\<customTrackingQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingqueries.md)|<span data-ttu-id="3ddde-135">Kod etkinliklerinizi tanımladığınız olayları izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ddde-135">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="3ddde-136">Sorgu için özel izleme kayıtları abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3ddde-136">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="3ddde-137">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="3ddde-137">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="3ddde-138">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ddde-138">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="3ddde-139">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="3ddde-139">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="3ddde-140">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için bu tür sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ddde-140">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="3ddde-141">Sorgu Hatası yayma kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3ddde-141">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="3ddde-142">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="3ddde-142">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="3ddde-143">Başlatılan ya da tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izlemek yapılandırma öğelerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ddde-143">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ddde-144">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ddde-144">Parent Elements</span></span>  
  
|<span data-ttu-id="3ddde-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="3ddde-145">Element</span></span>|<span data-ttu-id="3ddde-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ddde-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ddde-147">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="3ddde-147">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="3ddde-148">İş akışı izleme katılımcı kayıtlarında izleme için bir abonelik oluşturmak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ddde-148">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="3ddde-149">İzleme profili çalışma zamanında bir iş akışı örneğinin durumu değiştiğinde, gösterilen iş akışı olayları abone olmak için izleme katılımcı izin izleme sorgularını içerir.</span><span class="sxs-lookup"><span data-stu-id="3ddde-149">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="3ddde-150">Tanımlanan sorguları izleme profilinde bölüm abonelik tarafından döndürülen olayları türlerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3ddde-150">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ddde-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ddde-151">Remarks</span></span>  
 <span data-ttu-id="3ddde-152">Profilleri izleme çalışma zamanında belirli iş akışı örneğinin durumu değiştiğinde, gösterilen iş akışı olayları abone olmak için izleme katılımcı izin izleme sorgularını içerir.</span><span class="sxs-lookup"><span data-stu-id="3ddde-152">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="3ddde-153">İzlenmekte olan iş akışı örneği bu yapılandırma öğesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3ddde-153">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="3ddde-154">Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="3ddde-154">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="3ddde-155">Buna karşılık, sonuçta ortaya çıkan, olayları ayrıntılı yürütme akışı daha sonra yeniden oluşturmak için zengin çok belirli bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ddde-155">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="3ddde-156">İzleme profilleri belirli izleme kayıtları için iş akışı çalışma zamanı sorgu izin kayıtları izleme için bildirim temelli abonelikler olarak yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3ddde-156">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="3ddde-157">Kayıtları İzleme farklı sınıflara abone izin sorgu türleri sayıda vardır.</span><span class="sxs-lookup"><span data-stu-id="3ddde-157">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="3ddde-158">Sorgu tam listesi için bu konuda alt öğe listesini görmek ve [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="3ddde-158">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="3ddde-159">Aşağıdaki örnek, bir izleme profili abone olmak izleme katılımcı izin veren bir yapılandırma dosyası gösterir `Started` ve `Completed` iş akışı olayları.</span><span class="sxs-lookup"><span data-stu-id="3ddde-159">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ddde-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ddde-160">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="3ddde-161">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="3ddde-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="3ddde-162">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="3ddde-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
