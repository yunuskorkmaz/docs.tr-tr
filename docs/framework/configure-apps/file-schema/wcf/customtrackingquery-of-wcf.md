---
title: WCF &lt;customTrackingQuery&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c88a5d0e15acf67061976826a65faf5bfacb8384
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="2af32-102">WCF &lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="2af32-102">&lt;customTrackingQuery&gt; of WCF</span></span>
<span data-ttu-id="2af32-103">Kod etkinliklerinizi tanımladığınız olayları izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2af32-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="2af32-104">Sorgu için özel izleme kayıtları abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2af32-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="2af32-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2af32-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="2af32-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2af32-106">\<system.serviceModel></span></span>  
<span data-ttu-id="2af32-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="2af32-107">\<tracking></span></span>  
<span data-ttu-id="2af32-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="2af32-108">\<trackingProfile></span></span>  
<span data-ttu-id="2af32-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="2af32-109">\<workflow></span></span>  
<span data-ttu-id="2af32-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="2af32-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="2af32-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="2af32-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2af32-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2af32-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2af32-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2af32-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2af32-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2af32-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2af32-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2af32-115">Attributes</span></span>  
  
|<span data-ttu-id="2af32-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2af32-116">Attribute</span></span>|<span data-ttu-id="2af32-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2af32-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2af32-118">activityName</span><span class="sxs-lookup"><span data-stu-id="2af32-118">activityName</span></span>|<span data-ttu-id="2af32-119">İzleme kaydı oluşturulan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="2af32-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="2af32-120">name</span><span class="sxs-lookup"><span data-stu-id="2af32-120">name</span></span>|<span data-ttu-id="2af32-121">Yayılan özel izleme kaydın adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="2af32-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2af32-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2af32-122">Child Elements</span></span>  
 <span data-ttu-id="2af32-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="2af32-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2af32-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2af32-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2af32-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="2af32-125">Element</span></span>|<span data-ttu-id="2af32-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2af32-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2af32-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="2af32-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="2af32-128">Kod etkinliklerinizi tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="2af32-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2af32-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2af32-129">See Also</span></span>  
 <span data-ttu-id="2af32-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2af32-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>      
 <span data-ttu-id="2af32-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2af32-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="2af32-132">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="2af32-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="2af32-133">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="2af32-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
