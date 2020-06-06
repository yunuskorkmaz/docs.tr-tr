---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 6b43a570b4d4534adce1ef5ab394849651e3ac0e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398725"
---
# \<faultPropagationQuery>

<span data-ttu-id="93bfd-101">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="93bfd-101">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="93bfd-102">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="93bfd-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="93bfd-103">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="93bfd-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="93bfd-104">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="93bfd-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="93bfd-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="93bfd-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**

## <a name="syntax"></a><span data-ttu-id="93bfd-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93bfd-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="93bfd-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="93bfd-107">Attributes and Elements</span></span>

<span data-ttu-id="93bfd-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="93bfd-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="93bfd-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="93bfd-109">Attributes</span></span>

|<span data-ttu-id="93bfd-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="93bfd-110">Attribute</span></span>|<span data-ttu-id="93bfd-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93bfd-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="93bfd-112">activityName</span><span class="sxs-lookup"><span data-stu-id="93bfd-112">activityName</span></span>|<span data-ttu-id="93bfd-113">Hatayı yaydığı hata işleyicisi etkinliğinin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="93bfd-113">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="93bfd-114">Varsayılan değer \*, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="93bfd-114">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="93bfd-115">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="93bfd-115">faultHandlerActivityName</span></span>|<span data-ttu-id="93bfd-116">Hatanın kaynağı olan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="93bfd-116">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="93bfd-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="93bfd-117">Child Elements</span></span>

<span data-ttu-id="93bfd-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="93bfd-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="93bfd-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="93bfd-119">Parent Elements</span></span>

|<span data-ttu-id="93bfd-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="93bfd-120">Element</span></span>|<span data-ttu-id="93bfd-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93bfd-121">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries.md)|<span data-ttu-id="93bfd-122">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="93bfd-122">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="93bfd-123">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="93bfd-123">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="93bfd-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93bfd-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="93bfd-125">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="93bfd-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="93bfd-126">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="93bfd-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
