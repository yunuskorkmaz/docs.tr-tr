---
title: <bookmarkResumptionQueries>WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 94ff9f44f295b45c03e1bd8f52a85d6b7b0c6e3b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850132"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="c5950-102">\<WCF 'nin bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="c5950-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="c5950-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c5950-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="c5950-104">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c5950-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="c5950-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c5950-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="c5950-106">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c5950-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c5950-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c5950-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c5950-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c5950-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="c5950-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="c5950-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="c5950-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c5950-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="c5950-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c5950-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="c5950-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQueries >**</span><span class="sxs-lookup"><span data-stu-id="c5950-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="c5950-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5950-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5950-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="c5950-114">Attributes and elements</span></span>  
  
<span data-ttu-id="c5950-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5950-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5950-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5950-116">Attributes</span></span>  
  
<span data-ttu-id="c5950-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="c5950-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c5950-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c5950-118">Child elements</span></span>  
  
|<span data-ttu-id="c5950-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5950-119">Element</span></span>|<span data-ttu-id="c5950-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5950-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5950-121">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="c5950-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="c5950-122">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="c5950-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="c5950-123">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c5950-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5950-124">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="c5950-124">Parent elements</span></span>  
  
|<span data-ttu-id="c5950-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5950-125">Element</span></span>|<span data-ttu-id="c5950-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5950-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5950-127">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="c5950-127">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="c5950-128">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="c5950-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5950-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5950-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c5950-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c5950-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c5950-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c5950-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
