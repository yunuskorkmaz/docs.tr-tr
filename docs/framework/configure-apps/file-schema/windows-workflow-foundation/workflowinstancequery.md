---
title: "&lt;Workflowınstancequery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c81dc33aa08fa40eac8c91c54ce1964a3168dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowinstancequerygt"></a><span data-ttu-id="56957-102">&lt;Workflowınstancequery&gt;</span><span class="sxs-lookup"><span data-stu-id="56957-102">&lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="56957-103">Başlatılan ya da tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="56957-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="56957-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="56957-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="56957-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="56957-105">\<system.serviceModel></span></span>  
<span data-ttu-id="56957-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="56957-106">\<tracking></span></span>  
<span data-ttu-id="56957-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="56957-107">\<trackingProfile></span></span>  
<span data-ttu-id="56957-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="56957-108">\<workflow></span></span>  
<span data-ttu-id="56957-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="56957-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="56957-110">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="56957-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56957-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56957-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56957-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="56957-112">Attributes and Elements</span></span>  
 <span data-ttu-id="56957-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="56957-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56957-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="56957-114">Attributes</span></span>  
 <span data-ttu-id="56957-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="56957-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="56957-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="56957-116">Child Elements</span></span>  
  
|<span data-ttu-id="56957-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="56957-117">Element</span></span>|<span data-ttu-id="56957-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56957-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56957-119">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="56957-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="56957-120">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="56957-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="56957-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="56957-121">Parent Elements</span></span>  
  
|<span data-ttu-id="56957-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="56957-122">Element</span></span>|<span data-ttu-id="56957-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56957-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56957-124">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="56957-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="56957-125">Başlatılan ya da tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izlemek yapılandırma öğelerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="56957-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56957-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56957-126">Remarks</span></span>  
 <span data-ttu-id="56957-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="56957-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="56957-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="56957-128">Example</span></span>  
 <span data-ttu-id="56957-129">Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="56957-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="56957-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56957-130">See Also</span></span>  
 <span data-ttu-id="56957-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="56957-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="56957-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="56957-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="56957-133">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="56957-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="56957-134">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="56957-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
