---
title: WCF &lt;faultPropagationQuery&gt;
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: cf582fce4e899e62daa4f34f193a0232ec19a135
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149039"
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="f5564-102">WCF &lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="f5564-102">&lt;faultPropagationQuery&gt; of WCF</span></span>

<span data-ttu-id="f5564-103">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f5564-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f5564-104">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="f5564-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="f5564-105">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5564-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="f5564-106">Sorgu hata yayma kayıtlara abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f5564-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="f5564-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f5564-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="f5564-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f5564-108">\<system.serviceModel></span></span>  
<span data-ttu-id="f5564-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="f5564-109">\<tracking></span></span>  
<span data-ttu-id="f5564-110">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="f5564-110">\<profiles></span></span>  
<span data-ttu-id="f5564-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f5564-111">\<trackingProfile></span></span>  
<span data-ttu-id="f5564-112">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="f5564-112">\<workflow></span></span>  
<span data-ttu-id="f5564-113">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="f5564-113">\<faultPropagationQueries></span></span>  
<span data-ttu-id="f5564-114">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="f5564-114">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5564-115">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5564-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5564-116">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="f5564-116">Attributes and elements</span></span>

<span data-ttu-id="f5564-117">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5564-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5564-118">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f5564-118">Attributes</span></span>  
  
|<span data-ttu-id="f5564-119">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f5564-119">Attribute</span></span>|<span data-ttu-id="f5564-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5564-120">Description</span></span>|  
|---------------|-----------------|  
|`faultSourceActivityName`|<span data-ttu-id="f5564-121">Hata aktarılacaktır hata işleyicisi etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="f5564-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="f5564-122">Varsayılan \*, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5564-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|`faultHandlerActivityName`|<span data-ttu-id="f5564-123">Hata kaynağı olan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="f5564-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5564-124">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="f5564-124">Child elements</span></span>

<span data-ttu-id="f5564-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="f5564-125">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="f5564-126">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="f5564-126">Parent elements</span></span>  
  
|<span data-ttu-id="f5564-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="f5564-127">Element</span></span>|<span data-ttu-id="f5564-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5564-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5564-129">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="f5564-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="f5564-130">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f5564-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f5564-131">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="f5564-131">This event occurs each time a FaultHandler processes a fault.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="f5564-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5564-132">See also</span></span>  
 
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f5564-133">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f5564-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f5564-134">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f5564-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
