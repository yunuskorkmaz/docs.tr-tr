---
description: 'Hakkında daha fazla bilgi edinin: <faultPropagationQuery>'
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 08786bfa66d74f5f29353c4d6a86a2abd34df8f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748706"
---
# \<faultPropagationQuery>

<span data-ttu-id="fb37a-102">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb37a-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="fb37a-103">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="fb37a-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="fb37a-104">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb37a-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="fb37a-105">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fb37a-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="fb37a-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="fb37a-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**

## <a name="syntax"></a><span data-ttu-id="fb37a-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="fb37a-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="fb37a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb37a-108">Attributes and Elements</span></span>

<span data-ttu-id="fb37a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fb37a-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="fb37a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fb37a-110">Attributes</span></span>

|<span data-ttu-id="fb37a-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fb37a-111">Attribute</span></span>|<span data-ttu-id="fb37a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb37a-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="fb37a-113">activityName</span><span class="sxs-lookup"><span data-stu-id="fb37a-113">activityName</span></span>|<span data-ttu-id="fb37a-114">Hatayı yaydığı hata işleyicisi etkinliğinin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fb37a-114">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="fb37a-115">Varsayılan değer \*, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb37a-115">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="fb37a-116">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="fb37a-116">faultHandlerActivityName</span></span>|<span data-ttu-id="fb37a-117">Hatanın kaynağı olan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fb37a-117">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="fb37a-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb37a-118">Child Elements</span></span>

<span data-ttu-id="fb37a-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="fb37a-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fb37a-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb37a-120">Parent Elements</span></span>

|<span data-ttu-id="fb37a-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb37a-121">Element</span></span>|<span data-ttu-id="fb37a-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb37a-122">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries.md)|<span data-ttu-id="fb37a-123">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb37a-123">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="fb37a-124">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="fb37a-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="fb37a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb37a-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fb37a-126">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="fb37a-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fb37a-127">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="fb37a-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
