---
title: WCF &lt;faultPropagationQuery&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f017b695b91a08c1126b48c944977c054c73affe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="239d9-102">WCF &lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="239d9-102">&lt;faultPropagationQuery&gt; of WCF</span></span>
<span data-ttu-id="239d9-103">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="239d9-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="239d9-104">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="239d9-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="239d9-105">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için bu tür sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="239d9-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="239d9-106">Sorgu Hatası yayma kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="239d9-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="239d9-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="239d9-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="239d9-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="239d9-108">\<system.serviceModel></span></span>  
<span data-ttu-id="239d9-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="239d9-109">\<tracking></span></span>  
<span data-ttu-id="239d9-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="239d9-110">\<trackingProfile></span></span>  
<span data-ttu-id="239d9-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="239d9-111">\<workflow></span></span>  
<span data-ttu-id="239d9-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="239d9-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="239d9-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="239d9-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="239d9-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="239d9-114">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="239d9-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="239d9-115">Attributes and Elements</span></span>  
 <span data-ttu-id="239d9-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="239d9-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="239d9-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="239d9-117">Attributes</span></span>  
  
|<span data-ttu-id="239d9-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="239d9-118">Attribute</span></span>|<span data-ttu-id="239d9-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="239d9-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="239d9-120">activityName</span><span class="sxs-lookup"><span data-stu-id="239d9-120">activityName</span></span>|<span data-ttu-id="239d9-121">Hataya yayılan hata işleyicisi etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="239d9-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="239d9-122">Varsayılan değer *, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="239d9-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="239d9-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="239d9-123">faultHandlerActivityName</span></span>|<span data-ttu-id="239d9-124">Hata kaynağı etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="239d9-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="239d9-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="239d9-125">Child Elements</span></span>  
 <span data-ttu-id="239d9-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="239d9-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="239d9-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="239d9-127">Parent Elements</span></span>  
  
|<span data-ttu-id="239d9-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="239d9-128">Element</span></span>|<span data-ttu-id="239d9-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="239d9-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="239d9-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="239d9-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="239d9-131">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan yapılandırma öğelerinin bir listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="239d9-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="239d9-132">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="239d9-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="239d9-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="239d9-133">See Also</span></span>  
 <span data-ttu-id="239d9-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="239d9-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="239d9-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="239d9-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="239d9-136">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="239d9-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="239d9-137">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="239d9-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
