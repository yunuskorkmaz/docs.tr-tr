---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 6f1a9474f3f12005df364a6fb84dc63aa1b68e04
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108183"
---
# <a name="state"></a><span data-ttu-id="e017f-101">\<Durum ></span><span class="sxs-lookup"><span data-stu-id="e017f-101">\<state></span></span>
<span data-ttu-id="e017f-102">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e017f-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="e017f-103">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e017f-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e017f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e017f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e017f-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="e017f-105">\<tracking></span></span>  
<span data-ttu-id="e017f-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e017f-106">\<trackingProfile></span></span>  
<span data-ttu-id="e017f-107">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="e017f-107">\<workflow></span></span>  
<span data-ttu-id="e017f-108">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="e017f-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="e017f-109">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="e017f-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="e017f-110">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="e017f-110">\<states></span></span>  
<span data-ttu-id="e017f-111">\<Durum ></span><span class="sxs-lookup"><span data-stu-id="e017f-111">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e017f-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e017f-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e017f-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e017f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e017f-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e017f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e017f-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e017f-115">Attributes</span></span>  
  
|<span data-ttu-id="e017f-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e017f-116">Attribute</span></span>|<span data-ttu-id="e017f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e017f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e017f-118">name</span><span class="sxs-lookup"><span data-stu-id="e017f-118">name</span></span>|<span data-ttu-id="e017f-119">İzleme kayıt oluşturulduğunda izlenen iş akışı örneğinin abone olunan bir durumdan belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e017f-119">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e017f-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e017f-120">Child Elements</span></span>  
 <span data-ttu-id="e017f-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="e017f-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e017f-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e017f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e017f-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="e017f-123">Element</span></span>|<span data-ttu-id="e017f-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e017f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e017f-125">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="e017f-125">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="e017f-126">Abone olunan durumları izleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e017f-126">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e017f-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e017f-127">Remarks</span></span>  
 <span data-ttu-id="e017f-128">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e017f-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="e017f-129">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="e017f-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="e017f-130">Durum</span><span class="sxs-lookup"><span data-stu-id="e017f-130">State</span></span>|<span data-ttu-id="e017f-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e017f-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e017f-132">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="e017f-132">Aborted</span></span>|<span data-ttu-id="e017f-133">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e017f-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="e017f-134">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="e017f-134">Completed</span></span>|<span data-ttu-id="e017f-135">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e017f-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="e017f-136">Silindi</span><span class="sxs-lookup"><span data-stu-id="e017f-136">Deleted</span></span>|<span data-ttu-id="e017f-137">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="e017f-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="e017f-138">Boş</span><span class="sxs-lookup"><span data-stu-id="e017f-138">Idle</span></span>|<span data-ttu-id="e017f-139">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="e017f-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="e017f-140">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="e017f-140">Persisted</span></span>|<span data-ttu-id="e017f-141">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="e017f-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="e017f-142">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="e017f-142">Resumed</span></span>|<span data-ttu-id="e017f-143">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="e017f-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="e017f-144">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="e017f-144">Started</span></span>|<span data-ttu-id="e017f-145">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="e017f-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="e017f-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="e017f-146">UnhandledException</span></span>|<span data-ttu-id="e017f-147">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="e017f-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="e017f-148">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="e017f-148">Unloaded</span></span>|<span data-ttu-id="e017f-149">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="e017f-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="e017f-150">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="e017f-150">Canceled</span></span>|<span data-ttu-id="e017f-151">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e017f-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="e017f-152">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="e017f-152">Suspended</span></span>|<span data-ttu-id="e017f-153">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="e017f-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="e017f-154">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="e017f-154">Terminated</span></span>|<span data-ttu-id="e017f-155">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="e017f-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="e017f-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="e017f-156">Unsuspended</span></span>|<span data-ttu-id="e017f-157">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="e017f-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e017f-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="e017f-158">Example</span></span>  
 <span data-ttu-id="e017f-159">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="e017f-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e017f-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e017f-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e017f-161">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="e017f-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e017f-162">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="e017f-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
