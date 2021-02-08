---
description: 'WCF hakkında daha fazla bilgi edinin: <states><workflowInstanceQuery>'
title: <states> WCF, <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 66b3008b352d1f76c30aab9a0ec038836f33d408
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786648"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="230cf-103">\<states> WCF, \<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="230cf-103">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="230cf-104">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="230cf-104">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="230cf-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="230cf-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="230cf-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="230cf-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="230cf-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="230cf-107">Attributes and elements</span></span>

<span data-ttu-id="230cf-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="230cf-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="230cf-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="230cf-109">Attributes</span></span>  

<span data-ttu-id="230cf-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="230cf-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="230cf-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="230cf-111">Child elements</span></span>
  
|<span data-ttu-id="230cf-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="230cf-112">Element</span></span>|<span data-ttu-id="230cf-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="230cf-113">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="230cf-114">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durum.</span><span class="sxs-lookup"><span data-stu-id="230cf-114">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="230cf-115">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="230cf-115">Parent elements</span></span>  
  
|<span data-ttu-id="230cf-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="230cf-116">Element</span></span>|<span data-ttu-id="230cf-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="230cf-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="230cf-118">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="230cf-118">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="230cf-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="230cf-119">Remarks</span></span>

<span data-ttu-id="230cf-120">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="230cf-120">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="230cf-121">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="230cf-121">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="230cf-122">Durum</span><span class="sxs-lookup"><span data-stu-id="230cf-122">State</span></span>|<span data-ttu-id="230cf-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="230cf-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="230cf-124">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="230cf-124">Aborted</span></span>|<span data-ttu-id="230cf-125">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="230cf-125">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="230cf-126">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="230cf-126">Completed</span></span>|<span data-ttu-id="230cf-127">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="230cf-127">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="230cf-128">Silindi</span><span class="sxs-lookup"><span data-stu-id="230cf-128">Deleted</span></span>|<span data-ttu-id="230cf-129">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="230cf-129">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="230cf-130">Boş</span><span class="sxs-lookup"><span data-stu-id="230cf-130">Idle</span></span>|<span data-ttu-id="230cf-131">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="230cf-131">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="230cf-132">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="230cf-132">Persisted</span></span>|<span data-ttu-id="230cf-133">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="230cf-133">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="230cf-134">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="230cf-134">Resumed</span></span>|<span data-ttu-id="230cf-135">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="230cf-135">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="230cf-136">Başlarken</span><span class="sxs-lookup"><span data-stu-id="230cf-136">Started</span></span>|<span data-ttu-id="230cf-137">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="230cf-137">The workflow instance is started.</span></span>|  
|<span data-ttu-id="230cf-138">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="230cf-138">UnhandledException</span></span>|<span data-ttu-id="230cf-139">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="230cf-139">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="230cf-140">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="230cf-140">Unloaded</span></span>|<span data-ttu-id="230cf-141">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="230cf-141">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="230cf-142">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="230cf-142">Canceled</span></span>|<span data-ttu-id="230cf-143">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="230cf-143">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="230cf-144">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="230cf-144">Suspended</span></span>|<span data-ttu-id="230cf-145">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="230cf-145">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="230cf-146">Sonlandırıldı</span><span class="sxs-lookup"><span data-stu-id="230cf-146">Terminated</span></span>|<span data-ttu-id="230cf-147">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="230cf-147">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="230cf-148">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="230cf-148">Unsuspended</span></span>|<span data-ttu-id="230cf-149">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="230cf-149">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="230cf-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="230cf-150">Example</span></span>

<span data-ttu-id="230cf-151">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="230cf-151">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="230cf-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="230cf-152">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="230cf-153">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="230cf-153">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="230cf-154">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="230cf-154">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
