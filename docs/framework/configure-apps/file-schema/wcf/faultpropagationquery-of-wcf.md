---
title: WCF &lt;faultPropagationQuery&gt;
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: fe3dd90a5c6b26537ab461b4bf4993df5be625a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="b1970-102">WCF &lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="b1970-102">&lt;faultPropagationQuery&gt; of WCF</span></span>
<span data-ttu-id="b1970-103">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b1970-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b1970-104">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="b1970-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="b1970-105">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için bu tür sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1970-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="b1970-106">Sorgu Hatası yayma kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b1970-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="b1970-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b1970-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="b1970-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b1970-108">\<system.serviceModel></span></span>  
<span data-ttu-id="b1970-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="b1970-109">\<tracking></span></span>  
<span data-ttu-id="b1970-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b1970-110">\<trackingProfile></span></span>  
<span data-ttu-id="b1970-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="b1970-111">\<workflow></span></span>  
<span data-ttu-id="b1970-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="b1970-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="b1970-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="b1970-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1970-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1970-114">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1970-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1970-115">Attributes and Elements</span></span>  
 <span data-ttu-id="b1970-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1970-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1970-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b1970-117">Attributes</span></span>  
  
|<span data-ttu-id="b1970-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b1970-118">Attribute</span></span>|<span data-ttu-id="b1970-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1970-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1970-120">activityName</span><span class="sxs-lookup"><span data-stu-id="b1970-120">activityName</span></span>|<span data-ttu-id="b1970-121">Hataya yayılan hata işleyicisi etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="b1970-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="b1970-122">Varsayılan değer \*, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1970-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="b1970-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="b1970-123">faultHandlerActivityName</span></span>|<span data-ttu-id="b1970-124">Hata kaynağı etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="b1970-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1970-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1970-125">Child Elements</span></span>  
 <span data-ttu-id="b1970-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="b1970-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1970-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1970-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b1970-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1970-128">Element</span></span>|<span data-ttu-id="b1970-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1970-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1970-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="b1970-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="b1970-131">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan yapılandırma öğelerinin bir listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b1970-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b1970-132">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="b1970-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1970-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1970-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="b1970-134">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="b1970-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b1970-135">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="b1970-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
