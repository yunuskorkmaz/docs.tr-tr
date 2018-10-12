---
title: WCF &lt;faultPropagationQuery&gt;
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: c3853c470a9243835e071d35008dfff5b885591d
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123325"
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="0be32-102">WCF &lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="0be32-102">&lt;faultPropagationQuery&gt; of WCF</span></span>

<span data-ttu-id="0be32-103">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0be32-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="0be32-104">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="0be32-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="0be32-105">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0be32-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="0be32-106">Sorgu hata yayma kayıtlara abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0be32-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="0be32-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="0be32-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="0be32-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0be32-108">\<system.serviceModel></span></span>  
<span data-ttu-id="0be32-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="0be32-109">\<tracking></span></span>  
<span data-ttu-id="0be32-110">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="0be32-110">\<profiles></span></span>  
<span data-ttu-id="0be32-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="0be32-111">\<trackingProfile></span></span>  
<span data-ttu-id="0be32-112">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="0be32-112">\<workflow></span></span>  
<span data-ttu-id="0be32-113">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="0be32-113">\<faultPropagationQueries></span></span>  
<span data-ttu-id="0be32-114">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="0be32-114">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0be32-115">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0be32-115">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0be32-116">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="0be32-116">Attributes and elements</span></span>

<span data-ttu-id="0be32-117">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0be32-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0be32-118">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0be32-118">Attributes</span></span>  
  
|<span data-ttu-id="0be32-119">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0be32-119">Attribute</span></span>|<span data-ttu-id="0be32-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0be32-120">Description</span></span>|  
|---------------|-----------------|  
|`faultSourceActivityName`|<span data-ttu-id="0be32-121">Hata aktarılacaktır hata işleyicisi etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="0be32-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="0be32-122">Varsayılan \*, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0be32-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|`faultHandlerActivityName`|<span data-ttu-id="0be32-123">Hata kaynağı olan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="0be32-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0be32-124">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="0be32-124">Child elements</span></span>

<span data-ttu-id="0be32-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="0be32-125">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="0be32-126">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="0be32-126">Parent elements</span></span>  
  
|<span data-ttu-id="0be32-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="0be32-127">Element</span></span>|<span data-ttu-id="0be32-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0be32-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0be32-129">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="0be32-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="0be32-130">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0be32-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="0be32-131">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="0be32-131">This event occurs each time a FaultHandler processes a fault.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="0be32-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0be32-132">See also</span></span>  
 
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0be32-133">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="0be32-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0be32-134">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="0be32-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
