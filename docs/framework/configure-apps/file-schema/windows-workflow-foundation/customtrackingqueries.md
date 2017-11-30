---
title: '&lt;customTrackingQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 19a4a58a15db72129f17655e7043f2ee3ae7ffa2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="ca39b-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="ca39b-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="ca39b-103">Kod etkinliklerinizi tanımladığınız olayları izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ca39b-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ca39b-104">Sorgu için özel izleme kayıtları abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ca39b-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="ca39b-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ca39b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ca39b-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ca39b-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ca39b-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="ca39b-107">\<tracking></span></span>  
<span data-ttu-id="ca39b-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ca39b-108">\<trackingProfile></span></span>  
<span data-ttu-id="ca39b-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="ca39b-109">\<workflow></span></span>  
<span data-ttu-id="ca39b-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="ca39b-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca39b-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca39b-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca39b-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca39b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ca39b-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca39b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca39b-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ca39b-114">Attributes</span></span>  
 <span data-ttu-id="ca39b-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="ca39b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ca39b-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca39b-116">Child Elements</span></span>  
  
|<span data-ttu-id="ca39b-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca39b-117">Element</span></span>|<span data-ttu-id="ca39b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca39b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca39b-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="ca39b-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="ca39b-120">Kod etkinliklerinizi tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="ca39b-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca39b-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca39b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ca39b-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca39b-122">Element</span></span>|<span data-ttu-id="ca39b-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca39b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca39b-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="ca39b-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="ca39b-125">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="ca39b-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca39b-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ca39b-126">See Also</span></span>  
 <span data-ttu-id="ca39b-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ca39b-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="ca39b-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ca39b-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="ca39b-129">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="ca39b-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ca39b-130">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="ca39b-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
