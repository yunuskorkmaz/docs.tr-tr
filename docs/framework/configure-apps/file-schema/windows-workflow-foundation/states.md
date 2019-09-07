---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 1a7c839a5ff8fac9470aea71a4886d9000086e9e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398615"
---
# <a name="states"></a><span data-ttu-id="cd0c9-101">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="cd0c9-101">\<states></span></span>
<span data-ttu-id="cd0c9-102">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="cd0c9-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="cd0c9-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="cd0c9-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cd0c9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cd0c9-105">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cd0c9-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="cd0c9-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="cd0c9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="cd0c9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="cd0c9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="cd0c9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cd0c9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="cd0c9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WorkflowInstanceQueries >** ](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="cd0c9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="cd0c9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WorkflowInstanceQuery >** ](workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="cd0c9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)</span></span>\
<span data-ttu-id="cd0c9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<durumlar >**</span><span class="sxs-lookup"><span data-stu-id="cd0c9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd0c9-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd0c9-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd0c9-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd0c9-113">Attributes and Elements</span></span>  
 <span data-ttu-id="cd0c9-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd0c9-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cd0c9-115">Attributes</span></span>  
 <span data-ttu-id="cd0c9-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cd0c9-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd0c9-117">Child Elements</span></span>  
  
|<span data-ttu-id="cd0c9-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="cd0c9-118">Element</span></span>|<span data-ttu-id="cd0c9-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd0c9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd0c9-120">\<durum ></span><span class="sxs-lookup"><span data-stu-id="cd0c9-120">\<state></span></span>](states.md)|<span data-ttu-id="cd0c9-121">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durum.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd0c9-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd0c9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cd0c9-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="cd0c9-123">Element</span></span>|<span data-ttu-id="cd0c9-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd0c9-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd0c9-125">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="cd0c9-125">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="cd0c9-126">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd0c9-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd0c9-127">Remarks</span></span>  
 <span data-ttu-id="cd0c9-128">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="cd0c9-129">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="cd0c9-130">Durum</span><span class="sxs-lookup"><span data-stu-id="cd0c9-130">State</span></span>|<span data-ttu-id="cd0c9-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd0c9-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd0c9-132">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="cd0c9-132">Aborted</span></span>|<span data-ttu-id="cd0c9-133">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="cd0c9-134">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="cd0c9-134">Completed</span></span>|<span data-ttu-id="cd0c9-135">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="cd0c9-136">Silindi</span><span class="sxs-lookup"><span data-stu-id="cd0c9-136">Deleted</span></span>|<span data-ttu-id="cd0c9-137">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="cd0c9-138">Boş</span><span class="sxs-lookup"><span data-stu-id="cd0c9-138">Idle</span></span>|<span data-ttu-id="cd0c9-139">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="cd0c9-140">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="cd0c9-140">Persisted</span></span>|<span data-ttu-id="cd0c9-141">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="cd0c9-142">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="cd0c9-142">Resumed</span></span>|<span data-ttu-id="cd0c9-143">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="cd0c9-144">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="cd0c9-144">Started</span></span>|<span data-ttu-id="cd0c9-145">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="cd0c9-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="cd0c9-146">UnhandledException</span></span>|<span data-ttu-id="cd0c9-147">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="cd0c9-148">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="cd0c9-148">Unloaded</span></span>|<span data-ttu-id="cd0c9-149">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="cd0c9-150">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="cd0c9-150">Canceled</span></span>|<span data-ttu-id="cd0c9-151">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="cd0c9-152">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="cd0c9-152">Suspended</span></span>|<span data-ttu-id="cd0c9-153">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="cd0c9-154">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="cd0c9-154">Terminated</span></span>|<span data-ttu-id="cd0c9-155">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="cd0c9-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="cd0c9-156">Unsuspended</span></span>|<span data-ttu-id="cd0c9-157">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cd0c9-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd0c9-158">Example</span></span>  
 <span data-ttu-id="cd0c9-159">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd0c9-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd0c9-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cd0c9-161">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="cd0c9-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cd0c9-162">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="cd0c9-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
