---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 186990577ec4eedc7cae3710c455816c3162fc94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109415"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="f629e-101">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="f629e-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="f629e-102">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f629e-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="f629e-103">Sorgu için yer imi sürdürme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f629e-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="f629e-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f629e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f629e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f629e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f629e-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="f629e-106">\<tracking></span></span>  
<span data-ttu-id="f629e-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f629e-107">\<trackingProfile></span></span>  
<span data-ttu-id="f629e-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="f629e-108">\<workflow></span></span>  
<span data-ttu-id="f629e-109">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="f629e-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="f629e-110">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="f629e-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f629e-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f629e-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f629e-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f629e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f629e-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f629e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f629e-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f629e-114">Attributes</span></span>  
 <span data-ttu-id="f629e-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="f629e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f629e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f629e-116">Child Elements</span></span>  
  
|<span data-ttu-id="f629e-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="f629e-117">Element</span></span>|<span data-ttu-id="f629e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f629e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f629e-119">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="f629e-119">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="f629e-120">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="f629e-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="f629e-121">Sorgu için yer imi sürdürme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f629e-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f629e-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f629e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f629e-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="f629e-123">Element</span></span>|<span data-ttu-id="f629e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f629e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f629e-125">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="f629e-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f629e-126">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="f629e-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f629e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f629e-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f629e-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f629e-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f629e-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f629e-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
