---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: b2a81a42a17474bdb0124bec6d3c3eeefa514411
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398845"
---
# \<bookmarkResumptionQuery>
<span data-ttu-id="4c828-101">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c828-101">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="4c828-102">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4c828-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="4c828-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4c828-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="4c828-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c828-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c828-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c828-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4c828-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c828-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c828-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4c828-107">Attributes</span></span>  
  
|<span data-ttu-id="4c828-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4c828-108">Attribute</span></span>|<span data-ttu-id="4c828-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c828-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c828-110">name</span><span class="sxs-lookup"><span data-stu-id="4c828-110">name</span></span>|<span data-ttu-id="4c828-111">Abone olunacak yer işareti kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4c828-111">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c828-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c828-112">Child Elements</span></span>  
 <span data-ttu-id="4c828-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="4c828-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c828-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c828-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4c828-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="4c828-115">Element</span></span>|<span data-ttu-id="4c828-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c828-116">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="4c828-117">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c828-117">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c828-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c828-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4c828-119">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="4c828-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4c828-120">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="4c828-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
