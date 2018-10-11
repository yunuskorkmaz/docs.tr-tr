---
title: WCF &lt;workflowInstanceQuery&gt;
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: bb4b3e37bd8e8e4f47fd7a0cd6d493d985c2536e
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087641"
---
# <a name="ltworkflowinstancequerygt-of-wcf"></a><span data-ttu-id="61d8c-102">WCF &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="61d8c-102">&lt;workflowInstanceQuery&gt; of WCF</span></span>
<span data-ttu-id="61d8c-103">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="61d8c-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="61d8c-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="61d8c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="61d8c-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="61d8c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="61d8c-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="61d8c-106">\<tracking></span></span>  
<span data-ttu-id="61d8c-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="61d8c-107">\<trackingProfile></span></span>  
<span data-ttu-id="61d8c-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="61d8c-108">\<workflow></span></span>  
<span data-ttu-id="61d8c-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="61d8c-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="61d8c-110">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="61d8c-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61d8c-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61d8c-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61d8c-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="61d8c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="61d8c-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="61d8c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61d8c-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="61d8c-114">Attributes</span></span>  
 <span data-ttu-id="61d8c-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="61d8c-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="61d8c-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="61d8c-116">Child Elements</span></span>  
  
|<span data-ttu-id="61d8c-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="61d8c-117">Element</span></span>|<span data-ttu-id="61d8c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61d8c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61d8c-119">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="61d8c-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="61d8c-120">Abone olunan durumları izleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="61d8c-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61d8c-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="61d8c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="61d8c-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="61d8c-122">Element</span></span>|<span data-ttu-id="61d8c-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61d8c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61d8c-124">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="61d8c-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="61d8c-125">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleme yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="61d8c-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61d8c-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61d8c-126">Remarks</span></span>  
 <span data-ttu-id="61d8c-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="61d8c-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="61d8c-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="61d8c-128">Example</span></span>  
 <span data-ttu-id="61d8c-129">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="61d8c-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="61d8c-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61d8c-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="61d8c-131">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="61d8c-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="61d8c-132">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="61d8c-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
