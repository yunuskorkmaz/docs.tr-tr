---
title: WCF &lt;activityScheduledQuery&gt;
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: a3c4c8b338921c9d949edd83deb4d6073eb26b55
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123377"
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="50175-102">WCF &lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="50175-102">&lt;activityScheduledQuery&gt; of WCF</span></span>

<span data-ttu-id="50175-103">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="50175-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="50175-104">Sorgu zamanlanmış etkinlik kayıtlarına abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="50175-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="50175-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="50175-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="50175-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="50175-106">\<system.serviceModel></span></span>  
<span data-ttu-id="50175-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="50175-107">\<tracking></span></span>  
<span data-ttu-id="50175-108">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="50175-108">\<profiles></span></span>  
<span data-ttu-id="50175-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="50175-109">\<trackingProfile></span></span>  
<span data-ttu-id="50175-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="50175-110">\<workflow></span></span>  
<span data-ttu-id="50175-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="50175-111">\<activityScheduledQueries></span></span>  
<span data-ttu-id="50175-112">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="50175-112">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50175-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50175-113">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"   
                                  childActivityName="String"/>
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking> 
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50175-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="50175-114">Attributes and elements</span></span>  

<span data-ttu-id="50175-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="50175-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50175-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="50175-116">Attributes</span></span>  
  
|<span data-ttu-id="50175-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="50175-117">Attribute</span></span>|<span data-ttu-id="50175-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50175-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="50175-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="50175-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="50175-120">Kendisi için İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="50175-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50175-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="50175-121">Child elements</span></span>

<span data-ttu-id="50175-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="50175-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="50175-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="50175-123">Parent elements</span></span>  
  
|<span data-ttu-id="50175-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="50175-124">Element</span></span>|<span data-ttu-id="50175-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50175-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50175-126">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="50175-126">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="50175-127">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu.</span><span class="sxs-lookup"><span data-stu-id="50175-127">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50175-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50175-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="50175-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="50175-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="50175-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="50175-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
