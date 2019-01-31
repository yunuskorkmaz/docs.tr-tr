---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 2199e66342c6fa3afca9d8ccd3b620560b123ede
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260846"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="69efe-101">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="69efe-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="69efe-102">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="69efe-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="69efe-103">Sorgu zamanlanmış etkinlik kayıtlarına abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="69efe-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="69efe-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="69efe-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="69efe-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="69efe-105">\<system.serviceModel></span></span>  
<span data-ttu-id="69efe-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="69efe-106">\<tracking></span></span>  
<span data-ttu-id="69efe-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="69efe-107">\<trackingProfile></span></span>  
<span data-ttu-id="69efe-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="69efe-108">\<workflow></span></span>  
<span data-ttu-id="69efe-109">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="69efe-109">\<activityScheduledQueries></span></span>  
<span data-ttu-id="69efe-110">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="69efe-110">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69efe-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69efe-111">Syntax</span></span>  
  
```xml 
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69efe-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="69efe-112">Attributes and Elements</span></span>  
 <span data-ttu-id="69efe-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="69efe-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69efe-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="69efe-114">Attributes</span></span>  
  
|<span data-ttu-id="69efe-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="69efe-115">Attribute</span></span>|<span data-ttu-id="69efe-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69efe-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="69efe-117">activityName</span><span class="sxs-lookup"><span data-stu-id="69efe-117">activityName</span></span>|<span data-ttu-id="69efe-118">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="69efe-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="69efe-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="69efe-119">childActivityName</span></span>|<span data-ttu-id="69efe-120">Kendisi için İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="69efe-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69efe-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="69efe-121">Child Elements</span></span>  
 <span data-ttu-id="69efe-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="69efe-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69efe-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="69efe-123">Parent Elements</span></span>  
  
|<span data-ttu-id="69efe-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="69efe-124">Element</span></span>|<span data-ttu-id="69efe-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69efe-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69efe-126">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="69efe-126">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="69efe-127">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="69efe-127">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69efe-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69efe-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="69efe-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="69efe-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="69efe-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="69efe-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
