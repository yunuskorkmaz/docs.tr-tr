---
title: '&lt;bookmarkResumptionQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: a5eb00d1e094484e3ec01e0db18719ec50e4b953
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515081"
---
# <a name="ltbookmarkresumptionquerygt"></a><span data-ttu-id="37a18-102">&lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="37a18-102">&lt;bookmarkResumptionQuery&gt;</span></span>
<span data-ttu-id="37a18-103">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="37a18-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="37a18-104">Sorgu için yer imi sürdürme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="37a18-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="37a18-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="37a18-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="37a18-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="37a18-106">\<system.serviceModel></span></span>  
<span data-ttu-id="37a18-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="37a18-107">\<tracking></span></span>  
<span data-ttu-id="37a18-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="37a18-108">\<trackingProfile></span></span>  
<span data-ttu-id="37a18-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="37a18-109">\<workflow></span></span>  
<span data-ttu-id="37a18-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="37a18-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="37a18-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="37a18-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37a18-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37a18-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37a18-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="37a18-113">Attributes and Elements</span></span>  
 <span data-ttu-id="37a18-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="37a18-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37a18-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="37a18-115">Attributes</span></span>  
  
|<span data-ttu-id="37a18-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="37a18-116">Attribute</span></span>|<span data-ttu-id="37a18-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37a18-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37a18-118">name</span><span class="sxs-lookup"><span data-stu-id="37a18-118">name</span></span>|<span data-ttu-id="37a18-119">Abone olmak için yer imi kayıt adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="37a18-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37a18-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="37a18-120">Child Elements</span></span>  
 <span data-ttu-id="37a18-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="37a18-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37a18-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="37a18-122">Parent Elements</span></span>  
  
|<span data-ttu-id="37a18-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="37a18-123">Element</span></span>|<span data-ttu-id="37a18-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37a18-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37a18-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="37a18-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="37a18-126">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="37a18-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37a18-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37a18-127">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="37a18-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="37a18-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="37a18-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="37a18-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
