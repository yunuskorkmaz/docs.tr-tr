---
title: WCF &lt;bookmarkResumptionQuery&gt;
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 083b42efdd2b10dad870b6590fc20331a090f8aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="335b0-102">WCF &lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="335b0-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="335b0-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="335b0-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="335b0-104">Sorgu yer işareti sürdürme kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="335b0-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="335b0-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="335b0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="335b0-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="335b0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="335b0-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="335b0-107">\<tracking></span></span>  
<span data-ttu-id="335b0-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="335b0-108">\<trackingProfile></span></span>  
<span data-ttu-id="335b0-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="335b0-109">\<workflow></span></span>  
<span data-ttu-id="335b0-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="335b0-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="335b0-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="335b0-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="335b0-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="335b0-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="335b0-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="335b0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="335b0-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="335b0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="335b0-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="335b0-115">Attributes</span></span>  
  
|<span data-ttu-id="335b0-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="335b0-116">Attribute</span></span>|<span data-ttu-id="335b0-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="335b0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="335b0-118">name</span><span class="sxs-lookup"><span data-stu-id="335b0-118">name</span></span>|<span data-ttu-id="335b0-119">Abone olunacak yer işareti kaydın adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="335b0-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="335b0-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="335b0-120">Child Elements</span></span>  
 <span data-ttu-id="335b0-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="335b0-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="335b0-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="335b0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="335b0-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="335b0-123">Element</span></span>|<span data-ttu-id="335b0-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="335b0-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="335b0-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="335b0-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="335b0-126">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="335b0-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="335b0-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="335b0-127">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="335b0-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="335b0-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="335b0-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="335b0-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
