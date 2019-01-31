---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 7541ddcf4df8135d82b1f7f5ae2c02f031090e17
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275083"
---
# <a name="workflowinstancequery"></a><span data-ttu-id="4f525-101">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="4f525-101">\<workflowInstanceQuery></span></span>
<span data-ttu-id="4f525-102">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4f525-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="4f525-103">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4f525-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4f525-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4f525-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4f525-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="4f525-105">\<tracking></span></span>  
<span data-ttu-id="4f525-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4f525-106">\<trackingProfile></span></span>  
<span data-ttu-id="4f525-107">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="4f525-107">\<workflow></span></span>  
<span data-ttu-id="4f525-108">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="4f525-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="4f525-109">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="4f525-109">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f525-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f525-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f525-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f525-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4f525-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f525-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f525-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4f525-113">Attributes</span></span>  
 <span data-ttu-id="4f525-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="4f525-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4f525-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f525-115">Child Elements</span></span>  
  
|<span data-ttu-id="4f525-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="4f525-116">Element</span></span>|<span data-ttu-id="4f525-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f525-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f525-118">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="4f525-118">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="4f525-119">Abone olunan durumları izleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4f525-119">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f525-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f525-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4f525-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="4f525-121">Element</span></span>|<span data-ttu-id="4f525-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f525-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f525-123">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="4f525-123">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="4f525-124">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleme yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4f525-124">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f525-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f525-125">Remarks</span></span>  
 <span data-ttu-id="4f525-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="4f525-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="4f525-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f525-127">Example</span></span>  
 <span data-ttu-id="4f525-128">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="4f525-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f525-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f525-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4f525-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="4f525-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4f525-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="4f525-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
