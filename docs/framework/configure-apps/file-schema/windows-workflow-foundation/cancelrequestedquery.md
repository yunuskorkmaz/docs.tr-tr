---
title: '&lt;cancelRequestedQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e1697b245f9ab61cab3e4b26b1756259f0eba9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="0605f-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="0605f-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="0605f-103">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0605f-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="0605f-104">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0605f-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="0605f-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="0605f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="0605f-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="0605f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="0605f-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="0605f-107">\<tracking></span></span>  
<span data-ttu-id="0605f-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="0605f-108">\<trackingProfile></span></span>  
<span data-ttu-id="0605f-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="0605f-109">\<workflow></span></span>  
<span data-ttu-id="0605f-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="0605f-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="0605f-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="0605f-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0605f-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0605f-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0605f-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0605f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0605f-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0605f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0605f-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0605f-115">Attributes</span></span>  
  
|<span data-ttu-id="0605f-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0605f-116">Attribute</span></span>|<span data-ttu-id="0605f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0605f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0605f-118">activityName</span><span class="sxs-lookup"><span data-stu-id="0605f-118">activityName</span></span>|<span data-ttu-id="0605f-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="0605f-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="0605f-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="0605f-120">childActivityName</span></span>|<span data-ttu-id="0605f-121">İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="0605f-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0605f-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0605f-122">Child Elements</span></span>  
 <span data-ttu-id="0605f-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="0605f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0605f-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0605f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0605f-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="0605f-125">Element</span></span>|<span data-ttu-id="0605f-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0605f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0605f-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="0605f-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="0605f-128">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan yapılandırma öğelerinin bir listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0605f-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="0605f-129">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0605f-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0605f-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0605f-130">See Also</span></span>  
 <span data-ttu-id="0605f-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="0605f-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="0605f-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="0605f-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="0605f-133">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="0605f-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="0605f-134">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="0605f-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
