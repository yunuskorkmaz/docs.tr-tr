---
title: WCF &lt;cancelRequestedQueries&gt;
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: c9266d9ce1f6a61c4468fd95467e76730b966249
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480632"
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="da7b9-102">WCF &lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="da7b9-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="da7b9-103">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="da7b9-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="da7b9-104">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="da7b9-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="da7b9-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="da7b9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="da7b9-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="da7b9-106">\<system.serviceModel></span></span>  
<span data-ttu-id="da7b9-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="da7b9-107">\<tracking></span></span>  
<span data-ttu-id="da7b9-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="da7b9-108">\<trackingProfile></span></span>  
<span data-ttu-id="da7b9-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="da7b9-109">\<workflow></span></span>  
<span data-ttu-id="da7b9-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="da7b9-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da7b9-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da7b9-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="da7b9-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="da7b9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="da7b9-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="da7b9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da7b9-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="da7b9-114">Attributes</span></span>  
 <span data-ttu-id="da7b9-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="da7b9-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="da7b9-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="da7b9-116">Child Elements</span></span>  
  
|<span data-ttu-id="da7b9-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="da7b9-117">Element</span></span>|<span data-ttu-id="da7b9-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da7b9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da7b9-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="da7b9-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="da7b9-120">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir sorgu</span><span class="sxs-lookup"><span data-stu-id="da7b9-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da7b9-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="da7b9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="da7b9-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="da7b9-122">Element</span></span>|<span data-ttu-id="da7b9-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da7b9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da7b9-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="da7b9-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="da7b9-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> özelliği.</span><span class="sxs-lookup"><span data-stu-id="da7b9-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da7b9-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="da7b9-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="da7b9-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="da7b9-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="da7b9-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="da7b9-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
