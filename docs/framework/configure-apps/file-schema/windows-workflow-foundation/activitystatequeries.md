---
title: '&lt;activityStateQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: c215380530acef630ff99dc24e2fc9cf35bbd3d4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755480"
---
# <a name="ltactivitystatequeriesgt"></a><span data-ttu-id="02b56-102">&lt;activityStateQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="02b56-102">&lt;activityStateQueries&gt;</span></span>
<span data-ttu-id="02b56-103">Bir iş akışı örneği olun etkinliklerin ömrünü değişiklikleri izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="02b56-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="02b56-104">Örneğin, bir iş akışı örneği içinde "E-posta Gönder" etkinlik tamamlandıktan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02b56-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="02b56-105">Bu sorgu, etkinlik durumu kaydı nesnelere abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="02b56-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="02b56-106">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="02b56-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="02b56-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="02b56-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="02b56-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="02b56-108">\<system.serviceModel></span></span>  
<span data-ttu-id="02b56-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="02b56-109">\<tracking></span></span>  
<span data-ttu-id="02b56-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="02b56-110">\<trackingProfile></span></span>  
<span data-ttu-id="02b56-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="02b56-111">\<workflow></span></span>  
<span data-ttu-id="02b56-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="02b56-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02b56-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02b56-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02b56-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="02b56-114">Attributes and Elements</span></span>  
 <span data-ttu-id="02b56-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="02b56-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02b56-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="02b56-116">Attributes</span></span>  
 <span data-ttu-id="02b56-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="02b56-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="02b56-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="02b56-118">Child Elements</span></span>  
  
|<span data-ttu-id="02b56-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="02b56-119">Element</span></span>|<span data-ttu-id="02b56-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02b56-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02b56-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="02b56-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="02b56-122">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="02b56-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="02b56-123">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="02b56-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02b56-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="02b56-124">Parent Elements</span></span>  
  
|<span data-ttu-id="02b56-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="02b56-125">Element</span></span>|<span data-ttu-id="02b56-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02b56-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02b56-127">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="02b56-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="02b56-128">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="02b56-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02b56-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02b56-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="02b56-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="02b56-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="02b56-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="02b56-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
