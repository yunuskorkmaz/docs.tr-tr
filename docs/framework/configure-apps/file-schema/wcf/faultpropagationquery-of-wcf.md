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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 650be6a52651f9f55a868d135fd7d0dfa84b967a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="b2bbb-102">WCF &lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="b2bbb-102">&lt;faultPropagationQuery&gt; of WCF</span></span>
<span data-ttu-id="b2bbb-103">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b2bbb-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b2bbb-104">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="b2bbb-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="b2bbb-105">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için bu tür sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2bbb-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="b2bbb-106">Sorgu Hatası yayma kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b2bbb-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="b2bbb-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b2bbb-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="b2bbb-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b2bbb-108">\<system.serviceModel></span></span>  
<span data-ttu-id="b2bbb-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="b2bbb-109">\<tracking></span></span>  
<span data-ttu-id="b2bbb-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b2bbb-110">\<trackingProfile></span></span>  
<span data-ttu-id="b2bbb-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="b2bbb-111">\<workflow></span></span>  
<span data-ttu-id="b2bbb-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="b2bbb-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="b2bbb-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="b2bbb-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2bbb-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2bbb-114">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2bbb-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2bbb-115">Attributes and Elements</span></span>  
 <span data-ttu-id="b2bbb-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2bbb-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2bbb-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b2bbb-117">Attributes</span></span>  
  
|<span data-ttu-id="b2bbb-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b2bbb-118">Attribute</span></span>|<span data-ttu-id="b2bbb-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2bbb-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2bbb-120">activityName</span><span class="sxs-lookup"><span data-stu-id="b2bbb-120">activityName</span></span>|<span data-ttu-id="b2bbb-121">Hataya yayılan hata işleyicisi etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="b2bbb-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="b2bbb-122">Varsayılan değer *, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2bbb-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="b2bbb-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="b2bbb-123">faultHandlerActivityName</span></span>|<span data-ttu-id="b2bbb-124">Hata kaynağı etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="b2bbb-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2bbb-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2bbb-125">Child Elements</span></span>  
 <span data-ttu-id="b2bbb-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="b2bbb-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2bbb-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2bbb-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b2bbb-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="b2bbb-128">Element</span></span>|<span data-ttu-id="b2bbb-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2bbb-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2bbb-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="b2bbb-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="b2bbb-131">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan yapılandırma öğelerinin bir listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b2bbb-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b2bbb-132">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="b2bbb-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2bbb-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2bbb-133">See Also</span></span>  
 <span data-ttu-id="b2bbb-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b2bbb-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b2bbb-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b2bbb-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b2bbb-136">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="b2bbb-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b2bbb-137">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="b2bbb-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
