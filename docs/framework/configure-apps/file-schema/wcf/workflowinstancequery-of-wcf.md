---
title: <workflowInstanceQuery>WCF
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: 7e15d7654aeafa5fa7b87922283d6520d5493242
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915233"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="ea640-102">\<WCF 'de WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="ea640-102">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="ea640-103">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ea640-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="ea640-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ea640-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ea640-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ea640-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ea640-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="ea640-106">\<tracking></span></span>  
<span data-ttu-id="ea640-107">\<Profiller ></span><span class="sxs-lookup"><span data-stu-id="ea640-107">\<profiles></span></span>  
<span data-ttu-id="ea640-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ea640-108">\<trackingProfile></span></span>  
<span data-ttu-id="ea640-109">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="ea640-109">\<workflow></span></span>  
<span data-ttu-id="ea640-110">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="ea640-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="ea640-111">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="ea640-111">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea640-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea640-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea640-113">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="ea640-113">Attributes and elements</span></span>  

<span data-ttu-id="ea640-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea640-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea640-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ea640-115">Attributes</span></span>  

<span data-ttu-id="ea640-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="ea640-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ea640-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="ea640-117">Child elements</span></span>  
  
|<span data-ttu-id="ea640-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="ea640-118">Element</span></span>|<span data-ttu-id="ea640-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea640-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea640-120">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="ea640-120">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="ea640-121">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ea640-121">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ea640-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="ea640-122">Parent elements</span></span>  
  
|<span data-ttu-id="ea640-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="ea640-123">Element</span></span>|<span data-ttu-id="ea640-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea640-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea640-125">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="ea640-125">\<workflowInstanceQueries></span></span>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="ea640-126">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ea640-126">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea640-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea640-127">Remarks</span></span>  

<span data-ttu-id="ea640-128"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="ea640-128">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="ea640-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea640-129">Example</span></span>  

<span data-ttu-id="ea640-130">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="ea640-130">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="ea640-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea640-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ea640-132">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="ea640-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ea640-133">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="ea640-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
