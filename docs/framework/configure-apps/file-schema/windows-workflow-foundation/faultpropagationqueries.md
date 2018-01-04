---
title: '&lt;faultPropagationQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da7cf3a439e365c3ee087ffa1739c96041777e98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfaultpropagationqueriesgt"></a><span data-ttu-id="e1396-102">&lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="e1396-102">&lt;faultPropagationQueries&gt;</span></span>
<span data-ttu-id="e1396-103">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e1396-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e1396-104">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="e1396-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e1396-105">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için bu tür sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1396-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e1396-106">Sorgu Hatası yayma kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e1396-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="e1396-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e1396-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e1396-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e1396-108">\<system.serviceModel></span></span>  
<span data-ttu-id="e1396-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="e1396-109">\<tracking></span></span>  
<span data-ttu-id="e1396-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e1396-110">\<trackingProfile></span></span>  
<span data-ttu-id="e1396-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="e1396-111">\<workflow></span></span>  
<span data-ttu-id="e1396-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="e1396-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1396-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1396-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1396-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1396-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e1396-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e1396-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1396-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e1396-116">Attributes</span></span>  
 <span data-ttu-id="e1396-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="e1396-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e1396-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1396-118">Child Elements</span></span>  
  
|<span data-ttu-id="e1396-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="e1396-119">Element</span></span>|<span data-ttu-id="e1396-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1396-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1396-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="e1396-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="e1396-122">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="e1396-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e1396-123">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="e1396-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e1396-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1396-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e1396-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="e1396-125">Element</span></span>|<span data-ttu-id="e1396-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1396-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1396-127">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="e1396-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e1396-128">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="e1396-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1396-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1396-129">See Also</span></span>  
 <span data-ttu-id="e1396-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e1396-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e1396-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e1396-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="e1396-132">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="e1396-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e1396-133">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="e1396-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
