---
title: <states>WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 5b779cf1074687dbd648b23d04f7cf3a354a2014
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855033"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="b1610-102">\<WCF, \<WorkflowInstanceQuery > > durumlar</span><span class="sxs-lookup"><span data-stu-id="b1610-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="b1610-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b1610-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="b1610-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b1610-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="b1610-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1610-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b1610-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b1610-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b1610-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b1610-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="b1610-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="b1610-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="b1610-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b1610-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="b1610-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b1610-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="b1610-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WorkflowInstanceQueries >** ](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b1610-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="b1610-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WorkflowInstanceQuery >** ](workflowinstancequery-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b1610-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)</span></span>\
<span data-ttu-id="b1610-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<durumlar >**</span><span class="sxs-lookup"><span data-stu-id="b1610-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1610-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1610-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1610-115">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="b1610-115">Attributes and elements</span></span>

<span data-ttu-id="b1610-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1610-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1610-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b1610-117">Attributes</span></span>  

<span data-ttu-id="b1610-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="b1610-118">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b1610-119">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b1610-119">Child elements</span></span>
  
|<span data-ttu-id="b1610-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1610-120">Element</span></span>|<span data-ttu-id="b1610-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1610-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1610-122">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="b1610-122">\<states></span></span>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="b1610-123">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durum.</span><span class="sxs-lookup"><span data-stu-id="b1610-123">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1610-124">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="b1610-124">Parent elements</span></span>  
  
|<span data-ttu-id="b1610-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1610-125">Element</span></span>|<span data-ttu-id="b1610-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1610-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1610-127">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="b1610-127">\<workflowInstanceQuery></span></span>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="b1610-128">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="b1610-128">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1610-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1610-129">Remarks</span></span>

<span data-ttu-id="b1610-130">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b1610-130">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="b1610-131">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="b1610-131">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="b1610-132">Durum</span><span class="sxs-lookup"><span data-stu-id="b1610-132">State</span></span>|<span data-ttu-id="b1610-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1610-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b1610-134">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="b1610-134">Aborted</span></span>|<span data-ttu-id="b1610-135">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b1610-135">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="b1610-136">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="b1610-136">Completed</span></span>|<span data-ttu-id="b1610-137">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="b1610-137">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="b1610-138">Silindi</span><span class="sxs-lookup"><span data-stu-id="b1610-138">Deleted</span></span>|<span data-ttu-id="b1610-139">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="b1610-139">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="b1610-140">Boş</span><span class="sxs-lookup"><span data-stu-id="b1610-140">Idle</span></span>|<span data-ttu-id="b1610-141">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="b1610-141">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="b1610-142">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="b1610-142">Persisted</span></span>|<span data-ttu-id="b1610-143">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="b1610-143">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="b1610-144">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="b1610-144">Resumed</span></span>|<span data-ttu-id="b1610-145">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="b1610-145">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="b1610-146">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="b1610-146">Started</span></span>|<span data-ttu-id="b1610-147">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="b1610-147">The workflow instance is started.</span></span>|  
|<span data-ttu-id="b1610-148">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="b1610-148">UnhandledException</span></span>|<span data-ttu-id="b1610-149">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="b1610-149">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="b1610-150">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="b1610-150">Unloaded</span></span>|<span data-ttu-id="b1610-151">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b1610-151">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="b1610-152">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="b1610-152">Canceled</span></span>|<span data-ttu-id="b1610-153">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b1610-153">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="b1610-154">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="b1610-154">Suspended</span></span>|<span data-ttu-id="b1610-155">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="b1610-155">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="b1610-156">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="b1610-156">Terminated</span></span>|<span data-ttu-id="b1610-157">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="b1610-157">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="b1610-158">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="b1610-158">Unsuspended</span></span>|<span data-ttu-id="b1610-159">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="b1610-159">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b1610-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1610-160">Example</span></span>

<span data-ttu-id="b1610-161">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="b1610-161">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="b1610-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1610-162">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b1610-163">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="b1610-163">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b1610-164">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="b1610-164">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
