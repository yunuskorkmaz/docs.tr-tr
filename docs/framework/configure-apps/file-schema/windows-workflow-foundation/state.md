---
title: '&lt;Durumu&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 327a5e98a9ecf6ba23eaf47c3d6d73bfb7852ee7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757495"
---
# <a name="ltstategt"></a><span data-ttu-id="428cc-102">&lt;Durumu&gt;</span><span class="sxs-lookup"><span data-stu-id="428cc-102">&lt;state&gt;</span></span>
<span data-ttu-id="428cc-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="428cc-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="428cc-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="428cc-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="428cc-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="428cc-105">\<system.serviceModel></span></span>  
<span data-ttu-id="428cc-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="428cc-106">\<tracking></span></span>  
<span data-ttu-id="428cc-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="428cc-107">\<trackingProfile></span></span>  
<span data-ttu-id="428cc-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="428cc-108">\<workflow></span></span>  
<span data-ttu-id="428cc-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="428cc-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="428cc-110">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="428cc-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="428cc-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="428cc-111">\<states></span></span>  
<span data-ttu-id="428cc-112">\<durumu ></span><span class="sxs-lookup"><span data-stu-id="428cc-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="428cc-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="428cc-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="428cc-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="428cc-114">Attributes and Elements</span></span>  
 <span data-ttu-id="428cc-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="428cc-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="428cc-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="428cc-116">Attributes</span></span>  
  
|<span data-ttu-id="428cc-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="428cc-117">Attribute</span></span>|<span data-ttu-id="428cc-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="428cc-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="428cc-119">name</span><span class="sxs-lookup"><span data-stu-id="428cc-119">name</span></span>|<span data-ttu-id="428cc-120">İzleme kayıt oluşturulduğunda izlenen iş akışı örneği abone durumundan belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="428cc-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="428cc-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="428cc-121">Child Elements</span></span>  
 <span data-ttu-id="428cc-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="428cc-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="428cc-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="428cc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="428cc-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="428cc-124">Element</span></span>|<span data-ttu-id="428cc-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="428cc-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="428cc-126">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="428cc-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="428cc-127">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="428cc-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="428cc-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="428cc-128">Remarks</span></span>  
 <span data-ttu-id="428cc-129">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="428cc-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="428cc-130">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="428cc-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="428cc-131">Durum</span><span class="sxs-lookup"><span data-stu-id="428cc-131">State</span></span>|<span data-ttu-id="428cc-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="428cc-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="428cc-133">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="428cc-133">Aborted</span></span>|<span data-ttu-id="428cc-134">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="428cc-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="428cc-135">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="428cc-135">Completed</span></span>|<span data-ttu-id="428cc-136">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="428cc-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="428cc-137">Silindi</span><span class="sxs-lookup"><span data-stu-id="428cc-137">Deleted</span></span>|<span data-ttu-id="428cc-138">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="428cc-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="428cc-139">Boş</span><span class="sxs-lookup"><span data-stu-id="428cc-139">Idle</span></span>|<span data-ttu-id="428cc-140">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="428cc-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="428cc-141">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="428cc-141">Persisted</span></span>|<span data-ttu-id="428cc-142">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="428cc-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="428cc-143">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="428cc-143">Resumed</span></span>|<span data-ttu-id="428cc-144">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="428cc-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="428cc-145">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="428cc-145">Started</span></span>|<span data-ttu-id="428cc-146">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="428cc-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="428cc-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="428cc-147">UnhandledException</span></span>|<span data-ttu-id="428cc-148">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="428cc-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="428cc-149">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="428cc-149">Unloaded</span></span>|<span data-ttu-id="428cc-150">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="428cc-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="428cc-151">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="428cc-151">Canceled</span></span>|<span data-ttu-id="428cc-152">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="428cc-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="428cc-153">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="428cc-153">Suspended</span></span>|<span data-ttu-id="428cc-154">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="428cc-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="428cc-155">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="428cc-155">Terminated</span></span>|<span data-ttu-id="428cc-156">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="428cc-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="428cc-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="428cc-157">Unsuspended</span></span>|<span data-ttu-id="428cc-158">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="428cc-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="428cc-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="428cc-159">Example</span></span>  
 <span data-ttu-id="428cc-160">Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="428cc-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="428cc-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="428cc-161">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>      
 [<span data-ttu-id="428cc-162">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="428cc-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="428cc-163">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="428cc-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
