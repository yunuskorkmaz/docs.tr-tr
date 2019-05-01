---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 663dda571990a86dc71ea927c4e97241e0ed3fc1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790227"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="f508a-101">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="f508a-101">\<customTrackingQueries></span></span>
<span data-ttu-id="f508a-102">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f508a-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="f508a-103">Sorgu özel izleme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f508a-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="f508a-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f508a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f508a-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f508a-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f508a-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="f508a-106">\<tracking></span></span>  
<span data-ttu-id="f508a-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f508a-107">\<trackingProfile></span></span>  
<span data-ttu-id="f508a-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="f508a-108">\<workflow></span></span>  
<span data-ttu-id="f508a-109">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="f508a-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f508a-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f508a-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f508a-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f508a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f508a-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f508a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f508a-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f508a-113">Attributes</span></span>  
 <span data-ttu-id="f508a-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="f508a-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f508a-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f508a-115">Child Elements</span></span>  
  
|<span data-ttu-id="f508a-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="f508a-116">Element</span></span>|<span data-ttu-id="f508a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f508a-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f508a-118">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="f508a-118">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="f508a-119">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="f508a-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f508a-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f508a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f508a-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="f508a-121">Element</span></span>|<span data-ttu-id="f508a-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f508a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f508a-123">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="f508a-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f508a-124">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="f508a-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f508a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f508a-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f508a-126">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f508a-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f508a-127">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f508a-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
