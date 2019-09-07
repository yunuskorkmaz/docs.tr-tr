---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 7af75182cf38a6acb8a31b71e8b7b42103f8046b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398645"
---
# <a name="state"></a><span data-ttu-id="d4776-101">\<durum ></span><span class="sxs-lookup"><span data-stu-id="d4776-101">\<state></span></span>
<span data-ttu-id="d4776-102">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4776-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="d4776-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d4776-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d4776-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d4776-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d4776-105">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d4776-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="d4776-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="d4776-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="d4776-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="d4776-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="d4776-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d4776-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="d4776-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WorkflowInstanceQueries >** ](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="d4776-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="d4776-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WorkflowInstanceQuery >** ](workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="d4776-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)</span></span>\
<span data-ttu-id="d4776-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<durumlar >** ](states.md)</span><span class="sxs-lookup"><span data-stu-id="d4776-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)</span></span>\
<span data-ttu-id="d4776-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<durum >**</span><span class="sxs-lookup"><span data-stu-id="d4776-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4776-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4776-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4776-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4776-114">Attributes and Elements</span></span>  
 <span data-ttu-id="d4776-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4776-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4776-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d4776-116">Attributes</span></span>  
  
|<span data-ttu-id="d4776-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d4776-117">Attribute</span></span>|<span data-ttu-id="d4776-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4776-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4776-119">name</span><span class="sxs-lookup"><span data-stu-id="d4776-119">name</span></span>|<span data-ttu-id="d4776-120">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durumu belirten dize.</span><span class="sxs-lookup"><span data-stu-id="d4776-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4776-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4776-121">Child Elements</span></span>  
 <span data-ttu-id="d4776-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="d4776-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4776-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4776-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d4776-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="d4776-124">Element</span></span>|<span data-ttu-id="d4776-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4776-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4776-126">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="d4776-126">\<states></span></span>](states.md)|<span data-ttu-id="d4776-127">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d4776-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4776-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4776-128">Remarks</span></span>  
 <span data-ttu-id="d4776-129">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d4776-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="d4776-130">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="d4776-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="d4776-131">Durum</span><span class="sxs-lookup"><span data-stu-id="d4776-131">State</span></span>|<span data-ttu-id="d4776-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4776-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d4776-133">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="d4776-133">Aborted</span></span>|<span data-ttu-id="d4776-134">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d4776-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="d4776-135">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="d4776-135">Completed</span></span>|<span data-ttu-id="d4776-136">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d4776-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="d4776-137">Silindi</span><span class="sxs-lookup"><span data-stu-id="d4776-137">Deleted</span></span>|<span data-ttu-id="d4776-138">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="d4776-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="d4776-139">Boş</span><span class="sxs-lookup"><span data-stu-id="d4776-139">Idle</span></span>|<span data-ttu-id="d4776-140">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="d4776-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="d4776-141">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="d4776-141">Persisted</span></span>|<span data-ttu-id="d4776-142">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="d4776-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="d4776-143">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="d4776-143">Resumed</span></span>|<span data-ttu-id="d4776-144">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="d4776-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="d4776-145">Başlatıldı</span><span class="sxs-lookup"><span data-stu-id="d4776-145">Started</span></span>|<span data-ttu-id="d4776-146">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="d4776-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="d4776-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="d4776-147">UnhandledException</span></span>|<span data-ttu-id="d4776-148">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="d4776-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="d4776-149">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="d4776-149">Unloaded</span></span>|<span data-ttu-id="d4776-150">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="d4776-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="d4776-151">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="d4776-151">Canceled</span></span>|<span data-ttu-id="d4776-152">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d4776-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="d4776-153">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="d4776-153">Suspended</span></span>|<span data-ttu-id="d4776-154">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="d4776-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="d4776-155">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="d4776-155">Terminated</span></span>|<span data-ttu-id="d4776-156">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="d4776-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="d4776-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="d4776-157">Unsuspended</span></span>|<span data-ttu-id="d4776-158">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="d4776-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d4776-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4776-159">Example</span></span>  
 <span data-ttu-id="d4776-160">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="d4776-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4776-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4776-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d4776-162">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="d4776-162">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d4776-163">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="d4776-163">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
