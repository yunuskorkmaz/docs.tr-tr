---
title: <states>WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: ef4ce4b6fa6e60ead10b196b10a7c1489e15ac25
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938975"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="06577-102">\<WCF, \<WorkflowInstanceQuery > > durumlar</span><span class="sxs-lookup"><span data-stu-id="06577-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="06577-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="06577-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="06577-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="06577-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="06577-105">\<System. ServiceModel > \<izleme ></span><span class="sxs-lookup"><span data-stu-id="06577-105">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="06577-106">\<Profiller ></span><span class="sxs-lookup"><span data-stu-id="06577-106">\<profiles></span></span>  
<span data-ttu-id="06577-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="06577-107">\<trackingProfile></span></span>  
<span data-ttu-id="06577-108">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="06577-108">\<workflow></span></span>  
<span data-ttu-id="06577-109">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="06577-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="06577-110">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="06577-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="06577-111">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="06577-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06577-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06577-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06577-113">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="06577-113">Attributes and elements</span></span>

<span data-ttu-id="06577-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="06577-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06577-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="06577-115">Attributes</span></span>  

<span data-ttu-id="06577-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="06577-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="06577-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="06577-117">Child elements</span></span>
  
|<span data-ttu-id="06577-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="06577-118">Element</span></span>|<span data-ttu-id="06577-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06577-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06577-120">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="06577-120">\<states></span></span>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="06577-121">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durum.</span><span class="sxs-lookup"><span data-stu-id="06577-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06577-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="06577-122">Parent elements</span></span>  
  
|<span data-ttu-id="06577-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="06577-123">Element</span></span>|<span data-ttu-id="06577-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06577-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06577-125">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="06577-125">\<workflowInstanceQuery></span></span>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="06577-126">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="06577-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06577-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06577-127">Remarks</span></span>

<span data-ttu-id="06577-128">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="06577-128">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="06577-129">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="06577-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="06577-130">Durum</span><span class="sxs-lookup"><span data-stu-id="06577-130">State</span></span>|<span data-ttu-id="06577-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06577-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="06577-132">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="06577-132">Aborted</span></span>|<span data-ttu-id="06577-133">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="06577-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="06577-134">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="06577-134">Completed</span></span>|<span data-ttu-id="06577-135">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="06577-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="06577-136">Silindi</span><span class="sxs-lookup"><span data-stu-id="06577-136">Deleted</span></span>|<span data-ttu-id="06577-137">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="06577-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="06577-138">Boş</span><span class="sxs-lookup"><span data-stu-id="06577-138">Idle</span></span>|<span data-ttu-id="06577-139">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="06577-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="06577-140">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="06577-140">Persisted</span></span>|<span data-ttu-id="06577-141">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="06577-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="06577-142">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="06577-142">Resumed</span></span>|<span data-ttu-id="06577-143">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="06577-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="06577-144">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="06577-144">Started</span></span>|<span data-ttu-id="06577-145">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="06577-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="06577-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="06577-146">UnhandledException</span></span>|<span data-ttu-id="06577-147">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="06577-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="06577-148">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="06577-148">Unloaded</span></span>|<span data-ttu-id="06577-149">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="06577-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="06577-150">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="06577-150">Canceled</span></span>|<span data-ttu-id="06577-151">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="06577-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="06577-152">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="06577-152">Suspended</span></span>|<span data-ttu-id="06577-153">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="06577-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="06577-154">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="06577-154">Terminated</span></span>|<span data-ttu-id="06577-155">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="06577-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="06577-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="06577-156">Unsuspended</span></span>|<span data-ttu-id="06577-157">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="06577-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="06577-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="06577-158">Example</span></span>

<span data-ttu-id="06577-159">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="06577-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="06577-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06577-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="06577-161">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="06577-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="06577-162">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="06577-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
