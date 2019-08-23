---
title: <cancelRequestedQueries>WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 0f04fc928358c96ca3112422f1a6ccd039269e47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926240"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="a20d7-102">\<WCF > cancelRequestedQueries</span><span class="sxs-lookup"><span data-stu-id="a20d7-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="a20d7-103">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a20d7-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a20d7-104">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a20d7-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="a20d7-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a20d7-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a20d7-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a20d7-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a20d7-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="a20d7-107">\<tracking></span></span>  
<span data-ttu-id="a20d7-108">\<> \<TrackingProfile > profilleri</span><span class="sxs-lookup"><span data-stu-id="a20d7-108">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="a20d7-109">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="a20d7-109">\<workflow></span></span>  
<span data-ttu-id="a20d7-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="a20d7-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a20d7-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a20d7-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a20d7-112">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="a20d7-112">Attributes and elements</span></span>  

<span data-ttu-id="a20d7-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a20d7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a20d7-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a20d7-114">Attributes</span></span>

<span data-ttu-id="a20d7-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="a20d7-115">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="a20d7-116">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a20d7-116">Child elements</span></span>
  
|<span data-ttu-id="a20d7-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="a20d7-117">Element</span></span>|<span data-ttu-id="a20d7-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a20d7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a20d7-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="a20d7-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="a20d7-120">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan sorgu</span><span class="sxs-lookup"><span data-stu-id="a20d7-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a20d7-121">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="a20d7-121">Parent elements</span></span>  
  
|<span data-ttu-id="a20d7-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="a20d7-122">Element</span></span>|<span data-ttu-id="a20d7-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a20d7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a20d7-124">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="a20d7-124">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="a20d7-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a20d7-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a20d7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a20d7-126">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="a20d7-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a20d7-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a20d7-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a20d7-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
