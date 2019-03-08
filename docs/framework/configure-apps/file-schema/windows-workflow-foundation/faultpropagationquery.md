---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: f3e281ff8a9de9be41dd6ad9d01ab52798d8e89e
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679365"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="c1599-101">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="c1599-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="c1599-102">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c1599-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c1599-103">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="c1599-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="c1599-104">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1599-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="c1599-105">Sorgu hata yayma kayıtlara abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c1599-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="c1599-106">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c1599-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="c1599-107">\<system.serviceModel > \\</span><span class="sxs-lookup"><span data-stu-id="c1599-107">\<system.serviceModel>\\</span></span>
<span data-ttu-id="c1599-108">\<İzleme > \\</span><span class="sxs-lookup"><span data-stu-id="c1599-108">\<tracking>\\</span></span>
<span data-ttu-id="c1599-109">\<trackingProfile > \\</span><span class="sxs-lookup"><span data-stu-id="c1599-109">\<trackingProfile>\\</span></span>
<span data-ttu-id="c1599-110">\<İş akışı > \\</span><span class="sxs-lookup"><span data-stu-id="c1599-110">\<workflow>\\</span></span>
<span data-ttu-id="c1599-111">\<faultPropagationQueries > \\</span><span class="sxs-lookup"><span data-stu-id="c1599-111">\<faultPropagationQueries>\\</span></span>
<span data-ttu-id="c1599-112">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="c1599-112">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="c1599-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1599-113">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="c1599-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1599-114">Attributes and Elements</span></span>

<span data-ttu-id="c1599-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c1599-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1599-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c1599-116">Attributes</span></span>

|<span data-ttu-id="c1599-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c1599-117">Attribute</span></span>|<span data-ttu-id="c1599-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1599-118">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c1599-119">activityName</span><span class="sxs-lookup"><span data-stu-id="c1599-119">activityName</span></span>|<span data-ttu-id="c1599-120">Hata aktarılacaktır hata işleyicisi etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="c1599-120">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="c1599-121">Varsayılan değer \*, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1599-121">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="c1599-122">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="c1599-122">faultHandlerActivityName</span></span>|<span data-ttu-id="c1599-123">Hata kaynağı olan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="c1599-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c1599-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1599-124">Child Elements</span></span>

<span data-ttu-id="c1599-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="c1599-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c1599-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1599-126">Parent Elements</span></span>

|<span data-ttu-id="c1599-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="c1599-127">Element</span></span>|<span data-ttu-id="c1599-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1599-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1599-129">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="c1599-129">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="c1599-130">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c1599-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c1599-131">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="c1599-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c1599-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1599-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c1599-133">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c1599-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c1599-134">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c1599-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
