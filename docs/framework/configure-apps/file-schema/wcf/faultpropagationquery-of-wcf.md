---
title: <faultPropagationQuery>WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: a6ef4e198caec4a1f21cedf2ff46d390aeaa2d3b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855337"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="68e58-102">\<WCF > faultPropagationQuery</span><span class="sxs-lookup"><span data-stu-id="68e58-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="68e58-103">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="68e58-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="68e58-104">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="68e58-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="68e58-105">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="68e58-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="68e58-106">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="68e58-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="68e58-107">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="68e58-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="68e58-108">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="68e58-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="68e58-109">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="68e58-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="68e58-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="68e58-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="68e58-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="68e58-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="68e58-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="68e58-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="68e58-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="68e58-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="68e58-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<faultPropagationQueries >** ](faultpropagationqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="68e58-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)</span></span>\
<span data-ttu-id="68e58-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQuery >**</span><span class="sxs-lookup"><span data-stu-id="68e58-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="68e58-116">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68e58-116">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="68e58-117">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="68e58-117">Attributes and elements</span></span>

<span data-ttu-id="68e58-118">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68e58-118">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="68e58-119">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="68e58-119">Attributes</span></span>

|<span data-ttu-id="68e58-120">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="68e58-120">Attribute</span></span>|<span data-ttu-id="68e58-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68e58-121">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="68e58-122">Hatayı yaydığı hata işleyicisi etkinliğinin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="68e58-122">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="68e58-123">Varsayılan değer \*, tüm etkinlikler için hata yayma kayıtlarının döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="68e58-123">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="68e58-124">Hatanın kaynağı olan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="68e58-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="68e58-125">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="68e58-125">Child elements</span></span>

<span data-ttu-id="68e58-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="68e58-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="68e58-127">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="68e58-127">Parent elements</span></span>

|<span data-ttu-id="68e58-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="68e58-128">Element</span></span>|<span data-ttu-id="68e58-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68e58-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68e58-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="68e58-130">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="68e58-131">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="68e58-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="68e58-132">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="68e58-132">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="68e58-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68e58-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="68e58-134">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="68e58-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="68e58-135">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="68e58-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
