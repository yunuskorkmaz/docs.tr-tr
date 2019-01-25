---
title: '&lt;customTrackingQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 9ee5a4a25d379eafb936098597df1ec61ff09f0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725863"
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="d87b6-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="d87b6-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="d87b6-103">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d87b6-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="d87b6-104">Sorgu özel izleme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d87b6-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="d87b6-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d87b6-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d87b6-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d87b6-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d87b6-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="d87b6-107">\<tracking></span></span>  
<span data-ttu-id="d87b6-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d87b6-108">\<trackingProfile></span></span>  
<span data-ttu-id="d87b6-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="d87b6-109">\<workflow></span></span>  
<span data-ttu-id="d87b6-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="d87b6-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="d87b6-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="d87b6-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d87b6-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d87b6-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d87b6-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d87b6-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d87b6-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d87b6-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d87b6-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d87b6-115">Attributes</span></span>  
  
|<span data-ttu-id="d87b6-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d87b6-116">Attribute</span></span>|<span data-ttu-id="d87b6-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d87b6-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d87b6-118">activityName</span><span class="sxs-lookup"><span data-stu-id="d87b6-118">activityName</span></span>|<span data-ttu-id="d87b6-119">İzleme kayıt oluşturulan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="d87b6-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="d87b6-120">name</span><span class="sxs-lookup"><span data-stu-id="d87b6-120">name</span></span>|<span data-ttu-id="d87b6-121">Yayılan özel izleme kayıt adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="d87b6-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d87b6-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d87b6-122">Child Elements</span></span>  
 <span data-ttu-id="d87b6-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="d87b6-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d87b6-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d87b6-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d87b6-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="d87b6-125">Element</span></span>|<span data-ttu-id="d87b6-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d87b6-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d87b6-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="d87b6-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="d87b6-128">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="d87b6-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d87b6-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d87b6-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d87b6-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="d87b6-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d87b6-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="d87b6-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
