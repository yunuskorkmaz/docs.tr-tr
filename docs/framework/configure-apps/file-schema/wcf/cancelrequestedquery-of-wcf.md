---
description: WCF hakkında daha fazla bilgi edinin <cancelRequestedQuery>
title: <cancelRequestedQuery> WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: e477e33650eb901cf2e9275570d8538196c52b6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639178"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="d901e-103">\<cancelRequestedQuery> WCF</span><span class="sxs-lookup"><span data-stu-id="d901e-103">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="d901e-104">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d901e-104">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d901e-105">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d901e-105">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="d901e-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d901e-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  

## <a name="syntax"></a><span data-ttu-id="d901e-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d901e-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d901e-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="d901e-108">Attributes and elements</span></span>

<span data-ttu-id="d901e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d901e-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d901e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d901e-110">Attributes</span></span>  
  
|<span data-ttu-id="d901e-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d901e-111">Attribute</span></span>|<span data-ttu-id="d901e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d901e-112">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="d901e-113">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d901e-113">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="d901e-114">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d901e-114">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d901e-115">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d901e-115">Child elements</span></span>

<span data-ttu-id="d901e-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="d901e-116">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="d901e-117">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="d901e-117">Parent elements</span></span>
  
|<span data-ttu-id="d901e-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="d901e-118">Element</span></span>|<span data-ttu-id="d901e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d901e-119">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQueries>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="d901e-120">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d901e-120">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d901e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d901e-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d901e-122">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="d901e-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d901e-123">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="d901e-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
