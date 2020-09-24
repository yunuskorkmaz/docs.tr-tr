---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 6d8859db5faf84698b8984341dfff1444e7fc0ed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148563"
---
# \<workflowInstanceQuery>

<span data-ttu-id="de50f-101">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de50f-101">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="de50f-102">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="de50f-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="de50f-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="de50f-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de50f-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="de50f-104">Attributes and Elements</span></span>  

 <span data-ttu-id="de50f-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="de50f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de50f-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="de50f-106">Attributes</span></span>  

 <span data-ttu-id="de50f-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="de50f-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="de50f-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="de50f-108">Child Elements</span></span>  
  
|<span data-ttu-id="de50f-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="de50f-109">Element</span></span>|<span data-ttu-id="de50f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de50f-110">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="de50f-111">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="de50f-111">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de50f-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="de50f-112">Parent Elements</span></span>  
  
|<span data-ttu-id="de50f-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="de50f-113">Element</span></span>|<span data-ttu-id="de50f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de50f-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQueries>](workflowinstancequeries.md)|<span data-ttu-id="de50f-115">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de50f-115">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de50f-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de50f-116">Remarks</span></span>  

 <span data-ttu-id="de50f-117"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="de50f-117">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="de50f-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="de50f-118">Example</span></span>  

 <span data-ttu-id="de50f-119">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="de50f-119">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de50f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de50f-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="de50f-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="de50f-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="de50f-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="de50f-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
