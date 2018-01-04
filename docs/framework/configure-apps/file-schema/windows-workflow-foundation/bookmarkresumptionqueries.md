---
title: '&lt;bookmarkResumptionQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fb3cf8457dc19081e9eb51091453764513da8ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionqueriesgt"></a><span data-ttu-id="c42d0-102">&lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="c42d0-102">&lt;bookmarkResumptionQueries&gt;</span></span>
<span data-ttu-id="c42d0-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c42d0-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="c42d0-104">Sorgu yer işareti sürdürme kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c42d0-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="c42d0-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c42d0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c42d0-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c42d0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c42d0-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="c42d0-107">\<tracking></span></span>  
<span data-ttu-id="c42d0-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="c42d0-108">\<trackingProfile></span></span>  
<span data-ttu-id="c42d0-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="c42d0-109">\<workflow></span></span>  
<span data-ttu-id="c42d0-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="c42d0-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="c42d0-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="c42d0-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c42d0-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c42d0-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c42d0-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c42d0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c42d0-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c42d0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c42d0-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c42d0-115">Attributes</span></span>  
 <span data-ttu-id="c42d0-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="c42d0-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c42d0-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c42d0-117">Child Elements</span></span>  
  
|<span data-ttu-id="c42d0-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="c42d0-118">Element</span></span>|<span data-ttu-id="c42d0-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c42d0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c42d0-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="c42d0-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="c42d0-121">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="c42d0-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="c42d0-122">Sorgu yer işareti sürdürme kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c42d0-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c42d0-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c42d0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c42d0-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="c42d0-124">Element</span></span>|<span data-ttu-id="c42d0-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c42d0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c42d0-126">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="c42d0-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c42d0-127">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="c42d0-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c42d0-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c42d0-128">See Also</span></span>  
 <span data-ttu-id="c42d0-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c42d0-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="c42d0-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c42d0-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="c42d0-131">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c42d0-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c42d0-132">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c42d0-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
