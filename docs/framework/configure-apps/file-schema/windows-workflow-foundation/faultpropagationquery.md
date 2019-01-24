---
title: '&lt;faultPropagationQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: a91a6f61b39a780ed48ad8d5f5e0dfb9ef60da39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538342"
---
# <a name="ltfaultpropagationquerygt"></a><span data-ttu-id="00e9e-102">&lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="00e9e-102">&lt;faultPropagationQuery&gt;</span></span>
<span data-ttu-id="00e9e-103">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00e9e-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="00e9e-104">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="00e9e-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="00e9e-105">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="00e9e-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="00e9e-106">Sorgu hata yayma kayıtlara abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="00e9e-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="00e9e-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="00e9e-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="00e9e-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="00e9e-108">\<system.serviceModel></span></span>  
<span data-ttu-id="00e9e-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="00e9e-109">\<tracking></span></span>  
<span data-ttu-id="00e9e-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="00e9e-110">\<trackingProfile></span></span>  
<span data-ttu-id="00e9e-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="00e9e-111">\<workflow></span></span>  
<span data-ttu-id="00e9e-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="00e9e-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="00e9e-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="00e9e-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00e9e-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00e9e-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00e9e-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="00e9e-115">Attributes and Elements</span></span>  
 <span data-ttu-id="00e9e-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="00e9e-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00e9e-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="00e9e-117">Attributes</span></span>  
  
|<span data-ttu-id="00e9e-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="00e9e-118">Attribute</span></span>|<span data-ttu-id="00e9e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00e9e-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00e9e-120">activityName</span><span class="sxs-lookup"><span data-stu-id="00e9e-120">activityName</span></span>|<span data-ttu-id="00e9e-121">Hata aktarılacaktır hata işleyicisi etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="00e9e-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="00e9e-122">Varsayılan değer \*, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="00e9e-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="00e9e-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="00e9e-123">faultHandlerActivityName</span></span>|<span data-ttu-id="00e9e-124">Hata kaynağı olan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="00e9e-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00e9e-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="00e9e-125">Child Elements</span></span>  
 <span data-ttu-id="00e9e-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="00e9e-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00e9e-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="00e9e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="00e9e-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="00e9e-128">Element</span></span>|<span data-ttu-id="00e9e-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00e9e-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00e9e-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="00e9e-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="00e9e-131">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00e9e-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="00e9e-132">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="00e9e-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00e9e-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00e9e-133">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="00e9e-134">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="00e9e-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="00e9e-135">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="00e9e-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
