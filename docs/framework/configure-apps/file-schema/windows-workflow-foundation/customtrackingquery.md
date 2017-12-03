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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 908c340167d50d4d16e0eeff7cc2e01290b55e7a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="8ca44-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="8ca44-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="8ca44-103">Kod etkinliklerinizi tanımladığınız olayları izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8ca44-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="8ca44-104">Sorgu için özel izleme kayıtları abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8ca44-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="8ca44-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8ca44-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="8ca44-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8ca44-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8ca44-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="8ca44-107">\<tracking></span></span>  
<span data-ttu-id="8ca44-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="8ca44-108">\<trackingProfile></span></span>  
<span data-ttu-id="8ca44-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="8ca44-109">\<workflow></span></span>  
<span data-ttu-id="8ca44-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="8ca44-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="8ca44-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="8ca44-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca44-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ca44-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ca44-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ca44-113">Attributes and Elements</span></span>  
 <span data-ttu-id="8ca44-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ca44-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ca44-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8ca44-115">Attributes</span></span>  
  
|<span data-ttu-id="8ca44-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8ca44-116">Attribute</span></span>|<span data-ttu-id="8ca44-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ca44-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8ca44-118">activityName</span><span class="sxs-lookup"><span data-stu-id="8ca44-118">activityName</span></span>|<span data-ttu-id="8ca44-119">İzleme kaydı oluşturulan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="8ca44-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="8ca44-120">name</span><span class="sxs-lookup"><span data-stu-id="8ca44-120">name</span></span>|<span data-ttu-id="8ca44-121">Yayılan özel izleme kaydın adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="8ca44-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ca44-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ca44-122">Child Elements</span></span>  
 <span data-ttu-id="8ca44-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="8ca44-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ca44-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ca44-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8ca44-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="8ca44-125">Element</span></span>|<span data-ttu-id="8ca44-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ca44-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ca44-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="8ca44-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="8ca44-128">Kod etkinliklerinizi tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="8ca44-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ca44-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ca44-129">See Also</span></span>  
 <span data-ttu-id="8ca44-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8ca44-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="8ca44-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8ca44-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>         
 [<span data-ttu-id="8ca44-132">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="8ca44-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="8ca44-133">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="8ca44-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
