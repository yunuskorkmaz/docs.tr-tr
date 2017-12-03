---
title: '&lt;activityScheduledQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d860474c4a638a347f85c07862c330f58cc30c09
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivityscheduledqueriesgt"></a><span data-ttu-id="293c9-102">&lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="293c9-102">&lt;activityScheduledQueries&gt;</span></span>
<span data-ttu-id="293c9-103">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="293c9-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="293c9-104">Sorgu için zamanlanan etkinlik kayıtlarını abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="293c9-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="293c9-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="293c9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="293c9-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="293c9-106">\<system.serviceModel></span></span>  
<span data-ttu-id="293c9-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="293c9-107">\<tracking></span></span>  
<span data-ttu-id="293c9-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="293c9-108">\<trackingProfile></span></span>  
<span data-ttu-id="293c9-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="293c9-109">\<workflow></span></span>  
<span data-ttu-id="293c9-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="293c9-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="293c9-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="293c9-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="293c9-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="293c9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="293c9-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="293c9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="293c9-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="293c9-114">Attributes</span></span>  
 <span data-ttu-id="293c9-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="293c9-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="293c9-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="293c9-116">Child Elements</span></span>  
  
|<span data-ttu-id="293c9-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="293c9-117">Element</span></span>|<span data-ttu-id="293c9-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="293c9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="293c9-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="293c9-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="293c9-120">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="293c9-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="293c9-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="293c9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="293c9-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="293c9-122">Element</span></span>|<span data-ttu-id="293c9-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="293c9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="293c9-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="293c9-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="293c9-125">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="293c9-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="293c9-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="293c9-126">See Also</span></span>  
 <span data-ttu-id="293c9-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="293c9-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="293c9-128"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="293c9-128"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="293c9-129">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="293c9-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="293c9-130">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="293c9-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
