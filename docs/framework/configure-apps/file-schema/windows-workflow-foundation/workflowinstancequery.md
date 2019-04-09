---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 6fe02cfea91633da41c8ebc7d8a78dd005ad3f4a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080910"
---
# <a name="workflowinstancequery"></a><span data-ttu-id="4d801-101">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="4d801-101">\<workflowInstanceQuery></span></span>
<span data-ttu-id="4d801-102">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4d801-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="4d801-103">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4d801-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4d801-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4d801-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4d801-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="4d801-105">\<tracking></span></span>  
<span data-ttu-id="4d801-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4d801-106">\<trackingProfile></span></span>  
<span data-ttu-id="4d801-107">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="4d801-107">\<workflow></span></span>  
<span data-ttu-id="4d801-108">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="4d801-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="4d801-109">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="4d801-109">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d801-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d801-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d801-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d801-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4d801-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4d801-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d801-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4d801-113">Attributes</span></span>  
 <span data-ttu-id="4d801-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="4d801-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4d801-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d801-115">Child Elements</span></span>  
  
|<span data-ttu-id="4d801-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="4d801-116">Element</span></span>|<span data-ttu-id="4d801-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d801-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d801-118">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="4d801-118">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="4d801-119">Abone olunan durumları izleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4d801-119">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d801-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d801-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4d801-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="4d801-121">Element</span></span>|<span data-ttu-id="4d801-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d801-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d801-123">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="4d801-123">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="4d801-124">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleme yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4d801-124">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d801-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d801-125">Remarks</span></span>  
 <span data-ttu-id="4d801-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="4d801-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="4d801-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d801-127">Example</span></span>  
 <span data-ttu-id="4d801-128">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="4d801-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d801-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d801-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4d801-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="4d801-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4d801-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="4d801-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
