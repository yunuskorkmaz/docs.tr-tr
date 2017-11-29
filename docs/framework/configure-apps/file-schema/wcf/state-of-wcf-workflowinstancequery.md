---
title: WCF &lt;durumu&gt;, &lt;workflowInstanceQuery&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e26a55323ceedd06ceadbee6d993306411aa114a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="6e62a-102">WCF &lt;durumu&gt;, &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="6e62a-102">&lt;state&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="6e62a-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e62a-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="6e62a-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6e62a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="6e62a-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="6e62a-105">\<system.serviceModel></span></span>  
<span data-ttu-id="6e62a-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="6e62a-106">\<tracking></span></span>  
<span data-ttu-id="6e62a-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="6e62a-107">\<trackingProfile></span></span>  
<span data-ttu-id="6e62a-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="6e62a-108">\<workflow></span></span>  
<span data-ttu-id="6e62a-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="6e62a-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="6e62a-110">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="6e62a-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="6e62a-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="6e62a-111">\<states></span></span>  
<span data-ttu-id="6e62a-112">\<durumu ></span><span class="sxs-lookup"><span data-stu-id="6e62a-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e62a-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e62a-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e62a-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e62a-114">Attributes and Elements</span></span>  
 <span data-ttu-id="6e62a-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e62a-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e62a-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6e62a-116">Attributes</span></span>  
  
|<span data-ttu-id="6e62a-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6e62a-117">Attribute</span></span>|<span data-ttu-id="6e62a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e62a-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6e62a-119">name</span><span class="sxs-lookup"><span data-stu-id="6e62a-119">name</span></span>|<span data-ttu-id="6e62a-120">İzleme kayıt oluşturulduğunda izlenen iş akışı örneği abone durumundan belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="6e62a-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e62a-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e62a-121">Child Elements</span></span>  
 <span data-ttu-id="6e62a-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="6e62a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e62a-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e62a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6e62a-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e62a-124">Element</span></span>|<span data-ttu-id="6e62a-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e62a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e62a-126">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="6e62a-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="6e62a-127">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6e62a-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e62a-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e62a-128">Remarks</span></span>  
 <span data-ttu-id="6e62a-129">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6e62a-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="6e62a-130">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="6e62a-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="6e62a-131">Durum</span><span class="sxs-lookup"><span data-stu-id="6e62a-131">State</span></span>|<span data-ttu-id="6e62a-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e62a-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6e62a-133">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="6e62a-133">Aborted</span></span>|<span data-ttu-id="6e62a-134">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6e62a-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="6e62a-135">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="6e62a-135">Completed</span></span>|<span data-ttu-id="6e62a-136">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="6e62a-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="6e62a-137">Silindi</span><span class="sxs-lookup"><span data-stu-id="6e62a-137">Deleted</span></span>|<span data-ttu-id="6e62a-138">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="6e62a-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="6e62a-139">Boş</span><span class="sxs-lookup"><span data-stu-id="6e62a-139">Idle</span></span>|<span data-ttu-id="6e62a-140">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="6e62a-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="6e62a-141">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="6e62a-141">Persisted</span></span>|<span data-ttu-id="6e62a-142">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="6e62a-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="6e62a-143">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="6e62a-143">Resumed</span></span>|<span data-ttu-id="6e62a-144">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="6e62a-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="6e62a-145">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="6e62a-145">Started</span></span>|<span data-ttu-id="6e62a-146">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="6e62a-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="6e62a-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="6e62a-147">UnhandledException</span></span>|<span data-ttu-id="6e62a-148">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="6e62a-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="6e62a-149">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="6e62a-149">Unloaded</span></span>|<span data-ttu-id="6e62a-150">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="6e62a-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="6e62a-151">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="6e62a-151">Canceled</span></span>|<span data-ttu-id="6e62a-152">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6e62a-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="6e62a-153">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="6e62a-153">Suspended</span></span>|<span data-ttu-id="6e62a-154">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="6e62a-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="6e62a-155">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="6e62a-155">Terminated</span></span>|<span data-ttu-id="6e62a-156">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="6e62a-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="6e62a-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="6e62a-157">Unsuspended</span></span>|<span data-ttu-id="6e62a-158">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="6e62a-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6e62a-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e62a-159">Example</span></span>  
 <span data-ttu-id="6e62a-160">Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="6e62a-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e62a-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e62a-161">See Also</span></span>  
 <span data-ttu-id="6e62a-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6e62a-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="6e62a-163"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6e62a-163"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="6e62a-164"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6e62a-164"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="6e62a-165">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="6e62a-165">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="6e62a-166">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="6e62a-166">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
