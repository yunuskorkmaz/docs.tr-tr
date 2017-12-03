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
ms.openlocfilehash: e5e9050a01cf58c3c103fdbe4e8b22e173efaf5c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltstatesgt"></a><span data-ttu-id="b1ffd-102">&lt;durumları&gt;</span><span class="sxs-lookup"><span data-stu-id="b1ffd-102">&lt;states&gt;</span></span>
<span data-ttu-id="b1ffd-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="b1ffd-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b1ffd-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="b1ffd-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b1ffd-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b1ffd-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="b1ffd-106">\<tracking></span></span>  
<span data-ttu-id="b1ffd-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b1ffd-107">\<trackingProfile></span></span>  
<span data-ttu-id="b1ffd-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="b1ffd-108">\<workflow></span></span>  
<span data-ttu-id="b1ffd-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="b1ffd-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="b1ffd-110">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="b1ffd-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="b1ffd-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="b1ffd-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1ffd-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1ffd-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1ffd-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1ffd-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b1ffd-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1ffd-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b1ffd-115">Attributes</span></span>  
 <span data-ttu-id="b1ffd-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b1ffd-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1ffd-117">Child Elements</span></span>  
  
|<span data-ttu-id="b1ffd-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1ffd-118">Element</span></span>|<span data-ttu-id="b1ffd-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1ffd-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1ffd-120">\<durumu ></span><span class="sxs-lookup"><span data-stu-id="b1ffd-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="b1ffd-121">İzleme kayıt oluşturulduğunda izlenen iş akışı örneği abone durumundan.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1ffd-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1ffd-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b1ffd-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1ffd-123">Element</span></span>|<span data-ttu-id="b1ffd-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1ffd-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1ffd-125">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="b1ffd-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="b1ffd-126">Başlatılan ya da tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1ffd-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1ffd-127">Remarks</span></span>  
 <span data-ttu-id="b1ffd-128">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="b1ffd-129">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="b1ffd-130">Durum</span><span class="sxs-lookup"><span data-stu-id="b1ffd-130">State</span></span>|<span data-ttu-id="b1ffd-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1ffd-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b1ffd-132">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="b1ffd-132">Aborted</span></span>|<span data-ttu-id="b1ffd-133">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="b1ffd-134">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="b1ffd-134">Completed</span></span>|<span data-ttu-id="b1ffd-135">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="b1ffd-136">Silindi</span><span class="sxs-lookup"><span data-stu-id="b1ffd-136">Deleted</span></span>|<span data-ttu-id="b1ffd-137">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="b1ffd-138">Boş</span><span class="sxs-lookup"><span data-stu-id="b1ffd-138">Idle</span></span>|<span data-ttu-id="b1ffd-139">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="b1ffd-140">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="b1ffd-140">Persisted</span></span>|<span data-ttu-id="b1ffd-141">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="b1ffd-142">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="b1ffd-142">Resumed</span></span>|<span data-ttu-id="b1ffd-143">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="b1ffd-144">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="b1ffd-144">Started</span></span>|<span data-ttu-id="b1ffd-145">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="b1ffd-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="b1ffd-146">UnhandledException</span></span>|<span data-ttu-id="b1ffd-147">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="b1ffd-148">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="b1ffd-148">Unloaded</span></span>|<span data-ttu-id="b1ffd-149">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="b1ffd-150">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="b1ffd-150">Canceled</span></span>|<span data-ttu-id="b1ffd-151">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="b1ffd-152">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="b1ffd-152">Suspended</span></span>|<span data-ttu-id="b1ffd-153">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="b1ffd-154">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="b1ffd-154">Terminated</span></span>|<span data-ttu-id="b1ffd-155">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="b1ffd-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="b1ffd-156">Unsuspended</span></span>|<span data-ttu-id="b1ffd-157">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b1ffd-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1ffd-158">Example</span></span>  
 <span data-ttu-id="b1ffd-159">Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1ffd-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1ffd-160">See Also</span></span>  
 <span data-ttu-id="b1ffd-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b1ffd-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b1ffd-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b1ffd-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b1ffd-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b1ffd-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b1ffd-164">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="b1ffd-164">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b1ffd-165">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="b1ffd-165">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
