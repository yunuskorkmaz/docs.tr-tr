---
title: '&lt;faultPropagationQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 546b37279c8ba58f9dd9f07dabacb7af602ff232
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610064"
---
# <a name="ltfaultpropagationqueriesgt"></a><span data-ttu-id="c50bd-102">&lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="c50bd-102">&lt;faultPropagationQueries&gt;</span></span>
<span data-ttu-id="c50bd-103">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c50bd-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c50bd-104">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="c50bd-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="c50bd-105">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c50bd-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="c50bd-106">Sorgu hata yayma kayıtlara abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c50bd-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="c50bd-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c50bd-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="c50bd-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c50bd-108">\<system.serviceModel></span></span>  
<span data-ttu-id="c50bd-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="c50bd-109">\<tracking></span></span>  
<span data-ttu-id="c50bd-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c50bd-110">\<trackingProfile></span></span>  
<span data-ttu-id="c50bd-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="c50bd-111">\<workflow></span></span>  
<span data-ttu-id="c50bd-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="c50bd-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c50bd-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c50bd-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c50bd-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c50bd-114">Attributes and Elements</span></span>  
 <span data-ttu-id="c50bd-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c50bd-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c50bd-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c50bd-116">Attributes</span></span>  
 <span data-ttu-id="c50bd-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="c50bd-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c50bd-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c50bd-118">Child Elements</span></span>  
  
|<span data-ttu-id="c50bd-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="c50bd-119">Element</span></span>|<span data-ttu-id="c50bd-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c50bd-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c50bd-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="c50bd-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="c50bd-122">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="c50bd-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c50bd-123">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="c50bd-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c50bd-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c50bd-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c50bd-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c50bd-125">Element</span></span>|<span data-ttu-id="c50bd-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c50bd-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c50bd-127">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="c50bd-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c50bd-128">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="c50bd-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c50bd-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c50bd-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c50bd-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c50bd-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c50bd-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c50bd-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
