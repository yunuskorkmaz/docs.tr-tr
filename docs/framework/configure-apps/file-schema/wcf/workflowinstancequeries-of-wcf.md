---
title: WCF &lt;workflowInstanceQueries&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6ca8104ba2470593e07e03a7fe0bc80c9cd2f6a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowinstancequeriesgt-of-wcf"></a><span data-ttu-id="02703-102">WCF &lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="02703-102">&lt;workflowInstanceQueries&gt; of WCF</span></span>
<span data-ttu-id="02703-103">Başlatılan ya da tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izlemek yapılandırma öğelerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="02703-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="02703-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="02703-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="02703-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="02703-105">\<system.serviceModel></span></span>  
<span data-ttu-id="02703-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="02703-106">\<tracking></span></span>  
<span data-ttu-id="02703-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="02703-107">\<trackingProfile></span></span>  
<span data-ttu-id="02703-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="02703-108">\<workflow></span></span>  
<span data-ttu-id="02703-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="02703-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02703-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02703-110">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02703-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="02703-111">Attributes and Elements</span></span>  
 <span data-ttu-id="02703-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="02703-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02703-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="02703-113">Attributes</span></span>  
 <span data-ttu-id="02703-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="02703-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="02703-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="02703-115">Child Elements</span></span>  
  
|<span data-ttu-id="02703-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="02703-116">Element</span></span>|<span data-ttu-id="02703-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02703-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02703-118">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="02703-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="02703-119">İş akışı örneği yaşam döngüsü değişiklikleri izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="02703-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02703-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="02703-120">Parent Elements</span></span>  
  
|<span data-ttu-id="02703-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="02703-121">Element</span></span>|<span data-ttu-id="02703-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02703-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02703-123">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="02703-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="02703-124">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi [activityDefinitionId](http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) özelliği.</span><span class="sxs-lookup"><span data-stu-id="02703-124">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02703-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02703-125">Remarks</span></span>  
 <span data-ttu-id="02703-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="02703-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="02703-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="02703-127">Example</span></span>  
 <span data-ttu-id="02703-128">Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="02703-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="02703-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02703-129">See Also</span></span>  
 <span data-ttu-id="02703-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="02703-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="02703-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="02703-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="02703-132">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="02703-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="02703-133">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="02703-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
