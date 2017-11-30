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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 686b58d9efa4420de26fd7be52fe76208af63c6b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltactivityscheduledqueriesgt"></a><span data-ttu-id="e44cb-102">&lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="e44cb-102">&lt;activityScheduledQueries&gt;</span></span>
<span data-ttu-id="e44cb-103">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e44cb-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="e44cb-104">Sorgu için zamanlanan etkinlik kayıtlarını abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e44cb-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="e44cb-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e44cb-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e44cb-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e44cb-106">\<system.serviceModel></span></span>  
<span data-ttu-id="e44cb-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="e44cb-107">\<tracking></span></span>  
<span data-ttu-id="e44cb-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e44cb-108">\<trackingProfile></span></span>  
<span data-ttu-id="e44cb-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="e44cb-109">\<workflow></span></span>  
<span data-ttu-id="e44cb-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="e44cb-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e44cb-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e44cb-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e44cb-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e44cb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e44cb-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e44cb-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e44cb-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e44cb-114">Attributes</span></span>  
 <span data-ttu-id="e44cb-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="e44cb-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e44cb-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e44cb-116">Child Elements</span></span>  
  
|<span data-ttu-id="e44cb-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="e44cb-117">Element</span></span>|<span data-ttu-id="e44cb-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e44cb-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e44cb-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="e44cb-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="e44cb-120">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="e44cb-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e44cb-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e44cb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e44cb-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="e44cb-122">Element</span></span>|<span data-ttu-id="e44cb-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e44cb-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e44cb-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="e44cb-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e44cb-125">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="e44cb-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e44cb-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e44cb-126">See Also</span></span>  
 <span data-ttu-id="e44cb-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e44cb-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e44cb-128"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e44cb-128"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="e44cb-129">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="e44cb-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e44cb-130">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="e44cb-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
