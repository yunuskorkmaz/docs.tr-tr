---
title: WCF &lt;cancelRequestedQueries&gt;
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 40fbcafd641e93be6ba21635f4f6e6428be62c12
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193792"
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="fab6e-102">WCF &lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="fab6e-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="fab6e-103">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fab6e-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="fab6e-104">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fab6e-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="fab6e-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fab6e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="fab6e-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fab6e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="fab6e-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="fab6e-107">\<tracking></span></span>  
<span data-ttu-id="fab6e-108">\<profilleri > \<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="fab6e-108">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="fab6e-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="fab6e-109">\<workflow></span></span>  
<span data-ttu-id="fab6e-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="fab6e-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fab6e-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fab6e-111">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String"/>
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fab6e-112">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="fab6e-112">Attributes and elements</span></span>  

<span data-ttu-id="fab6e-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fab6e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fab6e-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fab6e-114">Attributes</span></span>

<span data-ttu-id="fab6e-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="fab6e-115">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="fab6e-116">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="fab6e-116">Child elements</span></span>
  
|<span data-ttu-id="fab6e-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="fab6e-117">Element</span></span>|<span data-ttu-id="fab6e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fab6e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fab6e-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="fab6e-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="fab6e-120">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir sorgu</span><span class="sxs-lookup"><span data-stu-id="fab6e-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fab6e-121">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="fab6e-121">Parent elements</span></span>  
  
|<span data-ttu-id="fab6e-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="fab6e-122">Element</span></span>|<span data-ttu-id="fab6e-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fab6e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fab6e-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="fab6e-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="fab6e-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fab6e-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fab6e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fab6e-126">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="fab6e-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="fab6e-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fab6e-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="fab6e-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
