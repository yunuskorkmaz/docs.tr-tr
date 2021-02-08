---
description: 'Hakkında daha fazla bilgi edinin: <states>'
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 9a66a1ce460db1f5f55fb99a191368635220f32f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781980"
---
# \<states>

<span data-ttu-id="506e2-102">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="506e2-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="506e2-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="506e2-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="506e2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="506e2-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="506e2-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="506e2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="506e2-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="506e2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="506e2-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="506e2-107">Attributes</span></span>  

 <span data-ttu-id="506e2-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="506e2-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="506e2-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="506e2-109">Child Elements</span></span>  
  
|<span data-ttu-id="506e2-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="506e2-110">Element</span></span>|<span data-ttu-id="506e2-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="506e2-111">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](states.md)|<span data-ttu-id="506e2-112">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durum.</span><span class="sxs-lookup"><span data-stu-id="506e2-112">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="506e2-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="506e2-113">Parent Elements</span></span>  
  
|<span data-ttu-id="506e2-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="506e2-114">Element</span></span>|<span data-ttu-id="506e2-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="506e2-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="506e2-116">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="506e2-116">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="506e2-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="506e2-117">Remarks</span></span>  

 <span data-ttu-id="506e2-118">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="506e2-118">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="506e2-119">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="506e2-119">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="506e2-120">Durum</span><span class="sxs-lookup"><span data-stu-id="506e2-120">State</span></span>|<span data-ttu-id="506e2-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="506e2-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="506e2-122">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="506e2-122">Aborted</span></span>|<span data-ttu-id="506e2-123">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="506e2-123">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="506e2-124">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="506e2-124">Completed</span></span>|<span data-ttu-id="506e2-125">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="506e2-125">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="506e2-126">Silindi</span><span class="sxs-lookup"><span data-stu-id="506e2-126">Deleted</span></span>|<span data-ttu-id="506e2-127">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="506e2-127">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="506e2-128">Boş</span><span class="sxs-lookup"><span data-stu-id="506e2-128">Idle</span></span>|<span data-ttu-id="506e2-129">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="506e2-129">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="506e2-130">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="506e2-130">Persisted</span></span>|<span data-ttu-id="506e2-131">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="506e2-131">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="506e2-132">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="506e2-132">Resumed</span></span>|<span data-ttu-id="506e2-133">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="506e2-133">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="506e2-134">Başlarken</span><span class="sxs-lookup"><span data-stu-id="506e2-134">Started</span></span>|<span data-ttu-id="506e2-135">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="506e2-135">The workflow instance is started.</span></span>|  
|<span data-ttu-id="506e2-136">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="506e2-136">UnhandledException</span></span>|<span data-ttu-id="506e2-137">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="506e2-137">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="506e2-138">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="506e2-138">Unloaded</span></span>|<span data-ttu-id="506e2-139">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="506e2-139">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="506e2-140">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="506e2-140">Canceled</span></span>|<span data-ttu-id="506e2-141">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="506e2-141">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="506e2-142">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="506e2-142">Suspended</span></span>|<span data-ttu-id="506e2-143">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="506e2-143">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="506e2-144">Sonlandırıldı</span><span class="sxs-lookup"><span data-stu-id="506e2-144">Terminated</span></span>|<span data-ttu-id="506e2-145">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="506e2-145">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="506e2-146">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="506e2-146">Unsuspended</span></span>|<span data-ttu-id="506e2-147">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="506e2-147">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="506e2-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="506e2-148">Example</span></span>  

 <span data-ttu-id="506e2-149">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="506e2-149">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="506e2-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="506e2-150">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="506e2-151">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="506e2-151">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="506e2-152">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="506e2-152">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
