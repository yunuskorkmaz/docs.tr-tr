---
title: '&lt;activityScheduledQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51db0762c10459d67929867a0fe44908dc7ec750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="62791-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="62791-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="62791-103">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="62791-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="62791-104">Sorgu için zamanlanan etkinlik kayıtlarını abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="62791-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="62791-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="62791-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="62791-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="62791-106">\<system.serviceModel></span></span>  
<span data-ttu-id="62791-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="62791-107">\<tracking></span></span>  
<span data-ttu-id="62791-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="62791-108">\<trackingProfile></span></span>  
<span data-ttu-id="62791-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="62791-109">\<workflow></span></span>  
<span data-ttu-id="62791-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="62791-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="62791-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="62791-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62791-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62791-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62791-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="62791-113">Attributes and Elements</span></span>  
 <span data-ttu-id="62791-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="62791-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62791-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="62791-115">Attributes</span></span>  
  
|<span data-ttu-id="62791-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="62791-116">Attribute</span></span>|<span data-ttu-id="62791-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62791-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62791-118">activityName</span><span class="sxs-lookup"><span data-stu-id="62791-118">activityName</span></span>|<span data-ttu-id="62791-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="62791-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="62791-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="62791-120">childActivityName</span></span>|<span data-ttu-id="62791-121">İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="62791-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62791-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="62791-122">Child Elements</span></span>  
 <span data-ttu-id="62791-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="62791-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62791-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="62791-124">Parent Elements</span></span>  
  
|<span data-ttu-id="62791-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="62791-125">Element</span></span>|<span data-ttu-id="62791-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62791-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62791-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="62791-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="62791-128">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="62791-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62791-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62791-129">See Also</span></span>  
 <span data-ttu-id="62791-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="62791-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="62791-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="62791-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="62791-132">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="62791-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="62791-133">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="62791-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
