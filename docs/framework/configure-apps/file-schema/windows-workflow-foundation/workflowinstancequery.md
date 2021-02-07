---
description: 'Hakkında daha fazla bilgi edinin: <workflowInstanceQuery>'
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 39949b99e7c6c12ff8618e6aa3a43582d15d4133
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697796"
---
# \<workflowInstanceQuery>

<span data-ttu-id="e22d9-102">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e22d9-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="e22d9-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e22d9-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="e22d9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e22d9-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e22d9-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e22d9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e22d9-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e22d9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e22d9-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e22d9-107">Attributes</span></span>  

 <span data-ttu-id="e22d9-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="e22d9-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e22d9-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e22d9-109">Child Elements</span></span>  
  
|<span data-ttu-id="e22d9-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="e22d9-110">Element</span></span>|<span data-ttu-id="e22d9-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e22d9-111">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="e22d9-112">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e22d9-112">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e22d9-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e22d9-113">Parent Elements</span></span>  
  
|<span data-ttu-id="e22d9-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="e22d9-114">Element</span></span>|<span data-ttu-id="e22d9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e22d9-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQueries>](workflowinstancequeries.md)|<span data-ttu-id="e22d9-116">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e22d9-116">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e22d9-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e22d9-117">Remarks</span></span>  

 <span data-ttu-id="e22d9-118"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="e22d9-118">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="e22d9-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="e22d9-119">Example</span></span>  

 <span data-ttu-id="e22d9-120">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="e22d9-120">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e22d9-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e22d9-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e22d9-122">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="e22d9-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e22d9-123">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="e22d9-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
