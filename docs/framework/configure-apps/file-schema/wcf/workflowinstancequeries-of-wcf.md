---
title: WCF &lt;workflowInstanceQueries&gt;
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 300637031c64f7c9e072f04835fc3590348ddc9e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192700"
---
# <a name="ltworkflowinstancequeriesgt-of-wcf"></a><span data-ttu-id="7d9c4-102">WCF &lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="7d9c4-102">&lt;workflowInstanceQueries&gt; of WCF</span></span>

<span data-ttu-id="7d9c4-103">Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleme yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7d9c4-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="7d9c4-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7d9c4-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7d9c4-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7d9c4-105">\<system.serviceModel></span></span>  
<span data-ttu-id="7d9c4-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="7d9c4-106">\<tracking></span></span>  
<span data-ttu-id="7d9c4-107">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="7d9c4-107">\<profiles></span></span>  
<span data-ttu-id="7d9c4-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7d9c4-108">\<trackingProfile></span></span>  
<span data-ttu-id="7d9c4-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="7d9c4-109">\<workflow></span></span>  
<span data-ttu-id="7d9c4-110">\<Workflowınstancequeries ></span><span class="sxs-lookup"><span data-stu-id="7d9c4-110">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d9c4-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d9c4-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d9c4-112">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="7d9c4-112">Attributes and elements</span></span>

<span data-ttu-id="7d9c4-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d9c4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d9c4-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7d9c4-114">Attributes</span></span>  

<span data-ttu-id="7d9c4-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="7d9c4-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7d9c4-116">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="7d9c4-116">Child elements</span></span>  
  
|<span data-ttu-id="7d9c4-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d9c4-117">Element</span></span>|<span data-ttu-id="7d9c4-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d9c4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d9c4-119">\<Workflowınstancequery ></span><span class="sxs-lookup"><span data-stu-id="7d9c4-119">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="7d9c4-120">İş akışı örneği yaşam döngüsü değişiklikleri izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="7d9c4-120">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d9c4-121">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="7d9c4-121">Parent elements</span></span>  
  
|<span data-ttu-id="7d9c4-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d9c4-122">Element</span></span>|<span data-ttu-id="7d9c4-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d9c4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d9c4-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="7d9c4-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="7d9c4-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi [activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) özelliği.</span><span class="sxs-lookup"><span data-stu-id="7d9c4-125">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d9c4-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d9c4-126">Remarks</span></span>

<span data-ttu-id="7d9c4-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="7d9c4-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="7d9c4-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d9c4-128">Example</span></span>  

<span data-ttu-id="7d9c4-129">İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.</span><span class="sxs-lookup"><span data-stu-id="7d9c4-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>  
    <states>  
      <state name="Started"/>  
    </states>  
  </workflowInstanceQuery>  
</workflowInstanceQueries>
```
  
## <a name="see-also"></a><span data-ttu-id="7d9c4-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d9c4-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7d9c4-131">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="7d9c4-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7d9c4-132">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="7d9c4-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
