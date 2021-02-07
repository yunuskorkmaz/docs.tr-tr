---
description: 'Hakkında daha fazla bilgi edinin: <bookmarkResumptionQuery>'
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: 4e6637b6edd54d9c1cf1a44986b362eb616bf14d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725252"
---
# \<bookmarkResumptionQuery>

<span data-ttu-id="aa171-102">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aa171-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="aa171-103">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="aa171-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="aa171-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="aa171-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="aa171-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="aa171-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa171-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa171-106">Attributes and Elements</span></span>  

 <span data-ttu-id="aa171-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aa171-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa171-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aa171-108">Attributes</span></span>  
  
|<span data-ttu-id="aa171-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="aa171-109">Attribute</span></span>|<span data-ttu-id="aa171-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa171-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aa171-111">name</span><span class="sxs-lookup"><span data-stu-id="aa171-111">name</span></span>|<span data-ttu-id="aa171-112">Abone olunacak yer işareti kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="aa171-112">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa171-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa171-113">Child Elements</span></span>  

 <span data-ttu-id="aa171-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="aa171-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa171-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa171-115">Parent Elements</span></span>  
  
|<span data-ttu-id="aa171-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="aa171-116">Element</span></span>|<span data-ttu-id="aa171-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa171-117">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="aa171-118">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aa171-118">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa171-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa171-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="aa171-120">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="aa171-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="aa171-121">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="aa171-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
