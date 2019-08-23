---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: dc04405204be7c5484d47b4a3767f846b11abf9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945497"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="64ed6-101">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="64ed6-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="64ed6-102">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="64ed6-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="64ed6-103">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="64ed6-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="64ed6-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="64ed6-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="64ed6-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="64ed6-105">\<system.serviceModel></span></span>  
<span data-ttu-id="64ed6-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="64ed6-106">\<tracking></span></span>  
<span data-ttu-id="64ed6-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="64ed6-107">\<trackingProfile></span></span>  
<span data-ttu-id="64ed6-108">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="64ed6-108">\<workflow></span></span>  
<span data-ttu-id="64ed6-109">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="64ed6-109">\<activityScheduledQueries></span></span>  
<span data-ttu-id="64ed6-110">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="64ed6-110">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64ed6-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64ed6-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64ed6-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="64ed6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="64ed6-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="64ed6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64ed6-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="64ed6-114">Attributes</span></span>  
  
|<span data-ttu-id="64ed6-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="64ed6-115">Attribute</span></span>|<span data-ttu-id="64ed6-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64ed6-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="64ed6-117">activityName</span><span class="sxs-lookup"><span data-stu-id="64ed6-117">activityName</span></span>|<span data-ttu-id="64ed6-118">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="64ed6-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="64ed6-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="64ed6-119">childActivityName</span></span>|<span data-ttu-id="64ed6-120">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="64ed6-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64ed6-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="64ed6-121">Child Elements</span></span>  
 <span data-ttu-id="64ed6-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="64ed6-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="64ed6-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="64ed6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="64ed6-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="64ed6-124">Element</span></span>|<span data-ttu-id="64ed6-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64ed6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64ed6-126">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="64ed6-126">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="64ed6-127">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="64ed6-127">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64ed6-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64ed6-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="64ed6-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="64ed6-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="64ed6-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="64ed6-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
