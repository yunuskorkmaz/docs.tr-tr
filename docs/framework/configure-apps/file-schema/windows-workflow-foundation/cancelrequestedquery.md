---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 5f2e46d5e4cdd64c37219476790b9ff92c606b6b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215319"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="487be-101">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="487be-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="487be-102">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="487be-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="487be-103">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="487be-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="487be-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="487be-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="487be-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="487be-105">\<system.serviceModel></span></span>  
<span data-ttu-id="487be-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="487be-106">\<tracking></span></span>  
<span data-ttu-id="487be-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="487be-107">\<trackingProfile></span></span>  
<span data-ttu-id="487be-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="487be-108">\<workflow></span></span>  
<span data-ttu-id="487be-109">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="487be-109">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="487be-110">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="487be-110">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="487be-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="487be-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="487be-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="487be-112">Attributes and Elements</span></span>  
 <span data-ttu-id="487be-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="487be-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="487be-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="487be-114">Attributes</span></span>  
  
|<span data-ttu-id="487be-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="487be-115">Attribute</span></span>|<span data-ttu-id="487be-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="487be-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="487be-117">activityName</span><span class="sxs-lookup"><span data-stu-id="487be-117">activityName</span></span>|<span data-ttu-id="487be-118">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="487be-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="487be-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="487be-119">childActivityName</span></span>|<span data-ttu-id="487be-120">Kendisi için İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="487be-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="487be-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="487be-121">Child Elements</span></span>  
 <span data-ttu-id="487be-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="487be-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="487be-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="487be-123">Parent Elements</span></span>  
  
|<span data-ttu-id="487be-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="487be-124">Element</span></span>|<span data-ttu-id="487be-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="487be-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="487be-126">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="487be-126">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="487be-127">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="487be-127">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="487be-128">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="487be-128">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="487be-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="487be-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="487be-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="487be-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="487be-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="487be-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
