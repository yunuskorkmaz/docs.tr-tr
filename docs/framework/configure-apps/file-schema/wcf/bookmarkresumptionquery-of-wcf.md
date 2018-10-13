---
title: WCF &lt;bookmarkResumptionQuery&gt;
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: f0721e7e14d543b1ff212fe59ed6a2de0a8a9968
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308446"
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="c42b9-102">WCF &lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="c42b9-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>

<span data-ttu-id="c42b9-103">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c42b9-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="c42b9-104">Sorgu için yer imi sürdürme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c42b9-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="c42b9-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c42b9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="c42b9-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c42b9-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c42b9-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="c42b9-107">\<tracking></span></span>  
<span data-ttu-id="c42b9-108">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="c42b9-108">\<profiles></span></span>  
<span data-ttu-id="c42b9-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c42b9-109">\<trackingProfile></span></span>  
<span data-ttu-id="c42b9-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="c42b9-110">\<workflow></span></span>  
<span data-ttu-id="c42b9-111">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="c42b9-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="c42b9-112">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="c42b9-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c42b9-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c42b9-113">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="c42b9-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="c42b9-114">Attributes and elements</span></span>

<span data-ttu-id="c42b9-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c42b9-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c42b9-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c42b9-116">Attributes</span></span>  
  
|<span data-ttu-id="c42b9-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c42b9-117">Attribute</span></span>|<span data-ttu-id="c42b9-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c42b9-118">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="c42b9-119">Abone olmak için yer imi kayıt adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="c42b9-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c42b9-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c42b9-120">Child elements</span></span>

<span data-ttu-id="c42b9-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="c42b9-121">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="c42b9-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="c42b9-122">Parent elements</span></span>  
  
|<span data-ttu-id="c42b9-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="c42b9-123">Element</span></span>|<span data-ttu-id="c42b9-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c42b9-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c42b9-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="c42b9-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="c42b9-126">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c42b9-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c42b9-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c42b9-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c42b9-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c42b9-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c42b9-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c42b9-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
