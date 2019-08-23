---
title: <cancelRequestedQuery>WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 7952520edbf799e5fab6864e50962c6ec2860928
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919642"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="5fa79-102">\<WCF için cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="5fa79-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="5fa79-103">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5fa79-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5fa79-104">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5fa79-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="5fa79-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5fa79-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="5fa79-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5fa79-106">\<system.serviceModel></span></span>  
<span data-ttu-id="5fa79-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="5fa79-107">\<tracking></span></span>  
<span data-ttu-id="5fa79-108">\<Profiller ></span><span class="sxs-lookup"><span data-stu-id="5fa79-108">\<profiles></span></span>  
<span data-ttu-id="5fa79-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5fa79-109">\<trackingProfile></span></span>  
<span data-ttu-id="5fa79-110">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="5fa79-110">\<workflow></span></span>  
<span data-ttu-id="5fa79-111">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="5fa79-111">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="5fa79-112">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="5fa79-112">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fa79-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fa79-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fa79-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="5fa79-114">Attributes and elements</span></span>

<span data-ttu-id="5fa79-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5fa79-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5fa79-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5fa79-116">Attributes</span></span>  
  
|<span data-ttu-id="5fa79-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5fa79-117">Attribute</span></span>|<span data-ttu-id="5fa79-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fa79-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="5fa79-119">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5fa79-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="5fa79-120">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5fa79-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fa79-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="5fa79-121">Child elements</span></span>

<span data-ttu-id="5fa79-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="5fa79-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="5fa79-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="5fa79-123">Parent elements</span></span>
  
|<span data-ttu-id="5fa79-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="5fa79-124">Element</span></span>|<span data-ttu-id="5fa79-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fa79-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fa79-126">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="5fa79-126">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="5fa79-127">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5fa79-127">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fa79-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fa79-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5fa79-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="5fa79-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5fa79-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="5fa79-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
