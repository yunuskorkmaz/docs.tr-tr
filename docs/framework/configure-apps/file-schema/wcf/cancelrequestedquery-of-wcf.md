---
title: WCF &lt;cancelRequestedQuery&gt;
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 41964561a460babc41de755e213971593047b707
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748524"
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="114f0-102">WCF &lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="114f0-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="114f0-103">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="114f0-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="114f0-104">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="114f0-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="114f0-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="114f0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="114f0-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="114f0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="114f0-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="114f0-107">\<tracking></span></span>  
<span data-ttu-id="114f0-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="114f0-108">\<trackingProfile></span></span>  
<span data-ttu-id="114f0-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="114f0-109">\<workflow></span></span>  
<span data-ttu-id="114f0-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="114f0-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="114f0-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="114f0-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="114f0-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="114f0-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="114f0-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="114f0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="114f0-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="114f0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="114f0-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="114f0-115">Attributes</span></span>  
  
|<span data-ttu-id="114f0-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="114f0-116">Attribute</span></span>|<span data-ttu-id="114f0-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="114f0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="114f0-118">activityName</span><span class="sxs-lookup"><span data-stu-id="114f0-118">activityName</span></span>|<span data-ttu-id="114f0-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="114f0-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="114f0-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="114f0-120">childActivityName</span></span>|<span data-ttu-id="114f0-121">İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="114f0-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="114f0-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="114f0-122">Child Elements</span></span>  
 <span data-ttu-id="114f0-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="114f0-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="114f0-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="114f0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="114f0-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="114f0-125">Element</span></span>|<span data-ttu-id="114f0-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="114f0-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="114f0-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="114f0-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="114f0-128">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan yapılandırma öğelerinin bir listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="114f0-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="114f0-129">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="114f0-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="114f0-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="114f0-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>     
 [<span data-ttu-id="114f0-131">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="114f0-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="114f0-132">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="114f0-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
