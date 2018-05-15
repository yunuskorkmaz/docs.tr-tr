---
title: WCF &lt;durumu&gt;, &lt;workflowInstanceQuery&gt;
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 69ebedec40243d3e6580b8350c1253fca83e0802
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="3593f-102">WCF &lt;durumu&gt;, &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="3593f-102">&lt;state&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="3593f-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3593f-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="3593f-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3593f-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="3593f-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3593f-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3593f-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="3593f-106">\<tracking></span></span>  
<span data-ttu-id="3593f-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3593f-107">\<trackingProfile></span></span>  
<span data-ttu-id="3593f-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="3593f-108">\<workflow></span></span>  
<span data-ttu-id="3593f-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="3593f-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="3593f-110">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="3593f-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="3593f-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="3593f-111">\<states></span></span>  
<span data-ttu-id="3593f-112">\<durumu ></span><span class="sxs-lookup"><span data-stu-id="3593f-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3593f-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3593f-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3593f-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3593f-114">Attributes and Elements</span></span>  
 <span data-ttu-id="3593f-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3593f-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3593f-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3593f-116">Attributes</span></span>  
  
|<span data-ttu-id="3593f-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3593f-117">Attribute</span></span>|<span data-ttu-id="3593f-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3593f-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3593f-119">name</span><span class="sxs-lookup"><span data-stu-id="3593f-119">name</span></span>|<span data-ttu-id="3593f-120">İzleme kayıt oluşturulduğunda izlenen iş akışı örneği abone durumundan belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3593f-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3593f-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3593f-121">Child Elements</span></span>  
 <span data-ttu-id="3593f-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="3593f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3593f-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3593f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3593f-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="3593f-124">Element</span></span>|<span data-ttu-id="3593f-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3593f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3593f-126">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="3593f-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="3593f-127">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3593f-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3593f-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3593f-128">Remarks</span></span>  
 <span data-ttu-id="3593f-129">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3593f-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="3593f-130">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="3593f-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="3593f-131">Durum</span><span class="sxs-lookup"><span data-stu-id="3593f-131">State</span></span>|<span data-ttu-id="3593f-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3593f-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3593f-133">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="3593f-133">Aborted</span></span>|<span data-ttu-id="3593f-134">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="3593f-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="3593f-135">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="3593f-135">Completed</span></span>|<span data-ttu-id="3593f-136">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="3593f-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="3593f-137">Silindi</span><span class="sxs-lookup"><span data-stu-id="3593f-137">Deleted</span></span>|<span data-ttu-id="3593f-138">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="3593f-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="3593f-139">Boş</span><span class="sxs-lookup"><span data-stu-id="3593f-139">Idle</span></span>|<span data-ttu-id="3593f-140">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="3593f-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="3593f-141">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="3593f-141">Persisted</span></span>|<span data-ttu-id="3593f-142">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="3593f-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="3593f-143">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="3593f-143">Resumed</span></span>|<span data-ttu-id="3593f-144">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="3593f-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="3593f-145">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="3593f-145">Started</span></span>|<span data-ttu-id="3593f-146">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3593f-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="3593f-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="3593f-147">UnhandledException</span></span>|<span data-ttu-id="3593f-148">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="3593f-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="3593f-149">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="3593f-149">Unloaded</span></span>|<span data-ttu-id="3593f-150">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="3593f-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="3593f-151">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="3593f-151">Canceled</span></span>|<span data-ttu-id="3593f-152">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="3593f-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="3593f-153">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="3593f-153">Suspended</span></span>|<span data-ttu-id="3593f-154">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="3593f-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="3593f-155">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="3593f-155">Terminated</span></span>|<span data-ttu-id="3593f-156">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="3593f-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="3593f-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="3593f-157">Unsuspended</span></span>|<span data-ttu-id="3593f-158">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="3593f-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3593f-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="3593f-159">Example</span></span>  
 <span data-ttu-id="3593f-160">Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="3593f-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3593f-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3593f-161">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="3593f-162">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="3593f-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="3593f-163">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="3593f-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
