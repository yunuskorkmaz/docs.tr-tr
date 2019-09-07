---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 6b43a570b4d4534adce1ef5ab394849651e3ac0e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398725"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="1f56b-101">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="1f56b-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="1f56b-102">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1f56b-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="1f56b-103">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="1f56b-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="1f56b-104">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f56b-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="1f56b-105">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1f56b-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="1f56b-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1f56b-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="1f56b-107">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f56b-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1f56b-108">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="1f56b-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="1f56b-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="1f56b-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="1f56b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="1f56b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="1f56b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="1f56b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="1f56b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<faultPropagationQueries >** ](faultpropagationqueries.md)</span><span class="sxs-lookup"><span data-stu-id="1f56b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)</span></span>\
<span data-ttu-id="1f56b-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQuery >**</span><span class="sxs-lookup"><span data-stu-id="1f56b-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1f56b-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f56b-114">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="1f56b-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f56b-115">Attributes and Elements</span></span>

<span data-ttu-id="1f56b-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f56b-116">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f56b-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1f56b-117">Attributes</span></span>

|<span data-ttu-id="1f56b-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1f56b-118">Attribute</span></span>|<span data-ttu-id="1f56b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f56b-119">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="1f56b-120">activityName</span><span class="sxs-lookup"><span data-stu-id="1f56b-120">activityName</span></span>|<span data-ttu-id="1f56b-121">Hatayı yaydığı hata işleyicisi etkinliğinin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="1f56b-121">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="1f56b-122">Varsayılan değer \*, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f56b-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="1f56b-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="1f56b-123">faultHandlerActivityName</span></span>|<span data-ttu-id="1f56b-124">Hatanın kaynağı olan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="1f56b-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1f56b-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f56b-125">Child Elements</span></span>

<span data-ttu-id="1f56b-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="1f56b-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f56b-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f56b-127">Parent Elements</span></span>

|<span data-ttu-id="1f56b-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="1f56b-128">Element</span></span>|<span data-ttu-id="1f56b-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f56b-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f56b-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="1f56b-130">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="1f56b-131">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1f56b-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="1f56b-132">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="1f56b-132">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="1f56b-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f56b-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1f56b-134">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="1f56b-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1f56b-135">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="1f56b-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
