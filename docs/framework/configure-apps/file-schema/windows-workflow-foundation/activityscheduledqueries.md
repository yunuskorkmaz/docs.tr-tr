---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: e6891144d613623b199e7279aa091d4d7cbe4445
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284563"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="c92a4-101">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="c92a4-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="c92a4-102">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c92a4-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="c92a4-103">Sorgu zamanlanmış etkinlik kayıtlarına abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c92a4-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="c92a4-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c92a4-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c92a4-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c92a4-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c92a4-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="c92a4-106">\<tracking></span></span>  
<span data-ttu-id="c92a4-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c92a4-107">\<trackingProfile></span></span>  
<span data-ttu-id="c92a4-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="c92a4-108">\<workflow></span></span>  
<span data-ttu-id="c92a4-109">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="c92a4-109">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c92a4-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c92a4-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c92a4-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c92a4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c92a4-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c92a4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c92a4-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c92a4-113">Attributes</span></span>  
 <span data-ttu-id="c92a4-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="c92a4-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c92a4-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c92a4-115">Child Elements</span></span>  
  
|<span data-ttu-id="c92a4-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="c92a4-116">Element</span></span>|<span data-ttu-id="c92a4-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c92a4-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c92a4-118">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="c92a4-118">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="c92a4-119">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="c92a4-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c92a4-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c92a4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c92a4-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="c92a4-121">Element</span></span>|<span data-ttu-id="c92a4-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c92a4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c92a4-123">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="c92a4-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c92a4-124">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="c92a4-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c92a4-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c92a4-125">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c92a4-126">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c92a4-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c92a4-127">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c92a4-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
