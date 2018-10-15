---
title: WCF &lt;customTrackingQuery&gt;
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: e13064afbd9f5dbc8d7216eb384001e1e005785c
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316239"
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="13d9e-102">WCF &lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="13d9e-102">&lt;customTrackingQuery&gt; of WCF</span></span>

<span data-ttu-id="13d9e-103">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="13d9e-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="13d9e-104">Sorgu özel izleme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="13d9e-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="13d9e-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="13d9e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="13d9e-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="13d9e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="13d9e-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="13d9e-107">\<tracking></span></span>  
<span data-ttu-id="13d9e-108">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="13d9e-108">\<profiles></span></span>  
<span data-ttu-id="13d9e-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="13d9e-109">\<trackingProfile></span></span>  
<span data-ttu-id="13d9e-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="13d9e-110">\<workflow></span></span>  
<span data-ttu-id="13d9e-111">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="13d9e-111">\<customTrackingQueries></span></span>  
<span data-ttu-id="13d9e-112">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="13d9e-112">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13d9e-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13d9e-113">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="13d9e-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="13d9e-114">Attributes and elements</span></span>  

<span data-ttu-id="13d9e-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="13d9e-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13d9e-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="13d9e-116">Attributes</span></span>  
  
|<span data-ttu-id="13d9e-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="13d9e-117">Attribute</span></span>|<span data-ttu-id="13d9e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13d9e-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="13d9e-119">İzleme kayıt oluşturulan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="13d9e-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="13d9e-120">Yayılan özel izleme kayıt adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="13d9e-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13d9e-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="13d9e-121">Child elements</span></span>

<span data-ttu-id="13d9e-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="13d9e-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="13d9e-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="13d9e-123">Parent elements</span></span>

|<span data-ttu-id="13d9e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="13d9e-124">Element</span></span>|<span data-ttu-id="13d9e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13d9e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13d9e-126">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="13d9e-126">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="13d9e-127">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="13d9e-127">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="13d9e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13d9e-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="13d9e-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="13d9e-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="13d9e-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="13d9e-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
