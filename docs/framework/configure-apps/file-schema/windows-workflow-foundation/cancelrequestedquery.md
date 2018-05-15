---
title: '&lt;cancelRequestedQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e532ea482108c9a5cabe13a99afddca10f8341d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="330fc-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="330fc-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="330fc-103">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="330fc-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="330fc-104">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="330fc-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="330fc-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="330fc-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="330fc-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="330fc-106">\<system.serviceModel></span></span>  
<span data-ttu-id="330fc-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="330fc-107">\<tracking></span></span>  
<span data-ttu-id="330fc-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="330fc-108">\<trackingProfile></span></span>  
<span data-ttu-id="330fc-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="330fc-109">\<workflow></span></span>  
<span data-ttu-id="330fc-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="330fc-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="330fc-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="330fc-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="330fc-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="330fc-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="330fc-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="330fc-113">Attributes and Elements</span></span>  
 <span data-ttu-id="330fc-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="330fc-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="330fc-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="330fc-115">Attributes</span></span>  
  
|<span data-ttu-id="330fc-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="330fc-116">Attribute</span></span>|<span data-ttu-id="330fc-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="330fc-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="330fc-118">activityName</span><span class="sxs-lookup"><span data-stu-id="330fc-118">activityName</span></span>|<span data-ttu-id="330fc-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="330fc-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="330fc-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="330fc-120">childActivityName</span></span>|<span data-ttu-id="330fc-121">İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="330fc-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="330fc-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="330fc-122">Child Elements</span></span>  
 <span data-ttu-id="330fc-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="330fc-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="330fc-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="330fc-124">Parent Elements</span></span>  
  
|<span data-ttu-id="330fc-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="330fc-125">Element</span></span>|<span data-ttu-id="330fc-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="330fc-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="330fc-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="330fc-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="330fc-128">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan yapılandırma öğelerinin bir listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="330fc-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="330fc-129">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="330fc-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="330fc-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="330fc-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="330fc-131">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="330fc-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="330fc-132">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="330fc-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
