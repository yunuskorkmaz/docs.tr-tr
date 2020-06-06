---
title: <bookmarkResumptionQueries>WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 94ff9f44f295b45c03e1bd8f52a85d6b7b0c6e3b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850132"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="fb6b3-102">\<bookmarkResumptionQueries>WCF</span><span class="sxs-lookup"><span data-stu-id="fb6b3-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="fb6b3-103">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb6b3-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="fb6b3-104">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fb6b3-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="fb6b3-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="fb6b3-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="fb6b3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb6b3-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb6b3-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="fb6b3-107">Attributes and elements</span></span>  
  
<span data-ttu-id="fb6b3-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fb6b3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb6b3-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fb6b3-109">Attributes</span></span>  
  
<span data-ttu-id="fb6b3-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="fb6b3-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fb6b3-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="fb6b3-111">Child elements</span></span>  
  
|<span data-ttu-id="fb6b3-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb6b3-112">Element</span></span>|<span data-ttu-id="fb6b3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb6b3-113">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="fb6b3-114">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="fb6b3-114">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="fb6b3-115">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fb6b3-115">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb6b3-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="fb6b3-116">Parent elements</span></span>  
  
|<span data-ttu-id="fb6b3-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb6b3-117">Element</span></span>|<span data-ttu-id="fb6b3-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb6b3-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="fb6b3-119">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="fb6b3-119">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb6b3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb6b3-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fb6b3-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="fb6b3-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fb6b3-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="fb6b3-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
