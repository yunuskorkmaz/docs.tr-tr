---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 89de9ef10449fbae78a8c5b558101a2cf6477b07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945529"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="8d56f-101">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="8d56f-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="8d56f-102">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8d56f-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="8d56f-103">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8d56f-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="8d56f-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8d56f-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="8d56f-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8d56f-105">\<system.serviceModel></span></span>  
<span data-ttu-id="8d56f-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="8d56f-106">\<tracking></span></span>  
<span data-ttu-id="8d56f-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8d56f-107">\<trackingProfile></span></span>  
<span data-ttu-id="8d56f-108">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="8d56f-108">\<workflow></span></span>  
<span data-ttu-id="8d56f-109">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="8d56f-109">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d56f-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d56f-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d56f-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d56f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8d56f-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8d56f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d56f-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8d56f-113">Attributes</span></span>  
 <span data-ttu-id="8d56f-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="8d56f-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d56f-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d56f-115">Child Elements</span></span>  
  
|<span data-ttu-id="8d56f-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="8d56f-116">Element</span></span>|<span data-ttu-id="8d56f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d56f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d56f-118">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="8d56f-118">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="8d56f-119">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="8d56f-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d56f-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d56f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8d56f-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="8d56f-121">Element</span></span>|<span data-ttu-id="8d56f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d56f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d56f-123">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="8d56f-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="8d56f-124">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="8d56f-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d56f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d56f-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8d56f-126">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="8d56f-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8d56f-127">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="8d56f-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
