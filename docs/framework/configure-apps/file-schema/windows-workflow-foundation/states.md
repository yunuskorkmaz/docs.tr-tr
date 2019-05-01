---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 30cb2efa4c00c8b292a8ace6a03306d6ac76a7f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797806"
---
# <a name="states"></a><span data-ttu-id="fd3ca-101">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="fd3ca-101">\<states></span></span>
<span data-ttu-id="fd3ca-102">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="fd3ca-103">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fd3ca-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="fd3ca-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fd3ca-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fd3ca-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="fd3ca-105">\<tracking></span></span>  
<span data-ttu-id="fd3ca-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="fd3ca-106">\<trackingProfile></span></span>  
<span data-ttu-id="fd3ca-107">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="fd3ca-107">\<workflow></span></span>  
<span data-ttu-id="fd3ca-108">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="fd3ca-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="fd3ca-109">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="fd3ca-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="fd3ca-110">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="fd3ca-110">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd3ca-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd3ca-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd3ca-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd3ca-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fd3ca-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd3ca-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fd3ca-114">Attributes</span></span>  
 <span data-ttu-id="fd3ca-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fd3ca-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd3ca-116">Child Elements</span></span>  
  
|<span data-ttu-id="fd3ca-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="fd3ca-117">Element</span></span>|<span data-ttu-id="fd3ca-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd3ca-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd3ca-119">\<Durum ></span><span class="sxs-lookup"><span data-stu-id="fd3ca-119">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="fd3ca-120">İzleme kayıt oluşturulduğunda izlenen iş akışı örneğinin abone olunan bir durumdan.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-120">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fd3ca-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd3ca-121">Parent Elements</span></span>  
  
|<span data-ttu-id="fd3ca-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="fd3ca-122">Element</span></span>|<span data-ttu-id="fd3ca-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd3ca-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd3ca-124">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="fd3ca-124">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="fd3ca-125">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen sorgu.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-125">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd3ca-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd3ca-126">Remarks</span></span>  
 <span data-ttu-id="fd3ca-127">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-127">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="fd3ca-128">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-128">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="fd3ca-129">Durum</span><span class="sxs-lookup"><span data-stu-id="fd3ca-129">State</span></span>|<span data-ttu-id="fd3ca-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd3ca-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd3ca-131">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="fd3ca-131">Aborted</span></span>|<span data-ttu-id="fd3ca-132">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-132">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="fd3ca-133">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="fd3ca-133">Completed</span></span>|<span data-ttu-id="fd3ca-134">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-134">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="fd3ca-135">Silindi</span><span class="sxs-lookup"><span data-stu-id="fd3ca-135">Deleted</span></span>|<span data-ttu-id="fd3ca-136">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-136">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="fd3ca-137">Boş</span><span class="sxs-lookup"><span data-stu-id="fd3ca-137">Idle</span></span>|<span data-ttu-id="fd3ca-138">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-138">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="fd3ca-139">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="fd3ca-139">Persisted</span></span>|<span data-ttu-id="fd3ca-140">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-140">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="fd3ca-141">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="fd3ca-141">Resumed</span></span>|<span data-ttu-id="fd3ca-142">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-142">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="fd3ca-143">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="fd3ca-143">Started</span></span>|<span data-ttu-id="fd3ca-144">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-144">The workflow instance is started.</span></span>|  
|<span data-ttu-id="fd3ca-145">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="fd3ca-145">UnhandledException</span></span>|<span data-ttu-id="fd3ca-146">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-146">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="fd3ca-147">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="fd3ca-147">Unloaded</span></span>|<span data-ttu-id="fd3ca-148">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-148">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="fd3ca-149">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="fd3ca-149">Canceled</span></span>|<span data-ttu-id="fd3ca-150">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-150">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="fd3ca-151">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="fd3ca-151">Suspended</span></span>|<span data-ttu-id="fd3ca-152">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-152">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="fd3ca-153">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="fd3ca-153">Terminated</span></span>|<span data-ttu-id="fd3ca-154">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-154">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="fd3ca-155">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="fd3ca-155">Unsuspended</span></span>|<span data-ttu-id="fd3ca-156">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-156">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fd3ca-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd3ca-157">Example</span></span>  
 <span data-ttu-id="fd3ca-158">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-158">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd3ca-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd3ca-159">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fd3ca-160">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="fd3ca-160">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fd3ca-161">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="fd3ca-161">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
