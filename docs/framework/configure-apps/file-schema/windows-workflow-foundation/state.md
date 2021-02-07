---
description: 'Hakkında daha fazla bilgi edinin: <state>'
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: c04ba8a791d08e65337ffc28cd86f5a4a6af150f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729764"
---
# \<state>

<span data-ttu-id="51833-102">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="51833-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="51833-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="51833-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="51833-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="51833-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51833-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="51833-105">Attributes and Elements</span></span>  

 <span data-ttu-id="51833-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="51833-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51833-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="51833-107">Attributes</span></span>  
  
|<span data-ttu-id="51833-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="51833-108">Attribute</span></span>|<span data-ttu-id="51833-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51833-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51833-110">name</span><span class="sxs-lookup"><span data-stu-id="51833-110">name</span></span>|<span data-ttu-id="51833-111">İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durumu belirten dize.</span><span class="sxs-lookup"><span data-stu-id="51833-111">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51833-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="51833-112">Child Elements</span></span>  

 <span data-ttu-id="51833-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="51833-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51833-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="51833-114">Parent Elements</span></span>  
  
|<span data-ttu-id="51833-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="51833-115">Element</span></span>|<span data-ttu-id="51833-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51833-116">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="51833-117">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="51833-117">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51833-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51833-118">Remarks</span></span>  

 <span data-ttu-id="51833-119">Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="51833-119">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="51833-120">Olası durum değerleri aşağıdaki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="51833-120">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="51833-121">Durum</span><span class="sxs-lookup"><span data-stu-id="51833-121">State</span></span>|<span data-ttu-id="51833-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51833-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="51833-123">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="51833-123">Aborted</span></span>|<span data-ttu-id="51833-124">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="51833-124">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="51833-125">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="51833-125">Completed</span></span>|<span data-ttu-id="51833-126">İş akışı örneği tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="51833-126">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="51833-127">Silindi</span><span class="sxs-lookup"><span data-stu-id="51833-127">Deleted</span></span>|<span data-ttu-id="51833-128">İş akışı örneği silinir.</span><span class="sxs-lookup"><span data-stu-id="51833-128">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="51833-129">Boş</span><span class="sxs-lookup"><span data-stu-id="51833-129">Idle</span></span>|<span data-ttu-id="51833-130">İş akışı örneği boş.</span><span class="sxs-lookup"><span data-stu-id="51833-130">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="51833-131">Kalıcı</span><span class="sxs-lookup"><span data-stu-id="51833-131">Persisted</span></span>|<span data-ttu-id="51833-132">İş akışı örneği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="51833-132">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="51833-133">Sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="51833-133">Resumed</span></span>|<span data-ttu-id="51833-134">İş akışı örneği işlemi devam etti.</span><span class="sxs-lookup"><span data-stu-id="51833-134">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="51833-135">Başlarken</span><span class="sxs-lookup"><span data-stu-id="51833-135">Started</span></span>|<span data-ttu-id="51833-136">İş akışı örneği başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="51833-136">The workflow instance is started.</span></span>|  
|<span data-ttu-id="51833-137">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="51833-137">UnhandledException</span></span>|<span data-ttu-id="51833-138">İş akışı örneği işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="51833-138">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="51833-139">Kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="51833-139">Unloaded</span></span>|<span data-ttu-id="51833-140">İş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="51833-140">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="51833-141">İptal edildi</span><span class="sxs-lookup"><span data-stu-id="51833-141">Canceled</span></span>|<span data-ttu-id="51833-142">İş akışı örneği iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="51833-142">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="51833-143">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="51833-143">Suspended</span></span>|<span data-ttu-id="51833-144">İş akışı örneği askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="51833-144">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="51833-145">Sonlandırıldı</span><span class="sxs-lookup"><span data-stu-id="51833-145">Terminated</span></span>|<span data-ttu-id="51833-146">İş akışı örneği sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="51833-146">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="51833-147">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="51833-147">Unsuspended</span></span>|<span data-ttu-id="51833-148">İş akışı örneği unsuspended.</span><span class="sxs-lookup"><span data-stu-id="51833-148">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="51833-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="51833-149">Example</span></span>  

 <span data-ttu-id="51833-150">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="51833-150">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="51833-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51833-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="51833-152">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="51833-152">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="51833-153">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="51833-153">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
