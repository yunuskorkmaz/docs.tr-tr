---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 049ca79355f13fd4ffacedbb7501d760361f0a81
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282028"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="a0e32-101">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="a0e32-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="a0e32-102">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a0e32-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a0e32-103">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a0e32-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="a0e32-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a0e32-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a0e32-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a0e32-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a0e32-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="a0e32-106">\<tracking></span></span>  
<span data-ttu-id="a0e32-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a0e32-107">\<trackingProfile></span></span>  
<span data-ttu-id="a0e32-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="a0e32-108">\<workflow></span></span>  
<span data-ttu-id="a0e32-109">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="a0e32-109">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="a0e32-110">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="a0e32-110">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0e32-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0e32-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0e32-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0e32-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a0e32-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0e32-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0e32-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a0e32-114">Attributes</span></span>  
  
|<span data-ttu-id="a0e32-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a0e32-115">Attribute</span></span>|<span data-ttu-id="a0e32-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0e32-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a0e32-117">activityName</span><span class="sxs-lookup"><span data-stu-id="a0e32-117">activityName</span></span>|<span data-ttu-id="a0e32-118">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="a0e32-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="a0e32-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="a0e32-119">childActivityName</span></span>|<span data-ttu-id="a0e32-120">Kendisi için İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="a0e32-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0e32-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0e32-121">Child Elements</span></span>  
 <span data-ttu-id="a0e32-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="a0e32-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0e32-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0e32-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a0e32-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0e32-124">Element</span></span>|<span data-ttu-id="a0e32-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0e32-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0e32-126">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="a0e32-126">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="a0e32-127">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a0e32-127">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a0e32-128">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a0e32-128">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0e32-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0e32-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a0e32-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a0e32-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a0e32-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a0e32-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
