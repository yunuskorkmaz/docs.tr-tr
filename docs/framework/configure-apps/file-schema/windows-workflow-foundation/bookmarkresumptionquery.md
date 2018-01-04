---
title: '&lt;bookmarkResumptionQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 821ded03ced33ee44c6588daefaf9049741abf8c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionquerygt"></a><span data-ttu-id="485de-102">&lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="485de-102">&lt;bookmarkResumptionQuery&gt;</span></span>
<span data-ttu-id="485de-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="485de-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="485de-104">Sorgu yer işareti sürdürme kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="485de-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="485de-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="485de-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="485de-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="485de-106">\<system.serviceModel></span></span>  
<span data-ttu-id="485de-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="485de-107">\<tracking></span></span>  
<span data-ttu-id="485de-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="485de-108">\<trackingProfile></span></span>  
<span data-ttu-id="485de-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="485de-109">\<workflow></span></span>  
<span data-ttu-id="485de-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="485de-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="485de-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="485de-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="485de-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="485de-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="485de-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="485de-113">Attributes and Elements</span></span>  
 <span data-ttu-id="485de-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="485de-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="485de-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="485de-115">Attributes</span></span>  
  
|<span data-ttu-id="485de-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="485de-116">Attribute</span></span>|<span data-ttu-id="485de-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="485de-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="485de-118">name</span><span class="sxs-lookup"><span data-stu-id="485de-118">name</span></span>|<span data-ttu-id="485de-119">Abone olunacak yer işareti kaydın adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="485de-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="485de-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="485de-120">Child Elements</span></span>  
 <span data-ttu-id="485de-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="485de-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="485de-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="485de-122">Parent Elements</span></span>  
  
|<span data-ttu-id="485de-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="485de-123">Element</span></span>|<span data-ttu-id="485de-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="485de-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="485de-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="485de-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="485de-126">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="485de-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="485de-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="485de-127">See Also</span></span>  
 <span data-ttu-id="485de-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="485de-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="485de-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="485de-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="485de-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="485de-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="485de-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="485de-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
