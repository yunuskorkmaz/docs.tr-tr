---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 402b938913575adfa9125b981dc2913680f07b73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790162"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="963de-101">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="963de-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="963de-102">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="963de-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="963de-103">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="963de-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="963de-104">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="963de-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="963de-105">Sorgu hata yayma kayıtlara abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="963de-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="963de-106">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="963de-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="963de-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="963de-107">\<system.serviceModel></span></span>  
<span data-ttu-id="963de-108">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="963de-108">\<tracking></span></span>  
<span data-ttu-id="963de-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="963de-109">\<trackingProfile></span></span>  
<span data-ttu-id="963de-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="963de-110">\<workflow></span></span>  
<span data-ttu-id="963de-111">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="963de-111">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="963de-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="963de-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="963de-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="963de-113">Attributes and Elements</span></span>  
 <span data-ttu-id="963de-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="963de-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="963de-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="963de-115">Attributes</span></span>  
 <span data-ttu-id="963de-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="963de-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="963de-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="963de-117">Child Elements</span></span>  
  
|<span data-ttu-id="963de-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="963de-118">Element</span></span>|<span data-ttu-id="963de-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="963de-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="963de-120">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="963de-120">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="963de-121">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="963de-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="963de-122">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="963de-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="963de-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="963de-123">Parent Elements</span></span>  
  
|<span data-ttu-id="963de-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="963de-124">Element</span></span>|<span data-ttu-id="963de-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="963de-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="963de-126">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="963de-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="963de-127">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="963de-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="963de-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="963de-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="963de-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="963de-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="963de-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="963de-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
