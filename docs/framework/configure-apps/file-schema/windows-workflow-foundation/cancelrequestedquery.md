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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c6b1137e89799af34d0808d83e56c7c333a49635
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="e4376-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="e4376-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="e4376-103">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e4376-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="e4376-104">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e4376-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="e4376-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e4376-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e4376-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e4376-106">\<system.serviceModel></span></span>  
<span data-ttu-id="e4376-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="e4376-107">\<tracking></span></span>  
<span data-ttu-id="e4376-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e4376-108">\<trackingProfile></span></span>  
<span data-ttu-id="e4376-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="e4376-109">\<workflow></span></span>  
<span data-ttu-id="e4376-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="e4376-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="e4376-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="e4376-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4376-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4376-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4376-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4376-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e4376-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4376-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4376-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e4376-115">Attributes</span></span>  
  
|<span data-ttu-id="e4376-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e4376-116">Attribute</span></span>|<span data-ttu-id="e4376-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4376-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4376-118">activityName</span><span class="sxs-lookup"><span data-stu-id="e4376-118">activityName</span></span>|<span data-ttu-id="e4376-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="e4376-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="e4376-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="e4376-120">childActivityName</span></span>|<span data-ttu-id="e4376-121">İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="e4376-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4376-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4376-122">Child Elements</span></span>  
 <span data-ttu-id="e4376-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="e4376-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4376-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4376-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e4376-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4376-125">Element</span></span>|<span data-ttu-id="e4376-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4376-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4376-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="e4376-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="e4376-128">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan yapılandırma öğelerinin bir listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e4376-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="e4376-129">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e4376-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4376-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4376-130">See Also</span></span>  
 <span data-ttu-id="e4376-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e4376-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e4376-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e4376-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="e4376-133">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="e4376-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e4376-134">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="e4376-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
