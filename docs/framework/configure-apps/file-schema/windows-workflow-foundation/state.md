---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 9ffe9f9f69f68b6f47cbc3a75200b2867aae2384
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947445"
---
# <a name="state"></a><span data-ttu-id="45eee-101">\<durum ></span><span class="sxs-lookup"><span data-stu-id="45eee-101">\<state></span></span>
<span data-ttu-id="45eee-102">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="45eee-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="45eee-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="45eee-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="45eee-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="45eee-104">\<system.serviceModel></span></span>  
<span data-ttu-id="45eee-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="45eee-105">\<tracking></span></span>  
<span data-ttu-id="45eee-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="45eee-106">\<trackingProfile></span></span>  
<span data-ttu-id="45eee-107">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="45eee-107">\<workflow></span></span>  
<span data-ttu-id="45eee-108">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="45eee-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="45eee-109">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="45eee-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="45eee-110">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="45eee-110">\<states></span></span>  
<span data-ttu-id="45eee-111">\<durum ></span><span class="sxs-lookup"><span data-stu-id="45eee-111">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45eee-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45eee-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45eee-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="45eee-113">Attributes and Elements</span></span>  
 <span data-ttu-id="45eee-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45eee-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45eee-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="45eee-115">Attributes</span></span>  
  
|<span data-ttu-id="45eee-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="45eee-116">Attribute</span></span>|<span data-ttu-id="45eee-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45eee-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45eee-118">name</span><span class="sxs-lookup"><span data-stu-id="45eee-118">name</span></span>|<span data-ttu-id="45eee-119">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durumu belirten dize.</span><span class="sxs-lookup"><span data-stu-id="45eee-119">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45eee-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="45eee-120">Child Elements</span></span>  
 <span data-ttu-id="45eee-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="45eee-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45eee-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="45eee-122">Parent Elements</span></span>  
  
|<span data-ttu-id="45eee-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="45eee-123">Element</span></span>|<span data-ttu-id="45eee-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45eee-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45eee-125">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="45eee-125">\<states></span></span>](states.md)|<span data-ttu-id="45eee-126">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="45eee-126">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45eee-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45eee-127">Remarks</span></span>  
 <span data-ttu-id="45eee-128">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="45eee-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="45eee-129">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="45eee-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="45eee-130">Durum</span><span class="sxs-lookup"><span data-stu-id="45eee-130">State</span></span>|<span data-ttu-id="45eee-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45eee-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="45eee-132">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="45eee-132">Aborted</span></span>|<span data-ttu-id="45eee-133">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="45eee-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="45eee-134">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="45eee-134">Completed</span></span>|<span data-ttu-id="45eee-135">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="45eee-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="45eee-136">Silindi</span><span class="sxs-lookup"><span data-stu-id="45eee-136">Deleted</span></span>|<span data-ttu-id="45eee-137">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="45eee-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="45eee-138">Boş</span><span class="sxs-lookup"><span data-stu-id="45eee-138">Idle</span></span>|<span data-ttu-id="45eee-139">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="45eee-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="45eee-140">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="45eee-140">Persisted</span></span>|<span data-ttu-id="45eee-141">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="45eee-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="45eee-142">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="45eee-142">Resumed</span></span>|<span data-ttu-id="45eee-143">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="45eee-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="45eee-144">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="45eee-144">Started</span></span>|<span data-ttu-id="45eee-145">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="45eee-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="45eee-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="45eee-146">UnhandledException</span></span>|<span data-ttu-id="45eee-147">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="45eee-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="45eee-148">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="45eee-148">Unloaded</span></span>|<span data-ttu-id="45eee-149">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="45eee-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="45eee-150">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="45eee-150">Canceled</span></span>|<span data-ttu-id="45eee-151">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="45eee-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="45eee-152">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="45eee-152">Suspended</span></span>|<span data-ttu-id="45eee-153">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="45eee-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="45eee-154">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="45eee-154">Terminated</span></span>|<span data-ttu-id="45eee-155">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="45eee-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="45eee-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="45eee-156">Unsuspended</span></span>|<span data-ttu-id="45eee-157">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="45eee-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="45eee-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="45eee-158">Example</span></span>  
 <span data-ttu-id="45eee-159">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="45eee-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45eee-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45eee-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="45eee-161">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="45eee-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="45eee-162">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="45eee-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
