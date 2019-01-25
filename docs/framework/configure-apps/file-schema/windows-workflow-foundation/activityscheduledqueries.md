---
title: '&lt;activityScheduledQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 2285dfae84f078483c03d85801051e29b79e74c3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561848"
---
# <a name="ltactivityscheduledqueriesgt"></a><span data-ttu-id="c6610-102">&lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="c6610-102">&lt;activityScheduledQueries&gt;</span></span>
<span data-ttu-id="c6610-103">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c6610-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="c6610-104">Sorgu zamanlanmış etkinlik kayıtlarına abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c6610-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="c6610-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c6610-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c6610-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c6610-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c6610-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="c6610-107">\<tracking></span></span>  
<span data-ttu-id="c6610-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c6610-108">\<trackingProfile></span></span>  
<span data-ttu-id="c6610-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="c6610-109">\<workflow></span></span>  
<span data-ttu-id="c6610-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="c6610-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6610-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6610-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6610-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6610-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c6610-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6610-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6610-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c6610-114">Attributes</span></span>  
 <span data-ttu-id="c6610-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="c6610-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c6610-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6610-116">Child Elements</span></span>  
  
|<span data-ttu-id="c6610-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6610-117">Element</span></span>|<span data-ttu-id="c6610-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6610-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6610-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="c6610-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="c6610-120">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="c6610-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6610-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6610-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c6610-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6610-122">Element</span></span>|<span data-ttu-id="c6610-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6610-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6610-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="c6610-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c6610-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="c6610-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6610-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6610-126">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c6610-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c6610-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c6610-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c6610-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
