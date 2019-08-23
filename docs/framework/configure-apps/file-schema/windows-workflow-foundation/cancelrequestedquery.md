---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: d9c3f91edb41bd034bcd978b075d62f74b6e308d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945879"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="8e728-101">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="8e728-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="8e728-102">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8e728-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="8e728-103">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8e728-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="8e728-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8e728-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="8e728-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8e728-105">\<system.serviceModel></span></span>  
<span data-ttu-id="8e728-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="8e728-106">\<tracking></span></span>  
<span data-ttu-id="8e728-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8e728-107">\<trackingProfile></span></span>  
<span data-ttu-id="8e728-108">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="8e728-108">\<workflow></span></span>  
<span data-ttu-id="8e728-109">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="8e728-109">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="8e728-110">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="8e728-110">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e728-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e728-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e728-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e728-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8e728-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8e728-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e728-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8e728-114">Attributes</span></span>  
  
|<span data-ttu-id="8e728-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8e728-115">Attribute</span></span>|<span data-ttu-id="8e728-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e728-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e728-117">activityName</span><span class="sxs-lookup"><span data-stu-id="8e728-117">activityName</span></span>|<span data-ttu-id="8e728-118">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8e728-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="8e728-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="8e728-119">childActivityName</span></span>|<span data-ttu-id="8e728-120">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8e728-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e728-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e728-121">Child Elements</span></span>  
 <span data-ttu-id="8e728-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="8e728-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e728-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e728-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8e728-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="8e728-124">Element</span></span>|<span data-ttu-id="8e728-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e728-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e728-126">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="8e728-126">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="8e728-127">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8e728-127">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="8e728-128">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8e728-128">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e728-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e728-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8e728-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="8e728-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8e728-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="8e728-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
