---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: e759f86e7746eaf3fdd72ed923612b24ef9b0c23
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150823"
---
# \<states>

<span data-ttu-id="fbac2-101">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fbac2-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="fbac2-102">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fbac2-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="fbac2-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="fbac2-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbac2-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fbac2-104">Attributes and Elements</span></span>  

 <span data-ttu-id="fbac2-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fbac2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbac2-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fbac2-106">Attributes</span></span>  

 <span data-ttu-id="fbac2-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="fbac2-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fbac2-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fbac2-108">Child Elements</span></span>  
  
|<span data-ttu-id="fbac2-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="fbac2-109">Element</span></span>|<span data-ttu-id="fbac2-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fbac2-110">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](states.md)|<span data-ttu-id="fbac2-111">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durum.</span><span class="sxs-lookup"><span data-stu-id="fbac2-111">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fbac2-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fbac2-112">Parent Elements</span></span>  
  
|<span data-ttu-id="fbac2-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="fbac2-113">Element</span></span>|<span data-ttu-id="fbac2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fbac2-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="fbac2-115">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="fbac2-115">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbac2-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fbac2-116">Remarks</span></span>  

 <span data-ttu-id="fbac2-117">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fbac2-117">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="fbac2-118">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="fbac2-118">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="fbac2-119">Durum</span><span class="sxs-lookup"><span data-stu-id="fbac2-119">State</span></span>|<span data-ttu-id="fbac2-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fbac2-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fbac2-121">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="fbac2-121">Aborted</span></span>|<span data-ttu-id="fbac2-122">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fbac2-122">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="fbac2-123">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="fbac2-123">Completed</span></span>|<span data-ttu-id="fbac2-124">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="fbac2-124">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="fbac2-125">Silindi</span><span class="sxs-lookup"><span data-stu-id="fbac2-125">Deleted</span></span>|<span data-ttu-id="fbac2-126">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="fbac2-126">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="fbac2-127">Boş</span><span class="sxs-lookup"><span data-stu-id="fbac2-127">Idle</span></span>|<span data-ttu-id="fbac2-128">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="fbac2-128">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="fbac2-129">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="fbac2-129">Persisted</span></span>|<span data-ttu-id="fbac2-130">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="fbac2-130">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="fbac2-131">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="fbac2-131">Resumed</span></span>|<span data-ttu-id="fbac2-132">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="fbac2-132">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="fbac2-133">Başlarken</span><span class="sxs-lookup"><span data-stu-id="fbac2-133">Started</span></span>|<span data-ttu-id="fbac2-134">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="fbac2-134">The workflow instance is started.</span></span>|  
|<span data-ttu-id="fbac2-135">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="fbac2-135">UnhandledException</span></span>|<span data-ttu-id="fbac2-136">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="fbac2-136">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="fbac2-137">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="fbac2-137">Unloaded</span></span>|<span data-ttu-id="fbac2-138">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="fbac2-138">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="fbac2-139">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="fbac2-139">Canceled</span></span>|<span data-ttu-id="fbac2-140">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fbac2-140">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="fbac2-141">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="fbac2-141">Suspended</span></span>|<span data-ttu-id="fbac2-142">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="fbac2-142">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="fbac2-143">Sonlandırıldı</span><span class="sxs-lookup"><span data-stu-id="fbac2-143">Terminated</span></span>|<span data-ttu-id="fbac2-144">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="fbac2-144">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="fbac2-145">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="fbac2-145">Unsuspended</span></span>|<span data-ttu-id="fbac2-146">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="fbac2-146">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fbac2-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="fbac2-147">Example</span></span>  

 <span data-ttu-id="fbac2-148">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="fbac2-148">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fbac2-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbac2-149">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fbac2-150">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="fbac2-150">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fbac2-151">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="fbac2-151">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
