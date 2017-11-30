---
title: '&lt;customTrackingQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fc06c34cb4db99f5e7b6850ed8e7cf7ed073ef72
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="fd997-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="fd997-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="fd997-103">Kod etkinliklerinizi tanımladığınız olayları izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fd997-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="fd997-104">Sorgu için özel izleme kayıtları abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fd997-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="fd997-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fd997-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="fd997-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="fd997-106">\<system.serviceModel></span></span>  
<span data-ttu-id="fd997-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="fd997-107">\<tracking></span></span>  
<span data-ttu-id="fd997-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="fd997-108">\<trackingProfile></span></span>  
<span data-ttu-id="fd997-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="fd997-109">\<workflow></span></span>  
<span data-ttu-id="fd997-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="fd997-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="fd997-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="fd997-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd997-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd997-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd997-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd997-113">Attributes and Elements</span></span>  
 <span data-ttu-id="fd997-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd997-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd997-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fd997-115">Attributes</span></span>  
  
|<span data-ttu-id="fd997-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fd997-116">Attribute</span></span>|<span data-ttu-id="fd997-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd997-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd997-118">activityName</span><span class="sxs-lookup"><span data-stu-id="fd997-118">activityName</span></span>|<span data-ttu-id="fd997-119">İzleme kaydı oluşturulan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="fd997-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="fd997-120">name</span><span class="sxs-lookup"><span data-stu-id="fd997-120">name</span></span>|<span data-ttu-id="fd997-121">Yayılan özel izleme kaydın adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="fd997-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd997-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd997-122">Child Elements</span></span>  
 <span data-ttu-id="fd997-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="fd997-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd997-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd997-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fd997-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="fd997-125">Element</span></span>|<span data-ttu-id="fd997-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd997-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd997-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="fd997-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="fd997-128">Kod etkinliklerinizi tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="fd997-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd997-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd997-129">See Also</span></span>  
 <span data-ttu-id="fd997-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fd997-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="fd997-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fd997-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>         
 [<span data-ttu-id="fd997-132">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="fd997-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="fd997-133">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="fd997-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
