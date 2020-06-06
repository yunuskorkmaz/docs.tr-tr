---
title: <faultPropagationQuery>WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: a6ef4e198caec4a1f21cedf2ff46d390aeaa2d3b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855337"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="e608a-102">\<faultPropagationQuery>WCF</span><span class="sxs-lookup"><span data-stu-id="e608a-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="e608a-103">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e608a-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e608a-104">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="e608a-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e608a-105">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e608a-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e608a-106">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e608a-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="e608a-107">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e608a-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**  

## <a name="syntax"></a><span data-ttu-id="e608a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e608a-108">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e608a-109">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="e608a-109">Attributes and elements</span></span>

<span data-ttu-id="e608a-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e608a-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e608a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e608a-111">Attributes</span></span>

|<span data-ttu-id="e608a-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e608a-112">Attribute</span></span>|<span data-ttu-id="e608a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e608a-113">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="e608a-114">Hatayı yaydığı hata işleyicisi etkinliğinin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e608a-114">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="e608a-115">Varsayılan değer \* , tüm etkinlikler için hata yayma kayıtlarının döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="e608a-115">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="e608a-116">Hatanın kaynağı olan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e608a-116">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e608a-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e608a-117">Child elements</span></span>

<span data-ttu-id="e608a-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="e608a-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e608a-119">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="e608a-119">Parent elements</span></span>

|<span data-ttu-id="e608a-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="e608a-120">Element</span></span>|<span data-ttu-id="e608a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e608a-121">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="e608a-122">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e608a-122">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e608a-123">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="e608a-123">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e608a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e608a-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e608a-125">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="e608a-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e608a-126">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="e608a-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
