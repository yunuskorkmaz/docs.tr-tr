---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: f3e281ff8a9de9be41dd6ad9d01ab52798d8e89e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794556"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="c116e-101">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="c116e-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="c116e-102">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c116e-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c116e-103">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="c116e-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="c116e-104">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c116e-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="c116e-105">Sorgu hata yayma kayıtlara abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c116e-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="c116e-106">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c116e-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="c116e-107">\<system.serviceModel > \\</span><span class="sxs-lookup"><span data-stu-id="c116e-107">\<system.serviceModel>\\</span></span>
<span data-ttu-id="c116e-108">\<İzleme > \\</span><span class="sxs-lookup"><span data-stu-id="c116e-108">\<tracking>\\</span></span>
<span data-ttu-id="c116e-109">\<trackingProfile > \\</span><span class="sxs-lookup"><span data-stu-id="c116e-109">\<trackingProfile>\\</span></span>
<span data-ttu-id="c116e-110">\<İş akışı > \\</span><span class="sxs-lookup"><span data-stu-id="c116e-110">\<workflow>\\</span></span>
<span data-ttu-id="c116e-111">\<faultPropagationQueries > \\</span><span class="sxs-lookup"><span data-stu-id="c116e-111">\<faultPropagationQueries>\\</span></span>
<span data-ttu-id="c116e-112">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="c116e-112">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="c116e-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c116e-113">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="c116e-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c116e-114">Attributes and Elements</span></span>

<span data-ttu-id="c116e-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c116e-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c116e-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c116e-116">Attributes</span></span>

|<span data-ttu-id="c116e-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c116e-117">Attribute</span></span>|<span data-ttu-id="c116e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c116e-118">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c116e-119">activityName</span><span class="sxs-lookup"><span data-stu-id="c116e-119">activityName</span></span>|<span data-ttu-id="c116e-120">Hata aktarılacaktır hata işleyicisi etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="c116e-120">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="c116e-121">Varsayılan değer \*, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c116e-121">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="c116e-122">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="c116e-122">faultHandlerActivityName</span></span>|<span data-ttu-id="c116e-123">Hata kaynağı olan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="c116e-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c116e-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c116e-124">Child Elements</span></span>

<span data-ttu-id="c116e-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="c116e-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c116e-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c116e-126">Parent Elements</span></span>

|<span data-ttu-id="c116e-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="c116e-127">Element</span></span>|<span data-ttu-id="c116e-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c116e-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c116e-129">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="c116e-129">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="c116e-130">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c116e-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c116e-131">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="c116e-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c116e-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c116e-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c116e-133">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c116e-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c116e-134">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c116e-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
