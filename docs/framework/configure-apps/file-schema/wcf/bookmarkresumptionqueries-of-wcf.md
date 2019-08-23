---
title: <bookmarkResumptionQueries>WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 5ec9827e9862866096265da576c91b10573012d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919736"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="a8ba1-102">\<WCF 'nin bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="a8ba1-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="a8ba1-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a8ba1-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="a8ba1-104">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a8ba1-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="a8ba1-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a8ba1-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="a8ba1-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a8ba1-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a8ba1-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="a8ba1-107">\<tracking></span></span>  
<span data-ttu-id="a8ba1-108">\<Profiller ></span><span class="sxs-lookup"><span data-stu-id="a8ba1-108">\<profiles></span></span>  
<span data-ttu-id="a8ba1-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a8ba1-109">\<trackingProfile></span></span>  
<span data-ttu-id="a8ba1-110">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="a8ba1-110">\<workflow></span></span>  
<span data-ttu-id="a8ba1-111">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="a8ba1-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="a8ba1-112">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="a8ba1-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8ba1-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8ba1-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8ba1-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="a8ba1-114">Attributes and elements</span></span>  
  
<span data-ttu-id="a8ba1-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8ba1-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8ba1-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8ba1-116">Attributes</span></span>  
  
<span data-ttu-id="a8ba1-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="a8ba1-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a8ba1-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a8ba1-118">Child elements</span></span>  
  
|<span data-ttu-id="a8ba1-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8ba1-119">Element</span></span>|<span data-ttu-id="a8ba1-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8ba1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8ba1-121">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="a8ba1-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="a8ba1-122">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="a8ba1-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="a8ba1-123">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a8ba1-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8ba1-124">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="a8ba1-124">Parent elements</span></span>  
  
|<span data-ttu-id="a8ba1-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8ba1-125">Element</span></span>|<span data-ttu-id="a8ba1-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8ba1-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8ba1-127">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="a8ba1-127">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="a8ba1-128">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a8ba1-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8ba1-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8ba1-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a8ba1-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a8ba1-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a8ba1-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a8ba1-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
