---
title: <cancelRequestedQuery> WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: bd6157e63761efa954744ab08ea6c66535def514
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673369"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="b28b5-102">\<cancelRequestedQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="b28b5-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="b28b5-103">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b28b5-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b28b5-104">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b28b5-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="b28b5-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b28b5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="b28b5-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b28b5-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b28b5-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="b28b5-107">\<tracking></span></span>  
<span data-ttu-id="b28b5-108">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="b28b5-108">\<profiles></span></span>  
<span data-ttu-id="b28b5-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b28b5-109">\<trackingProfile></span></span>  
<span data-ttu-id="b28b5-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="b28b5-110">\<workflow></span></span>  
<span data-ttu-id="b28b5-111">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="b28b5-111">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="b28b5-112">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="b28b5-112">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b28b5-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b28b5-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b28b5-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="b28b5-114">Attributes and elements</span></span>

<span data-ttu-id="b28b5-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b28b5-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b28b5-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b28b5-116">Attributes</span></span>  
  
|<span data-ttu-id="b28b5-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b28b5-117">Attribute</span></span>|<span data-ttu-id="b28b5-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b28b5-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="b28b5-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="b28b5-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="b28b5-120">Kendisi için İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="b28b5-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b28b5-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b28b5-121">Child elements</span></span>

<span data-ttu-id="b28b5-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="b28b5-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="b28b5-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="b28b5-123">Parent elements</span></span>
  
|<span data-ttu-id="b28b5-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="b28b5-124">Element</span></span>|<span data-ttu-id="b28b5-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b28b5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b28b5-126">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="b28b5-126">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="b28b5-127">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b28b5-127">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b28b5-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b28b5-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b28b5-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="b28b5-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b28b5-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="b28b5-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
