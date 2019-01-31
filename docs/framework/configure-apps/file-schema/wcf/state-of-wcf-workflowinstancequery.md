---
title: <state> WCF, <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 1615c83ffe0735d9e55e822f2651da41d02b1610
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270874"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="c9429-102">\<durumu >, WCF \<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="c9429-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="c9429-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c9429-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="c9429-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c9429-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c9429-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c9429-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c9429-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="c9429-106">\<tracking></span></span>  
<span data-ttu-id="c9429-107">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="c9429-107">\<profiles></span></span>  
<span data-ttu-id="c9429-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c9429-108">\<trackingProfile></span></span>  
<span data-ttu-id="c9429-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="c9429-109">\<workflow></span></span>  
<span data-ttu-id="c9429-110">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="c9429-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="c9429-111">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="c9429-111">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="c9429-112">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="c9429-112">\<states></span></span>  
<span data-ttu-id="c9429-113">\<Durum ></span><span class="sxs-lookup"><span data-stu-id="c9429-113">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9429-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9429-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
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
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9429-115">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="c9429-115">Attributes and elements</span></span>

<span data-ttu-id="c9429-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9429-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="c9429-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9429-117">Attributes</span></span>

|<span data-ttu-id="c9429-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9429-118">Attribute</span></span>|<span data-ttu-id="c9429-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9429-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="c9429-120">İzleme kayıt oluşturulduğunda izlenen iş akışı örneğinin abone olunan bir durumdan belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c9429-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9429-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c9429-121">Child elements</span></span>

<span data-ttu-id="c9429-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="c9429-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9429-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="c9429-123">Parent elements</span></span>

|<span data-ttu-id="c9429-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9429-124">Element</span></span>|<span data-ttu-id="c9429-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9429-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9429-126">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="c9429-126">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="c9429-127">Abone olunan durumları izleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c9429-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9429-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9429-128">Remarks</span></span>  

<span data-ttu-id="c9429-129">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c9429-129">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="c9429-130">Olası durum değerleri aşağıdaki tabloda açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="c9429-130">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="c9429-131">Durum</span><span class="sxs-lookup"><span data-stu-id="c9429-131">State</span></span>|<span data-ttu-id="c9429-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9429-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9429-133">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="c9429-133">Aborted</span></span>|<span data-ttu-id="c9429-134">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c9429-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="c9429-135">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="c9429-135">Completed</span></span>|<span data-ttu-id="c9429-136">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c9429-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="c9429-137">Silindi</span><span class="sxs-lookup"><span data-stu-id="c9429-137">Deleted</span></span>|<span data-ttu-id="c9429-138">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="c9429-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="c9429-139">Boş</span><span class="sxs-lookup"><span data-stu-id="c9429-139">Idle</span></span>|<span data-ttu-id="c9429-140">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="c9429-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="c9429-141">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="c9429-141">Persisted</span></span>|<span data-ttu-id="c9429-142">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="c9429-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="c9429-143">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="c9429-143">Resumed</span></span>|<span data-ttu-id="c9429-144">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="c9429-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="c9429-145">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="c9429-145">Started</span></span>|<span data-ttu-id="c9429-146">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="c9429-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="c9429-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="c9429-147">UnhandledException</span></span>|<span data-ttu-id="c9429-148">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="c9429-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="c9429-149">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="c9429-149">Unloaded</span></span>|<span data-ttu-id="c9429-150">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c9429-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="c9429-151">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="c9429-151">Canceled</span></span>|<span data-ttu-id="c9429-152">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c9429-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="c9429-153">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="c9429-153">Suspended</span></span>|<span data-ttu-id="c9429-154">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="c9429-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="c9429-155">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="c9429-155">Terminated</span></span>|<span data-ttu-id="c9429-156">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="c9429-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="c9429-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="c9429-157">Unsuspended</span></span>|<span data-ttu-id="c9429-158">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="c9429-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c9429-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9429-159">Example</span></span>

<span data-ttu-id="c9429-160">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="c9429-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="c9429-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9429-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c9429-162">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c9429-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c9429-163">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c9429-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
