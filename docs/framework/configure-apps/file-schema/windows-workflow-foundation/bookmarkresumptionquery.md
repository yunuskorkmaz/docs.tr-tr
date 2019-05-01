---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: e43ba66e2c3ccfbb723b1eea8ef6774ad3f9f2aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790279"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="3af90-101">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="3af90-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="3af90-102">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3af90-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="3af90-103">Sorgu için yer imi sürdürme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3af90-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="3af90-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3af90-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="3af90-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3af90-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3af90-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="3af90-106">\<tracking></span></span>  
<span data-ttu-id="3af90-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3af90-107">\<trackingProfile></span></span>  
<span data-ttu-id="3af90-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="3af90-108">\<workflow></span></span>  
<span data-ttu-id="3af90-109">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="3af90-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="3af90-110">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="3af90-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3af90-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3af90-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3af90-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3af90-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3af90-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3af90-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3af90-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3af90-114">Attributes</span></span>  
  
|<span data-ttu-id="3af90-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3af90-115">Attribute</span></span>|<span data-ttu-id="3af90-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3af90-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3af90-117">name</span><span class="sxs-lookup"><span data-stu-id="3af90-117">name</span></span>|<span data-ttu-id="3af90-118">Abone olmak için yer imi kayıt adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="3af90-118">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3af90-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3af90-119">Child Elements</span></span>  
 <span data-ttu-id="3af90-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="3af90-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3af90-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3af90-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3af90-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="3af90-122">Element</span></span>|<span data-ttu-id="3af90-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3af90-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3af90-124">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="3af90-124">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="3af90-125">İş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3af90-125">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3af90-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3af90-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3af90-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="3af90-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3af90-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="3af90-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
