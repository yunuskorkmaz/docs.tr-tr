---
title: WCF &lt;bookmarkResumptionQuery&gt;
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 07215347da19a05d5915296668d990853fdae646
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087797"
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="20361-102">WCF &lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="20361-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="20361-103">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="20361-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="20361-104">Sorgu için yer imi sürdürme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="20361-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="20361-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="20361-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="20361-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="20361-106">\<system.serviceModel></span></span>  
<span data-ttu-id="20361-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="20361-107">\<tracking></span></span>  
<span data-ttu-id="20361-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="20361-108">\<trackingProfile></span></span>  
<span data-ttu-id="20361-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="20361-109">\<workflow></span></span>  
<span data-ttu-id="20361-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="20361-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="20361-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="20361-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20361-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20361-112">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="20361-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="20361-113">Attributes and Elements</span></span>  
 <span data-ttu-id="20361-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20361-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20361-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="20361-115">Attributes</span></span>  
  
|<span data-ttu-id="20361-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="20361-116">Attribute</span></span>|<span data-ttu-id="20361-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20361-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20361-118">name</span><span class="sxs-lookup"><span data-stu-id="20361-118">name</span></span>|<span data-ttu-id="20361-119">Abone olmak için yer imi kayıt adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="20361-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20361-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="20361-120">Child Elements</span></span>  
 <span data-ttu-id="20361-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="20361-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20361-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="20361-122">Parent Elements</span></span>  
  
|<span data-ttu-id="20361-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="20361-123">Element</span></span>|<span data-ttu-id="20361-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20361-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20361-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="20361-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="20361-126">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="20361-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20361-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20361-127">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="20361-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="20361-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="20361-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="20361-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
