---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: e54f98c980f60d02377e38d53d9d0eb48581eec0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61613322"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="1689a-101">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="1689a-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="1689a-102">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleme yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1689a-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="1689a-103">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1689a-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="1689a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1689a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1689a-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="1689a-105">\<tracking></span></span>  
<span data-ttu-id="1689a-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="1689a-106">\<trackingProfile></span></span>  
<span data-ttu-id="1689a-107">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="1689a-107">\<workflow></span></span>  
<span data-ttu-id="1689a-108">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="1689a-108">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1689a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1689a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1689a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1689a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1689a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1689a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1689a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1689a-112">Attributes</span></span>  
 <span data-ttu-id="1689a-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="1689a-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1689a-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1689a-114">Child Elements</span></span>  
  
|<span data-ttu-id="1689a-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="1689a-115">Element</span></span>|<span data-ttu-id="1689a-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1689a-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1689a-117">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="1689a-117">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="1689a-118">İş akışı örneği yaşam döngüsü değişiklikleri izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="1689a-118">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1689a-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1689a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1689a-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="1689a-120">Element</span></span>|<span data-ttu-id="1689a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1689a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1689a-122">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="1689a-122">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="1689a-123">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="1689a-123">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1689a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1689a-124">Remarks</span></span>  
 <span data-ttu-id="1689a-125"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="1689a-125">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="1689a-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="1689a-126">Example</span></span>  
 <span data-ttu-id="1689a-127">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="1689a-127">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1689a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1689a-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1689a-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="1689a-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1689a-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="1689a-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
