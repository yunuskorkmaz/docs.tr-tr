---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 663dda571990a86dc71ea927c4e97241e0ed3fc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120087"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="9be95-101">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="9be95-101">\<customTrackingQueries></span></span>
<span data-ttu-id="9be95-102">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9be95-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="9be95-103">Sorgu özel izleme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9be95-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="9be95-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9be95-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="9be95-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9be95-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9be95-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="9be95-106">\<tracking></span></span>  
<span data-ttu-id="9be95-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9be95-107">\<trackingProfile></span></span>  
<span data-ttu-id="9be95-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="9be95-108">\<workflow></span></span>  
<span data-ttu-id="9be95-109">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="9be95-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9be95-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9be95-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9be95-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9be95-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9be95-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9be95-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9be95-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9be95-113">Attributes</span></span>  
 <span data-ttu-id="9be95-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="9be95-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9be95-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9be95-115">Child Elements</span></span>  
  
|<span data-ttu-id="9be95-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="9be95-116">Element</span></span>|<span data-ttu-id="9be95-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9be95-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9be95-118">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="9be95-118">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="9be95-119">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="9be95-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9be95-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9be95-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9be95-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="9be95-121">Element</span></span>|<span data-ttu-id="9be95-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9be95-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9be95-123">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="9be95-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="9be95-124">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="9be95-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9be95-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9be95-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9be95-126">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="9be95-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9be95-127">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="9be95-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
