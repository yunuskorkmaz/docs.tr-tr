---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 30cb2efa4c00c8b292a8ace6a03306d6ac76a7f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073128"
---
# <a name="states"></a><span data-ttu-id="565b5-101">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="565b5-101">\<states></span></span>
<span data-ttu-id="565b5-102">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="565b5-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="565b5-103">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="565b5-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="565b5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="565b5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="565b5-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="565b5-105">\<tracking></span></span>  
<span data-ttu-id="565b5-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="565b5-106">\<trackingProfile></span></span>  
<span data-ttu-id="565b5-107">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="565b5-107">\<workflow></span></span>  
<span data-ttu-id="565b5-108">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="565b5-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="565b5-109">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="565b5-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="565b5-110">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="565b5-110">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="565b5-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="565b5-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="565b5-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="565b5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="565b5-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="565b5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="565b5-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="565b5-114">Attributes</span></span>  
 <span data-ttu-id="565b5-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="565b5-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="565b5-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="565b5-116">Child Elements</span></span>  
  
|<span data-ttu-id="565b5-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="565b5-117">Element</span></span>|<span data-ttu-id="565b5-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="565b5-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="565b5-119">\<Durum ></span><span class="sxs-lookup"><span data-stu-id="565b5-119">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="565b5-120">İzleme kayıt oluşturulduğunda izlenen iş akışı örneğinin abone olunan bir durumdan.</span><span class="sxs-lookup"><span data-stu-id="565b5-120">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="565b5-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="565b5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="565b5-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="565b5-122">Element</span></span>|<span data-ttu-id="565b5-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="565b5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="565b5-124">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="565b5-124">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="565b5-125">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen sorgu.</span><span class="sxs-lookup"><span data-stu-id="565b5-125">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="565b5-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="565b5-126">Remarks</span></span>  
 <span data-ttu-id="565b5-127">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="565b5-127">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="565b5-128">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="565b5-128">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="565b5-129">Durum</span><span class="sxs-lookup"><span data-stu-id="565b5-129">State</span></span>|<span data-ttu-id="565b5-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="565b5-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="565b5-131">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="565b5-131">Aborted</span></span>|<span data-ttu-id="565b5-132">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="565b5-132">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="565b5-133">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="565b5-133">Completed</span></span>|<span data-ttu-id="565b5-134">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="565b5-134">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="565b5-135">Silindi</span><span class="sxs-lookup"><span data-stu-id="565b5-135">Deleted</span></span>|<span data-ttu-id="565b5-136">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="565b5-136">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="565b5-137">Boş</span><span class="sxs-lookup"><span data-stu-id="565b5-137">Idle</span></span>|<span data-ttu-id="565b5-138">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="565b5-138">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="565b5-139">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="565b5-139">Persisted</span></span>|<span data-ttu-id="565b5-140">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="565b5-140">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="565b5-141">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="565b5-141">Resumed</span></span>|<span data-ttu-id="565b5-142">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="565b5-142">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="565b5-143">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="565b5-143">Started</span></span>|<span data-ttu-id="565b5-144">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="565b5-144">The workflow instance is started.</span></span>|  
|<span data-ttu-id="565b5-145">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="565b5-145">UnhandledException</span></span>|<span data-ttu-id="565b5-146">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="565b5-146">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="565b5-147">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="565b5-147">Unloaded</span></span>|<span data-ttu-id="565b5-148">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="565b5-148">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="565b5-149">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="565b5-149">Canceled</span></span>|<span data-ttu-id="565b5-150">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="565b5-150">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="565b5-151">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="565b5-151">Suspended</span></span>|<span data-ttu-id="565b5-152">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="565b5-152">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="565b5-153">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="565b5-153">Terminated</span></span>|<span data-ttu-id="565b5-154">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="565b5-154">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="565b5-155">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="565b5-155">Unsuspended</span></span>|<span data-ttu-id="565b5-156">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="565b5-156">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="565b5-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="565b5-157">Example</span></span>  
 <span data-ttu-id="565b5-158">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="565b5-158">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="565b5-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="565b5-159">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="565b5-160">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="565b5-160">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="565b5-161">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="565b5-161">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
