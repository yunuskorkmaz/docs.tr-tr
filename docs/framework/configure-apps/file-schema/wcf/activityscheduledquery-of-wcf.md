---
title: <activityScheduledQuery> WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: 5087d56092296f8c68b719ec0945993adeb3de0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704725"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="20c58-102">\<activityScheduledQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="20c58-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="20c58-103">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="20c58-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="20c58-104">Sorgu zamanlanmış etkinlik kayıtlarına abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="20c58-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="20c58-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="20c58-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="20c58-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="20c58-106">\<system.serviceModel></span></span>  
<span data-ttu-id="20c58-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="20c58-107">\<tracking></span></span>  
<span data-ttu-id="20c58-108">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="20c58-108">\<profiles></span></span>  
<span data-ttu-id="20c58-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="20c58-109">\<trackingProfile></span></span>  
<span data-ttu-id="20c58-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="20c58-110">\<workflow></span></span>  
<span data-ttu-id="20c58-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="20c58-111">\<activityScheduledQueries></span></span>  
<span data-ttu-id="20c58-112">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="20c58-112">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20c58-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20c58-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20c58-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="20c58-114">Attributes and elements</span></span>  

<span data-ttu-id="20c58-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20c58-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20c58-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="20c58-116">Attributes</span></span>  
  
|<span data-ttu-id="20c58-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="20c58-117">Attribute</span></span>|<span data-ttu-id="20c58-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20c58-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="20c58-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="20c58-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="20c58-120">Kendisi için İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="20c58-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20c58-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="20c58-121">Child elements</span></span>

<span data-ttu-id="20c58-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="20c58-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="20c58-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="20c58-123">Parent elements</span></span>  
  
|<span data-ttu-id="20c58-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="20c58-124">Element</span></span>|<span data-ttu-id="20c58-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20c58-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20c58-126">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="20c58-126">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="20c58-127">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu.</span><span class="sxs-lookup"><span data-stu-id="20c58-127">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20c58-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20c58-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="20c58-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="20c58-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="20c58-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="20c58-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
