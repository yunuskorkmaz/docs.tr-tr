---
title: <bookmarkResumptionQuery>WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: ee8457645a0b54e21ef27c2891ebea97d6cc547b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926352"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="1bc1c-102">\<WCF 'nin bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="1bc1c-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="1bc1c-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1bc1c-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="1bc1c-104">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1bc1c-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="1bc1c-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1bc1c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="1bc1c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1bc1c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="1bc1c-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="1bc1c-107">\<tracking></span></span>  
<span data-ttu-id="1bc1c-108">\<Profiller ></span><span class="sxs-lookup"><span data-stu-id="1bc1c-108">\<profiles></span></span>  
<span data-ttu-id="1bc1c-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="1bc1c-109">\<trackingProfile></span></span>  
<span data-ttu-id="1bc1c-110">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="1bc1c-110">\<workflow></span></span>  
<span data-ttu-id="1bc1c-111">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="1bc1c-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="1bc1c-112">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="1bc1c-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bc1c-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1bc1c-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1bc1c-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="1bc1c-114">Attributes and elements</span></span>

<span data-ttu-id="1bc1c-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1bc1c-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1bc1c-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1bc1c-116">Attributes</span></span>  
  
|<span data-ttu-id="1bc1c-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1bc1c-117">Attribute</span></span>|<span data-ttu-id="1bc1c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bc1c-118">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="1bc1c-119">Abone olunacak yer işareti kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="1bc1c-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1bc1c-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="1bc1c-120">Child elements</span></span>

<span data-ttu-id="1bc1c-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="1bc1c-121">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="1bc1c-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="1bc1c-122">Parent elements</span></span>  
  
|<span data-ttu-id="1bc1c-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="1bc1c-123">Element</span></span>|<span data-ttu-id="1bc1c-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bc1c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1bc1c-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="1bc1c-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="1bc1c-126">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1bc1c-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1bc1c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bc1c-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1bc1c-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="1bc1c-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1bc1c-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="1bc1c-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
