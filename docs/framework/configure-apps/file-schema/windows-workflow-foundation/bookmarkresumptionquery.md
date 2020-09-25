---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: efd1e4e54223ff9f5d60b4087fbe5b6bebf1af2f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189597"
---
# \<bookmarkResumptionQuery>

<span data-ttu-id="90334-101">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="90334-101">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="90334-102">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="90334-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="90334-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="90334-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="90334-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="90334-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90334-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="90334-105">Attributes and Elements</span></span>  

 <span data-ttu-id="90334-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="90334-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90334-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="90334-107">Attributes</span></span>  
  
|<span data-ttu-id="90334-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="90334-108">Attribute</span></span>|<span data-ttu-id="90334-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90334-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="90334-110">name</span><span class="sxs-lookup"><span data-stu-id="90334-110">name</span></span>|<span data-ttu-id="90334-111">Abone olunacak yer işareti kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="90334-111">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90334-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="90334-112">Child Elements</span></span>  

 <span data-ttu-id="90334-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="90334-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90334-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="90334-114">Parent Elements</span></span>  
  
|<span data-ttu-id="90334-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="90334-115">Element</span></span>|<span data-ttu-id="90334-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90334-116">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="90334-117">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="90334-117">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90334-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90334-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="90334-119">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="90334-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="90334-120">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="90334-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
