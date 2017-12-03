---
title: WCF &lt;activityScheduledQuery&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 260b77789df6a03b640895ed158c94bfd1533f9b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="89ae4-102">WCF &lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="89ae4-102">&lt;activityScheduledQuery&gt; of WCF</span></span>
<span data-ttu-id="89ae4-103">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="89ae4-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="89ae4-104">Sorgu için zamanlanan etkinlik kayıtlarını abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="89ae4-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="89ae4-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="89ae4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="89ae4-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="89ae4-106">\<system.serviceModel></span></span>  
<span data-ttu-id="89ae4-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="89ae4-107">\<tracking></span></span>  
<span data-ttu-id="89ae4-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="89ae4-108">\<trackingProfile></span></span>  
<span data-ttu-id="89ae4-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="89ae4-109">\<workflow></span></span>  
<span data-ttu-id="89ae4-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="89ae4-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="89ae4-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="89ae4-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89ae4-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89ae4-112">Syntax</span></span>  
  
```xml
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89ae4-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="89ae4-113">Attributes and Elements</span></span>  
 <span data-ttu-id="89ae4-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="89ae4-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89ae4-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="89ae4-115">Attributes</span></span>  
  
|<span data-ttu-id="89ae4-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="89ae4-116">Attribute</span></span>|<span data-ttu-id="89ae4-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89ae4-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89ae4-118">activityName</span><span class="sxs-lookup"><span data-stu-id="89ae4-118">activityName</span></span>|<span data-ttu-id="89ae4-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="89ae4-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="89ae4-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="89ae4-120">childActivityName</span></span>|<span data-ttu-id="89ae4-121">İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="89ae4-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89ae4-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="89ae4-122">Child Elements</span></span>  
 <span data-ttu-id="89ae4-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="89ae4-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89ae4-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="89ae4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="89ae4-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="89ae4-125">Element</span></span>|<span data-ttu-id="89ae4-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89ae4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89ae4-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="89ae4-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="89ae4-128">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="89ae4-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89ae4-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89ae4-129">See Also</span></span>  
 <span data-ttu-id="89ae4-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span><span class="sxs-lookup"><span data-stu-id="89ae4-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span></span>     
 <span data-ttu-id="89ae4-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="89ae4-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="89ae4-132">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="89ae4-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="89ae4-133">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="89ae4-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
