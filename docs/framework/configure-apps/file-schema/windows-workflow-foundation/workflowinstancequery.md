---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: f0a3c3a27b40000432b40b7008f81251fe771ca2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913136"
---
# <a name="workflowinstancequery"></a><span data-ttu-id="88221-101">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="88221-101">\<workflowInstanceQuery></span></span>
<span data-ttu-id="88221-102">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="88221-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="88221-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="88221-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="88221-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="88221-104">\<system.serviceModel></span></span>  
<span data-ttu-id="88221-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="88221-105">\<tracking></span></span>  
<span data-ttu-id="88221-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="88221-106">\<trackingProfile></span></span>  
<span data-ttu-id="88221-107">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="88221-107">\<workflow></span></span>  
<span data-ttu-id="88221-108">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="88221-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="88221-109">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="88221-109">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88221-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88221-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88221-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="88221-111">Attributes and Elements</span></span>  
 <span data-ttu-id="88221-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="88221-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88221-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="88221-113">Attributes</span></span>  
 <span data-ttu-id="88221-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="88221-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="88221-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="88221-115">Child Elements</span></span>  
  
|<span data-ttu-id="88221-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="88221-116">Element</span></span>|<span data-ttu-id="88221-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88221-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88221-118">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="88221-118">\<states></span></span>](states.md)|<span data-ttu-id="88221-119">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="88221-119">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="88221-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="88221-120">Parent Elements</span></span>  
  
|<span data-ttu-id="88221-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="88221-121">Element</span></span>|<span data-ttu-id="88221-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88221-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88221-123">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="88221-123">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="88221-124">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="88221-124">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88221-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88221-125">Remarks</span></span>  
 <span data-ttu-id="88221-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="88221-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="88221-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="88221-127">Example</span></span>  
 <span data-ttu-id="88221-128">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="88221-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="88221-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88221-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="88221-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="88221-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="88221-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="88221-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
