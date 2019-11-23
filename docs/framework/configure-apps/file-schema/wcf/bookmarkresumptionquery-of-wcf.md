---
title: WCF <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 8cb254599a9742305ec958fd77174f4c4b8a57c2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833998"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="86333-102">WCF \<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="86333-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="86333-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="86333-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="86333-104">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="86333-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="86333-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="86333-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="86333-106">[ **\<yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="86333-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="86333-107">[**System. serviceModel >\<** ](system-servicemodel.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="86333-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="86333-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<izleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="86333-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="86333-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<profilleri >** </span><span class="sxs-lookup"><span data-stu-id="86333-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="86333-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="86333-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="86333-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="86333-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="86333-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bookmarkResumptionQueries >** ](bookmarkresumptionqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="86333-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)</span></span>\
<span data-ttu-id="86333-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**bookmarkResumptionQuery >**</span><span class="sxs-lookup"><span data-stu-id="86333-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86333-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86333-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86333-115">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="86333-115">Attributes and elements</span></span>

<span data-ttu-id="86333-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="86333-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86333-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="86333-117">Attributes</span></span>  
  
|<span data-ttu-id="86333-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="86333-118">Attribute</span></span>|<span data-ttu-id="86333-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86333-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="86333-120">Abone olunacak yer işareti kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="86333-120">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86333-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="86333-121">Child elements</span></span>

<span data-ttu-id="86333-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="86333-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="86333-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="86333-123">Parent elements</span></span>  
  
|<span data-ttu-id="86333-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="86333-124">Element</span></span>|<span data-ttu-id="86333-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86333-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86333-126">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="86333-126">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="86333-127">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="86333-127">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86333-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86333-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="86333-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="86333-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="86333-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="86333-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
