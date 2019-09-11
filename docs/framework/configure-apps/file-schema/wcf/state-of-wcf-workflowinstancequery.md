---
title: <state>WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 80f7532f3c51680a2e34713b526dc43822db61b9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854955"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="c9e21-102">\<WCF, \<WorkflowInstanceQuery > durum ></span><span class="sxs-lookup"><span data-stu-id="c9e21-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="c9e21-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c9e21-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="c9e21-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c9e21-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c9e21-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c9e21-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c9e21-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c9e21-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c9e21-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c9e21-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="c9e21-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="c9e21-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="c9e21-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c9e21-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="c9e21-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c9e21-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="c9e21-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WorkflowInstanceQueries >** ](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c9e21-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="c9e21-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WorkflowInstanceQuery >** ](workflowinstancequery-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c9e21-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)</span></span>\
<span data-ttu-id="c9e21-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<durumlar >** ](states-of-wcf-workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="c9e21-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-wcf-workflowinstancequery.md)</span></span>\
<span data-ttu-id="c9e21-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<durum >**</span><span class="sxs-lookup"><span data-stu-id="c9e21-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9e21-115">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9e21-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9e21-116">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="c9e21-116">Attributes and elements</span></span>

<span data-ttu-id="c9e21-117">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9e21-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="c9e21-118">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9e21-118">Attributes</span></span>

|<span data-ttu-id="c9e21-119">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9e21-119">Attribute</span></span>|<span data-ttu-id="c9e21-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9e21-120">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="c9e21-121">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durumu belirten dize.</span><span class="sxs-lookup"><span data-stu-id="c9e21-121">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9e21-122">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c9e21-122">Child elements</span></span>

<span data-ttu-id="c9e21-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="c9e21-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9e21-124">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="c9e21-124">Parent elements</span></span>

|<span data-ttu-id="c9e21-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9e21-125">Element</span></span>|<span data-ttu-id="c9e21-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9e21-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9e21-127">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="c9e21-127">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="c9e21-128">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c9e21-128">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9e21-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9e21-129">Remarks</span></span>  

<span data-ttu-id="c9e21-130">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c9e21-130">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="c9e21-131">Olası durum değerleri aşağıdaki tabloda açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="c9e21-131">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="c9e21-132">Durum</span><span class="sxs-lookup"><span data-stu-id="c9e21-132">State</span></span>|<span data-ttu-id="c9e21-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9e21-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9e21-134">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="c9e21-134">Aborted</span></span>|<span data-ttu-id="c9e21-135">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c9e21-135">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="c9e21-136">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="c9e21-136">Completed</span></span>|<span data-ttu-id="c9e21-137">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c9e21-137">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="c9e21-138">Silindi</span><span class="sxs-lookup"><span data-stu-id="c9e21-138">Deleted</span></span>|<span data-ttu-id="c9e21-139">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="c9e21-139">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="c9e21-140">Boş</span><span class="sxs-lookup"><span data-stu-id="c9e21-140">Idle</span></span>|<span data-ttu-id="c9e21-141">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="c9e21-141">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="c9e21-142">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="c9e21-142">Persisted</span></span>|<span data-ttu-id="c9e21-143">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="c9e21-143">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="c9e21-144">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="c9e21-144">Resumed</span></span>|<span data-ttu-id="c9e21-145">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="c9e21-145">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="c9e21-146">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="c9e21-146">Started</span></span>|<span data-ttu-id="c9e21-147">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="c9e21-147">The workflow instance is started.</span></span>|  
|<span data-ttu-id="c9e21-148">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="c9e21-148">UnhandledException</span></span>|<span data-ttu-id="c9e21-149">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="c9e21-149">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="c9e21-150">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="c9e21-150">Unloaded</span></span>|<span data-ttu-id="c9e21-151">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c9e21-151">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="c9e21-152">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="c9e21-152">Canceled</span></span>|<span data-ttu-id="c9e21-153">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c9e21-153">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="c9e21-154">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="c9e21-154">Suspended</span></span>|<span data-ttu-id="c9e21-155">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="c9e21-155">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="c9e21-156">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="c9e21-156">Terminated</span></span>|<span data-ttu-id="c9e21-157">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="c9e21-157">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="c9e21-158">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="c9e21-158">Unsuspended</span></span>|<span data-ttu-id="c9e21-159">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="c9e21-159">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c9e21-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9e21-160">Example</span></span>

<span data-ttu-id="c9e21-161">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="c9e21-161">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="c9e21-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9e21-162">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c9e21-163">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c9e21-163">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c9e21-164">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c9e21-164">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
