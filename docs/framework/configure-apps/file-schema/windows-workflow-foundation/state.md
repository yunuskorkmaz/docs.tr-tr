---
title: '&lt;durumu&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 8e381671d9282218a4e5bf0ae979bec79c7cfe78
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523057"
---
# <a name="ltstategt"></a><span data-ttu-id="6d99b-102">&lt;durumu&gt;</span><span class="sxs-lookup"><span data-stu-id="6d99b-102">&lt;state&gt;</span></span>
<span data-ttu-id="6d99b-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6d99b-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="6d99b-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6d99b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="6d99b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6d99b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="6d99b-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="6d99b-106">\<tracking></span></span>  
<span data-ttu-id="6d99b-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="6d99b-107">\<trackingProfile></span></span>  
<span data-ttu-id="6d99b-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="6d99b-108">\<workflow></span></span>  
<span data-ttu-id="6d99b-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="6d99b-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="6d99b-110">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="6d99b-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="6d99b-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="6d99b-111">\<states></span></span>  
<span data-ttu-id="6d99b-112">\<Durum ></span><span class="sxs-lookup"><span data-stu-id="6d99b-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d99b-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d99b-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d99b-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d99b-114">Attributes and Elements</span></span>  
 <span data-ttu-id="6d99b-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6d99b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d99b-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6d99b-116">Attributes</span></span>  
  
|<span data-ttu-id="6d99b-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6d99b-117">Attribute</span></span>|<span data-ttu-id="6d99b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d99b-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6d99b-119">name</span><span class="sxs-lookup"><span data-stu-id="6d99b-119">name</span></span>|<span data-ttu-id="6d99b-120">İzleme kayıt oluşturulduğunda izlenen iş akışı örneğinin abone olunan bir durumdan belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="6d99b-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d99b-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d99b-121">Child Elements</span></span>  
 <span data-ttu-id="6d99b-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d99b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d99b-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d99b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6d99b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="6d99b-124">Element</span></span>|<span data-ttu-id="6d99b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d99b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d99b-126">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="6d99b-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="6d99b-127">Abone olunan durumları izleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6d99b-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d99b-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d99b-128">Remarks</span></span>  
 <span data-ttu-id="6d99b-129">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6d99b-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="6d99b-130">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="6d99b-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="6d99b-131">Durum</span><span class="sxs-lookup"><span data-stu-id="6d99b-131">State</span></span>|<span data-ttu-id="6d99b-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d99b-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6d99b-133">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="6d99b-133">Aborted</span></span>|<span data-ttu-id="6d99b-134">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6d99b-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="6d99b-135">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="6d99b-135">Completed</span></span>|<span data-ttu-id="6d99b-136">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="6d99b-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="6d99b-137">Silindi</span><span class="sxs-lookup"><span data-stu-id="6d99b-137">Deleted</span></span>|<span data-ttu-id="6d99b-138">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="6d99b-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="6d99b-139">Boş</span><span class="sxs-lookup"><span data-stu-id="6d99b-139">Idle</span></span>|<span data-ttu-id="6d99b-140">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="6d99b-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="6d99b-141">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="6d99b-141">Persisted</span></span>|<span data-ttu-id="6d99b-142">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="6d99b-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="6d99b-143">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="6d99b-143">Resumed</span></span>|<span data-ttu-id="6d99b-144">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="6d99b-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="6d99b-145">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="6d99b-145">Started</span></span>|<span data-ttu-id="6d99b-146">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="6d99b-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="6d99b-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="6d99b-147">UnhandledException</span></span>|<span data-ttu-id="6d99b-148">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="6d99b-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="6d99b-149">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="6d99b-149">Unloaded</span></span>|<span data-ttu-id="6d99b-150">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="6d99b-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="6d99b-151">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="6d99b-151">Canceled</span></span>|<span data-ttu-id="6d99b-152">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6d99b-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="6d99b-153">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="6d99b-153">Suspended</span></span>|<span data-ttu-id="6d99b-154">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="6d99b-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="6d99b-155">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="6d99b-155">Terminated</span></span>|<span data-ttu-id="6d99b-156">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="6d99b-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="6d99b-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="6d99b-157">Unsuspended</span></span>|<span data-ttu-id="6d99b-158">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="6d99b-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6d99b-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d99b-159">Example</span></span>  
 <span data-ttu-id="6d99b-160">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="6d99b-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d99b-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d99b-161">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6d99b-162">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="6d99b-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6d99b-163">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="6d99b-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
