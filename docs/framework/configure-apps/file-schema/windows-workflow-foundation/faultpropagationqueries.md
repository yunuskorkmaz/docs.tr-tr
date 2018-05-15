---
title: '&lt;faultPropagationQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 5fd6ffc9560247089c7fbb60b0e5a7d3a417ea6f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltfaultpropagationqueriesgt"></a><span data-ttu-id="177e2-102">&lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="177e2-102">&lt;faultPropagationQueries&gt;</span></span>
<span data-ttu-id="177e2-103">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="177e2-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="177e2-104">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="177e2-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="177e2-105">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için bu tür sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="177e2-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="177e2-106">Sorgu Hatası yayma kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="177e2-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="177e2-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="177e2-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="177e2-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="177e2-108">\<system.serviceModel></span></span>  
<span data-ttu-id="177e2-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="177e2-109">\<tracking></span></span>  
<span data-ttu-id="177e2-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="177e2-110">\<trackingProfile></span></span>  
<span data-ttu-id="177e2-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="177e2-111">\<workflow></span></span>  
<span data-ttu-id="177e2-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="177e2-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="177e2-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="177e2-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="177e2-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="177e2-114">Attributes and Elements</span></span>  
 <span data-ttu-id="177e2-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="177e2-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="177e2-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="177e2-116">Attributes</span></span>  
 <span data-ttu-id="177e2-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="177e2-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="177e2-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="177e2-118">Child Elements</span></span>  
  
|<span data-ttu-id="177e2-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="177e2-119">Element</span></span>|<span data-ttu-id="177e2-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="177e2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="177e2-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="177e2-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="177e2-122">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="177e2-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="177e2-123">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="177e2-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="177e2-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="177e2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="177e2-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="177e2-125">Element</span></span>|<span data-ttu-id="177e2-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="177e2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="177e2-127">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="177e2-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="177e2-128">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="177e2-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="177e2-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="177e2-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="177e2-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="177e2-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="177e2-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="177e2-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
