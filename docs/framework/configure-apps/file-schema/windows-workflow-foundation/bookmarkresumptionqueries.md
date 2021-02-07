---
description: 'Hakkında daha fazla bilgi edinin: <bookmarkResumptionQueries>'
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: e8ff21e2183fe31411674e9d4de6bf3d99d14836
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698160"
---
# \<bookmarkResumptionQueries>

<span data-ttu-id="54a74-102">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="54a74-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="54a74-103">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="54a74-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="54a74-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="54a74-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="54a74-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="54a74-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54a74-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="54a74-106">Attributes and Elements</span></span>  

 <span data-ttu-id="54a74-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="54a74-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54a74-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="54a74-108">Attributes</span></span>  

 <span data-ttu-id="54a74-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="54a74-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="54a74-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="54a74-110">Child Elements</span></span>  
  
|<span data-ttu-id="54a74-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="54a74-111">Element</span></span>|<span data-ttu-id="54a74-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54a74-112">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery.md)|<span data-ttu-id="54a74-113">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="54a74-113">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="54a74-114">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="54a74-114">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54a74-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="54a74-115">Parent Elements</span></span>  
  
|<span data-ttu-id="54a74-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="54a74-116">Element</span></span>|<span data-ttu-id="54a74-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54a74-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="54a74-118">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="54a74-118">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54a74-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54a74-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="54a74-120">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="54a74-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="54a74-121">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="54a74-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
