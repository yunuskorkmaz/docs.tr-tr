---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: 7fb298bcbc5b4bf5d699d3c79936ca3c15f67c0e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268190"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="3c975-101">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="3c975-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="3c975-102">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3c975-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="3c975-103">Sorgu için yer imi sürdürme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3c975-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="3c975-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3c975-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="3c975-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3c975-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3c975-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="3c975-106">\<tracking></span></span>  
<span data-ttu-id="3c975-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3c975-107">\<trackingProfile></span></span>  
<span data-ttu-id="3c975-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="3c975-108">\<workflow></span></span>  
<span data-ttu-id="3c975-109">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="3c975-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="3c975-110">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="3c975-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c975-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c975-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c975-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c975-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3c975-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3c975-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c975-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3c975-114">Attributes</span></span>  
  
|<span data-ttu-id="3c975-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3c975-115">Attribute</span></span>|<span data-ttu-id="3c975-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c975-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c975-117">name</span><span class="sxs-lookup"><span data-stu-id="3c975-117">name</span></span>|<span data-ttu-id="3c975-118">Abone olmak için yer imi kayıt adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="3c975-118">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c975-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c975-119">Child Elements</span></span>  
 <span data-ttu-id="3c975-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="3c975-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c975-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c975-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3c975-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="3c975-122">Element</span></span>|<span data-ttu-id="3c975-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c975-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c975-124">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="3c975-124">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="3c975-125">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3c975-125">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c975-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c975-126">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3c975-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="3c975-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3c975-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="3c975-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
