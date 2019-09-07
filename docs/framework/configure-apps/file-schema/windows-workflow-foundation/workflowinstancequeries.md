---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 11e301de1ab3dbd4c97f236bfd07c5de4a632272
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398573"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="4ea92-101">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="4ea92-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="4ea92-102">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4ea92-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="4ea92-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4ea92-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4ea92-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4ea92-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4ea92-105">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4ea92-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="4ea92-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="4ea92-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="4ea92-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="4ea92-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="4ea92-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4ea92-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="4ea92-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<WorkflowInstanceQueries >**</span><span class="sxs-lookup"><span data-stu-id="4ea92-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ea92-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ea92-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ea92-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ea92-111">Attributes and Elements</span></span>  

<span data-ttu-id="4ea92-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ea92-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ea92-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4ea92-113">Attributes</span></span>  

<span data-ttu-id="4ea92-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="4ea92-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4ea92-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ea92-115">Child Elements</span></span>  
  
|<span data-ttu-id="4ea92-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ea92-116">Element</span></span>|<span data-ttu-id="4ea92-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ea92-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ea92-118">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="4ea92-118">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="4ea92-119">İş akışı örneği yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="4ea92-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ea92-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ea92-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4ea92-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ea92-121">Element</span></span>|<span data-ttu-id="4ea92-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ea92-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ea92-123">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="4ea92-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="4ea92-124">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="4ea92-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ea92-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ea92-125">Remarks</span></span>  

<span data-ttu-id="4ea92-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="4ea92-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="4ea92-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ea92-127">Example</span></span>  

<span data-ttu-id="4ea92-128">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="4ea92-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ea92-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ea92-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4ea92-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="4ea92-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4ea92-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="4ea92-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
