---
title: WCF &lt;bookmarkResumptionQueries&gt;
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: d2b3365f3793c114003bbd9b9da664448bbac243
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50135109"
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="1683a-102">WCF &lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="1683a-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>

<span data-ttu-id="1683a-103">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1683a-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="1683a-104">Sorgu için yer imi sürdürme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1683a-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="1683a-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1683a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="1683a-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1683a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="1683a-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="1683a-107">\<tracking></span></span>  
<span data-ttu-id="1683a-108">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="1683a-108">\<profiles></span></span>  
<span data-ttu-id="1683a-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="1683a-109">\<trackingProfile></span></span>  
<span data-ttu-id="1683a-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="1683a-110">\<workflow></span></span>  
<span data-ttu-id="1683a-111">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="1683a-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="1683a-112">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="1683a-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1683a-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1683a-113">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="1683a-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="1683a-114">Attributes and elements</span></span>

<span data-ttu-id="1683a-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1683a-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1683a-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1683a-116">Attributes</span></span>

<span data-ttu-id="1683a-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="1683a-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1683a-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="1683a-118">Child elements</span></span>  
  
|<span data-ttu-id="1683a-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="1683a-119">Element</span></span>|<span data-ttu-id="1683a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1683a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1683a-121">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="1683a-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="1683a-122">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="1683a-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="1683a-123">Sorgu için yer imi sürdürme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1683a-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1683a-124">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="1683a-124">Parent elements</span></span>  
  
|<span data-ttu-id="1683a-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="1683a-125">Element</span></span>|<span data-ttu-id="1683a-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1683a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1683a-127">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="1683a-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="1683a-128">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="1683a-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1683a-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1683a-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType> 
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
- [<span data-ttu-id="1683a-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="1683a-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="1683a-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="1683a-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
