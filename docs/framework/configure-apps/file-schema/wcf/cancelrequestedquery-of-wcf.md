---
title: WCF &lt;cancelRequestedQuery&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6fc9df52c691e13802607714977f3aa778cde84e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="68067-102">WCF &lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="68067-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="68067-103">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="68067-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="68067-104">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="68067-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="68067-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="68067-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="68067-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="68067-106">\<system.serviceModel></span></span>  
<span data-ttu-id="68067-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="68067-107">\<tracking></span></span>  
<span data-ttu-id="68067-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="68067-108">\<trackingProfile></span></span>  
<span data-ttu-id="68067-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="68067-109">\<workflow></span></span>  
<span data-ttu-id="68067-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="68067-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="68067-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="68067-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68067-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68067-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="68067-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="68067-113">Attributes and Elements</span></span>  
 <span data-ttu-id="68067-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68067-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68067-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="68067-115">Attributes</span></span>  
  
|<span data-ttu-id="68067-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="68067-116">Attribute</span></span>|<span data-ttu-id="68067-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68067-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68067-118">activityName</span><span class="sxs-lookup"><span data-stu-id="68067-118">activityName</span></span>|<span data-ttu-id="68067-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="68067-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="68067-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="68067-120">childActivityName</span></span>|<span data-ttu-id="68067-121">İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="68067-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68067-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="68067-122">Child Elements</span></span>  
 <span data-ttu-id="68067-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="68067-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="68067-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="68067-124">Parent Elements</span></span>  
  
|<span data-ttu-id="68067-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="68067-125">Element</span></span>|<span data-ttu-id="68067-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68067-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68067-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="68067-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="68067-128">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan yapılandırma öğelerinin bir listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="68067-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="68067-129">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="68067-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68067-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68067-130">See Also</span></span>  
 <span data-ttu-id="68067-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="68067-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="68067-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="68067-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>     
 [<span data-ttu-id="68067-133">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="68067-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="68067-134">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="68067-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
