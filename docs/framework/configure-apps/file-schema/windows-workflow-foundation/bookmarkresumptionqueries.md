---
title: '&lt;bookmarkResumptionQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: b0ce29213f1f281e8581b90dda17aba1bdc29072
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756247"
---
# <a name="ltbookmarkresumptionqueriesgt"></a><span data-ttu-id="eca67-102">&lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="eca67-102">&lt;bookmarkResumptionQueries&gt;</span></span>
<span data-ttu-id="eca67-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eca67-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="eca67-104">Sorgu yer işareti sürdürme kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="eca67-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="eca67-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="eca67-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="eca67-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eca67-106">\<system.serviceModel></span></span>  
<span data-ttu-id="eca67-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="eca67-107">\<tracking></span></span>  
<span data-ttu-id="eca67-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="eca67-108">\<trackingProfile></span></span>  
<span data-ttu-id="eca67-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="eca67-109">\<workflow></span></span>  
<span data-ttu-id="eca67-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="eca67-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="eca67-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="eca67-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eca67-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eca67-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eca67-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eca67-113">Attributes and Elements</span></span>  
 <span data-ttu-id="eca67-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eca67-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eca67-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eca67-115">Attributes</span></span>  
 <span data-ttu-id="eca67-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="eca67-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eca67-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eca67-117">Child Elements</span></span>  
  
|<span data-ttu-id="eca67-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="eca67-118">Element</span></span>|<span data-ttu-id="eca67-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eca67-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eca67-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="eca67-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="eca67-121">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="eca67-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="eca67-122">Sorgu yer işareti sürdürme kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="eca67-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eca67-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eca67-123">Parent Elements</span></span>  
  
|<span data-ttu-id="eca67-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="eca67-124">Element</span></span>|<span data-ttu-id="eca67-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eca67-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eca67-126">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="eca67-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="eca67-127">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="eca67-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eca67-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eca67-128">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="eca67-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="eca67-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="eca67-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="eca67-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
