---
title: WCF &lt;workflowInstanceQuery&gt;
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: 447564e46e5e74432802341d9f63adbb72667ab4
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123312"
---
# <a name="ltworkflowinstancequerygt-of-wcf"></a><span data-ttu-id="f2742-102">WCF &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="f2742-102">&lt;workflowInstanceQuery&gt; of WCF</span></span>

<span data-ttu-id="f2742-103">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2742-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="f2742-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f2742-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f2742-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f2742-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f2742-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="f2742-106">\<tracking></span></span>  
<span data-ttu-id="f2742-107">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="f2742-107">\<profiles></span></span>  
<span data-ttu-id="f2742-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f2742-108">\<trackingProfile></span></span>  
<span data-ttu-id="f2742-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="f2742-109">\<workflow></span></span>  
<span data-ttu-id="f2742-110">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="f2742-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="f2742-111">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="f2742-111">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2742-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2742-112">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
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
  </profiles>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2742-113">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="f2742-113">Attributes and elements</span></span>  

<span data-ttu-id="f2742-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2742-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2742-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2742-115">Attributes</span></span>  

<span data-ttu-id="f2742-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="f2742-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f2742-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="f2742-117">Child elements</span></span>  
  
|<span data-ttu-id="f2742-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2742-118">Element</span></span>|<span data-ttu-id="f2742-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2742-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2742-120">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="f2742-120">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="f2742-121">Abone olunan durumları izleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f2742-121">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2742-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="f2742-122">Parent elements</span></span>  
  
|<span data-ttu-id="f2742-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2742-123">Element</span></span>|<span data-ttu-id="f2742-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2742-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2742-125">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="f2742-125">\<workflowInstanceQueries></span></span>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="f2742-126">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleme yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2742-126">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2742-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2742-127">Remarks</span></span>  

<span data-ttu-id="f2742-128"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="f2742-128">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="f2742-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="f2742-129">Example</span></span>  

<span data-ttu-id="f2742-130">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="f2742-130">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2742-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2742-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f2742-132">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f2742-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f2742-133">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f2742-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
