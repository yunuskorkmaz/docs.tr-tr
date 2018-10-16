---
title: WCF &lt;cancelRequestedQuery&gt;
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 3943d604b586eec37a1d153f10ac049fc9bd5747
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347576"
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="9685c-102">WCF &lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="9685c-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>

<span data-ttu-id="9685c-103">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9685c-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="9685c-104">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9685c-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="9685c-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9685c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="9685c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9685c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="9685c-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="9685c-107">\<tracking></span></span>  
<span data-ttu-id="9685c-108">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="9685c-108">\<profiles></span></span>  
<span data-ttu-id="9685c-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9685c-109">\<trackingProfile></span></span>  
<span data-ttu-id="9685c-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="9685c-110">\<workflow></span></span>  
<span data-ttu-id="9685c-111">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="9685c-111">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="9685c-112">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="9685c-112">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9685c-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9685c-113">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                              childActivityName="String"/>
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9685c-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="9685c-114">Attributes and elements</span></span>

<span data-ttu-id="9685c-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9685c-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9685c-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9685c-116">Attributes</span></span>  
  
|<span data-ttu-id="9685c-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9685c-117">Attribute</span></span>|<span data-ttu-id="9685c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9685c-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="9685c-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="9685c-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="9685c-120">Kendisi için İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="9685c-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9685c-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="9685c-121">Child elements</span></span>

<span data-ttu-id="9685c-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="9685c-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="9685c-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="9685c-123">Parent elements</span></span>
  
|<span data-ttu-id="9685c-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="9685c-124">Element</span></span>|<span data-ttu-id="9685c-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9685c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9685c-126">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="9685c-126">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="9685c-127">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9685c-127">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9685c-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9685c-128">See also</span></span>  

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9685c-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="9685c-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9685c-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="9685c-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
