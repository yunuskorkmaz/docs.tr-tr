---
title: WCF &lt;bookmarkResumptionQuery&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 124b05d8e1ce9831a1efb3c6e62cc5e9fd3058fc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="73c44-102">WCF &lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="73c44-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="73c44-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73c44-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="73c44-104">Sorgu yer işareti sürdürme kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="73c44-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="73c44-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="73c44-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="73c44-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="73c44-106">\<system.serviceModel></span></span>  
<span data-ttu-id="73c44-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="73c44-107">\<tracking></span></span>  
<span data-ttu-id="73c44-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="73c44-108">\<trackingProfile></span></span>  
<span data-ttu-id="73c44-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="73c44-109">\<workflow></span></span>  
<span data-ttu-id="73c44-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="73c44-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="73c44-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="73c44-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73c44-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73c44-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="73c44-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="73c44-113">Attributes and Elements</span></span>  
 <span data-ttu-id="73c44-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73c44-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73c44-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="73c44-115">Attributes</span></span>  
  
|<span data-ttu-id="73c44-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="73c44-116">Attribute</span></span>|<span data-ttu-id="73c44-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73c44-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73c44-118">name</span><span class="sxs-lookup"><span data-stu-id="73c44-118">name</span></span>|<span data-ttu-id="73c44-119">Abone olunacak yer işareti kaydın adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="73c44-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73c44-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="73c44-120">Child Elements</span></span>  
 <span data-ttu-id="73c44-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="73c44-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73c44-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="73c44-122">Parent Elements</span></span>  
  
|<span data-ttu-id="73c44-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="73c44-123">Element</span></span>|<span data-ttu-id="73c44-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73c44-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73c44-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="73c44-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="73c44-126">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73c44-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73c44-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73c44-127">See Also</span></span>  
 <span data-ttu-id="73c44-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="73c44-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="73c44-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="73c44-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="73c44-130">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="73c44-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="73c44-131">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="73c44-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
