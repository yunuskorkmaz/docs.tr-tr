---
title: '&lt;bookmarkResumptionQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: ae6a81123379ecd0e7fdc72f4e115a462f81eb90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555043"
---
# <a name="ltbookmarkresumptionqueriesgt"></a><span data-ttu-id="3e98a-102">&lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="3e98a-102">&lt;bookmarkResumptionQueries&gt;</span></span>
<span data-ttu-id="3e98a-103">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3e98a-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="3e98a-104">Sorgu için yer imi sürdürme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3e98a-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="3e98a-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3e98a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="3e98a-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3e98a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="3e98a-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="3e98a-107">\<tracking></span></span>  
<span data-ttu-id="3e98a-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3e98a-108">\<trackingProfile></span></span>  
<span data-ttu-id="3e98a-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="3e98a-109">\<workflow></span></span>  
<span data-ttu-id="3e98a-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="3e98a-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="3e98a-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="3e98a-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e98a-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e98a-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e98a-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e98a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="3e98a-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e98a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e98a-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e98a-115">Attributes</span></span>  
 <span data-ttu-id="3e98a-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="3e98a-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3e98a-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e98a-117">Child Elements</span></span>  
  
|<span data-ttu-id="3e98a-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e98a-118">Element</span></span>|<span data-ttu-id="3e98a-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e98a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e98a-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="3e98a-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="3e98a-121">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="3e98a-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="3e98a-122">Sorgu için yer imi sürdürme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3e98a-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e98a-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e98a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3e98a-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e98a-124">Element</span></span>|<span data-ttu-id="3e98a-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e98a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e98a-126">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="3e98a-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="3e98a-127">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="3e98a-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e98a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e98a-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3e98a-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="3e98a-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3e98a-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="3e98a-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
