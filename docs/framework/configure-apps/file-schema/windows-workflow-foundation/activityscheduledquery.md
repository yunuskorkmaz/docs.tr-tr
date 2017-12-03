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
ms.openlocfilehash: 32b0e1b068e1f6fef3ce18b0e4dfa628ccaa8a79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="b2f4a-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="b2f4a-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="b2f4a-103">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b2f4a-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="b2f4a-104">Sorgu için zamanlanan etkinlik kayıtlarını abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b2f4a-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="b2f4a-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b2f4a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="b2f4a-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b2f4a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b2f4a-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="b2f4a-107">\<tracking></span></span>  
<span data-ttu-id="b2f4a-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b2f4a-108">\<trackingProfile></span></span>  
<span data-ttu-id="b2f4a-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="b2f4a-109">\<workflow></span></span>  
<span data-ttu-id="b2f4a-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="b2f4a-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="b2f4a-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="b2f4a-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2f4a-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2f4a-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2f4a-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2f4a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b2f4a-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2f4a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2f4a-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b2f4a-115">Attributes</span></span>  
  
|<span data-ttu-id="b2f4a-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b2f4a-116">Attribute</span></span>|<span data-ttu-id="b2f4a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2f4a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2f4a-118">activityName</span><span class="sxs-lookup"><span data-stu-id="b2f4a-118">activityName</span></span>|<span data-ttu-id="b2f4a-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="b2f4a-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="b2f4a-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="b2f4a-120">childActivityName</span></span>|<span data-ttu-id="b2f4a-121">İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="b2f4a-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2f4a-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2f4a-122">Child Elements</span></span>  
 <span data-ttu-id="b2f4a-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="b2f4a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2f4a-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2f4a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b2f4a-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="b2f4a-125">Element</span></span>|<span data-ttu-id="b2f4a-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2f4a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2f4a-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="b2f4a-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="b2f4a-128">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="b2f4a-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2f4a-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2f4a-129">See Also</span></span>  
 <span data-ttu-id="b2f4a-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b2f4a-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b2f4a-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b2f4a-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b2f4a-132">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="b2f4a-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b2f4a-133">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="b2f4a-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
