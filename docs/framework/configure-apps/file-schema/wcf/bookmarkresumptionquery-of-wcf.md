---
title: <bookmarkResumptionQuery>WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 8cb254599a9742305ec958fd77174f4c4b8a57c2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71833998"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="9c6e1-102">\<bookmarkResumptionQuery>WCF</span><span class="sxs-lookup"><span data-stu-id="9c6e1-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="9c6e1-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9c6e1-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="9c6e1-104">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9c6e1-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="9c6e1-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9c6e1-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="9c6e1-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c6e1-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c6e1-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="9c6e1-107">Attributes and elements</span></span>

<span data-ttu-id="9c6e1-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9c6e1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c6e1-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9c6e1-109">Attributes</span></span>  
  
|<span data-ttu-id="9c6e1-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9c6e1-110">Attribute</span></span>|<span data-ttu-id="9c6e1-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c6e1-111">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="9c6e1-112">Abone olunacak yer işareti kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9c6e1-112">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c6e1-113">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="9c6e1-113">Child elements</span></span>

<span data-ttu-id="9c6e1-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="9c6e1-114">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="9c6e1-115">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="9c6e1-115">Parent elements</span></span>  
  
|<span data-ttu-id="9c6e1-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="9c6e1-116">Element</span></span>|<span data-ttu-id="9c6e1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c6e1-117">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="9c6e1-118">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9c6e1-118">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c6e1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c6e1-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9c6e1-120">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="9c6e1-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9c6e1-121">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="9c6e1-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
