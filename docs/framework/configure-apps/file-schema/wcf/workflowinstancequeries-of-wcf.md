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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f02336dc35083009f601b3c4fb3568585a0beeef
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltworkflowinstancequeriesgt-of-wcf"></a><span data-ttu-id="b0f33-102">WCF &lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="b0f33-102">&lt;workflowInstanceQueries&gt; of WCF</span></span>
<span data-ttu-id="b0f33-103">Başlatılan ya da tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izlemek yapılandırma öğelerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b0f33-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="b0f33-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b0f33-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="b0f33-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b0f33-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b0f33-106">\<tracking></span><span class="sxs-lookup"><span data-stu-id="b0f33-106">\<tracking></span></span>  
<span data-ttu-id="b0f33-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b0f33-107">\<trackingProfile></span></span>  
<span data-ttu-id="b0f33-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="b0f33-108">\<workflow></span></span>  
<span data-ttu-id="b0f33-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="b0f33-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0f33-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0f33-110">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0f33-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0f33-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b0f33-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0f33-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0f33-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0f33-113">Attributes</span></span>  
 <span data-ttu-id="b0f33-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="b0f33-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b0f33-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0f33-115">Child Elements</span></span>  
  
|<span data-ttu-id="b0f33-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0f33-116">Element</span></span>|<span data-ttu-id="b0f33-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0f33-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0f33-118">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="b0f33-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="b0f33-119">İş akışı örneği yaşam döngüsü değişiklikleri izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="b0f33-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0f33-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0f33-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b0f33-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0f33-121">Element</span></span>|<span data-ttu-id="b0f33-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0f33-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0f33-123">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="b0f33-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="b0f33-124">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi [activityDefinitionId](http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) özelliği.</span><span class="sxs-lookup"><span data-stu-id="b0f33-124">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0f33-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0f33-125">Remarks</span></span>  
 <span data-ttu-id="b0f33-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="b0f33-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="b0f33-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0f33-127">Example</span></span>  
 <span data-ttu-id="b0f33-128">Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="b0f33-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0f33-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b0f33-129">See Also</span></span>  
 <span data-ttu-id="b0f33-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b0f33-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b0f33-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b0f33-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b0f33-132">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="b0f33-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b0f33-133">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="b0f33-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
