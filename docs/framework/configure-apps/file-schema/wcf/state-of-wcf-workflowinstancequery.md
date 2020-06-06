---
title: <state>WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 80f7532f3c51680a2e34713b526dc43822db61b9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854955"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="392f9-102">\<state>WCF,\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="392f9-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="392f9-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="392f9-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="392f9-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="392f9-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
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
  
## <a name="syntax"></a><span data-ttu-id="392f9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="392f9-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="392f9-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="392f9-106">Attributes and elements</span></span>

<span data-ttu-id="392f9-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="392f9-107">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="392f9-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="392f9-108">Attributes</span></span>

|<span data-ttu-id="392f9-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="392f9-109">Attribute</span></span>|<span data-ttu-id="392f9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="392f9-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="392f9-111">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durumu belirten dize.</span><span class="sxs-lookup"><span data-stu-id="392f9-111">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="392f9-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="392f9-112">Child elements</span></span>

<span data-ttu-id="392f9-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="392f9-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="392f9-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="392f9-114">Parent elements</span></span>

|<span data-ttu-id="392f9-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="392f9-115">Element</span></span>|<span data-ttu-id="392f9-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="392f9-116">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="392f9-117">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="392f9-117">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="392f9-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="392f9-118">Remarks</span></span>  

<span data-ttu-id="392f9-119">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="392f9-119">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="392f9-120">Olası durum değerleri aşağıdaki tabloda açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="392f9-120">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="392f9-121">Eyalet</span><span class="sxs-lookup"><span data-stu-id="392f9-121">State</span></span>|<span data-ttu-id="392f9-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="392f9-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="392f9-123">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="392f9-123">Aborted</span></span>|<span data-ttu-id="392f9-124">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="392f9-124">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="392f9-125">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="392f9-125">Completed</span></span>|<span data-ttu-id="392f9-126">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="392f9-126">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="392f9-127">Silindi</span><span class="sxs-lookup"><span data-stu-id="392f9-127">Deleted</span></span>|<span data-ttu-id="392f9-128">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="392f9-128">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="392f9-129">Boş</span><span class="sxs-lookup"><span data-stu-id="392f9-129">Idle</span></span>|<span data-ttu-id="392f9-130">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="392f9-130">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="392f9-131">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="392f9-131">Persisted</span></span>|<span data-ttu-id="392f9-132">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="392f9-132">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="392f9-133">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="392f9-133">Resumed</span></span>|<span data-ttu-id="392f9-134">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="392f9-134">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="392f9-135">Başlarken</span><span class="sxs-lookup"><span data-stu-id="392f9-135">Started</span></span>|<span data-ttu-id="392f9-136">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="392f9-136">The workflow instance is started.</span></span>|  
|<span data-ttu-id="392f9-137">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="392f9-137">UnhandledException</span></span>|<span data-ttu-id="392f9-138">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="392f9-138">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="392f9-139">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="392f9-139">Unloaded</span></span>|<span data-ttu-id="392f9-140">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="392f9-140">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="392f9-141">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="392f9-141">Canceled</span></span>|<span data-ttu-id="392f9-142">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="392f9-142">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="392f9-143">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="392f9-143">Suspended</span></span>|<span data-ttu-id="392f9-144">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="392f9-144">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="392f9-145">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="392f9-145">Terminated</span></span>|<span data-ttu-id="392f9-146">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="392f9-146">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="392f9-147">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="392f9-147">Unsuspended</span></span>|<span data-ttu-id="392f9-148">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="392f9-148">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="392f9-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="392f9-149">Example</span></span>

<span data-ttu-id="392f9-150">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="392f9-150">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="392f9-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="392f9-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="392f9-152">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="392f9-152">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="392f9-153">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="392f9-153">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
