---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 563e0cbd3f50887e1c9e3d47a3c9502acc13b2c9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398861"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="73b9d-101">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="73b9d-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="73b9d-102">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73b9d-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="73b9d-103">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="73b9d-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="73b9d-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="73b9d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="73b9d-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="73b9d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="73b9d-106">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="73b9d-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="73b9d-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="73b9d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="73b9d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="73b9d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="73b9d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="73b9d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="73b9d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQueries >**</span><span class="sxs-lookup"><span data-stu-id="73b9d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="73b9d-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73b9d-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73b9d-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="73b9d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="73b9d-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73b9d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73b9d-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="73b9d-114">Attributes</span></span>  
 <span data-ttu-id="73b9d-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="73b9d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="73b9d-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="73b9d-116">Child Elements</span></span>  
  
|<span data-ttu-id="73b9d-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="73b9d-117">Element</span></span>|<span data-ttu-id="73b9d-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73b9d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73b9d-119">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="73b9d-119">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery.md)|<span data-ttu-id="73b9d-120">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="73b9d-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="73b9d-121">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="73b9d-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73b9d-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="73b9d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="73b9d-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="73b9d-123">Element</span></span>|<span data-ttu-id="73b9d-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73b9d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73b9d-125">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="73b9d-125">\<workflow></span></span>](workflow.md)|<span data-ttu-id="73b9d-126">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="73b9d-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73b9d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73b9d-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="73b9d-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="73b9d-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="73b9d-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="73b9d-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
