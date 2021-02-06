---
description: WCF hakkında daha fazla bilgi edinin <bookmarkResumptionQuery>
title: <bookmarkResumptionQuery> WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 9dadab3e304a2507a404bf43c377df46d5b33dda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639334"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="c2935-103">\<bookmarkResumptionQuery> WCF</span><span class="sxs-lookup"><span data-stu-id="c2935-103">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="c2935-104">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c2935-104">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="c2935-105">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c2935-105">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="c2935-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c2935-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="c2935-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="c2935-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2935-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="c2935-108">Attributes and elements</span></span>

<span data-ttu-id="c2935-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c2935-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2935-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c2935-110">Attributes</span></span>  
  
|<span data-ttu-id="c2935-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c2935-111">Attribute</span></span>|<span data-ttu-id="c2935-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2935-112">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="c2935-113">Abone olunacak yer işareti kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c2935-113">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2935-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c2935-114">Child elements</span></span>

<span data-ttu-id="c2935-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="c2935-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="c2935-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="c2935-116">Parent elements</span></span>  
  
|<span data-ttu-id="c2935-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="c2935-117">Element</span></span>|<span data-ttu-id="c2935-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2935-118">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="c2935-119">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c2935-119">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2935-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2935-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c2935-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c2935-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c2935-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c2935-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
