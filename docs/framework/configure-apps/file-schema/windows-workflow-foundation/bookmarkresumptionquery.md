---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: b2a81a42a17474bdb0124bec6d3c3eeefa514411
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398845"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="81edd-101">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="81edd-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="81edd-102">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="81edd-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="81edd-103">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="81edd-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="81edd-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="81edd-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="81edd-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="81edd-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="81edd-106">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="81edd-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="81edd-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="81edd-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="81edd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="81edd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="81edd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="81edd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="81edd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bookmarkResumptionQueries >** ](bookmarkresumptionqueries.md)</span><span class="sxs-lookup"><span data-stu-id="81edd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)</span></span>\
<span data-ttu-id="81edd-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQuery >**</span><span class="sxs-lookup"><span data-stu-id="81edd-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81edd-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81edd-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81edd-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="81edd-113">Attributes and Elements</span></span>  
 <span data-ttu-id="81edd-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81edd-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81edd-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="81edd-115">Attributes</span></span>  
  
|<span data-ttu-id="81edd-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="81edd-116">Attribute</span></span>|<span data-ttu-id="81edd-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81edd-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81edd-118">name</span><span class="sxs-lookup"><span data-stu-id="81edd-118">name</span></span>|<span data-ttu-id="81edd-119">Abone olunacak yer işareti kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="81edd-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81edd-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="81edd-120">Child Elements</span></span>  
 <span data-ttu-id="81edd-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="81edd-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81edd-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="81edd-122">Parent Elements</span></span>  
  
|<span data-ttu-id="81edd-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="81edd-123">Element</span></span>|<span data-ttu-id="81edd-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81edd-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81edd-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="81edd-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="81edd-126">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="81edd-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81edd-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81edd-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="81edd-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="81edd-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="81edd-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="81edd-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
