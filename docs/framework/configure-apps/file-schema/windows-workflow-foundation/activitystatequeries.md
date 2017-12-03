---
title: '&lt;activityStateQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 175089dad7809e412444681076163163bd6831e7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivitystatequeriesgt"></a><span data-ttu-id="7ae0f-102">&lt;activityStateQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="7ae0f-102">&lt;activityStateQueries&gt;</span></span>
<span data-ttu-id="7ae0f-103">Bir iş akışı örneği olun etkinliklerin ömrünü değişiklikleri izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7ae0f-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="7ae0f-104">Örneğin, bir iş akışı örneği içinde "E-posta Gönder" etkinlik tamamlandıktan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ae0f-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="7ae0f-105">Bu sorgu, etkinlik durumu kaydı nesnelere abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7ae0f-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="7ae0f-106">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="7ae0f-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="7ae0f-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="7ae0f-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="7ae0f-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7ae0f-108">\<system.serviceModel></span></span>  
<span data-ttu-id="7ae0f-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="7ae0f-109">\<tracking></span></span>  
<span data-ttu-id="7ae0f-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="7ae0f-110">\<trackingProfile></span></span>  
<span data-ttu-id="7ae0f-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="7ae0f-111">\<workflow></span></span>  
<span data-ttu-id="7ae0f-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="7ae0f-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ae0f-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ae0f-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ae0f-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ae0f-114">Attributes and Elements</span></span>  
 <span data-ttu-id="7ae0f-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7ae0f-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ae0f-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7ae0f-116">Attributes</span></span>  
 <span data-ttu-id="7ae0f-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="7ae0f-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7ae0f-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ae0f-118">Child Elements</span></span>  
  
|<span data-ttu-id="7ae0f-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="7ae0f-119">Element</span></span>|<span data-ttu-id="7ae0f-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ae0f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ae0f-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="7ae0f-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="7ae0f-122">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="7ae0f-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="7ae0f-123">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="7ae0f-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7ae0f-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ae0f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7ae0f-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="7ae0f-125">Element</span></span>|<span data-ttu-id="7ae0f-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ae0f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ae0f-127">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="7ae0f-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="7ae0f-128">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="7ae0f-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ae0f-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ae0f-129">See Also</span></span>  
 <span data-ttu-id="7ae0f-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7ae0f-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="7ae0f-131"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7ae0f-131"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="7ae0f-132">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="7ae0f-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="7ae0f-133">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="7ae0f-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
