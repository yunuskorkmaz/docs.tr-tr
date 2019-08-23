---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 0a32e6ee22cdf984e64c1b8fa16836c4c56d0380
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932734"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="f3baa-101">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="f3baa-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="f3baa-102">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f3baa-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="f3baa-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f3baa-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f3baa-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f3baa-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f3baa-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="f3baa-105">\<tracking></span></span>  
<span data-ttu-id="f3baa-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f3baa-106">\<trackingProfile></span></span>  
<span data-ttu-id="f3baa-107">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="f3baa-107">\<workflow></span></span>  
<span data-ttu-id="f3baa-108">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="f3baa-108">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3baa-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3baa-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3baa-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3baa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f3baa-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f3baa-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3baa-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f3baa-112">Attributes</span></span>  
 <span data-ttu-id="f3baa-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="f3baa-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f3baa-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3baa-114">Child Elements</span></span>  
  
|<span data-ttu-id="f3baa-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="f3baa-115">Element</span></span>|<span data-ttu-id="f3baa-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3baa-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3baa-117">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="f3baa-117">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="f3baa-118">İş akışı örneği yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="f3baa-118">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3baa-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3baa-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f3baa-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="f3baa-120">Element</span></span>|<span data-ttu-id="f3baa-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3baa-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3baa-122">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="f3baa-122">\<workflow></span></span>](workflow.md)|<span data-ttu-id="f3baa-123">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="f3baa-123">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3baa-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3baa-124">Remarks</span></span>  
 <span data-ttu-id="f3baa-125"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="f3baa-125">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="f3baa-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3baa-126">Example</span></span>  
 <span data-ttu-id="f3baa-127">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="f3baa-127">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3baa-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3baa-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f3baa-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f3baa-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f3baa-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f3baa-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
