---
description: WCF hakkında daha fazla bilgi edinin <workflowInstanceQuery>
title: <workflowInstanceQuery> WCF
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: 30df1a6b4fc0aeac5b7094f1a1f7d9d02599c94d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682325"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="10153-103">\<workflowInstanceQuery> WCF</span><span class="sxs-lookup"><span data-stu-id="10153-103">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="10153-104">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="10153-104">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="10153-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="10153-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="10153-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="10153-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10153-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="10153-107">Attributes and elements</span></span>  

<span data-ttu-id="10153-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10153-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10153-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10153-109">Attributes</span></span>  

<span data-ttu-id="10153-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="10153-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="10153-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="10153-111">Child elements</span></span>  
  
|<span data-ttu-id="10153-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="10153-112">Element</span></span>|<span data-ttu-id="10153-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10153-113">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="10153-114">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="10153-114">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="10153-115">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="10153-115">Parent elements</span></span>  
  
|<span data-ttu-id="10153-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="10153-116">Element</span></span>|<span data-ttu-id="10153-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10153-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQueries>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="10153-118">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="10153-118">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10153-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10153-119">Remarks</span></span>  

<span data-ttu-id="10153-120"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="10153-120">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="10153-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="10153-121">Example</span></span>  

<span data-ttu-id="10153-122">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="10153-122">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="10153-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10153-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="10153-124">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="10153-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="10153-125">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="10153-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
