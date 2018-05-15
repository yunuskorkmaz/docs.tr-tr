---
title: '&lt;activityScheduledQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 6192fea9a520a3f453593e5efac964a5d32a492f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltactivityscheduledqueriesgt"></a><span data-ttu-id="afa5d-102">&lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="afa5d-102">&lt;activityScheduledQueries&gt;</span></span>
<span data-ttu-id="afa5d-103">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="afa5d-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="afa5d-104">Sorgu için zamanlanan etkinlik kayıtlarını abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="afa5d-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="afa5d-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="afa5d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="afa5d-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="afa5d-106">\<system.serviceModel></span></span>  
<span data-ttu-id="afa5d-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="afa5d-107">\<tracking></span></span>  
<span data-ttu-id="afa5d-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="afa5d-108">\<trackingProfile></span></span>  
<span data-ttu-id="afa5d-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="afa5d-109">\<workflow></span></span>  
<span data-ttu-id="afa5d-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="afa5d-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afa5d-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="afa5d-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afa5d-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="afa5d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="afa5d-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="afa5d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afa5d-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="afa5d-114">Attributes</span></span>  
 <span data-ttu-id="afa5d-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="afa5d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="afa5d-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="afa5d-116">Child Elements</span></span>  
  
|<span data-ttu-id="afa5d-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="afa5d-117">Element</span></span>|<span data-ttu-id="afa5d-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afa5d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afa5d-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="afa5d-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="afa5d-120">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="afa5d-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="afa5d-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="afa5d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="afa5d-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="afa5d-122">Element</span></span>|<span data-ttu-id="afa5d-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afa5d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afa5d-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="afa5d-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="afa5d-125">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="afa5d-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afa5d-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="afa5d-126">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="afa5d-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="afa5d-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="afa5d-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="afa5d-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
