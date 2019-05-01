---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 186990577ec4eedc7cae3710c455816c3162fc94
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790292"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="ca591-101">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="ca591-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="ca591-102">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ca591-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="ca591-103">Sorgu için yer imi sürdürme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ca591-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="ca591-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ca591-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ca591-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ca591-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ca591-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="ca591-106">\<tracking></span></span>  
<span data-ttu-id="ca591-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ca591-107">\<trackingProfile></span></span>  
<span data-ttu-id="ca591-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="ca591-108">\<workflow></span></span>  
<span data-ttu-id="ca591-109">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="ca591-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="ca591-110">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="ca591-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca591-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca591-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca591-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca591-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ca591-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca591-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca591-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ca591-114">Attributes</span></span>  
 <span data-ttu-id="ca591-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="ca591-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ca591-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca591-116">Child Elements</span></span>  
  
|<span data-ttu-id="ca591-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca591-117">Element</span></span>|<span data-ttu-id="ca591-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca591-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca591-119">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="ca591-119">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="ca591-120">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="ca591-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="ca591-121">Sorgu için yer imi sürdürme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ca591-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca591-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca591-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ca591-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca591-123">Element</span></span>|<span data-ttu-id="ca591-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca591-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca591-125">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="ca591-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="ca591-126">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="ca591-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca591-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca591-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ca591-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="ca591-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ca591-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="ca591-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
