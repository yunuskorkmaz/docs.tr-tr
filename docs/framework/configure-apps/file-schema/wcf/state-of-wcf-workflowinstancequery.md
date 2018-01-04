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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edb6cc424be51e03b3c34182a2b456a9658e2bc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="2a95e-102">WCF &lt;durumu&gt;, &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="2a95e-102">&lt;state&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="2a95e-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2a95e-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="2a95e-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2a95e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="2a95e-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2a95e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="2a95e-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="2a95e-106">\<tracking></span></span>  
<span data-ttu-id="2a95e-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="2a95e-107">\<trackingProfile></span></span>  
<span data-ttu-id="2a95e-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="2a95e-108">\<workflow></span></span>  
<span data-ttu-id="2a95e-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="2a95e-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="2a95e-110">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="2a95e-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="2a95e-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="2a95e-111">\<states></span></span>  
<span data-ttu-id="2a95e-112">\<durumu ></span><span class="sxs-lookup"><span data-stu-id="2a95e-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a95e-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a95e-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a95e-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a95e-114">Attributes and Elements</span></span>  
 <span data-ttu-id="2a95e-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a95e-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a95e-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2a95e-116">Attributes</span></span>  
  
|<span data-ttu-id="2a95e-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2a95e-117">Attribute</span></span>|<span data-ttu-id="2a95e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a95e-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a95e-119">name</span><span class="sxs-lookup"><span data-stu-id="2a95e-119">name</span></span>|<span data-ttu-id="2a95e-120">İzleme kayıt oluşturulduğunda izlenen iş akışı örneği abone durumundan belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2a95e-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a95e-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a95e-121">Child Elements</span></span>  
 <span data-ttu-id="2a95e-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="2a95e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a95e-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a95e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2a95e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="2a95e-124">Element</span></span>|<span data-ttu-id="2a95e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a95e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a95e-126">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="2a95e-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="2a95e-127">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2a95e-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a95e-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a95e-128">Remarks</span></span>  
 <span data-ttu-id="2a95e-129">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2a95e-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="2a95e-130">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="2a95e-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="2a95e-131">Durum</span><span class="sxs-lookup"><span data-stu-id="2a95e-131">State</span></span>|<span data-ttu-id="2a95e-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a95e-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a95e-133">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="2a95e-133">Aborted</span></span>|<span data-ttu-id="2a95e-134">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="2a95e-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="2a95e-135">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="2a95e-135">Completed</span></span>|<span data-ttu-id="2a95e-136">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="2a95e-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="2a95e-137">Silindi</span><span class="sxs-lookup"><span data-stu-id="2a95e-137">Deleted</span></span>|<span data-ttu-id="2a95e-138">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="2a95e-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="2a95e-139">Boş</span><span class="sxs-lookup"><span data-stu-id="2a95e-139">Idle</span></span>|<span data-ttu-id="2a95e-140">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="2a95e-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="2a95e-141">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="2a95e-141">Persisted</span></span>|<span data-ttu-id="2a95e-142">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="2a95e-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="2a95e-143">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="2a95e-143">Resumed</span></span>|<span data-ttu-id="2a95e-144">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="2a95e-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="2a95e-145">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="2a95e-145">Started</span></span>|<span data-ttu-id="2a95e-146">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="2a95e-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="2a95e-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="2a95e-147">UnhandledException</span></span>|<span data-ttu-id="2a95e-148">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="2a95e-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="2a95e-149">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="2a95e-149">Unloaded</span></span>|<span data-ttu-id="2a95e-150">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="2a95e-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="2a95e-151">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="2a95e-151">Canceled</span></span>|<span data-ttu-id="2a95e-152">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="2a95e-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="2a95e-153">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="2a95e-153">Suspended</span></span>|<span data-ttu-id="2a95e-154">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="2a95e-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="2a95e-155">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="2a95e-155">Terminated</span></span>|<span data-ttu-id="2a95e-156">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="2a95e-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="2a95e-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="2a95e-157">Unsuspended</span></span>|<span data-ttu-id="2a95e-158">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="2a95e-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2a95e-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a95e-159">Example</span></span>  
 <span data-ttu-id="2a95e-160">Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="2a95e-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a95e-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a95e-161">See Also</span></span>  
 <span data-ttu-id="2a95e-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2a95e-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="2a95e-163"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2a95e-163"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="2a95e-164"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2a95e-164"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="2a95e-165">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="2a95e-165">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="2a95e-166">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="2a95e-166">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
