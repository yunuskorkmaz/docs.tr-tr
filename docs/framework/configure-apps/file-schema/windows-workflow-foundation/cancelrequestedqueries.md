---
title: '&lt;cancelRequestedQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 5bc2e3ffeb93bdfcd45638d6b50e218c03706f42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520691"
---
# <a name="ltcancelrequestedqueriesgt"></a><span data-ttu-id="f7a62-102">&lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="f7a62-102">&lt;cancelRequestedQueries&gt;</span></span>
<span data-ttu-id="f7a62-103">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f7a62-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="f7a62-104">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f7a62-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="f7a62-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f7a62-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f7a62-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f7a62-106">\<system.serviceModel></span></span>  
<span data-ttu-id="f7a62-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="f7a62-107">\<tracking></span></span>  
<span data-ttu-id="f7a62-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f7a62-108">\<trackingProfile></span></span>  
<span data-ttu-id="f7a62-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="f7a62-109">\<workflow></span></span>  
<span data-ttu-id="f7a62-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="f7a62-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7a62-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7a62-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7a62-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7a62-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f7a62-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f7a62-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7a62-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f7a62-114">Attributes</span></span>  
 <span data-ttu-id="f7a62-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="f7a62-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f7a62-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7a62-116">Child Elements</span></span>  
  
|<span data-ttu-id="f7a62-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="f7a62-117">Element</span></span>|<span data-ttu-id="f7a62-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7a62-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7a62-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="f7a62-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="f7a62-120">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir sorgu</span><span class="sxs-lookup"><span data-stu-id="f7a62-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f7a62-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7a62-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f7a62-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="f7a62-122">Element</span></span>|<span data-ttu-id="f7a62-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7a62-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7a62-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="f7a62-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f7a62-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="f7a62-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f7a62-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7a62-126">See also</span></span>
- [<span data-ttu-id="f7a62-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f7a62-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f7a62-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f7a62-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
