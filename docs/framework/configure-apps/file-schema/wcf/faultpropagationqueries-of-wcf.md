---
title: WCF &lt;faultPropagationQueries&gt;
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 5db043b5d4d150628df386dafb6e7bd351a0a28a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754012"
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a><span data-ttu-id="75077-102">WCF &lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="75077-102">&lt;faultPropagationQueries&gt; of WCF</span></span>
<span data-ttu-id="75077-103">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="75077-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="75077-104">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="75077-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="75077-105">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için bu tür sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="75077-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="75077-106">Sorgu Hatası yayma kayıtlara abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="75077-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="75077-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="75077-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="75077-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="75077-108">\<system.serviceModel></span></span>  
<span data-ttu-id="75077-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="75077-109">\<tracking></span></span>  
<span data-ttu-id="75077-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="75077-110">\<trackingProfile></span></span>  
<span data-ttu-id="75077-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="75077-111">\<workflow></span></span>  
<span data-ttu-id="75077-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="75077-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75077-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75077-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75077-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="75077-114">Attributes and Elements</span></span>  
 <span data-ttu-id="75077-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="75077-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75077-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="75077-116">Attributes</span></span>  
 <span data-ttu-id="75077-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="75077-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="75077-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="75077-118">Child Elements</span></span>  
  
|<span data-ttu-id="75077-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="75077-119">Element</span></span>|<span data-ttu-id="75077-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75077-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75077-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="75077-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="75077-122">İçinde bir etkinlik oluşan hataların işlenmesi izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="75077-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="75077-123">Bu olay bir FaultHandler bir arıza her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="75077-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="75077-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="75077-124">Parent Elements</span></span>  
  
|<span data-ttu-id="75077-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="75077-125">Element</span></span>|<span data-ttu-id="75077-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75077-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75077-127">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="75077-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="75077-128">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="75077-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75077-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="75077-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="75077-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="75077-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="75077-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="75077-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
