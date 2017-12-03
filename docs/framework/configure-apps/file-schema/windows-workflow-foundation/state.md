---
title: '&lt;durumu&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f1ed21f359e9f0e2b07154bc37d3352dd52db12
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltstategt"></a><span data-ttu-id="7b2f1-102">&lt;durumu&gt;</span><span class="sxs-lookup"><span data-stu-id="7b2f1-102">&lt;state&gt;</span></span>
<span data-ttu-id="7b2f1-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="7b2f1-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7b2f1-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7b2f1-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7b2f1-105">\<system.serviceModel></span></span>  
<span data-ttu-id="7b2f1-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="7b2f1-106">\<tracking></span></span>  
<span data-ttu-id="7b2f1-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="7b2f1-107">\<trackingProfile></span></span>  
<span data-ttu-id="7b2f1-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="7b2f1-108">\<workflow></span></span>  
<span data-ttu-id="7b2f1-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="7b2f1-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="7b2f1-110">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="7b2f1-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="7b2f1-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="7b2f1-111">\<states></span></span>  
<span data-ttu-id="7b2f1-112">\<durumu ></span><span class="sxs-lookup"><span data-stu-id="7b2f1-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b2f1-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b2f1-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b2f1-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b2f1-114">Attributes and Elements</span></span>  
 <span data-ttu-id="7b2f1-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b2f1-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7b2f1-116">Attributes</span></span>  
  
|<span data-ttu-id="7b2f1-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7b2f1-117">Attribute</span></span>|<span data-ttu-id="7b2f1-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b2f1-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7b2f1-119">name</span><span class="sxs-lookup"><span data-stu-id="7b2f1-119">name</span></span>|<span data-ttu-id="7b2f1-120">İzleme kayıt oluşturulduğunda izlenen iş akışı örneği abone durumundan belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b2f1-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b2f1-121">Child Elements</span></span>  
 <span data-ttu-id="7b2f1-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b2f1-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b2f1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7b2f1-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="7b2f1-124">Element</span></span>|<span data-ttu-id="7b2f1-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b2f1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b2f1-126">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="7b2f1-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="7b2f1-127">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b2f1-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b2f1-128">Remarks</span></span>  
 <span data-ttu-id="7b2f1-129">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="7b2f1-130">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="7b2f1-131">Durum</span><span class="sxs-lookup"><span data-stu-id="7b2f1-131">State</span></span>|<span data-ttu-id="7b2f1-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b2f1-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7b2f1-133">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="7b2f1-133">Aborted</span></span>|<span data-ttu-id="7b2f1-134">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="7b2f1-135">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="7b2f1-135">Completed</span></span>|<span data-ttu-id="7b2f1-136">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="7b2f1-137">Silindi</span><span class="sxs-lookup"><span data-stu-id="7b2f1-137">Deleted</span></span>|<span data-ttu-id="7b2f1-138">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="7b2f1-139">Boş</span><span class="sxs-lookup"><span data-stu-id="7b2f1-139">Idle</span></span>|<span data-ttu-id="7b2f1-140">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="7b2f1-141">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="7b2f1-141">Persisted</span></span>|<span data-ttu-id="7b2f1-142">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="7b2f1-143">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="7b2f1-143">Resumed</span></span>|<span data-ttu-id="7b2f1-144">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="7b2f1-145">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="7b2f1-145">Started</span></span>|<span data-ttu-id="7b2f1-146">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="7b2f1-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="7b2f1-147">UnhandledException</span></span>|<span data-ttu-id="7b2f1-148">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="7b2f1-149">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="7b2f1-149">Unloaded</span></span>|<span data-ttu-id="7b2f1-150">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="7b2f1-151">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="7b2f1-151">Canceled</span></span>|<span data-ttu-id="7b2f1-152">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="7b2f1-153">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="7b2f1-153">Suspended</span></span>|<span data-ttu-id="7b2f1-154">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="7b2f1-155">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="7b2f1-155">Terminated</span></span>|<span data-ttu-id="7b2f1-156">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="7b2f1-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="7b2f1-157">Unsuspended</span></span>|<span data-ttu-id="7b2f1-158">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7b2f1-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b2f1-159">Example</span></span>  
 <span data-ttu-id="7b2f1-160">Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b2f1-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-161">See Also</span></span>  
 <span data-ttu-id="7b2f1-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7b2f1-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="7b2f1-163"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7b2f1-163"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="7b2f1-164"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7b2f1-164"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>      
 [<span data-ttu-id="7b2f1-165">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="7b2f1-165">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="7b2f1-166">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="7b2f1-166">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
