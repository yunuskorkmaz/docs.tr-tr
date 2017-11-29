---
title: WCF &lt;bookmarkResumptionQueries&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7afa80a0abfa29c02cdf2ec6c96d2049f98db436
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="7989b-102">WCF &lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="7989b-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>
<span data-ttu-id="7989b-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7989b-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7989b-104">Sorgu yer işareti sürdürme kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7989b-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="7989b-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7989b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="7989b-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7989b-106">\<system.serviceModel></span></span>  
<span data-ttu-id="7989b-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="7989b-107">\<tracking></span></span>  
<span data-ttu-id="7989b-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="7989b-108">\<trackingProfile></span></span>  
<span data-ttu-id="7989b-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="7989b-109">\<workflow></span></span>  
<span data-ttu-id="7989b-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="7989b-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="7989b-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="7989b-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7989b-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7989b-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7989b-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7989b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7989b-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7989b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7989b-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7989b-115">Attributes</span></span>  
 <span data-ttu-id="7989b-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="7989b-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7989b-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7989b-117">Child Elements</span></span>  
  
|<span data-ttu-id="7989b-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="7989b-118">Element</span></span>|<span data-ttu-id="7989b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7989b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7989b-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="7989b-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="7989b-121">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="7989b-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7989b-122">Sorgu yer işareti sürdürme kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7989b-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7989b-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7989b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7989b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="7989b-124">Element</span></span>|<span data-ttu-id="7989b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7989b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7989b-126">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="7989b-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="7989b-127">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="7989b-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7989b-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7989b-128">See Also</span></span>  
 <span data-ttu-id="7989b-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7989b-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="7989b-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7989b-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="7989b-131">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="7989b-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="7989b-132">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="7989b-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
