---
title: <activityScheduledQueries> WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 1c9c292080016d7a2d0014ed07be371c0e247621
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701131"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="06853-102">\<activityScheduledQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="06853-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="06853-103">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="06853-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="06853-104">Sorgu zamanlanmış etkinlik kayıtlarına abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="06853-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="06853-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="06853-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="06853-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="06853-106">\<system.serviceModel></span></span>  
<span data-ttu-id="06853-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="06853-107">\<tracking></span></span>  
<span data-ttu-id="06853-108">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="06853-108">\<profiles></span></span>  
<span data-ttu-id="06853-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="06853-109">\<trackingProfile></span></span>  
<span data-ttu-id="06853-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="06853-110">\<workflow></span></span>  
<span data-ttu-id="06853-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="06853-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06853-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06853-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06853-113">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="06853-113">Attributes and elements</span></span>  

<span data-ttu-id="06853-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="06853-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06853-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="06853-115">Attributes</span></span>  

<span data-ttu-id="06853-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="06853-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="06853-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="06853-117">Child elements</span></span>  
  
|<span data-ttu-id="06853-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="06853-118">Element</span></span>|<span data-ttu-id="06853-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06853-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06853-120">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="06853-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="06853-121">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="06853-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06853-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="06853-122">Parent elements</span></span>  
  
|<span data-ttu-id="06853-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="06853-123">Element</span></span>|<span data-ttu-id="06853-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06853-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06853-125">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="06853-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="06853-126">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="06853-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06853-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06853-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="06853-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="06853-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="06853-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="06853-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
