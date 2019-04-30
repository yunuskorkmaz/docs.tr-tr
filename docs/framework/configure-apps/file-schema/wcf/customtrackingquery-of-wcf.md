---
title: <customTrackingQuery> WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 0a5e7c034ce1ef12a8d7d5b1753e2e441e48e293
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673179"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="839e2-102">\<customTrackingQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="839e2-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="839e2-103">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="839e2-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="839e2-104">Sorgu özel izleme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="839e2-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="839e2-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="839e2-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="839e2-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="839e2-106">\<system.serviceModel></span></span>  
<span data-ttu-id="839e2-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="839e2-107">\<tracking></span></span>  
<span data-ttu-id="839e2-108">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="839e2-108">\<profiles></span></span>  
<span data-ttu-id="839e2-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="839e2-109">\<trackingProfile></span></span>  
<span data-ttu-id="839e2-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="839e2-110">\<workflow></span></span>  
<span data-ttu-id="839e2-111">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="839e2-111">\<customTrackingQueries></span></span>  
<span data-ttu-id="839e2-112">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="839e2-112">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="839e2-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="839e2-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="839e2-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="839e2-114">Attributes and elements</span></span>  

<span data-ttu-id="839e2-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="839e2-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="839e2-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="839e2-116">Attributes</span></span>  
  
|<span data-ttu-id="839e2-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="839e2-117">Attribute</span></span>|<span data-ttu-id="839e2-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="839e2-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="839e2-119">İzleme kayıt oluşturulan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="839e2-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="839e2-120">Yayılan özel izleme kayıt adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="839e2-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="839e2-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="839e2-121">Child elements</span></span>

<span data-ttu-id="839e2-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="839e2-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="839e2-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="839e2-123">Parent elements</span></span>

|<span data-ttu-id="839e2-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="839e2-124">Element</span></span>|<span data-ttu-id="839e2-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="839e2-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="839e2-126">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="839e2-126">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="839e2-127">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="839e2-127">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="839e2-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="839e2-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="839e2-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="839e2-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="839e2-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="839e2-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
