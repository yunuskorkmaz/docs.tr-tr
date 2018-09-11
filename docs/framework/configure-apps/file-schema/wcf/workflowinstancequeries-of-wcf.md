---
title: WCF &lt;workflowInstanceQueries&gt;
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: dfa75a7e4729244ba5887e6666c0fdfe840e9faf
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342150"
---
# <a name="ltworkflowinstancequeriesgt-of-wcf"></a><span data-ttu-id="d8046-102">WCF &lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="d8046-102">&lt;workflowInstanceQueries&gt; of WCF</span></span>
<span data-ttu-id="d8046-103">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleme yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d8046-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="d8046-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d8046-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="d8046-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d8046-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d8046-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="d8046-106">\<tracking></span></span>  
<span data-ttu-id="d8046-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d8046-107">\<trackingProfile></span></span>  
<span data-ttu-id="d8046-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="d8046-108">\<workflow></span></span>  
<span data-ttu-id="d8046-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="d8046-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8046-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8046-110">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8046-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8046-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d8046-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8046-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8046-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d8046-113">Attributes</span></span>  
 <span data-ttu-id="d8046-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="d8046-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d8046-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8046-115">Child Elements</span></span>  
  
|<span data-ttu-id="d8046-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="d8046-116">Element</span></span>|<span data-ttu-id="d8046-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8046-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8046-118">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="d8046-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="d8046-119">İş akışı örneği yaşam döngüsü değişiklikleri izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="d8046-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8046-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8046-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d8046-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="d8046-121">Element</span></span>|<span data-ttu-id="d8046-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8046-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8046-123">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="d8046-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="d8046-124">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi [activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) özelliği.</span><span class="sxs-lookup"><span data-stu-id="d8046-124">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8046-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8046-125">Remarks</span></span>  
 <span data-ttu-id="d8046-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="d8046-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="d8046-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8046-127">Example</span></span>  
 <span data-ttu-id="d8046-128">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="d8046-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8046-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8046-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="d8046-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="d8046-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d8046-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="d8046-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
