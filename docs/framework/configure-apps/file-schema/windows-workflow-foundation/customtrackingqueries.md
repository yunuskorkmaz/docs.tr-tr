---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: a4689e55962cd32d738682129aaa0612a4684384
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264650"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="e6b16-101">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="e6b16-101">\<customTrackingQueries></span></span>
<span data-ttu-id="e6b16-102">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e6b16-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="e6b16-103">Sorgu özel izleme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e6b16-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="e6b16-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e6b16-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e6b16-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e6b16-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e6b16-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="e6b16-106">\<tracking></span></span>  
<span data-ttu-id="e6b16-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e6b16-107">\<trackingProfile></span></span>  
<span data-ttu-id="e6b16-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="e6b16-108">\<workflow></span></span>  
<span data-ttu-id="e6b16-109">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="e6b16-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b16-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6b16-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6b16-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6b16-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e6b16-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6b16-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6b16-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e6b16-113">Attributes</span></span>  
 <span data-ttu-id="e6b16-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="e6b16-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e6b16-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6b16-115">Child Elements</span></span>  
  
|<span data-ttu-id="e6b16-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="e6b16-116">Element</span></span>|<span data-ttu-id="e6b16-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6b16-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6b16-118">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="e6b16-118">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="e6b16-119">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="e6b16-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6b16-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6b16-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e6b16-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="e6b16-121">Element</span></span>|<span data-ttu-id="e6b16-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6b16-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6b16-123">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="e6b16-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e6b16-124">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="e6b16-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6b16-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6b16-125">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e6b16-126">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="e6b16-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e6b16-127">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="e6b16-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
