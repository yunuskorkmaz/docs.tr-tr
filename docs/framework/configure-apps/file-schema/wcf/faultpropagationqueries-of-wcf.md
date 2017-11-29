---
title: WCF &lt;faultPropagationQueries&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e122e8c6194545a02f6db429d550eabed5d49b27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a><span data-ttu-id="14240-102">WCF &lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="14240-102">&lt;faultPropagationQueries&gt; of WCF</span></span>
<span data-ttu-id="14240-103">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="14240-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="14240-104">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="14240-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="14240-105">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için bu tür sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="14240-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="14240-106">Sorgu Hatası yayma kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="14240-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="14240-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="14240-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="14240-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="14240-108">\<system.serviceModel></span></span>  
<span data-ttu-id="14240-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="14240-109">\<tracking></span></span>  
<span data-ttu-id="14240-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="14240-110">\<trackingProfile></span></span>  
<span data-ttu-id="14240-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="14240-111">\<workflow></span></span>  
<span data-ttu-id="14240-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="14240-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14240-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14240-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="14240-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="14240-114">Attributes and Elements</span></span>  
 <span data-ttu-id="14240-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="14240-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14240-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="14240-116">Attributes</span></span>  
 <span data-ttu-id="14240-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="14240-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="14240-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="14240-118">Child Elements</span></span>  
  
|<span data-ttu-id="14240-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="14240-119">Element</span></span>|<span data-ttu-id="14240-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14240-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14240-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="14240-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="14240-122">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="14240-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="14240-123">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="14240-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14240-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="14240-124">Parent Elements</span></span>  
  
|<span data-ttu-id="14240-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="14240-125">Element</span></span>|<span data-ttu-id="14240-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14240-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14240-127">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="14240-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="14240-128">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="14240-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14240-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14240-129">See Also</span></span>  
 <span data-ttu-id="14240-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="14240-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="14240-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="14240-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="14240-132">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="14240-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="14240-133">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="14240-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
