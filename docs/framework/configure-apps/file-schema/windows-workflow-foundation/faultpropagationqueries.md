---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: b8052138a729fcba7cb158d81a63126f59e0c4fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69988739"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="ddef3-101">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="ddef3-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="ddef3-102">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ddef3-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ddef3-103">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="ddef3-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="ddef3-104">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ddef3-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="ddef3-105">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ddef3-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="ddef3-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ddef3-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ddef3-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ddef3-107">\<system.serviceModel></span></span>  
<span data-ttu-id="ddef3-108">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="ddef3-108">\<tracking></span></span>  
<span data-ttu-id="ddef3-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ddef3-109">\<trackingProfile></span></span>  
<span data-ttu-id="ddef3-110">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="ddef3-110">\<workflow></span></span>  
<span data-ttu-id="ddef3-111">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="ddef3-111">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddef3-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ddef3-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddef3-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddef3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ddef3-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ddef3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddef3-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ddef3-115">Attributes</span></span>  
 <span data-ttu-id="ddef3-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="ddef3-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ddef3-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddef3-117">Child Elements</span></span>  
  
|<span data-ttu-id="ddef3-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="ddef3-118">Element</span></span>|<span data-ttu-id="ddef3-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddef3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddef3-120">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="ddef3-120">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="ddef3-121">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="ddef3-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ddef3-122">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="ddef3-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ddef3-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddef3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ddef3-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="ddef3-124">Element</span></span>|<span data-ttu-id="ddef3-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddef3-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddef3-126">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="ddef3-126">\<workflow></span></span>](workflow.md)|<span data-ttu-id="ddef3-127">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ddef3-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ddef3-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddef3-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ddef3-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="ddef3-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ddef3-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="ddef3-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
