---
title: WCF &lt;cancelRequestedQueries&gt;
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 9cf2761bdab36d95b5077e36174565659230b512
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145451"
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="47544-102">WCF &lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="47544-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="47544-103">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="47544-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="47544-104">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="47544-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="47544-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="47544-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="47544-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="47544-106">\<system.serviceModel></span></span>  
<span data-ttu-id="47544-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="47544-107">\<tracking></span></span>  
<span data-ttu-id="47544-108">\<profilleri > \<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="47544-108">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="47544-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="47544-109">\<workflow></span></span>  
<span data-ttu-id="47544-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="47544-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47544-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47544-111">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47544-112">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="47544-112">Attributes and elements</span></span>  

<span data-ttu-id="47544-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47544-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47544-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="47544-114">Attributes</span></span>

<span data-ttu-id="47544-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="47544-115">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="47544-116">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="47544-116">Child elements</span></span>
  
|<span data-ttu-id="47544-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="47544-117">Element</span></span>|<span data-ttu-id="47544-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47544-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47544-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="47544-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="47544-120">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir sorgu</span><span class="sxs-lookup"><span data-stu-id="47544-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="47544-121">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="47544-121">Parent elements</span></span>  
  
|<span data-ttu-id="47544-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="47544-122">Element</span></span>|<span data-ttu-id="47544-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47544-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47544-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="47544-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="47544-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> özelliği.</span><span class="sxs-lookup"><span data-stu-id="47544-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47544-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47544-126">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="47544-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="47544-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="47544-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="47544-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
