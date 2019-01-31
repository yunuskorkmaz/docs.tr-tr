---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 989d6e99457108336c38fb1eece4c9ac2444c974
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271505"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="59800-101">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="59800-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="59800-102">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="59800-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="59800-103">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="59800-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="59800-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="59800-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="59800-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="59800-105">\<system.serviceModel></span></span>  
<span data-ttu-id="59800-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="59800-106">\<tracking></span></span>  
<span data-ttu-id="59800-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="59800-107">\<trackingProfile></span></span>  
<span data-ttu-id="59800-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="59800-108">\<workflow></span></span>  
<span data-ttu-id="59800-109">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="59800-109">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59800-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59800-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59800-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="59800-111">Attributes and Elements</span></span>  
 <span data-ttu-id="59800-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="59800-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59800-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="59800-113">Attributes</span></span>  
 <span data-ttu-id="59800-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="59800-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="59800-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="59800-115">Child Elements</span></span>  
  
|<span data-ttu-id="59800-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="59800-116">Element</span></span>|<span data-ttu-id="59800-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59800-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59800-118">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="59800-118">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="59800-119">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir sorgu</span><span class="sxs-lookup"><span data-stu-id="59800-119">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59800-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="59800-120">Parent Elements</span></span>  
  
|<span data-ttu-id="59800-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="59800-121">Element</span></span>|<span data-ttu-id="59800-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59800-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59800-123">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="59800-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="59800-124">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="59800-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59800-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59800-125">See also</span></span>
- [<span data-ttu-id="59800-126">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="59800-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="59800-127">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="59800-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
