---
title: WCF &lt;cancelRequestedQuery&gt;
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 38d946a213131e8dcb6f4100d0ad67f7c167f342
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086407"
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="5f73b-102">WCF &lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="5f73b-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="5f73b-103">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5f73b-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5f73b-104">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5f73b-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="5f73b-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5f73b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="5f73b-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5f73b-106">\<system.serviceModel></span></span>  
<span data-ttu-id="5f73b-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="5f73b-107">\<tracking></span></span>  
<span data-ttu-id="5f73b-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5f73b-108">\<trackingProfile></span></span>  
<span data-ttu-id="5f73b-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="5f73b-109">\<workflow></span></span>  
<span data-ttu-id="5f73b-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="5f73b-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="5f73b-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="5f73b-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f73b-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f73b-112">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="5f73b-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f73b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5f73b-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5f73b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f73b-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5f73b-115">Attributes</span></span>  
  
|<span data-ttu-id="5f73b-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5f73b-116">Attribute</span></span>|<span data-ttu-id="5f73b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f73b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f73b-118">activityName</span><span class="sxs-lookup"><span data-stu-id="5f73b-118">activityName</span></span>|<span data-ttu-id="5f73b-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="5f73b-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="5f73b-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="5f73b-120">childActivityName</span></span>|<span data-ttu-id="5f73b-121">Kendisi için İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="5f73b-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f73b-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f73b-122">Child Elements</span></span>  
 <span data-ttu-id="5f73b-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="5f73b-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f73b-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f73b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5f73b-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="5f73b-125">Element</span></span>|<span data-ttu-id="5f73b-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f73b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f73b-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="5f73b-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="5f73b-128">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5f73b-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5f73b-129">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5f73b-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f73b-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f73b-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>     
 [<span data-ttu-id="5f73b-131">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="5f73b-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="5f73b-132">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="5f73b-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
