---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: aa6ee435c66303b5089b459ecc4ed3023297636d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398965"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="f373f-101">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="f373f-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="f373f-102">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f373f-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="f373f-103">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f373f-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="f373f-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f373f-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f373f-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f373f-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f373f-106">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f373f-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="f373f-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="f373f-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="f373f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="f373f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="f373f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f373f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="f373f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityScheduledQueries >** ](activityscheduledqueries.md)</span><span class="sxs-lookup"><span data-stu-id="f373f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)</span></span>\
<span data-ttu-id="f373f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQuery >**</span><span class="sxs-lookup"><span data-stu-id="f373f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f373f-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f373f-112">Syntax</span></span>  
  
```xml 
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f373f-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f373f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f373f-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f373f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f373f-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f373f-115">Attributes</span></span>  
  
|<span data-ttu-id="f373f-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f373f-116">Attribute</span></span>|<span data-ttu-id="f373f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f373f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f373f-118">activityName</span><span class="sxs-lookup"><span data-stu-id="f373f-118">activityName</span></span>|<span data-ttu-id="f373f-119">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f373f-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="f373f-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="f373f-120">childActivityName</span></span>|<span data-ttu-id="f373f-121">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f373f-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f373f-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f373f-122">Child Elements</span></span>  
 <span data-ttu-id="f373f-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="f373f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f373f-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f373f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f373f-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="f373f-125">Element</span></span>|<span data-ttu-id="f373f-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f373f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f373f-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="f373f-127">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="f373f-128">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="f373f-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f373f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f373f-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f373f-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f373f-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f373f-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f373f-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
