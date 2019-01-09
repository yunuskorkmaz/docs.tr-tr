---
title: WCF &lt;activityScheduledQueries&gt;
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: d6bc2360ccdeebe291de495e6ee5c7e22f26590a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145581"
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="5d6a0-102">WCF &lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="5d6a0-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="5d6a0-103">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5d6a0-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="5d6a0-104">Sorgu zamanlanmış etkinlik kayıtlarına abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5d6a0-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="5d6a0-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5d6a0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="5d6a0-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5d6a0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="5d6a0-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="5d6a0-107">\<tracking></span></span>  
<span data-ttu-id="5d6a0-108">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="5d6a0-108">\<profiles></span></span>  
<span data-ttu-id="5d6a0-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5d6a0-109">\<trackingProfile></span></span>  
<span data-ttu-id="5d6a0-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="5d6a0-110">\<workflow></span></span>  
<span data-ttu-id="5d6a0-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="5d6a0-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d6a0-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d6a0-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d6a0-113">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="5d6a0-113">Attributes and elements</span></span>  

<span data-ttu-id="5d6a0-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5d6a0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d6a0-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5d6a0-115">Attributes</span></span>  

<span data-ttu-id="5d6a0-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="5d6a0-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5d6a0-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="5d6a0-117">Child elements</span></span>  
  
|<span data-ttu-id="5d6a0-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="5d6a0-118">Element</span></span>|<span data-ttu-id="5d6a0-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d6a0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d6a0-120">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="5d6a0-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="5d6a0-121">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="5d6a0-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5d6a0-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="5d6a0-122">Parent elements</span></span>  
  
|<span data-ttu-id="5d6a0-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="5d6a0-123">Element</span></span>|<span data-ttu-id="5d6a0-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d6a0-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d6a0-125">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="5d6a0-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="5d6a0-126">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="5d6a0-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d6a0-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d6a0-127">See also</span></span>  

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="5d6a0-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="5d6a0-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5d6a0-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="5d6a0-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
