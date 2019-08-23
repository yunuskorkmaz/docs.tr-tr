---
title: <workflowInstanceQueries>WCF
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: feae65a75f9f0b2b1b398f3f9e80ac4c8d971dcc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915309"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="a50ac-102">\<WCF > WorkflowInstanceQueries</span><span class="sxs-lookup"><span data-stu-id="a50ac-102">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="a50ac-103">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a50ac-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="a50ac-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a50ac-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a50ac-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a50ac-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a50ac-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="a50ac-106">\<tracking></span></span>  
<span data-ttu-id="a50ac-107">\<Profiller ></span><span class="sxs-lookup"><span data-stu-id="a50ac-107">\<profiles></span></span>  
<span data-ttu-id="a50ac-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a50ac-108">\<trackingProfile></span></span>  
<span data-ttu-id="a50ac-109">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="a50ac-109">\<workflow></span></span>  
<span data-ttu-id="a50ac-110">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="a50ac-110">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a50ac-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a50ac-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a50ac-112">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="a50ac-112">Attributes and elements</span></span>

<span data-ttu-id="a50ac-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a50ac-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a50ac-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a50ac-114">Attributes</span></span>  

<span data-ttu-id="a50ac-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="a50ac-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a50ac-116">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a50ac-116">Child elements</span></span>  
  
|<span data-ttu-id="a50ac-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="a50ac-117">Element</span></span>|<span data-ttu-id="a50ac-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a50ac-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a50ac-119">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="a50ac-119">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="a50ac-120">İş akışı örneği yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="a50ac-120">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a50ac-121">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="a50ac-121">Parent elements</span></span>  
  
|<span data-ttu-id="a50ac-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="a50ac-122">Element</span></span>|<span data-ttu-id="a50ac-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a50ac-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a50ac-124">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="a50ac-124">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="a50ac-125">[ActivityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="a50ac-125">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a50ac-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a50ac-126">Remarks</span></span>

<span data-ttu-id="a50ac-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="a50ac-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="a50ac-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="a50ac-128">Example</span></span>  

<span data-ttu-id="a50ac-129">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="a50ac-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="a50ac-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a50ac-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a50ac-131">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a50ac-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a50ac-132">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a50ac-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
