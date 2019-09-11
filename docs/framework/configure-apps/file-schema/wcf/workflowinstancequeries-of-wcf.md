---
title: <workflowInstanceQueries>WCF
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 8a58767745efab67fb7550de8770fec2c6226117
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854777"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="0c0bf-102">\<WCF > WorkflowInstanceQueries</span><span class="sxs-lookup"><span data-stu-id="0c0bf-102">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="0c0bf-103">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0c0bf-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="0c0bf-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="0c0bf-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="0c0bf-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0c0bf-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0c0bf-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0c0bf-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0c0bf-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0c0bf-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="0c0bf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="0c0bf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="0c0bf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0c0bf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="0c0bf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0c0bf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="0c0bf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<WorkflowInstanceQueries >**</span><span class="sxs-lookup"><span data-stu-id="0c0bf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c0bf-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c0bf-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c0bf-113">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="0c0bf-113">Attributes and elements</span></span>

<span data-ttu-id="0c0bf-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0c0bf-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c0bf-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0c0bf-115">Attributes</span></span>  

<span data-ttu-id="0c0bf-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="0c0bf-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0c0bf-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="0c0bf-117">Child elements</span></span>  
  
|<span data-ttu-id="0c0bf-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c0bf-118">Element</span></span>|<span data-ttu-id="0c0bf-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c0bf-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c0bf-120">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="0c0bf-120">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="0c0bf-121">İş akışı örneği yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="0c0bf-121">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c0bf-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="0c0bf-122">Parent elements</span></span>  
  
|<span data-ttu-id="0c0bf-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c0bf-123">Element</span></span>|<span data-ttu-id="0c0bf-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c0bf-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c0bf-125">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="0c0bf-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="0c0bf-126">[ActivityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="0c0bf-126">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c0bf-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c0bf-127">Remarks</span></span>

<span data-ttu-id="0c0bf-128"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="0c0bf-128">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="0c0bf-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c0bf-129">Example</span></span>  

<span data-ttu-id="0c0bf-130">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="0c0bf-130">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="0c0bf-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c0bf-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0c0bf-132">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="0c0bf-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0c0bf-133">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="0c0bf-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
