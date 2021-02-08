---
description: WCF hakkında daha fazla bilgi edinin <faultPropagationQuery>
title: <faultPropagationQuery> WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: cd26bf76fec54371ef0455b93c98650bdab19068
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782071"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="e0259-103">\<faultPropagationQuery> WCF</span><span class="sxs-lookup"><span data-stu-id="e0259-103">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="e0259-104">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e0259-104">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e0259-105">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="e0259-105">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e0259-106">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0259-106">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e0259-107">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e0259-107">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="e0259-108">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e0259-108">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**  

## <a name="syntax"></a><span data-ttu-id="e0259-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0259-109">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e0259-110">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="e0259-110">Attributes and elements</span></span>

<span data-ttu-id="e0259-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0259-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0259-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e0259-112">Attributes</span></span>

|<span data-ttu-id="e0259-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e0259-113">Attribute</span></span>|<span data-ttu-id="e0259-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0259-114">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="e0259-115">Hatayı yaydığı hata işleyicisi etkinliğinin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e0259-115">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="e0259-116">Varsayılan değer \* , tüm etkinlikler için hata yayma kayıtlarının döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0259-116">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="e0259-117">Hatanın kaynağı olan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e0259-117">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e0259-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e0259-118">Child elements</span></span>

<span data-ttu-id="e0259-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0259-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e0259-120">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="e0259-120">Parent elements</span></span>

|<span data-ttu-id="e0259-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0259-121">Element</span></span>|<span data-ttu-id="e0259-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0259-122">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="e0259-123">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e0259-123">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e0259-124">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="e0259-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e0259-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0259-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e0259-126">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="e0259-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e0259-127">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="e0259-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
