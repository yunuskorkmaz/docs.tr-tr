---
description: WCF hakkında daha fazla bilgi edinin <workflowInstanceQueries>
title: <workflowInstanceQueries> WCF
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: d4dc4827cba5a1732070b5269350ca3dd9bf2c47
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682338"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="24801-103">\<workflowInstanceQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="24801-103">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="24801-104">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="24801-104">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="24801-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="24801-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="24801-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="24801-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24801-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="24801-107">Attributes and elements</span></span>

<span data-ttu-id="24801-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="24801-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24801-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="24801-109">Attributes</span></span>  

<span data-ttu-id="24801-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="24801-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="24801-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="24801-111">Child elements</span></span>  
  
|<span data-ttu-id="24801-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="24801-112">Element</span></span>|<span data-ttu-id="24801-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24801-113">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="24801-114">İş akışı örneği yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="24801-114">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24801-115">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="24801-115">Parent elements</span></span>  
  
|<span data-ttu-id="24801-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="24801-116">Element</span></span>|<span data-ttu-id="24801-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24801-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="24801-118">[ActivityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="24801-118">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24801-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24801-119">Remarks</span></span>

<span data-ttu-id="24801-120"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="24801-120">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="24801-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="24801-121">Example</span></span>  

<span data-ttu-id="24801-122">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="24801-122">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="24801-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24801-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="24801-124">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="24801-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="24801-125">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="24801-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
