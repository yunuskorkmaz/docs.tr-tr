---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: 9043deb66e1a4314df97f4da41103e74676a270c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945955"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="431d7-101">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="431d7-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="431d7-102">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="431d7-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="431d7-103">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="431d7-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="431d7-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="431d7-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="431d7-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="431d7-105">\<system.serviceModel></span></span>  
<span data-ttu-id="431d7-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="431d7-106">\<tracking></span></span>  
<span data-ttu-id="431d7-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="431d7-107">\<trackingProfile></span></span>  
<span data-ttu-id="431d7-108">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="431d7-108">\<workflow></span></span>  
<span data-ttu-id="431d7-109">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="431d7-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="431d7-110">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="431d7-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="431d7-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="431d7-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="431d7-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="431d7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="431d7-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="431d7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="431d7-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="431d7-114">Attributes</span></span>  
  
|<span data-ttu-id="431d7-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="431d7-115">Attribute</span></span>|<span data-ttu-id="431d7-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="431d7-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="431d7-117">name</span><span class="sxs-lookup"><span data-stu-id="431d7-117">name</span></span>|<span data-ttu-id="431d7-118">Abone olunacak yer işareti kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="431d7-118">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="431d7-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="431d7-119">Child Elements</span></span>  
 <span data-ttu-id="431d7-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="431d7-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="431d7-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="431d7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="431d7-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="431d7-122">Element</span></span>|<span data-ttu-id="431d7-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="431d7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="431d7-124">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="431d7-124">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="431d7-125">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="431d7-125">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="431d7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="431d7-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="431d7-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="431d7-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="431d7-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="431d7-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
