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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84c9635b37c592b4d82635deb58880d81d2fb5cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="8b1aa-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="8b1aa-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="8b1aa-103">Kod etkinliklerinizi tanımladığınız olayları izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8b1aa-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="8b1aa-104">Sorgu için özel izleme kayıtları abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8b1aa-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="8b1aa-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8b1aa-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="8b1aa-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8b1aa-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8b1aa-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="8b1aa-107">\<tracking></span></span>  
<span data-ttu-id="8b1aa-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="8b1aa-108">\<trackingProfile></span></span>  
<span data-ttu-id="8b1aa-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="8b1aa-109">\<workflow></span></span>  
<span data-ttu-id="8b1aa-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="8b1aa-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b1aa-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b1aa-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b1aa-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b1aa-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8b1aa-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b1aa-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b1aa-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8b1aa-114">Attributes</span></span>  
 <span data-ttu-id="8b1aa-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="8b1aa-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8b1aa-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b1aa-116">Child Elements</span></span>  
  
|<span data-ttu-id="8b1aa-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="8b1aa-117">Element</span></span>|<span data-ttu-id="8b1aa-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b1aa-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b1aa-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="8b1aa-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="8b1aa-120">Kod etkinliklerinizi tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="8b1aa-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8b1aa-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b1aa-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8b1aa-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="8b1aa-122">Element</span></span>|<span data-ttu-id="8b1aa-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b1aa-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b1aa-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="8b1aa-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="8b1aa-125">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="8b1aa-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b1aa-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8b1aa-126">See Also</span></span>  
 <span data-ttu-id="8b1aa-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8b1aa-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="8b1aa-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8b1aa-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="8b1aa-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="8b1aa-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="8b1aa-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="8b1aa-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
