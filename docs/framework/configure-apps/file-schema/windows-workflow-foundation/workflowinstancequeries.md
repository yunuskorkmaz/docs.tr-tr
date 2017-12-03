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
ms.openlocfilehash: fef440aa086253cd4f7df709ee5b5764fe7b2789
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowinstancequeriesgt"></a><span data-ttu-id="54a3a-102">&lt;Workflowınstancequeries&gt;</span><span class="sxs-lookup"><span data-stu-id="54a3a-102">&lt;workflowInstanceQueries&gt;</span></span>
<span data-ttu-id="54a3a-103">Başlatılan ya da tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izlemek yapılandırma öğelerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="54a3a-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="54a3a-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="54a3a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="54a3a-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="54a3a-105">\<system.serviceModel></span></span>  
<span data-ttu-id="54a3a-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="54a3a-106">\<tracking></span></span>  
<span data-ttu-id="54a3a-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="54a3a-107">\<trackingProfile></span></span>  
<span data-ttu-id="54a3a-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="54a3a-108">\<workflow></span></span>  
<span data-ttu-id="54a3a-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="54a3a-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54a3a-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54a3a-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54a3a-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="54a3a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="54a3a-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="54a3a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54a3a-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="54a3a-113">Attributes</span></span>  
 <span data-ttu-id="54a3a-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="54a3a-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="54a3a-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="54a3a-115">Child Elements</span></span>  
  
|<span data-ttu-id="54a3a-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="54a3a-116">Element</span></span>|<span data-ttu-id="54a3a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54a3a-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54a3a-118">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="54a3a-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="54a3a-119">İş akışı örneği yaşam döngüsü değişiklikleri izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="54a3a-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54a3a-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="54a3a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="54a3a-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="54a3a-121">Element</span></span>|<span data-ttu-id="54a3a-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54a3a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54a3a-123">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="54a3a-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="54a3a-124">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="54a3a-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54a3a-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54a3a-125">Remarks</span></span>  
 <span data-ttu-id="54a3a-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="54a3a-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="54a3a-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="54a3a-127">Example</span></span>  
 <span data-ttu-id="54a3a-128">Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="54a3a-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="54a3a-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54a3a-129">See Also</span></span>  
 <span data-ttu-id="54a3a-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="54a3a-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="54a3a-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="54a3a-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="54a3a-132">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="54a3a-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="54a3a-133">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="54a3a-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
