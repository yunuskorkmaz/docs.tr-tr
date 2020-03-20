---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 6901244009956a499458858bf73f8fd83ec52e13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152267"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="bc31b-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="bc31b-101">\<customTrackingQueries></span></span>
<span data-ttu-id="bc31b-102">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bc31b-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="bc31b-103">Sorgu, bir izleme katılımcısının özel izleme kayıtlarına abone olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bc31b-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="bc31b-104">Profil sorgularını izleme hakkında daha fazla bilgi için [bkz.](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bc31b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="bc31b-105">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bc31b-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bc31b-106">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="bc31b-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="bc31b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="bc31b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="bc31b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<izlemeProfil>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="bc31b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="bc31b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<iş akışı>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="bc31b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="bc31b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span><span class="sxs-lookup"><span data-stu-id="bc31b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc31b-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc31b-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc31b-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc31b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bc31b-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc31b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc31b-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bc31b-114">Attributes</span></span>  
 <span data-ttu-id="bc31b-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="bc31b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bc31b-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc31b-116">Child Elements</span></span>  
  
|<span data-ttu-id="bc31b-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="bc31b-117">Element</span></span>|<span data-ttu-id="bc31b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc31b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc31b-119">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="bc31b-119">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="bc31b-120">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="bc31b-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bc31b-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc31b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="bc31b-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="bc31b-122">Element</span></span>|<span data-ttu-id="bc31b-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc31b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc31b-124">\<iş akışı></span><span class="sxs-lookup"><span data-stu-id="bc31b-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="bc31b-125">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="bc31b-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc31b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc31b-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bc31b-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="bc31b-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bc31b-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="bc31b-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
