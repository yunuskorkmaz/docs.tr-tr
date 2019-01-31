---
title: <workflowInstanceQuery> WCF
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: 726d4db3bad9f57663790e2bb4e081faba28f1ef
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278778"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="9f639-102">\<Workflowınstancequery > WCF</span><span class="sxs-lookup"><span data-stu-id="9f639-102">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="9f639-103">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9f639-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="9f639-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9f639-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="9f639-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9f639-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9f639-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="9f639-106">\<tracking></span></span>  
<span data-ttu-id="9f639-107">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="9f639-107">\<profiles></span></span>  
<span data-ttu-id="9f639-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9f639-108">\<trackingProfile></span></span>  
<span data-ttu-id="9f639-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="9f639-109">\<workflow></span></span>  
<span data-ttu-id="9f639-110">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="9f639-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="9f639-111">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="9f639-111">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f639-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f639-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f639-113">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="9f639-113">Attributes and elements</span></span>  

<span data-ttu-id="9f639-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9f639-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f639-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9f639-115">Attributes</span></span>  

<span data-ttu-id="9f639-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="9f639-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9f639-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="9f639-117">Child elements</span></span>  
  
|<span data-ttu-id="9f639-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f639-118">Element</span></span>|<span data-ttu-id="9f639-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f639-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f639-120">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="9f639-120">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="9f639-121">Abone olunan durumları izleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9f639-121">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f639-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="9f639-122">Parent elements</span></span>  
  
|<span data-ttu-id="9f639-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f639-123">Element</span></span>|<span data-ttu-id="9f639-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f639-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f639-125">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="9f639-125">\<workflowInstanceQueries></span></span>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="9f639-126">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleme yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9f639-126">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f639-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f639-127">Remarks</span></span>  

<span data-ttu-id="9f639-128"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="9f639-128">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="9f639-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f639-129">Example</span></span>  

<span data-ttu-id="9f639-130">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="9f639-130">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="9f639-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f639-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9f639-132">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="9f639-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9f639-133">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="9f639-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
