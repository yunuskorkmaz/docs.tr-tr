---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 4e525bc4c77649a6c6d70ddb2408b6ecce4a0f09
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263777"
---
# <a name="customtrackingquery"></a><span data-ttu-id="d850e-101">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="d850e-101">\<customTrackingQuery></span></span>
<span data-ttu-id="d850e-102">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d850e-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="d850e-103">Sorgu özel izleme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d850e-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="d850e-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d850e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d850e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d850e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d850e-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="d850e-106">\<tracking></span></span>  
<span data-ttu-id="d850e-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d850e-107">\<trackingProfile></span></span>  
<span data-ttu-id="d850e-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="d850e-108">\<workflow></span></span>  
<span data-ttu-id="d850e-109">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="d850e-109">\<customTrackingQueries></span></span>  
<span data-ttu-id="d850e-110">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="d850e-110">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d850e-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d850e-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d850e-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d850e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d850e-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d850e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d850e-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d850e-114">Attributes</span></span>  
  
|<span data-ttu-id="d850e-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d850e-115">Attribute</span></span>|<span data-ttu-id="d850e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d850e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d850e-117">activityName</span><span class="sxs-lookup"><span data-stu-id="d850e-117">activityName</span></span>|<span data-ttu-id="d850e-118">İzleme kayıt oluşturulan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="d850e-118">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="d850e-119">name</span><span class="sxs-lookup"><span data-stu-id="d850e-119">name</span></span>|<span data-ttu-id="d850e-120">Yayılan özel izleme kayıt adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="d850e-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d850e-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d850e-121">Child Elements</span></span>  
 <span data-ttu-id="d850e-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="d850e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d850e-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d850e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d850e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="d850e-124">Element</span></span>|<span data-ttu-id="d850e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d850e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d850e-126">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="d850e-126">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="d850e-127">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="d850e-127">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d850e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d850e-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d850e-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="d850e-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d850e-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="d850e-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
