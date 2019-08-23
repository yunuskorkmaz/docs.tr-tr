---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 628dbf801cae5f61dc7d518c27df3380dd2d3d23
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945942"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="4fb8e-101">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="4fb8e-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="4fb8e-102">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4fb8e-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="4fb8e-103">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4fb8e-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="4fb8e-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4fb8e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4fb8e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4fb8e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="4fb8e-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="4fb8e-106">\<tracking></span></span>  
<span data-ttu-id="4fb8e-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4fb8e-107">\<trackingProfile></span></span>  
<span data-ttu-id="4fb8e-108">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="4fb8e-108">\<workflow></span></span>  
<span data-ttu-id="4fb8e-109">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="4fb8e-109">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fb8e-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4fb8e-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fb8e-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fb8e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4fb8e-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4fb8e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fb8e-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4fb8e-113">Attributes</span></span>  
 <span data-ttu-id="4fb8e-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="4fb8e-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4fb8e-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fb8e-115">Child Elements</span></span>  
  
|<span data-ttu-id="4fb8e-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="4fb8e-116">Element</span></span>|<span data-ttu-id="4fb8e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fb8e-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fb8e-118">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="4fb8e-118">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="4fb8e-119">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan sorgu</span><span class="sxs-lookup"><span data-stu-id="4fb8e-119">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4fb8e-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fb8e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4fb8e-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="4fb8e-121">Element</span></span>|<span data-ttu-id="4fb8e-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fb8e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fb8e-123">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="4fb8e-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="4fb8e-124">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="4fb8e-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fb8e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fb8e-125">See also</span></span>

- [<span data-ttu-id="4fb8e-126">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="4fb8e-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4fb8e-127">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="4fb8e-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
