---
title: <states> WCF, <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: fad6f9c8871f79e4a1e26c893eed86ba168f6d01
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281469"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="63cab-102">\<durumları >, WCF \<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="63cab-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="63cab-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="63cab-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="63cab-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="63cab-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="63cab-105">\<system.serviceModel> \<tracking></span><span class="sxs-lookup"><span data-stu-id="63cab-105">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="63cab-106">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="63cab-106">\<profiles></span></span>  
<span data-ttu-id="63cab-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="63cab-107">\<trackingProfile></span></span>  
<span data-ttu-id="63cab-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="63cab-108">\<workflow></span></span>  
<span data-ttu-id="63cab-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="63cab-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="63cab-110">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="63cab-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="63cab-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="63cab-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63cab-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63cab-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63cab-113">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="63cab-113">Attributes and elements</span></span>

<span data-ttu-id="63cab-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="63cab-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63cab-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="63cab-115">Attributes</span></span>  

<span data-ttu-id="63cab-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="63cab-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="63cab-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="63cab-117">Child elements</span></span>
  
|<span data-ttu-id="63cab-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="63cab-118">Element</span></span>|<span data-ttu-id="63cab-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63cab-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63cab-120">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="63cab-120">\<states></span></span>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="63cab-121">İzleme kayıt oluşturulduğunda izlenen iş akışı örneğinin abone olunan bir durumdan.</span><span class="sxs-lookup"><span data-stu-id="63cab-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63cab-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="63cab-122">Parent elements</span></span>  
  
|<span data-ttu-id="63cab-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="63cab-123">Element</span></span>|<span data-ttu-id="63cab-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63cab-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63cab-125">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="63cab-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="63cab-126">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen sorgu.</span><span class="sxs-lookup"><span data-stu-id="63cab-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63cab-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63cab-127">Remarks</span></span>

<span data-ttu-id="63cab-128">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="63cab-128">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="63cab-129">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="63cab-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="63cab-130">Durum</span><span class="sxs-lookup"><span data-stu-id="63cab-130">State</span></span>|<span data-ttu-id="63cab-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63cab-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="63cab-132">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="63cab-132">Aborted</span></span>|<span data-ttu-id="63cab-133">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="63cab-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="63cab-134">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="63cab-134">Completed</span></span>|<span data-ttu-id="63cab-135">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="63cab-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="63cab-136">Silindi</span><span class="sxs-lookup"><span data-stu-id="63cab-136">Deleted</span></span>|<span data-ttu-id="63cab-137">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="63cab-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="63cab-138">Boş</span><span class="sxs-lookup"><span data-stu-id="63cab-138">Idle</span></span>|<span data-ttu-id="63cab-139">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="63cab-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="63cab-140">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="63cab-140">Persisted</span></span>|<span data-ttu-id="63cab-141">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="63cab-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="63cab-142">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="63cab-142">Resumed</span></span>|<span data-ttu-id="63cab-143">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="63cab-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="63cab-144">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="63cab-144">Started</span></span>|<span data-ttu-id="63cab-145">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="63cab-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="63cab-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="63cab-146">UnhandledException</span></span>|<span data-ttu-id="63cab-147">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="63cab-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="63cab-148">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="63cab-148">Unloaded</span></span>|<span data-ttu-id="63cab-149">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="63cab-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="63cab-150">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="63cab-150">Canceled</span></span>|<span data-ttu-id="63cab-151">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="63cab-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="63cab-152">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="63cab-152">Suspended</span></span>|<span data-ttu-id="63cab-153">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="63cab-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="63cab-154">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="63cab-154">Terminated</span></span>|<span data-ttu-id="63cab-155">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="63cab-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="63cab-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="63cab-156">Unsuspended</span></span>|<span data-ttu-id="63cab-157">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="63cab-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="63cab-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="63cab-158">Example</span></span>

<span data-ttu-id="63cab-159">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="63cab-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="63cab-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63cab-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="63cab-161">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="63cab-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="63cab-162">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="63cab-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
