---
title: <faultPropagationQuery> WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: 1670f8fdf72bc202a4a595034f3818ab43b11be6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276061"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="99af0-102">\<faultPropagationQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="99af0-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="99af0-103">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="99af0-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="99af0-104">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="99af0-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="99af0-105">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="99af0-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="99af0-106">Sorgu hata yayma kayıtlara abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="99af0-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="99af0-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="99af0-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="99af0-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="99af0-108">\<system.serviceModel></span></span>  
<span data-ttu-id="99af0-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="99af0-109">\<tracking></span></span>  
<span data-ttu-id="99af0-110">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="99af0-110">\<profiles></span></span>  
<span data-ttu-id="99af0-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="99af0-111">\<trackingProfile></span></span>  
<span data-ttu-id="99af0-112">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="99af0-112">\<workflow></span></span>  
<span data-ttu-id="99af0-113">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="99af0-113">\<faultPropagationQueries></span></span>  
<span data-ttu-id="99af0-114">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="99af0-114">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99af0-115">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99af0-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99af0-116">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="99af0-116">Attributes and elements</span></span>

<span data-ttu-id="99af0-117">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="99af0-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="99af0-118">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="99af0-118">Attributes</span></span>  
  
|<span data-ttu-id="99af0-119">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="99af0-119">Attribute</span></span>|<span data-ttu-id="99af0-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99af0-120">Description</span></span>|  
|---------------|-----------------|  
|`faultSourceActivityName`|<span data-ttu-id="99af0-121">Hata aktarılacaktır hata işleyicisi etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="99af0-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="99af0-122">Varsayılan \*, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="99af0-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|`faultHandlerActivityName`|<span data-ttu-id="99af0-123">Hata kaynağı olan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="99af0-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99af0-124">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="99af0-124">Child elements</span></span>

<span data-ttu-id="99af0-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="99af0-125">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="99af0-126">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="99af0-126">Parent elements</span></span>  
  
|<span data-ttu-id="99af0-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="99af0-127">Element</span></span>|<span data-ttu-id="99af0-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99af0-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99af0-129">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="99af0-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="99af0-130">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="99af0-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="99af0-131">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="99af0-131">This event occurs each time a FaultHandler processes a fault.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="99af0-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99af0-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="99af0-133">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="99af0-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="99af0-134">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="99af0-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
