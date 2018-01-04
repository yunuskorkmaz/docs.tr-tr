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
ms.workload: dotnet
ms.openlocfilehash: 2af49aab76e82a97aeee92b4799b91011f70c509
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="1d6ff-102">WCF &lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="1d6ff-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="1d6ff-103">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1d6ff-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="1d6ff-104">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1d6ff-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="1d6ff-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1d6ff-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="1d6ff-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="1d6ff-106">\<system.serviceModel></span></span>  
<span data-ttu-id="1d6ff-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="1d6ff-107">\<tracking></span></span>  
<span data-ttu-id="1d6ff-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="1d6ff-108">\<trackingProfile></span></span>  
<span data-ttu-id="1d6ff-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="1d6ff-109">\<workflow></span></span>  
<span data-ttu-id="1d6ff-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="1d6ff-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="1d6ff-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="1d6ff-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d6ff-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d6ff-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1d6ff-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d6ff-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1d6ff-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1d6ff-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d6ff-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1d6ff-115">Attributes</span></span>  
  
|<span data-ttu-id="1d6ff-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1d6ff-116">Attribute</span></span>|<span data-ttu-id="1d6ff-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d6ff-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d6ff-118">activityName</span><span class="sxs-lookup"><span data-stu-id="1d6ff-118">activityName</span></span>|<span data-ttu-id="1d6ff-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="1d6ff-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="1d6ff-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="1d6ff-120">childActivityName</span></span>|<span data-ttu-id="1d6ff-121">İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="1d6ff-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d6ff-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d6ff-122">Child Elements</span></span>  
 <span data-ttu-id="1d6ff-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="1d6ff-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d6ff-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d6ff-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1d6ff-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d6ff-125">Element</span></span>|<span data-ttu-id="1d6ff-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d6ff-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d6ff-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="1d6ff-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="1d6ff-128">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan yapılandırma öğelerinin bir listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1d6ff-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="1d6ff-129">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1d6ff-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d6ff-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d6ff-130">See Also</span></span>  
 <span data-ttu-id="1d6ff-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1d6ff-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="1d6ff-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1d6ff-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>     
 [<span data-ttu-id="1d6ff-133">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="1d6ff-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="1d6ff-134">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="1d6ff-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
