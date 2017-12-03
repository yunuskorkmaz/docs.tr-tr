---
title: WFC &lt;activityStateQueries&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ec6cb2d077f95f53a2ee0daf8e2819ae91cb13b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a><span data-ttu-id="7e66c-102">WFC &lt;activityStateQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="7e66c-102">&lt;activityStateQueries&gt; of WCF</span></span>
<span data-ttu-id="7e66c-103">Bir iş akışı örneği olun etkinliklerin ömrünü değişiklikleri izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7e66c-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="7e66c-104">Örneğin, bir iş akışı örneği içinde "E-posta Gönder" etkinlik tamamlandıktan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e66c-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="7e66c-105">Bu sorgu, etkinlik durumu kaydı nesnelere abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7e66c-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="7e66c-106">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="7e66c-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="7e66c-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="7e66c-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="7e66c-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7e66c-108">\<system.serviceModel></span></span>  
<span data-ttu-id="7e66c-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="7e66c-109">\<tracking></span></span>  
<span data-ttu-id="7e66c-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="7e66c-110">\<trackingProfile></span></span>  
<span data-ttu-id="7e66c-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="7e66c-111">\<workflow></span></span>  
<span data-ttu-id="7e66c-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="7e66c-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e66c-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e66c-113">Syntax</span></span>  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e66c-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e66c-114">Attributes and Elements</span></span>  
 <span data-ttu-id="7e66c-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7e66c-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e66c-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7e66c-116">Attributes</span></span>  
 <span data-ttu-id="7e66c-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="7e66c-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7e66c-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e66c-118">Child Elements</span></span>  
  
|<span data-ttu-id="7e66c-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="7e66c-119">Element</span></span>|<span data-ttu-id="7e66c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e66c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e66c-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="7e66c-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="7e66c-122">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="7e66c-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="7e66c-123">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="7e66c-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e66c-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e66c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7e66c-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="7e66c-125">Element</span></span>|<span data-ttu-id="7e66c-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e66c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e66c-127">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="7e66c-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="7e66c-128">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="7e66c-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e66c-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e66c-129">See Also</span></span>  
 <span data-ttu-id="7e66c-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="7e66c-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection></span></span>    
 <span data-ttu-id="7e66c-131"><xref:System.Activities.Tracking.ActivityStateQuery></span><span class="sxs-lookup"><span data-stu-id="7e66c-131"><xref:System.Activities.Tracking.ActivityStateQuery></span></span>    
 [<span data-ttu-id="7e66c-132">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="7e66c-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="7e66c-133">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="7e66c-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
