---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: f048612673a9b6b69c3cdded6526c76359c444e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945985"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="7d6a9-101">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="7d6a9-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="7d6a9-102">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7d6a9-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7d6a9-103">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7d6a9-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="7d6a9-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7d6a9-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7d6a9-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7d6a9-105">\<system.serviceModel></span></span>  
<span data-ttu-id="7d6a9-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="7d6a9-106">\<tracking></span></span>  
<span data-ttu-id="7d6a9-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7d6a9-107">\<trackingProfile></span></span>  
<span data-ttu-id="7d6a9-108">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="7d6a9-108">\<workflow></span></span>  
<span data-ttu-id="7d6a9-109">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="7d6a9-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="7d6a9-110">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="7d6a9-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d6a9-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d6a9-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d6a9-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d6a9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7d6a9-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d6a9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d6a9-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7d6a9-114">Attributes</span></span>  
 <span data-ttu-id="7d6a9-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="7d6a9-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7d6a9-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d6a9-116">Child Elements</span></span>  
  
|<span data-ttu-id="7d6a9-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d6a9-117">Element</span></span>|<span data-ttu-id="7d6a9-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d6a9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d6a9-119">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="7d6a9-119">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery.md)|<span data-ttu-id="7d6a9-120">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="7d6a9-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7d6a9-121">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7d6a9-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d6a9-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d6a9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7d6a9-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d6a9-123">Element</span></span>|<span data-ttu-id="7d6a9-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d6a9-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d6a9-125">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="7d6a9-125">\<workflow></span></span>](workflow.md)|<span data-ttu-id="7d6a9-126">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="7d6a9-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d6a9-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d6a9-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7d6a9-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="7d6a9-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7d6a9-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="7d6a9-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
