---
title: WCF &lt;activityScheduledQuery&gt;
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: fd7830bc178de0693f0632cea3b390d792408ec1
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147886"
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="49ca5-102">WCF &lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="49ca5-102">&lt;activityScheduledQuery&gt; of WCF</span></span>

<span data-ttu-id="49ca5-103">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="49ca5-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="49ca5-104">Sorgu zamanlanmış etkinlik kayıtlarına abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="49ca5-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="49ca5-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="49ca5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="49ca5-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="49ca5-106">\<system.serviceModel></span></span>  
<span data-ttu-id="49ca5-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="49ca5-107">\<tracking></span></span>  
<span data-ttu-id="49ca5-108">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="49ca5-108">\<profiles></span></span>  
<span data-ttu-id="49ca5-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="49ca5-109">\<trackingProfile></span></span>  
<span data-ttu-id="49ca5-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="49ca5-110">\<workflow></span></span>  
<span data-ttu-id="49ca5-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="49ca5-111">\<activityScheduledQueries></span></span>  
<span data-ttu-id="49ca5-112">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="49ca5-112">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49ca5-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49ca5-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49ca5-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="49ca5-114">Attributes and elements</span></span>  

<span data-ttu-id="49ca5-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="49ca5-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49ca5-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="49ca5-116">Attributes</span></span>  
  
|<span data-ttu-id="49ca5-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="49ca5-117">Attribute</span></span>|<span data-ttu-id="49ca5-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49ca5-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="49ca5-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="49ca5-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="49ca5-120">Kendisi için İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="49ca5-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49ca5-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="49ca5-121">Child elements</span></span>

<span data-ttu-id="49ca5-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="49ca5-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="49ca5-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="49ca5-123">Parent elements</span></span>  
  
|<span data-ttu-id="49ca5-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="49ca5-124">Element</span></span>|<span data-ttu-id="49ca5-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49ca5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49ca5-126">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="49ca5-126">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="49ca5-127">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu.</span><span class="sxs-lookup"><span data-stu-id="49ca5-127">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49ca5-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49ca5-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="49ca5-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="49ca5-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="49ca5-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="49ca5-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
