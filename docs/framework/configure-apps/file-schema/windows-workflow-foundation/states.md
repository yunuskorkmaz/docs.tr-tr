---
title: '&lt;durumları&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: d1ec35b1c434b8188fde7b546e2dee42a93f5c91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550584"
---
# <a name="ltstatesgt"></a><span data-ttu-id="3f217-102">&lt;durumları&gt;</span><span class="sxs-lookup"><span data-stu-id="3f217-102">&lt;states&gt;</span></span>
<span data-ttu-id="3f217-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3f217-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="3f217-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3f217-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="3f217-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3f217-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3f217-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="3f217-106">\<tracking></span></span>  
<span data-ttu-id="3f217-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3f217-107">\<trackingProfile></span></span>  
<span data-ttu-id="3f217-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="3f217-108">\<workflow></span></span>  
<span data-ttu-id="3f217-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="3f217-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="3f217-110">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="3f217-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="3f217-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="3f217-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f217-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f217-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f217-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f217-113">Attributes and Elements</span></span>  
 <span data-ttu-id="3f217-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f217-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f217-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3f217-115">Attributes</span></span>  
 <span data-ttu-id="3f217-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="3f217-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3f217-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f217-117">Child Elements</span></span>  
  
|<span data-ttu-id="3f217-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f217-118">Element</span></span>|<span data-ttu-id="3f217-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f217-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f217-120">\<Durum ></span><span class="sxs-lookup"><span data-stu-id="3f217-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="3f217-121">İzleme kayıt oluşturulduğunda izlenen iş akışı örneğinin abone olunan bir durumdan.</span><span class="sxs-lookup"><span data-stu-id="3f217-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f217-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f217-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3f217-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f217-123">Element</span></span>|<span data-ttu-id="3f217-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f217-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f217-125">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="3f217-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="3f217-126">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen sorgu.</span><span class="sxs-lookup"><span data-stu-id="3f217-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f217-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f217-127">Remarks</span></span>  
 <span data-ttu-id="3f217-128">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3f217-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="3f217-129">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="3f217-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="3f217-130">Durum</span><span class="sxs-lookup"><span data-stu-id="3f217-130">State</span></span>|<span data-ttu-id="3f217-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f217-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3f217-132">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="3f217-132">Aborted</span></span>|<span data-ttu-id="3f217-133">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="3f217-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="3f217-134">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="3f217-134">Completed</span></span>|<span data-ttu-id="3f217-135">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="3f217-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="3f217-136">Silindi</span><span class="sxs-lookup"><span data-stu-id="3f217-136">Deleted</span></span>|<span data-ttu-id="3f217-137">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="3f217-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="3f217-138">Boş</span><span class="sxs-lookup"><span data-stu-id="3f217-138">Idle</span></span>|<span data-ttu-id="3f217-139">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="3f217-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="3f217-140">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="3f217-140">Persisted</span></span>|<span data-ttu-id="3f217-141">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="3f217-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="3f217-142">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="3f217-142">Resumed</span></span>|<span data-ttu-id="3f217-143">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="3f217-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="3f217-144">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="3f217-144">Started</span></span>|<span data-ttu-id="3f217-145">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3f217-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="3f217-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="3f217-146">UnhandledException</span></span>|<span data-ttu-id="3f217-147">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="3f217-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="3f217-148">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="3f217-148">Unloaded</span></span>|<span data-ttu-id="3f217-149">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="3f217-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="3f217-150">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="3f217-150">Canceled</span></span>|<span data-ttu-id="3f217-151">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="3f217-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="3f217-152">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="3f217-152">Suspended</span></span>|<span data-ttu-id="3f217-153">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="3f217-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="3f217-154">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="3f217-154">Terminated</span></span>|<span data-ttu-id="3f217-155">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="3f217-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="3f217-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="3f217-156">Unsuspended</span></span>|<span data-ttu-id="3f217-157">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="3f217-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3f217-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f217-158">Example</span></span>  
 <span data-ttu-id="3f217-159">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="3f217-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f217-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f217-160">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3f217-161">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="3f217-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3f217-162">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="3f217-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
