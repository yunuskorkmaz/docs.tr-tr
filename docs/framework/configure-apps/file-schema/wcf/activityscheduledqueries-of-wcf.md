---
title: WCF &lt;activityScheduledQueries&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 97726c7faa08477351d4496650b6c08b643cdb76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="71884-102">WCF &lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="71884-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="71884-103">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="71884-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="71884-104">Sorgu için zamanlanan etkinlik kayıtlarını abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="71884-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="71884-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="71884-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="71884-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="71884-106">\<system.serviceModel></span></span>  
<span data-ttu-id="71884-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="71884-107">\<tracking></span></span>  
<span data-ttu-id="71884-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="71884-108">\<trackingProfile></span></span>  
<span data-ttu-id="71884-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="71884-109">\<workflow></span></span>  
<span data-ttu-id="71884-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="71884-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71884-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71884-111">Syntax</span></span>  
  
```xml  
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71884-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="71884-112">Attributes and Elements</span></span>  
 <span data-ttu-id="71884-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="71884-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71884-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="71884-114">Attributes</span></span>  
 <span data-ttu-id="71884-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="71884-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="71884-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="71884-116">Child Elements</span></span>  
  
|<span data-ttu-id="71884-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="71884-117">Element</span></span>|<span data-ttu-id="71884-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71884-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71884-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="71884-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="71884-120">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="71884-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="71884-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="71884-121">Parent Elements</span></span>  
  
|<span data-ttu-id="71884-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="71884-122">Element</span></span>|<span data-ttu-id="71884-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71884-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71884-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="71884-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="71884-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="71884-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71884-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71884-126">See Also</span></span>  
 <span data-ttu-id="71884-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="71884-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span></span>     
 <span data-ttu-id="71884-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="71884-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="71884-129">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="71884-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="71884-130">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="71884-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
