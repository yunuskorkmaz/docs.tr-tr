---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 763754b95a7f39c7f35e05df28589b69352168e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152430"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="2b2c4-101">\<etkinlikPlanlanmışSorgular></span><span class="sxs-lookup"><span data-stu-id="2b2c4-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="2b2c4-102">Bir üst etkinlik tarafından yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgukoleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2b2c4-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="2b2c4-103">Sorgu, bir izleme katılımcısının etkinlik zamanlanan kayıtlara abone olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2b2c4-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="2b2c4-104">Profil sorgularını izleme hakkında daha fazla bilgi için [bkz.](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2b2c4-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="2b2c4-105">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b2c4-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2b2c4-106">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2b2c4-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="2b2c4-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="2b2c4-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="2b2c4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<izlemeProfil>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="2b2c4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="2b2c4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<iş akışı>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2b2c4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="2b2c4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etkinlikPlanlanmışSorgular>**</span><span class="sxs-lookup"><span data-stu-id="2b2c4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b2c4-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b2c4-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b2c4-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b2c4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2b2c4-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b2c4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b2c4-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2b2c4-114">Attributes</span></span>  
 <span data-ttu-id="2b2c4-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="2b2c4-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2b2c4-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b2c4-116">Child Elements</span></span>  
  
|<span data-ttu-id="2b2c4-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b2c4-117">Element</span></span>|<span data-ttu-id="2b2c4-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b2c4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b2c4-119">\<etkinlikScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="2b2c4-119">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="2b2c4-120">Bir üst etkinlik tarafından yürütülmesi için zamanlanan bir etkinliği izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="2b2c4-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b2c4-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b2c4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2b2c4-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b2c4-122">Element</span></span>|<span data-ttu-id="2b2c4-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b2c4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b2c4-124">\<iş akışı></span><span class="sxs-lookup"><span data-stu-id="2b2c4-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="2b2c4-125">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="2b2c4-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b2c4-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b2c4-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2b2c4-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="2b2c4-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2b2c4-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="2b2c4-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
