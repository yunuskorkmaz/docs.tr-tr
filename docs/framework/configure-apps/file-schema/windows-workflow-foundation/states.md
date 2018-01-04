---
title: "&lt;durumları&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c73ff606d9b8cdaf069b65f7faa48431a974123
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltstatesgt"></a><span data-ttu-id="e0206-102">&lt;durumları&gt;</span><span class="sxs-lookup"><span data-stu-id="e0206-102">&lt;states&gt;</span></span>
<span data-ttu-id="e0206-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e0206-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="e0206-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e0206-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e0206-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e0206-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e0206-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="e0206-106">\<tracking></span></span>  
<span data-ttu-id="e0206-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e0206-107">\<trackingProfile></span></span>  
<span data-ttu-id="e0206-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="e0206-108">\<workflow></span></span>  
<span data-ttu-id="e0206-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="e0206-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="e0206-110">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="e0206-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="e0206-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="e0206-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0206-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0206-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0206-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0206-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e0206-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0206-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0206-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e0206-115">Attributes</span></span>  
 <span data-ttu-id="e0206-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0206-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e0206-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0206-117">Child Elements</span></span>  
  
|<span data-ttu-id="e0206-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0206-118">Element</span></span>|<span data-ttu-id="e0206-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0206-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0206-120">\<durumu ></span><span class="sxs-lookup"><span data-stu-id="e0206-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="e0206-121">İzleme kayıt oluşturulduğunda izlenen iş akışı örneği abone durumundan.</span><span class="sxs-lookup"><span data-stu-id="e0206-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e0206-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0206-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e0206-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0206-123">Element</span></span>|<span data-ttu-id="e0206-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0206-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0206-125">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="e0206-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="e0206-126">Başlatılan ya da tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="e0206-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0206-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0206-127">Remarks</span></span>  
 <span data-ttu-id="e0206-128">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e0206-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="e0206-129">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="e0206-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="e0206-130">Durum</span><span class="sxs-lookup"><span data-stu-id="e0206-130">State</span></span>|<span data-ttu-id="e0206-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0206-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e0206-132">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="e0206-132">Aborted</span></span>|<span data-ttu-id="e0206-133">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e0206-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="e0206-134">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="e0206-134">Completed</span></span>|<span data-ttu-id="e0206-135">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e0206-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="e0206-136">Silindi</span><span class="sxs-lookup"><span data-stu-id="e0206-136">Deleted</span></span>|<span data-ttu-id="e0206-137">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="e0206-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="e0206-138">Boş</span><span class="sxs-lookup"><span data-stu-id="e0206-138">Idle</span></span>|<span data-ttu-id="e0206-139">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="e0206-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="e0206-140">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="e0206-140">Persisted</span></span>|<span data-ttu-id="e0206-141">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="e0206-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="e0206-142">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="e0206-142">Resumed</span></span>|<span data-ttu-id="e0206-143">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="e0206-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="e0206-144">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="e0206-144">Started</span></span>|<span data-ttu-id="e0206-145">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="e0206-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="e0206-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="e0206-146">UnhandledException</span></span>|<span data-ttu-id="e0206-147">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="e0206-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="e0206-148">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="e0206-148">Unloaded</span></span>|<span data-ttu-id="e0206-149">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="e0206-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="e0206-150">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="e0206-150">Canceled</span></span>|<span data-ttu-id="e0206-151">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e0206-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="e0206-152">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="e0206-152">Suspended</span></span>|<span data-ttu-id="e0206-153">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="e0206-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="e0206-154">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="e0206-154">Terminated</span></span>|<span data-ttu-id="e0206-155">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="e0206-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="e0206-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="e0206-156">Unsuspended</span></span>|<span data-ttu-id="e0206-157">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="e0206-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e0206-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0206-158">Example</span></span>  
 <span data-ttu-id="e0206-159">Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="e0206-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0206-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0206-160">See Also</span></span>  
 <span data-ttu-id="e0206-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e0206-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e0206-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e0206-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e0206-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e0206-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="e0206-164">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="e0206-164">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e0206-165">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="e0206-165">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
