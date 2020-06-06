---
title: <workflowInstanceQuery>WCF
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: eaf0cd204265aac7c1421e3de0c33963e6bbb7a1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854732"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="4cfe9-102">\<workflowInstanceQuery>WCF</span><span class="sxs-lookup"><span data-stu-id="4cfe9-102">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="4cfe9-103">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4cfe9-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="4cfe9-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4cfe9-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="4cfe9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cfe9-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4cfe9-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="4cfe9-106">Attributes and elements</span></span>  

<span data-ttu-id="4cfe9-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4cfe9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4cfe9-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4cfe9-108">Attributes</span></span>  

<span data-ttu-id="4cfe9-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="4cfe9-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4cfe9-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="4cfe9-110">Child elements</span></span>  
  
|<span data-ttu-id="4cfe9-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="4cfe9-111">Element</span></span>|<span data-ttu-id="4cfe9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cfe9-112">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="4cfe9-113">İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4cfe9-113">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4cfe9-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="4cfe9-114">Parent elements</span></span>  
  
|<span data-ttu-id="4cfe9-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="4cfe9-115">Element</span></span>|<span data-ttu-id="4cfe9-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cfe9-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQueries>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="4cfe9-117">Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4cfe9-117">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cfe9-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cfe9-118">Remarks</span></span>  

<span data-ttu-id="4cfe9-119"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="4cfe9-119">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="4cfe9-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="4cfe9-120">Example</span></span>  

<span data-ttu-id="4cfe9-121">Aşağıdaki yapılandırma `Started` Bu sorguyu kullanarak örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="4cfe9-121">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="4cfe9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cfe9-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4cfe9-123">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="4cfe9-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4cfe9-124">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="4cfe9-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
