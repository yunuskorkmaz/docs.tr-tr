---
title: WCF &lt;cancelRequestedQueries&gt;
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 4d746290f01e702979d1dd0165ad3fc5299e1b75
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087758"
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="5ab7a-102">WCF &lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="5ab7a-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="5ab7a-103">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5ab7a-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5ab7a-104">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5ab7a-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="5ab7a-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5ab7a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="5ab7a-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5ab7a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="5ab7a-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="5ab7a-107">\<tracking></span></span>  
<span data-ttu-id="5ab7a-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5ab7a-108">\<trackingProfile></span></span>  
<span data-ttu-id="5ab7a-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="5ab7a-109">\<workflow></span></span>  
<span data-ttu-id="5ab7a-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="5ab7a-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ab7a-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ab7a-111">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="5ab7a-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ab7a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5ab7a-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ab7a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ab7a-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ab7a-114">Attributes</span></span>  
 <span data-ttu-id="5ab7a-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ab7a-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5ab7a-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ab7a-116">Child Elements</span></span>  
  
|<span data-ttu-id="5ab7a-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ab7a-117">Element</span></span>|<span data-ttu-id="5ab7a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ab7a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ab7a-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="5ab7a-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="5ab7a-120">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir sorgu</span><span class="sxs-lookup"><span data-stu-id="5ab7a-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ab7a-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ab7a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5ab7a-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ab7a-122">Element</span></span>|<span data-ttu-id="5ab7a-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ab7a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ab7a-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="5ab7a-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="5ab7a-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5ab7a-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ab7a-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ab7a-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="5ab7a-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="5ab7a-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="5ab7a-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="5ab7a-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
