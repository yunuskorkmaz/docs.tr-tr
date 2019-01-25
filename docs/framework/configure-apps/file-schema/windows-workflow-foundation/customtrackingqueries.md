---
title: '&lt;customTrackingQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 757bbe500ec3edccef465b7ff23b2c974e4a5011
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598847"
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="18c8c-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="18c8c-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="18c8c-103">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="18c8c-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="18c8c-104">Sorgu özel izleme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="18c8c-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="18c8c-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="18c8c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="18c8c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="18c8c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="18c8c-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="18c8c-107">\<tracking></span></span>  
<span data-ttu-id="18c8c-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="18c8c-108">\<trackingProfile></span></span>  
<span data-ttu-id="18c8c-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="18c8c-109">\<workflow></span></span>  
<span data-ttu-id="18c8c-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="18c8c-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18c8c-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18c8c-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18c8c-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="18c8c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="18c8c-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="18c8c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18c8c-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="18c8c-114">Attributes</span></span>  
 <span data-ttu-id="18c8c-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="18c8c-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="18c8c-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="18c8c-116">Child Elements</span></span>  
  
|<span data-ttu-id="18c8c-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="18c8c-117">Element</span></span>|<span data-ttu-id="18c8c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18c8c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18c8c-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="18c8c-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="18c8c-120">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="18c8c-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18c8c-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="18c8c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="18c8c-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="18c8c-122">Element</span></span>|<span data-ttu-id="18c8c-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18c8c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18c8c-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="18c8c-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="18c8c-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="18c8c-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18c8c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18c8c-126">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="18c8c-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="18c8c-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="18c8c-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="18c8c-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
