---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 563e0cbd3f50887e1c9e3d47a3c9502acc13b2c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398861"
---
# \<bookmarkResumptionQueries>
<span data-ttu-id="21eb4-101">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="21eb4-101">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="21eb4-102">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="21eb4-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="21eb4-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="21eb4-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="21eb4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21eb4-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21eb4-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="21eb4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="21eb4-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21eb4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21eb4-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="21eb4-107">Attributes</span></span>  
 <span data-ttu-id="21eb4-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="21eb4-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="21eb4-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="21eb4-109">Child Elements</span></span>  
  
|<span data-ttu-id="21eb4-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="21eb4-110">Element</span></span>|<span data-ttu-id="21eb4-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21eb4-111">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery.md)|<span data-ttu-id="21eb4-112">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="21eb4-112">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="21eb4-113">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="21eb4-113">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21eb4-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="21eb4-114">Parent Elements</span></span>  
  
|<span data-ttu-id="21eb4-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="21eb4-115">Element</span></span>|<span data-ttu-id="21eb4-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21eb4-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="21eb4-117">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="21eb4-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21eb4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21eb4-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="21eb4-119">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="21eb4-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="21eb4-120">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="21eb4-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
