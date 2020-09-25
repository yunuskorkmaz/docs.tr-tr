---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 047d13bc8477214fa1e3c9ffdbed6785b29da637
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189596"
---
# \<bookmarkResumptionQueries>

<span data-ttu-id="03ece-101">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="03ece-101">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="03ece-102">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="03ece-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="03ece-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="03ece-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="03ece-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="03ece-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03ece-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="03ece-105">Attributes and Elements</span></span>  

 <span data-ttu-id="03ece-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="03ece-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03ece-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="03ece-107">Attributes</span></span>  

 <span data-ttu-id="03ece-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="03ece-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="03ece-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="03ece-109">Child Elements</span></span>  
  
|<span data-ttu-id="03ece-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="03ece-110">Element</span></span>|<span data-ttu-id="03ece-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03ece-111">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery.md)|<span data-ttu-id="03ece-112">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="03ece-112">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="03ece-113">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="03ece-113">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="03ece-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="03ece-114">Parent Elements</span></span>  
  
|<span data-ttu-id="03ece-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="03ece-115">Element</span></span>|<span data-ttu-id="03ece-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03ece-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="03ece-117">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="03ece-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03ece-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03ece-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="03ece-119">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="03ece-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="03ece-120">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="03ece-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
