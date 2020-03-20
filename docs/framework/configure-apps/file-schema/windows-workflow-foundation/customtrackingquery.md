---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: a02d71811709b2c285ab7081b89ee3082ec5b43d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152215"
---
# <a name="customtrackingquery"></a><span data-ttu-id="c20e3-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="c20e3-101">\<customTrackingQuery></span></span>
<span data-ttu-id="c20e3-102">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c20e3-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="c20e3-103">Sorgu, bir izleme katılımcısının özel izleme kayıtlarına abone olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c20e3-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="c20e3-104">Profil sorgularını izleme hakkında daha fazla bilgi için [bkz.](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c20e3-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c20e3-105">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c20e3-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c20e3-106">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c20e3-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="c20e3-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="c20e3-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="c20e3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<izlemeProfil>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="c20e3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="c20e3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<iş akışı>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c20e3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="c20e3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)</span><span class="sxs-lookup"><span data-stu-id="c20e3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)</span></span>\
<span data-ttu-id="c20e3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span><span class="sxs-lookup"><span data-stu-id="c20e3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c20e3-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c20e3-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c20e3-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c20e3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c20e3-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c20e3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c20e3-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c20e3-115">Attributes</span></span>  
  
|<span data-ttu-id="c20e3-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c20e3-116">Attribute</span></span>|<span data-ttu-id="c20e3-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c20e3-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c20e3-118">activityName</span><span class="sxs-lookup"><span data-stu-id="c20e3-118">activityName</span></span>|<span data-ttu-id="c20e3-119">İzleme kaydını oluşturan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="c20e3-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="c20e3-120">ad</span><span class="sxs-lookup"><span data-stu-id="c20e3-120">name</span></span>|<span data-ttu-id="c20e3-121">Yayılan özel izleme kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c20e3-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c20e3-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c20e3-122">Child Elements</span></span>  
 <span data-ttu-id="c20e3-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="c20e3-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c20e3-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c20e3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c20e3-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c20e3-125">Element</span></span>|<span data-ttu-id="c20e3-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c20e3-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c20e3-127">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="c20e3-127">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="c20e3-128">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="c20e3-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c20e3-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c20e3-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c20e3-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c20e3-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c20e3-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c20e3-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
