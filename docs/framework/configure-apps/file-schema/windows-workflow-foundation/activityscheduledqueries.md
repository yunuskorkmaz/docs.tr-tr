---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 7217fb886cc96e1ad19f96e2c6542277cfc7979e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175766"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="0e674-101">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="0e674-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="0e674-102">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0e674-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="0e674-103">Sorgu zamanlanmış etkinlik kayıtlarına abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0e674-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="0e674-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="0e674-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="0e674-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0e674-105">\<system.serviceModel></span></span>  
<span data-ttu-id="0e674-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="0e674-106">\<tracking></span></span>  
<span data-ttu-id="0e674-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="0e674-107">\<trackingProfile></span></span>  
<span data-ttu-id="0e674-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="0e674-108">\<workflow></span></span>  
<span data-ttu-id="0e674-109">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="0e674-109">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e674-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e674-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e674-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e674-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0e674-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e674-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e674-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0e674-113">Attributes</span></span>  
 <span data-ttu-id="0e674-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="0e674-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0e674-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e674-115">Child Elements</span></span>  
  
|<span data-ttu-id="0e674-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e674-116">Element</span></span>|<span data-ttu-id="0e674-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e674-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e674-118">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="0e674-118">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="0e674-119">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="0e674-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e674-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e674-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0e674-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e674-121">Element</span></span>|<span data-ttu-id="0e674-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e674-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e674-123">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="0e674-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="0e674-124">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="0e674-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e674-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e674-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0e674-126">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="0e674-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0e674-127">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="0e674-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
