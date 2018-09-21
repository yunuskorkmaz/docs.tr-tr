---
title: WCF &lt;workflowInstanceQueries&gt;
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: dfa75a7e4729244ba5887e6666c0fdfe840e9faf
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46527965"
---
# <a name="ltworkflowinstancequeriesgt-of-wcf"></a><span data-ttu-id="a0d5f-102">WCF &lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="a0d5f-102">&lt;workflowInstanceQueries&gt; of WCF</span></span>
<span data-ttu-id="a0d5f-103">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleme yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a0d5f-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="a0d5f-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a0d5f-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="a0d5f-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a0d5f-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a0d5f-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="a0d5f-106">\<tracking></span></span>  
<span data-ttu-id="a0d5f-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a0d5f-107">\<trackingProfile></span></span>  
<span data-ttu-id="a0d5f-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="a0d5f-108">\<workflow></span></span>  
<span data-ttu-id="a0d5f-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="a0d5f-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d5f-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0d5f-110">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0d5f-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0d5f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a0d5f-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0d5f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0d5f-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a0d5f-113">Attributes</span></span>  
 <span data-ttu-id="a0d5f-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="a0d5f-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a0d5f-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0d5f-115">Child Elements</span></span>  
  
|<span data-ttu-id="a0d5f-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0d5f-116">Element</span></span>|<span data-ttu-id="a0d5f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0d5f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0d5f-118">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="a0d5f-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="a0d5f-119">İş akışı örneği yaşam döngüsü değişiklikleri izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="a0d5f-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0d5f-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0d5f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a0d5f-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0d5f-121">Element</span></span>|<span data-ttu-id="a0d5f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0d5f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0d5f-123">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="a0d5f-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="a0d5f-124">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi [activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) özelliği.</span><span class="sxs-lookup"><span data-stu-id="a0d5f-124">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0d5f-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0d5f-125">Remarks</span></span>  
 <span data-ttu-id="a0d5f-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="a0d5f-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="a0d5f-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0d5f-127">Example</span></span>  
 <span data-ttu-id="a0d5f-128">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="a0d5f-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0d5f-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0d5f-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="a0d5f-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a0d5f-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a0d5f-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a0d5f-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
