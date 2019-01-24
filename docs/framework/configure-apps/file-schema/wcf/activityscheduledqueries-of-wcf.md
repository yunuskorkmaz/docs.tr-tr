---
title: WCF &lt;activityScheduledQueries&gt;
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 5430058049e8a09c1e2a289e1f997338c23b9d94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492162"
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="8e0be-102">WCF &lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="8e0be-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="8e0be-103">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8e0be-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="8e0be-104">Sorgu zamanlanmış etkinlik kayıtlarına abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8e0be-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="8e0be-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8e0be-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="8e0be-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8e0be-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8e0be-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="8e0be-107">\<tracking></span></span>  
<span data-ttu-id="8e0be-108">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="8e0be-108">\<profiles></span></span>  
<span data-ttu-id="8e0be-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8e0be-109">\<trackingProfile></span></span>  
<span data-ttu-id="8e0be-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="8e0be-110">\<workflow></span></span>  
<span data-ttu-id="8e0be-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="8e0be-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e0be-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e0be-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e0be-113">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="8e0be-113">Attributes and elements</span></span>  

<span data-ttu-id="8e0be-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8e0be-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e0be-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8e0be-115">Attributes</span></span>  

<span data-ttu-id="8e0be-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="8e0be-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8e0be-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="8e0be-117">Child elements</span></span>  
  
|<span data-ttu-id="8e0be-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="8e0be-118">Element</span></span>|<span data-ttu-id="8e0be-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e0be-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e0be-120">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="8e0be-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="8e0be-121">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="8e0be-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e0be-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="8e0be-122">Parent elements</span></span>  
  
|<span data-ttu-id="8e0be-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="8e0be-123">Element</span></span>|<span data-ttu-id="8e0be-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e0be-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e0be-125">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="8e0be-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="8e0be-126">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="8e0be-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e0be-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e0be-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="8e0be-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="8e0be-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8e0be-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="8e0be-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
