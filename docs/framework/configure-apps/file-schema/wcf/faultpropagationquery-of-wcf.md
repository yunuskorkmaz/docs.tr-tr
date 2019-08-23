---
title: <faultPropagationQuery>WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: 6ba6478ca500c0a8ef150966a97898f8743ffdf8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925627"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="80103-102">\<WCF > faultPropagationQuery</span><span class="sxs-lookup"><span data-stu-id="80103-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="80103-103">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="80103-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="80103-104">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="80103-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="80103-105">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="80103-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="80103-106">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="80103-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="80103-107">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="80103-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="80103-108">\<System. serviceModel > </span><span class="sxs-lookup"><span data-stu-id="80103-108">\<system.serviceModel></span></span>\
<span data-ttu-id="80103-109">\<İzleme > </span><span class="sxs-lookup"><span data-stu-id="80103-109">\<tracking></span></span>\
<span data-ttu-id="80103-110">\<Profiller > </span><span class="sxs-lookup"><span data-stu-id="80103-110">\<profiles></span></span>\
<span data-ttu-id="80103-111">\<trackingProfile > </span><span class="sxs-lookup"><span data-stu-id="80103-111">\<trackingProfile></span></span>\
<span data-ttu-id="80103-112">\<iş akışı > </span><span class="sxs-lookup"><span data-stu-id="80103-112">\<workflow></span></span>\
<span data-ttu-id="80103-113">\<faultPropagationQueries > </span><span class="sxs-lookup"><span data-stu-id="80103-113">\<faultPropagationQueries></span></span>\
<span data-ttu-id="80103-114">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="80103-114">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="80103-115">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80103-115">Syntax</span></span>

```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String" />
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80103-116">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="80103-116">Attributes and elements</span></span>

<span data-ttu-id="80103-117">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80103-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="80103-118">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="80103-118">Attributes</span></span>

|<span data-ttu-id="80103-119">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="80103-119">Attribute</span></span>|<span data-ttu-id="80103-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80103-120">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="80103-121">Hatayı yaydığı hata işleyicisi etkinliğinin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="80103-121">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="80103-122">Varsayılan değer \*, tüm etkinlikler için hata yayma kayıtlarının döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="80103-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="80103-123">Hatanın kaynağı olan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="80103-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="80103-124">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="80103-124">Child elements</span></span>

<span data-ttu-id="80103-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="80103-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="80103-126">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="80103-126">Parent elements</span></span>

|<span data-ttu-id="80103-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="80103-127">Element</span></span>|<span data-ttu-id="80103-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80103-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80103-129">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="80103-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="80103-130">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="80103-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="80103-131">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="80103-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="80103-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80103-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="80103-133">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="80103-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="80103-134">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="80103-134">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
