---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 68e44584858e55c136bc3c3dc5f1fb333485fa17
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397512"
---
# <a name="workflowinstancequery"></a><span data-ttu-id="306bc-101">\<WorkflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="306bc-101">\<workflowInstanceQuery></span></span>
<span data-ttu-id="306bc-102">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="306bc-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="306bc-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="306bc-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="306bc-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="306bc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="306bc-105">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="306bc-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="306bc-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="306bc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="306bc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="306bc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="306bc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="306bc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="306bc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WorkflowInstanceQueries >** ](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="306bc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="306bc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<WorkflowInstanceQuery >**</span><span class="sxs-lookup"><span data-stu-id="306bc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="306bc-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="306bc-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="306bc-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="306bc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="306bc-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="306bc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="306bc-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="306bc-114">Attributes</span></span>  
 <span data-ttu-id="306bc-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="306bc-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="306bc-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="306bc-116">Child Elements</span></span>  
  
|<span data-ttu-id="306bc-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="306bc-117">Element</span></span>|<span data-ttu-id="306bc-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="306bc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="306bc-119">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="306bc-119">\<states></span></span>](states.md)|<span data-ttu-id="306bc-120">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="306bc-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="306bc-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="306bc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="306bc-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="306bc-122">Element</span></span>|<span data-ttu-id="306bc-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="306bc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="306bc-124">\<WorkflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="306bc-124">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="306bc-125">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="306bc-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="306bc-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="306bc-126">Remarks</span></span>  
 <span data-ttu-id="306bc-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="306bc-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="306bc-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="306bc-128">Example</span></span>  
 <span data-ttu-id="306bc-129">Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="306bc-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="306bc-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="306bc-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="306bc-131">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="306bc-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="306bc-132">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="306bc-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
