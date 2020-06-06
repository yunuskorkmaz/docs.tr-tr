---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 1a7c839a5ff8fac9470aea71a4886d9000086e9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398615"
---
# \<states>
<span data-ttu-id="47b7c-101">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="47b7c-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="47b7c-102">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="47b7c-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="47b7c-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47b7c-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47b7c-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="47b7c-104">Attributes and Elements</span></span>  
 <span data-ttu-id="47b7c-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47b7c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47b7c-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="47b7c-106">Attributes</span></span>  
 <span data-ttu-id="47b7c-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="47b7c-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="47b7c-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="47b7c-108">Child Elements</span></span>  
  
|<span data-ttu-id="47b7c-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="47b7c-109">Element</span></span>|<span data-ttu-id="47b7c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47b7c-110">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](states.md)|<span data-ttu-id="47b7c-111">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durum.</span><span class="sxs-lookup"><span data-stu-id="47b7c-111">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="47b7c-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="47b7c-112">Parent Elements</span></span>  
  
|<span data-ttu-id="47b7c-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="47b7c-113">Element</span></span>|<span data-ttu-id="47b7c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47b7c-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="47b7c-115">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="47b7c-115">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47b7c-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47b7c-116">Remarks</span></span>  
 <span data-ttu-id="47b7c-117">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="47b7c-117">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="47b7c-118">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="47b7c-118">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="47b7c-119">Eyalet</span><span class="sxs-lookup"><span data-stu-id="47b7c-119">State</span></span>|<span data-ttu-id="47b7c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47b7c-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="47b7c-121">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="47b7c-121">Aborted</span></span>|<span data-ttu-id="47b7c-122">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="47b7c-122">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="47b7c-123">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="47b7c-123">Completed</span></span>|<span data-ttu-id="47b7c-124">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="47b7c-124">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="47b7c-125">Silindi</span><span class="sxs-lookup"><span data-stu-id="47b7c-125">Deleted</span></span>|<span data-ttu-id="47b7c-126">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="47b7c-126">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="47b7c-127">Boş</span><span class="sxs-lookup"><span data-stu-id="47b7c-127">Idle</span></span>|<span data-ttu-id="47b7c-128">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="47b7c-128">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="47b7c-129">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="47b7c-129">Persisted</span></span>|<span data-ttu-id="47b7c-130">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="47b7c-130">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="47b7c-131">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="47b7c-131">Resumed</span></span>|<span data-ttu-id="47b7c-132">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="47b7c-132">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="47b7c-133">Başlarken</span><span class="sxs-lookup"><span data-stu-id="47b7c-133">Started</span></span>|<span data-ttu-id="47b7c-134">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="47b7c-134">The workflow instance is started.</span></span>|  
|<span data-ttu-id="47b7c-135">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="47b7c-135">UnhandledException</span></span>|<span data-ttu-id="47b7c-136">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="47b7c-136">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="47b7c-137">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="47b7c-137">Unloaded</span></span>|<span data-ttu-id="47b7c-138">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="47b7c-138">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="47b7c-139">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="47b7c-139">Canceled</span></span>|<span data-ttu-id="47b7c-140">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="47b7c-140">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="47b7c-141">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="47b7c-141">Suspended</span></span>|<span data-ttu-id="47b7c-142">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="47b7c-142">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="47b7c-143">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="47b7c-143">Terminated</span></span>|<span data-ttu-id="47b7c-144">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="47b7c-144">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="47b7c-145">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="47b7c-145">Unsuspended</span></span>|<span data-ttu-id="47b7c-146">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="47b7c-146">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="47b7c-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="47b7c-147">Example</span></span>  
 <span data-ttu-id="47b7c-148">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="47b7c-148">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47b7c-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47b7c-149">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="47b7c-150">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="47b7c-150">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="47b7c-151">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="47b7c-151">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
