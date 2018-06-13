---
title: '&lt;durumları&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: fe02106d8d7f70cb328214c7e464d80a41b75528
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757284"
---
# <a name="ltstatesgt"></a><span data-ttu-id="92843-102">&lt;durumları&gt;</span><span class="sxs-lookup"><span data-stu-id="92843-102">&lt;states&gt;</span></span>
<span data-ttu-id="92843-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="92843-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="92843-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="92843-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="92843-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="92843-105">\<system.serviceModel></span></span>  
<span data-ttu-id="92843-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="92843-106">\<tracking></span></span>  
<span data-ttu-id="92843-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="92843-107">\<trackingProfile></span></span>  
<span data-ttu-id="92843-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="92843-108">\<workflow></span></span>  
<span data-ttu-id="92843-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="92843-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="92843-110">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="92843-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="92843-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="92843-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92843-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92843-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92843-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="92843-113">Attributes and Elements</span></span>  
 <span data-ttu-id="92843-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="92843-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92843-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="92843-115">Attributes</span></span>  
 <span data-ttu-id="92843-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="92843-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="92843-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="92843-117">Child Elements</span></span>  
  
|<span data-ttu-id="92843-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="92843-118">Element</span></span>|<span data-ttu-id="92843-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92843-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92843-120">\<durumu ></span><span class="sxs-lookup"><span data-stu-id="92843-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="92843-121">İzleme kayıt oluşturulduğunda izlenen iş akışı örneği abone durumundan.</span><span class="sxs-lookup"><span data-stu-id="92843-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92843-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="92843-122">Parent Elements</span></span>  
  
|<span data-ttu-id="92843-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="92843-123">Element</span></span>|<span data-ttu-id="92843-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92843-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92843-125">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="92843-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="92843-126">Başlatılan ya da tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="92843-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92843-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92843-127">Remarks</span></span>  
 <span data-ttu-id="92843-128">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="92843-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="92843-129">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="92843-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="92843-130">Durum</span><span class="sxs-lookup"><span data-stu-id="92843-130">State</span></span>|<span data-ttu-id="92843-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92843-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92843-132">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="92843-132">Aborted</span></span>|<span data-ttu-id="92843-133">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="92843-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="92843-134">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="92843-134">Completed</span></span>|<span data-ttu-id="92843-135">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="92843-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="92843-136">Silindi</span><span class="sxs-lookup"><span data-stu-id="92843-136">Deleted</span></span>|<span data-ttu-id="92843-137">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="92843-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="92843-138">Boş</span><span class="sxs-lookup"><span data-stu-id="92843-138">Idle</span></span>|<span data-ttu-id="92843-139">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="92843-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="92843-140">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="92843-140">Persisted</span></span>|<span data-ttu-id="92843-141">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="92843-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="92843-142">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="92843-142">Resumed</span></span>|<span data-ttu-id="92843-143">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="92843-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="92843-144">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="92843-144">Started</span></span>|<span data-ttu-id="92843-145">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="92843-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="92843-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="92843-146">UnhandledException</span></span>|<span data-ttu-id="92843-147">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="92843-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="92843-148">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="92843-148">Unloaded</span></span>|<span data-ttu-id="92843-149">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="92843-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="92843-150">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="92843-150">Canceled</span></span>|<span data-ttu-id="92843-151">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="92843-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="92843-152">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="92843-152">Suspended</span></span>|<span data-ttu-id="92843-153">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="92843-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="92843-154">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="92843-154">Terminated</span></span>|<span data-ttu-id="92843-155">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="92843-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="92843-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="92843-156">Unsuspended</span></span>|<span data-ttu-id="92843-157">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="92843-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="92843-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="92843-158">Example</span></span>  
 <span data-ttu-id="92843-159">Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="92843-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="92843-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="92843-160">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="92843-161">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="92843-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="92843-162">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="92843-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
