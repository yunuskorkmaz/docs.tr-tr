---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 1b1315aa176f26c356726c5edf1c851bb4c63a47
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148614"
---
# \<workflowInstanceQueries>

<span data-ttu-id="169b8-101">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="169b8-101">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="169b8-102">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="169b8-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="169b8-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="169b8-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="169b8-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="169b8-104">Attributes and Elements</span></span>  

<span data-ttu-id="169b8-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="169b8-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="169b8-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="169b8-106">Attributes</span></span>  

<span data-ttu-id="169b8-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="169b8-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="169b8-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="169b8-108">Child Elements</span></span>  
  
|<span data-ttu-id="169b8-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="169b8-109">Element</span></span>|<span data-ttu-id="169b8-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="169b8-110">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="169b8-111">İş akışı örneği yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="169b8-111">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="169b8-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="169b8-112">Parent Elements</span></span>  
  
|<span data-ttu-id="169b8-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="169b8-113">Element</span></span>|<span data-ttu-id="169b8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="169b8-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="169b8-115">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="169b8-115">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="169b8-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="169b8-116">Remarks</span></span>  

<span data-ttu-id="169b8-117"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="169b8-117">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="169b8-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="169b8-118">Example</span></span>  

<span data-ttu-id="169b8-119">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="169b8-119">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="169b8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="169b8-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="169b8-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="169b8-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="169b8-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="169b8-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
