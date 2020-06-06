---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 7af75182cf38a6acb8a31b71e8b7b42103f8046b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398645"
---
# \<state>
<span data-ttu-id="c97b2-101">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c97b2-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="c97b2-102">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c97b2-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="c97b2-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c97b2-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c97b2-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c97b2-104">Attributes and Elements</span></span>  
 <span data-ttu-id="c97b2-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c97b2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c97b2-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c97b2-106">Attributes</span></span>  
  
|<span data-ttu-id="c97b2-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c97b2-107">Attribute</span></span>|<span data-ttu-id="c97b2-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c97b2-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c97b2-109">name</span><span class="sxs-lookup"><span data-stu-id="c97b2-109">name</span></span>|<span data-ttu-id="c97b2-110">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durumu belirten dize.</span><span class="sxs-lookup"><span data-stu-id="c97b2-110">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c97b2-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c97b2-111">Child Elements</span></span>  
 <span data-ttu-id="c97b2-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="c97b2-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c97b2-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c97b2-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c97b2-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="c97b2-114">Element</span></span>|<span data-ttu-id="c97b2-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c97b2-115">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="c97b2-116">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c97b2-116">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c97b2-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c97b2-117">Remarks</span></span>  
 <span data-ttu-id="c97b2-118">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c97b2-118">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="c97b2-119">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="c97b2-119">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="c97b2-120">Eyalet</span><span class="sxs-lookup"><span data-stu-id="c97b2-120">State</span></span>|<span data-ttu-id="c97b2-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c97b2-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c97b2-122">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="c97b2-122">Aborted</span></span>|<span data-ttu-id="c97b2-123">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c97b2-123">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="c97b2-124">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="c97b2-124">Completed</span></span>|<span data-ttu-id="c97b2-125">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c97b2-125">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="c97b2-126">Silindi</span><span class="sxs-lookup"><span data-stu-id="c97b2-126">Deleted</span></span>|<span data-ttu-id="c97b2-127">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="c97b2-127">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="c97b2-128">Boş</span><span class="sxs-lookup"><span data-stu-id="c97b2-128">Idle</span></span>|<span data-ttu-id="c97b2-129">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="c97b2-129">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="c97b2-130">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="c97b2-130">Persisted</span></span>|<span data-ttu-id="c97b2-131">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="c97b2-131">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="c97b2-132">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="c97b2-132">Resumed</span></span>|<span data-ttu-id="c97b2-133">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="c97b2-133">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="c97b2-134">Başlarken</span><span class="sxs-lookup"><span data-stu-id="c97b2-134">Started</span></span>|<span data-ttu-id="c97b2-135">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="c97b2-135">The workflow instance is started.</span></span>|  
|<span data-ttu-id="c97b2-136">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="c97b2-136">UnhandledException</span></span>|<span data-ttu-id="c97b2-137">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="c97b2-137">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="c97b2-138">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="c97b2-138">Unloaded</span></span>|<span data-ttu-id="c97b2-139">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c97b2-139">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="c97b2-140">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="c97b2-140">Canceled</span></span>|<span data-ttu-id="c97b2-141">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c97b2-141">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="c97b2-142">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="c97b2-142">Suspended</span></span>|<span data-ttu-id="c97b2-143">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="c97b2-143">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="c97b2-144">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="c97b2-144">Terminated</span></span>|<span data-ttu-id="c97b2-145">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="c97b2-145">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="c97b2-146">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="c97b2-146">Unsuspended</span></span>|<span data-ttu-id="c97b2-147">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="c97b2-147">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c97b2-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="c97b2-148">Example</span></span>  
 <span data-ttu-id="c97b2-149">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="c97b2-149">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c97b2-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c97b2-150">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c97b2-151">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c97b2-151">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c97b2-152">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c97b2-152">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
