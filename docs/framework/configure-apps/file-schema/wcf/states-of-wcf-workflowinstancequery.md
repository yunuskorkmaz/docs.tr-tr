---
title: <states>WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 5b779cf1074687dbd648b23d04f7cf3a354a2014
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855033"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="4aa91-102">\<states>WCF,\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="4aa91-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="4aa91-103">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4aa91-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="4aa91-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4aa91-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="4aa91-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4aa91-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4aa91-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="4aa91-106">Attributes and elements</span></span>

<span data-ttu-id="4aa91-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4aa91-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4aa91-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4aa91-108">Attributes</span></span>  

<span data-ttu-id="4aa91-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="4aa91-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4aa91-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="4aa91-110">Child elements</span></span>
  
|<span data-ttu-id="4aa91-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="4aa91-111">Element</span></span>|<span data-ttu-id="4aa91-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4aa91-112">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="4aa91-113">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durum.</span><span class="sxs-lookup"><span data-stu-id="4aa91-113">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4aa91-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="4aa91-114">Parent elements</span></span>  
  
|<span data-ttu-id="4aa91-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="4aa91-115">Element</span></span>|<span data-ttu-id="4aa91-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4aa91-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="4aa91-117">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="4aa91-117">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4aa91-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4aa91-118">Remarks</span></span>

<span data-ttu-id="4aa91-119">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4aa91-119">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="4aa91-120">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="4aa91-120">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="4aa91-121">Eyalet</span><span class="sxs-lookup"><span data-stu-id="4aa91-121">State</span></span>|<span data-ttu-id="4aa91-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4aa91-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4aa91-123">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="4aa91-123">Aborted</span></span>|<span data-ttu-id="4aa91-124">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="4aa91-124">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="4aa91-125">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="4aa91-125">Completed</span></span>|<span data-ttu-id="4aa91-126">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="4aa91-126">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="4aa91-127">Silindi</span><span class="sxs-lookup"><span data-stu-id="4aa91-127">Deleted</span></span>|<span data-ttu-id="4aa91-128">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="4aa91-128">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="4aa91-129">Boş</span><span class="sxs-lookup"><span data-stu-id="4aa91-129">Idle</span></span>|<span data-ttu-id="4aa91-130">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="4aa91-130">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="4aa91-131">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="4aa91-131">Persisted</span></span>|<span data-ttu-id="4aa91-132">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="4aa91-132">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="4aa91-133">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="4aa91-133">Resumed</span></span>|<span data-ttu-id="4aa91-134">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="4aa91-134">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="4aa91-135">Başlarken</span><span class="sxs-lookup"><span data-stu-id="4aa91-135">Started</span></span>|<span data-ttu-id="4aa91-136">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="4aa91-136">The workflow instance is started.</span></span>|  
|<span data-ttu-id="4aa91-137">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="4aa91-137">UnhandledException</span></span>|<span data-ttu-id="4aa91-138">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="4aa91-138">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="4aa91-139">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="4aa91-139">Unloaded</span></span>|<span data-ttu-id="4aa91-140">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="4aa91-140">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="4aa91-141">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="4aa91-141">Canceled</span></span>|<span data-ttu-id="4aa91-142">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="4aa91-142">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="4aa91-143">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="4aa91-143">Suspended</span></span>|<span data-ttu-id="4aa91-144">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="4aa91-144">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="4aa91-145">Sona erdi</span><span class="sxs-lookup"><span data-stu-id="4aa91-145">Terminated</span></span>|<span data-ttu-id="4aa91-146">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="4aa91-146">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="4aa91-147">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="4aa91-147">Unsuspended</span></span>|<span data-ttu-id="4aa91-148">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="4aa91-148">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4aa91-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="4aa91-149">Example</span></span>

<span data-ttu-id="4aa91-150">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="4aa91-150">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="4aa91-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4aa91-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4aa91-152">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="4aa91-152">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4aa91-153">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="4aa91-153">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
