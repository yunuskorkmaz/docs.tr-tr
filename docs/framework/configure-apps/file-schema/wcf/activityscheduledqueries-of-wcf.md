---
title: <activityScheduledQueries>WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 83e71e2038377ae4c1c3b17334eece3f30c919f6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920329"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="fec1b-102">\<WCF > activityScheduledQueries</span><span class="sxs-lookup"><span data-stu-id="fec1b-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="fec1b-103">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fec1b-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="fec1b-104">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fec1b-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="fec1b-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fec1b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="fec1b-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fec1b-106">\<system.serviceModel></span></span>  
<span data-ttu-id="fec1b-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="fec1b-107">\<tracking></span></span>  
<span data-ttu-id="fec1b-108">\<Profiller ></span><span class="sxs-lookup"><span data-stu-id="fec1b-108">\<profiles></span></span>  
<span data-ttu-id="fec1b-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="fec1b-109">\<trackingProfile></span></span>  
<span data-ttu-id="fec1b-110">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="fec1b-110">\<workflow></span></span>  
<span data-ttu-id="fec1b-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="fec1b-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fec1b-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fec1b-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fec1b-113">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="fec1b-113">Attributes and elements</span></span>  

<span data-ttu-id="fec1b-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fec1b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fec1b-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fec1b-115">Attributes</span></span>  

<span data-ttu-id="fec1b-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="fec1b-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fec1b-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="fec1b-117">Child elements</span></span>  
  
|<span data-ttu-id="fec1b-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="fec1b-118">Element</span></span>|<span data-ttu-id="fec1b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fec1b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fec1b-120">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="fec1b-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="fec1b-121">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="fec1b-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fec1b-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="fec1b-122">Parent elements</span></span>  
  
|<span data-ttu-id="fec1b-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="fec1b-123">Element</span></span>|<span data-ttu-id="fec1b-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fec1b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fec1b-125">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="fec1b-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="fec1b-126">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="fec1b-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fec1b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fec1b-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="fec1b-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="fec1b-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fec1b-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="fec1b-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
