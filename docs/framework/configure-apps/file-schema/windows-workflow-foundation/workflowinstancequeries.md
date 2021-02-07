---
description: 'Hakkında daha fazla bilgi edinin: <workflowInstanceQueries>'
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 7672bcd574c15f130b8553881e53994afe9cda93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697848"
---
# \<workflowInstanceQueries>

<span data-ttu-id="381ea-102">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="381ea-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="381ea-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="381ea-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="381ea-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="381ea-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="381ea-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="381ea-105">Attributes and Elements</span></span>  

<span data-ttu-id="381ea-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="381ea-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="381ea-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="381ea-107">Attributes</span></span>  

<span data-ttu-id="381ea-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="381ea-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="381ea-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="381ea-109">Child Elements</span></span>  
  
|<span data-ttu-id="381ea-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="381ea-110">Element</span></span>|<span data-ttu-id="381ea-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="381ea-111">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="381ea-112">İş akışı örneği yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="381ea-112">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="381ea-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="381ea-113">Parent Elements</span></span>  
  
|<span data-ttu-id="381ea-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="381ea-114">Element</span></span>|<span data-ttu-id="381ea-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="381ea-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="381ea-116">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="381ea-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="381ea-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="381ea-117">Remarks</span></span>  

<span data-ttu-id="381ea-118"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="381ea-118">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="381ea-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="381ea-119">Example</span></span>  

<span data-ttu-id="381ea-120">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="381ea-120">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="381ea-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="381ea-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="381ea-122">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="381ea-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="381ea-123">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="381ea-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
