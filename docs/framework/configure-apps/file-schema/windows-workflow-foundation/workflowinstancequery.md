---
title: '&lt;Workflowınstancequery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: eb8b84f70025df3a8a8ac96f61dec6755eb3a364
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757846"
---
# <a name="ltworkflowinstancequerygt"></a><span data-ttu-id="5f4dc-102">&lt;Workflowınstancequery&gt;</span><span class="sxs-lookup"><span data-stu-id="5f4dc-102">&lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="5f4dc-103">Başlatılan ya da tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5f4dc-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="5f4dc-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5f4dc-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="5f4dc-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5f4dc-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5f4dc-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="5f4dc-106">\<tracking></span></span>  
<span data-ttu-id="5f4dc-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5f4dc-107">\<trackingProfile></span></span>  
<span data-ttu-id="5f4dc-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="5f4dc-108">\<workflow></span></span>  
<span data-ttu-id="5f4dc-109">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="5f4dc-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="5f4dc-110">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="5f4dc-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f4dc-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f4dc-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f4dc-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f4dc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5f4dc-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5f4dc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f4dc-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5f4dc-114">Attributes</span></span>  
 <span data-ttu-id="5f4dc-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="5f4dc-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5f4dc-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f4dc-116">Child Elements</span></span>  
  
|<span data-ttu-id="5f4dc-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="5f4dc-117">Element</span></span>|<span data-ttu-id="5f4dc-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f4dc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f4dc-119">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="5f4dc-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="5f4dc-120">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5f4dc-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f4dc-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f4dc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5f4dc-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="5f4dc-122">Element</span></span>|<span data-ttu-id="5f4dc-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f4dc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f4dc-124">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="5f4dc-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="5f4dc-125">Başlatılan ya da tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izlemek yapılandırma öğelerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5f4dc-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f4dc-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f4dc-126">Remarks</span></span>  
 <span data-ttu-id="5f4dc-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="5f4dc-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="5f4dc-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f4dc-128">Example</span></span>  
 <span data-ttu-id="5f4dc-129">Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="5f4dc-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f4dc-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f4dc-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="5f4dc-131">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="5f4dc-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="5f4dc-132">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="5f4dc-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
