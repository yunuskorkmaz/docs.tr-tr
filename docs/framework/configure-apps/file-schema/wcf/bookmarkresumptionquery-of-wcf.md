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
ms.workload: dotnet
ms.openlocfilehash: 3240fcf026869aee7540c0e792ccd81e2592e620
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="a3a0f-102">WCF &lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="a3a0f-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="a3a0f-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a3a0f-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="a3a0f-104">Sorgu yer işareti sürdürme kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a3a0f-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="a3a0f-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a3a0f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="a3a0f-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a3a0f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a3a0f-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="a3a0f-107">\<tracking></span></span>  
<span data-ttu-id="a3a0f-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="a3a0f-108">\<trackingProfile></span></span>  
<span data-ttu-id="a3a0f-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="a3a0f-109">\<workflow></span></span>  
<span data-ttu-id="a3a0f-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="a3a0f-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="a3a0f-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="a3a0f-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3a0f-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3a0f-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a3a0f-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3a0f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a3a0f-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a3a0f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3a0f-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a3a0f-115">Attributes</span></span>  
  
|<span data-ttu-id="a3a0f-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a3a0f-116">Attribute</span></span>|<span data-ttu-id="a3a0f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3a0f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3a0f-118">name</span><span class="sxs-lookup"><span data-stu-id="a3a0f-118">name</span></span>|<span data-ttu-id="a3a0f-119">Abone olunacak yer işareti kaydın adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="a3a0f-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3a0f-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3a0f-120">Child Elements</span></span>  
 <span data-ttu-id="a3a0f-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="a3a0f-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3a0f-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3a0f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a3a0f-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="a3a0f-123">Element</span></span>|<span data-ttu-id="a3a0f-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3a0f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3a0f-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="a3a0f-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="a3a0f-126">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a3a0f-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3a0f-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a3a0f-127">See Also</span></span>  
 <span data-ttu-id="a3a0f-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a3a0f-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="a3a0f-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a3a0f-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="a3a0f-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a3a0f-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a3a0f-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a3a0f-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
