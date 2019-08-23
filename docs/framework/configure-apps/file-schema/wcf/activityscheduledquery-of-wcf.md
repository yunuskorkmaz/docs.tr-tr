---
title: <activityScheduledQuery>WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: 7787ada68210ff832ff3fd1ec93c9d346e4d2eaa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926922"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="ba95c-102">\<WCF activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="ba95c-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="ba95c-103">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ba95c-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="ba95c-104">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ba95c-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="ba95c-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ba95c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ba95c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ba95c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ba95c-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="ba95c-107">\<tracking></span></span>  
<span data-ttu-id="ba95c-108">\<Profiller ></span><span class="sxs-lookup"><span data-stu-id="ba95c-108">\<profiles></span></span>  
<span data-ttu-id="ba95c-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ba95c-109">\<trackingProfile></span></span>  
<span data-ttu-id="ba95c-110">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="ba95c-110">\<workflow></span></span>  
<span data-ttu-id="ba95c-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="ba95c-111">\<activityScheduledQueries></span></span>  
<span data-ttu-id="ba95c-112">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="ba95c-112">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba95c-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba95c-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba95c-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="ba95c-114">Attributes and elements</span></span>  

<span data-ttu-id="ba95c-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ba95c-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba95c-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ba95c-116">Attributes</span></span>  
  
|<span data-ttu-id="ba95c-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ba95c-117">Attribute</span></span>|<span data-ttu-id="ba95c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba95c-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="ba95c-119">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ba95c-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="ba95c-120">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ba95c-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba95c-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="ba95c-121">Child elements</span></span>

<span data-ttu-id="ba95c-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="ba95c-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="ba95c-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="ba95c-123">Parent elements</span></span>  
  
|<span data-ttu-id="ba95c-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="ba95c-124">Element</span></span>|<span data-ttu-id="ba95c-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba95c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba95c-126">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="ba95c-126">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="ba95c-127">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ba95c-127">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba95c-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba95c-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="ba95c-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="ba95c-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ba95c-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="ba95c-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
