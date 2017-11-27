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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 58196baafe92cd34986acbfae9e44ade3212cb33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltfaultpropagationqueriesgt"></a><span data-ttu-id="4539b-102">&lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="4539b-102">&lt;faultPropagationQueries&gt;</span></span>
<span data-ttu-id="4539b-103">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4539b-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="4539b-104">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="4539b-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="4539b-105">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için bu tür sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4539b-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="4539b-106">Sorgu Hatası yayma kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4539b-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="4539b-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4539b-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="4539b-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="4539b-108">\<system.serviceModel></span></span>  
<span data-ttu-id="4539b-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="4539b-109">\<tracking></span></span>  
<span data-ttu-id="4539b-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="4539b-110">\<trackingProfile></span></span>  
<span data-ttu-id="4539b-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="4539b-111">\<workflow></span></span>  
<span data-ttu-id="4539b-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="4539b-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4539b-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4539b-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4539b-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4539b-114">Attributes and Elements</span></span>  
 <span data-ttu-id="4539b-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4539b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4539b-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4539b-116">Attributes</span></span>  
 <span data-ttu-id="4539b-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="4539b-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4539b-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4539b-118">Child Elements</span></span>  
  
|<span data-ttu-id="4539b-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="4539b-119">Element</span></span>|<span data-ttu-id="4539b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4539b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4539b-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="4539b-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="4539b-122">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="4539b-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="4539b-123">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="4539b-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4539b-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4539b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4539b-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="4539b-125">Element</span></span>|<span data-ttu-id="4539b-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4539b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4539b-127">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="4539b-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="4539b-128">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="4539b-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4539b-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4539b-129">See Also</span></span>  
 <span data-ttu-id="4539b-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4539b-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="4539b-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4539b-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="4539b-132">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="4539b-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="4539b-133">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="4539b-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
