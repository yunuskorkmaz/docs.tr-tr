---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: f77a613f4eb0456a0085096aa478d37c78122217
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946309"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="e0151-101">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="e0151-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="e0151-102">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e0151-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e0151-103">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="e0151-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e0151-104">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0151-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e0151-105">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e0151-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="e0151-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e0151-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="e0151-107">\<System. serviceModel > </span><span class="sxs-lookup"><span data-stu-id="e0151-107">\<system.serviceModel></span></span>\
<span data-ttu-id="e0151-108">\<İzleme > </span><span class="sxs-lookup"><span data-stu-id="e0151-108">\<tracking></span></span>\
<span data-ttu-id="e0151-109">\<trackingProfile > </span><span class="sxs-lookup"><span data-stu-id="e0151-109">\<trackingProfile></span></span>\
<span data-ttu-id="e0151-110">\<iş akışı > </span><span class="sxs-lookup"><span data-stu-id="e0151-110">\<workflow></span></span>\
<span data-ttu-id="e0151-111">\<faultPropagationQueries > </span><span class="sxs-lookup"><span data-stu-id="e0151-111">\<faultPropagationQueries></span></span>\
<span data-ttu-id="e0151-112">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="e0151-112">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="e0151-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0151-113">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e0151-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0151-114">Attributes and Elements</span></span>

<span data-ttu-id="e0151-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0151-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0151-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e0151-116">Attributes</span></span>

|<span data-ttu-id="e0151-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e0151-117">Attribute</span></span>|<span data-ttu-id="e0151-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0151-118">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="e0151-119">activityName</span><span class="sxs-lookup"><span data-stu-id="e0151-119">activityName</span></span>|<span data-ttu-id="e0151-120">Hatayı yaydığı hata işleyicisi etkinliğinin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e0151-120">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="e0151-121">Varsayılan değer \*, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0151-121">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="e0151-122">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="e0151-122">faultHandlerActivityName</span></span>|<span data-ttu-id="e0151-123">Hatanın kaynağı olan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e0151-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e0151-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0151-124">Child Elements</span></span>

<span data-ttu-id="e0151-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0151-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e0151-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0151-126">Parent Elements</span></span>

|<span data-ttu-id="e0151-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0151-127">Element</span></span>|<span data-ttu-id="e0151-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0151-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0151-129">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="e0151-129">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="e0151-130">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e0151-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e0151-131">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="e0151-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e0151-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0151-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e0151-133">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="e0151-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e0151-134">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="e0151-134">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
