---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: fd0b57d7d08cf77ba7792e079b7abd2ff8f2839e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947402"
---
# <a name="states"></a><span data-ttu-id="da7b2-101">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="da7b2-101">\<states></span></span>
<span data-ttu-id="da7b2-102">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="da7b2-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="da7b2-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="da7b2-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="da7b2-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="da7b2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="da7b2-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="da7b2-105">\<tracking></span></span>  
<span data-ttu-id="da7b2-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="da7b2-106">\<trackingProfile></span></span>  
<span data-ttu-id="da7b2-107">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="da7b2-107">\<workflow></span></span>  
<span data-ttu-id="da7b2-108">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="da7b2-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="da7b2-109">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="da7b2-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="da7b2-110">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="da7b2-110">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da7b2-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da7b2-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da7b2-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="da7b2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="da7b2-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="da7b2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da7b2-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="da7b2-114">Attributes</span></span>  
 <span data-ttu-id="da7b2-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="da7b2-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="da7b2-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="da7b2-116">Child Elements</span></span>  
  
|<span data-ttu-id="da7b2-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="da7b2-117">Element</span></span>|<span data-ttu-id="da7b2-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da7b2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da7b2-119">\<durum ></span><span class="sxs-lookup"><span data-stu-id="da7b2-119">\<state></span></span>](states.md)|<span data-ttu-id="da7b2-120">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durum.</span><span class="sxs-lookup"><span data-stu-id="da7b2-120">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da7b2-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="da7b2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="da7b2-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="da7b2-122">Element</span></span>|<span data-ttu-id="da7b2-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da7b2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da7b2-124">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="da7b2-124">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="da7b2-125">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="da7b2-125">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da7b2-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da7b2-126">Remarks</span></span>  
 <span data-ttu-id="da7b2-127">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="da7b2-127">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="da7b2-128">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="da7b2-128">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="da7b2-129">Durum</span><span class="sxs-lookup"><span data-stu-id="da7b2-129">State</span></span>|<span data-ttu-id="da7b2-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da7b2-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="da7b2-131">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="da7b2-131">Aborted</span></span>|<span data-ttu-id="da7b2-132">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="da7b2-132">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="da7b2-133">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="da7b2-133">Completed</span></span>|<span data-ttu-id="da7b2-134">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="da7b2-134">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="da7b2-135">Silindi</span><span class="sxs-lookup"><span data-stu-id="da7b2-135">Deleted</span></span>|<span data-ttu-id="da7b2-136">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="da7b2-136">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="da7b2-137">Boş</span><span class="sxs-lookup"><span data-stu-id="da7b2-137">Idle</span></span>|<span data-ttu-id="da7b2-138">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="da7b2-138">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="da7b2-139">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="da7b2-139">Persisted</span></span>|<span data-ttu-id="da7b2-140">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="da7b2-140">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="da7b2-141">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="da7b2-141">Resumed</span></span>|<span data-ttu-id="da7b2-142">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="da7b2-142">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="da7b2-143">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="da7b2-143">Started</span></span>|<span data-ttu-id="da7b2-144">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="da7b2-144">The workflow instance is started.</span></span>|  
|<span data-ttu-id="da7b2-145">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="da7b2-145">UnhandledException</span></span>|<span data-ttu-id="da7b2-146">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="da7b2-146">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="da7b2-147">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="da7b2-147">Unloaded</span></span>|<span data-ttu-id="da7b2-148">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="da7b2-148">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="da7b2-149">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="da7b2-149">Canceled</span></span>|<span data-ttu-id="da7b2-150">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="da7b2-150">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="da7b2-151">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="da7b2-151">Suspended</span></span>|<span data-ttu-id="da7b2-152">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="da7b2-152">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="da7b2-153">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="da7b2-153">Terminated</span></span>|<span data-ttu-id="da7b2-154">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="da7b2-154">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="da7b2-155">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="da7b2-155">Unsuspended</span></span>|<span data-ttu-id="da7b2-156">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="da7b2-156">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="da7b2-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="da7b2-157">Example</span></span>  
 <span data-ttu-id="da7b2-158">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="da7b2-158">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="da7b2-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da7b2-159">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="da7b2-160">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="da7b2-160">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="da7b2-161">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="da7b2-161">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
