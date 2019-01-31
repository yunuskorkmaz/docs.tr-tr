---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 1a6899eaa04ad16192e07f4bc2ad1abe6e4aedd5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257375"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="543dc-101">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="543dc-101">\<faultPropagationQuery></span></span>
<span data-ttu-id="543dc-102">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="543dc-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="543dc-103">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="543dc-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="543dc-104">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="543dc-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="543dc-105">Sorgu hata yayma kayıtlara abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="543dc-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="543dc-106">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="543dc-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="543dc-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="543dc-107">\<system.serviceModel></span></span>  
<span data-ttu-id="543dc-108">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="543dc-108">\<tracking></span></span>  
<span data-ttu-id="543dc-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="543dc-109">\<trackingProfile></span></span>  
<span data-ttu-id="543dc-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="543dc-110">\<workflow></span></span>  
<span data-ttu-id="543dc-111">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="543dc-111">\<faultPropagationQueries></span></span>  
<span data-ttu-id="543dc-112">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="543dc-112">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="543dc-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="543dc-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="543dc-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="543dc-114">Attributes and Elements</span></span>  
 <span data-ttu-id="543dc-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="543dc-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="543dc-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="543dc-116">Attributes</span></span>  
  
|<span data-ttu-id="543dc-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="543dc-117">Attribute</span></span>|<span data-ttu-id="543dc-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="543dc-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="543dc-119">activityName</span><span class="sxs-lookup"><span data-stu-id="543dc-119">activityName</span></span>|<span data-ttu-id="543dc-120">Hata aktarılacaktır hata işleyicisi etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="543dc-120">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="543dc-121">Varsayılan değer \*, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="543dc-121">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="543dc-122">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="543dc-122">faultHandlerActivityName</span></span>|<span data-ttu-id="543dc-123">Hata kaynağı olan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="543dc-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="543dc-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="543dc-124">Child Elements</span></span>  
 <span data-ttu-id="543dc-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="543dc-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="543dc-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="543dc-126">Parent Elements</span></span>  
  
|<span data-ttu-id="543dc-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="543dc-127">Element</span></span>|<span data-ttu-id="543dc-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="543dc-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="543dc-129">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="543dc-129">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="543dc-130">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="543dc-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="543dc-131">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="543dc-131">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="543dc-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="543dc-132">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="543dc-133">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="543dc-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="543dc-134">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="543dc-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
