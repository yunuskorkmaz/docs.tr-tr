---
title: '@no__t-WCF için 0'
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 8cb254599a9742305ec958fd77174f4c4b8a57c2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833998"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="d591e-102">WCF \<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="d591e-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="d591e-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d591e-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="d591e-104">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d591e-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="d591e-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d591e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="d591e-106">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d591e-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d591e-107">&nbsp; @ no__t-1[ **\<system. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d591e-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d591e-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<tracking >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="d591e-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="d591e-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<profiles >** </span><span class="sxs-lookup"><span data-stu-id="d591e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="d591e-110">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0trackingProfile >** ](trackingprofile-of-wcf.md)1</span><span class="sxs-lookup"><span data-stu-id="d591e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\</span></span>
<span data-ttu-id="d591e-111">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9[ **&nbsp;2workflow >** ](workflow-of-wcf.md)3</span><span class="sxs-lookup"><span data-stu-id="d591e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\</span></span>
<span data-ttu-id="d591e-112">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 @ no__t-10 @ no__t-11[ **&nbsp;4bookmarkResumptionQueries >** ](bookmarkresumptionqueries-of-wcf.md)5</span><span class="sxs-lookup"><span data-stu-id="d591e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)\</span></span>
<span data-ttu-id="d591e-113">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 @ no__t-10 @ no__t-11 @ no__t-12 @ no__t-13 **&nbsp;5bookmarkResumptionQuery >**</span><span class="sxs-lookup"><span data-stu-id="d591e-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d591e-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d591e-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d591e-115">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="d591e-115">Attributes and elements</span></span>

<span data-ttu-id="d591e-116">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="d591e-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d591e-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d591e-117">Attributes</span></span>  
  
|<span data-ttu-id="d591e-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d591e-118">Attribute</span></span>|<span data-ttu-id="d591e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d591e-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="d591e-120">Abone olunacak yer işareti kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d591e-120">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d591e-121">Alt öğeler</span><span class="sxs-lookup"><span data-stu-id="d591e-121">Child elements</span></span>

<span data-ttu-id="d591e-122">Hiçbiri.</span><span class="sxs-lookup"><span data-stu-id="d591e-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="d591e-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="d591e-123">Parent elements</span></span>  
  
|<span data-ttu-id="d591e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="d591e-124">Element</span></span>|<span data-ttu-id="d591e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d591e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d591e-126">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="d591e-126">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="d591e-127">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d591e-127">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d591e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d591e-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d591e-129">İş akışı Izleme ve Izleme</span><span class="sxs-lookup"><span data-stu-id="d591e-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d591e-130">İzleme profilleri</span><span class="sxs-lookup"><span data-stu-id="d591e-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
