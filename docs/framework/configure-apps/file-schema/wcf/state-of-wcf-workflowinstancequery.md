---
description: 'WCF hakkında daha fazla bilgi edinin: <state><workflowInstanceQuery>'
title: <state> WCF, <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 8dbf741473e5f3c15c1833868c2c17abdfba6643
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682650"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="f0675-103">\<state> WCF, \<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="f0675-103">\<state> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="f0675-104">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f0675-104">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="f0675-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f0675-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-wcf-workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="f0675-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f0675-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0675-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="f0675-107">Attributes and elements</span></span>

<span data-ttu-id="f0675-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f0675-108">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="f0675-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f0675-109">Attributes</span></span>

|<span data-ttu-id="f0675-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f0675-110">Attribute</span></span>|<span data-ttu-id="f0675-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0675-111">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="f0675-112">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durumu belirten dize.</span><span class="sxs-lookup"><span data-stu-id="f0675-112">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0675-113">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="f0675-113">Child elements</span></span>

<span data-ttu-id="f0675-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="f0675-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f0675-115">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="f0675-115">Parent elements</span></span>

|<span data-ttu-id="f0675-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0675-116">Element</span></span>|<span data-ttu-id="f0675-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0675-117">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="f0675-118">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f0675-118">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0675-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0675-119">Remarks</span></span>  

<span data-ttu-id="f0675-120">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f0675-120">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="f0675-121">Olası durum değerleri aşağıdaki tabloda açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="f0675-121">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="f0675-122">Durum</span><span class="sxs-lookup"><span data-stu-id="f0675-122">State</span></span>|<span data-ttu-id="f0675-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0675-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f0675-124">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="f0675-124">Aborted</span></span>|<span data-ttu-id="f0675-125">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f0675-125">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="f0675-126">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="f0675-126">Completed</span></span>|<span data-ttu-id="f0675-127">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="f0675-127">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="f0675-128">Silindi</span><span class="sxs-lookup"><span data-stu-id="f0675-128">Deleted</span></span>|<span data-ttu-id="f0675-129">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="f0675-129">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="f0675-130">Boş</span><span class="sxs-lookup"><span data-stu-id="f0675-130">Idle</span></span>|<span data-ttu-id="f0675-131">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="f0675-131">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="f0675-132">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="f0675-132">Persisted</span></span>|<span data-ttu-id="f0675-133">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="f0675-133">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="f0675-134">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="f0675-134">Resumed</span></span>|<span data-ttu-id="f0675-135">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="f0675-135">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="f0675-136">Başlarken</span><span class="sxs-lookup"><span data-stu-id="f0675-136">Started</span></span>|<span data-ttu-id="f0675-137">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="f0675-137">The workflow instance is started.</span></span>|  
|<span data-ttu-id="f0675-138">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="f0675-138">UnhandledException</span></span>|<span data-ttu-id="f0675-139">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="f0675-139">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="f0675-140">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="f0675-140">Unloaded</span></span>|<span data-ttu-id="f0675-141">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="f0675-141">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="f0675-142">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="f0675-142">Canceled</span></span>|<span data-ttu-id="f0675-143">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f0675-143">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="f0675-144">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="f0675-144">Suspended</span></span>|<span data-ttu-id="f0675-145">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="f0675-145">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="f0675-146">Sonlandırıldı</span><span class="sxs-lookup"><span data-stu-id="f0675-146">Terminated</span></span>|<span data-ttu-id="f0675-147">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="f0675-147">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="f0675-148">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="f0675-148">Unsuspended</span></span>|<span data-ttu-id="f0675-149">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="f0675-149">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f0675-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0675-150">Example</span></span>

<span data-ttu-id="f0675-151">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="f0675-151">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="f0675-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0675-152">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f0675-153">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f0675-153">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f0675-154">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f0675-154">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
