---
title: <state>WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 99387a8f60e96beb2ec7706d9abf4bb6ae84b868
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938215"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="07306-102">\<WCF, \<WorkflowInstanceQuery > durum ></span><span class="sxs-lookup"><span data-stu-id="07306-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="07306-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07306-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="07306-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="07306-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="07306-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="07306-105">\<system.serviceModel></span></span>  
<span data-ttu-id="07306-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="07306-106">\<tracking></span></span>  
<span data-ttu-id="07306-107">\<Profiller ></span><span class="sxs-lookup"><span data-stu-id="07306-107">\<profiles></span></span>  
<span data-ttu-id="07306-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="07306-108">\<trackingProfile></span></span>  
<span data-ttu-id="07306-109">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="07306-109">\<workflow></span></span>  
<span data-ttu-id="07306-110">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="07306-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="07306-111">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="07306-111">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="07306-112">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="07306-112">\<states></span></span>  
<span data-ttu-id="07306-113">\<durum ></span><span class="sxs-lookup"><span data-stu-id="07306-113">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07306-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07306-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07306-115">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="07306-115">Attributes and elements</span></span>

<span data-ttu-id="07306-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="07306-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="07306-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="07306-117">Attributes</span></span>

|<span data-ttu-id="07306-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="07306-118">Attribute</span></span>|<span data-ttu-id="07306-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07306-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="07306-120">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durumu belirten dize.</span><span class="sxs-lookup"><span data-stu-id="07306-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07306-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="07306-121">Child elements</span></span>

<span data-ttu-id="07306-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="07306-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="07306-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="07306-123">Parent elements</span></span>

|<span data-ttu-id="07306-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="07306-124">Element</span></span>|<span data-ttu-id="07306-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07306-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07306-126">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="07306-126">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="07306-127">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="07306-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07306-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07306-128">Remarks</span></span>  

<span data-ttu-id="07306-129">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="07306-129">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="07306-130">Olası durum değerleri aşağıdaki tabloda açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="07306-130">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="07306-131">Durum</span><span class="sxs-lookup"><span data-stu-id="07306-131">State</span></span>|<span data-ttu-id="07306-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07306-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07306-133">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="07306-133">Aborted</span></span>|<span data-ttu-id="07306-134">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="07306-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="07306-135">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="07306-135">Completed</span></span>|<span data-ttu-id="07306-136">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="07306-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="07306-137">Silindi</span><span class="sxs-lookup"><span data-stu-id="07306-137">Deleted</span></span>|<span data-ttu-id="07306-138">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="07306-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="07306-139">Boş</span><span class="sxs-lookup"><span data-stu-id="07306-139">Idle</span></span>|<span data-ttu-id="07306-140">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="07306-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="07306-141">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="07306-141">Persisted</span></span>|<span data-ttu-id="07306-142">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="07306-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="07306-143">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="07306-143">Resumed</span></span>|<span data-ttu-id="07306-144">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="07306-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="07306-145">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="07306-145">Started</span></span>|<span data-ttu-id="07306-146">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="07306-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="07306-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="07306-147">UnhandledException</span></span>|<span data-ttu-id="07306-148">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="07306-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="07306-149">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="07306-149">Unloaded</span></span>|<span data-ttu-id="07306-150">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="07306-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="07306-151">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="07306-151">Canceled</span></span>|<span data-ttu-id="07306-152">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="07306-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="07306-153">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="07306-153">Suspended</span></span>|<span data-ttu-id="07306-154">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="07306-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="07306-155">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="07306-155">Terminated</span></span>|<span data-ttu-id="07306-156">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="07306-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="07306-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="07306-157">Unsuspended</span></span>|<span data-ttu-id="07306-158">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="07306-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="07306-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="07306-159">Example</span></span>

<span data-ttu-id="07306-160">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="07306-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="07306-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07306-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="07306-162">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="07306-162">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="07306-163">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="07306-163">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
