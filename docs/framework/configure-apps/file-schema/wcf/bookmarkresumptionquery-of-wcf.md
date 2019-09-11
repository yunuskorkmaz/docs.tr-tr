---
title: <bookmarkResumptionQuery>WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 36d169b78e78692c7b45c75d5d375bddbba1c66f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850111"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="759a8-102">\<WCF 'nin bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="759a8-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="759a8-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="759a8-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="759a8-104">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="759a8-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="759a8-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="759a8-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="759a8-106">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="759a8-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="759a8-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="759a8-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="759a8-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="759a8-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="759a8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="759a8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="759a8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="759a8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="759a8-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="759a8-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="759a8-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bookmarkResumptionQueries >** ](bookmarkresumptionqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="759a8-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)</span></span>\
<span data-ttu-id="759a8-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQuery >**</span><span class="sxs-lookup"><span data-stu-id="759a8-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="759a8-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="759a8-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="759a8-115">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="759a8-115">Attributes and elements</span></span>

<span data-ttu-id="759a8-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="759a8-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="759a8-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="759a8-117">Attributes</span></span>  
  
|<span data-ttu-id="759a8-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="759a8-118">Attribute</span></span>|<span data-ttu-id="759a8-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="759a8-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="759a8-120">Abone olunacak yer işareti kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="759a8-120">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="759a8-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="759a8-121">Child elements</span></span>

<span data-ttu-id="759a8-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="759a8-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="759a8-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="759a8-123">Parent elements</span></span>  
  
|<span data-ttu-id="759a8-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="759a8-124">Element</span></span>|<span data-ttu-id="759a8-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="759a8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="759a8-126">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="759a8-126">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="759a8-127">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="759a8-127">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="759a8-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="759a8-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="759a8-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="759a8-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="759a8-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="759a8-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
