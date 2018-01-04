---
title: "&lt;Workflowınstancequeries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a65f6b888e210c1786395bbbb9f60050fe8e2c1b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowinstancequeriesgt"></a><span data-ttu-id="1944a-102">&lt;Workflowınstancequeries&gt;</span><span class="sxs-lookup"><span data-stu-id="1944a-102">&lt;workflowInstanceQueries&gt;</span></span>
<span data-ttu-id="1944a-103">Başlatılan ya da tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izlemek yapılandırma öğelerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1944a-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="1944a-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1944a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="1944a-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="1944a-105">\<system.serviceModel></span></span>  
<span data-ttu-id="1944a-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="1944a-106">\<tracking></span></span>  
<span data-ttu-id="1944a-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="1944a-107">\<trackingProfile></span></span>  
<span data-ttu-id="1944a-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="1944a-108">\<workflow></span></span>  
<span data-ttu-id="1944a-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="1944a-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1944a-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1944a-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1944a-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1944a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1944a-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1944a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1944a-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1944a-113">Attributes</span></span>  
 <span data-ttu-id="1944a-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="1944a-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1944a-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1944a-115">Child Elements</span></span>  
  
|<span data-ttu-id="1944a-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="1944a-116">Element</span></span>|<span data-ttu-id="1944a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1944a-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1944a-118">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="1944a-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="1944a-119">İş akışı örneği yaşam döngüsü değişiklikleri izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="1944a-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1944a-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1944a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1944a-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="1944a-121">Element</span></span>|<span data-ttu-id="1944a-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1944a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1944a-123">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="1944a-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="1944a-124">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="1944a-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1944a-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1944a-125">Remarks</span></span>  
 <span data-ttu-id="1944a-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="1944a-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="1944a-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="1944a-127">Example</span></span>  
 <span data-ttu-id="1944a-128">Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="1944a-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1944a-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1944a-129">See Also</span></span>  
 <span data-ttu-id="1944a-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1944a-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="1944a-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1944a-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="1944a-132">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="1944a-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="1944a-133">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="1944a-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
