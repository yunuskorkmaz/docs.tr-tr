---
title: WCF &lt;bookmarkResumptionQueries&gt;
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 8a83f521e444838b6495221c00211710dd99ab6b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753046"
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="103ef-102">WCF &lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="103ef-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>
<span data-ttu-id="103ef-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="103ef-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="103ef-104">Sorgu yer işareti sürdürme kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="103ef-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="103ef-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="103ef-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="103ef-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="103ef-106">\<system.serviceModel></span></span>  
<span data-ttu-id="103ef-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="103ef-107">\<tracking></span></span>  
<span data-ttu-id="103ef-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="103ef-108">\<trackingProfile></span></span>  
<span data-ttu-id="103ef-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="103ef-109">\<workflow></span></span>  
<span data-ttu-id="103ef-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="103ef-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="103ef-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="103ef-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="103ef-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="103ef-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="103ef-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="103ef-113">Attributes and Elements</span></span>  
 <span data-ttu-id="103ef-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="103ef-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="103ef-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="103ef-115">Attributes</span></span>  
 <span data-ttu-id="103ef-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="103ef-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="103ef-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="103ef-117">Child Elements</span></span>  
  
|<span data-ttu-id="103ef-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="103ef-118">Element</span></span>|<span data-ttu-id="103ef-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="103ef-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="103ef-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="103ef-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="103ef-121">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="103ef-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="103ef-122">Sorgu yer işareti sürdürme kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="103ef-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="103ef-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="103ef-123">Parent Elements</span></span>  
  
|<span data-ttu-id="103ef-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="103ef-124">Element</span></span>|<span data-ttu-id="103ef-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="103ef-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="103ef-126">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="103ef-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="103ef-127">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="103ef-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="103ef-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="103ef-128">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="103ef-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="103ef-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="103ef-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="103ef-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
