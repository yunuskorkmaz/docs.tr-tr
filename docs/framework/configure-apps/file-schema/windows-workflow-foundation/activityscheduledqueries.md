---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: a43242e2f22c48a57c11f6f03657d7d3de27ff48
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398976"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="a8556-101">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="a8556-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="a8556-102">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a8556-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="a8556-103">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a8556-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="a8556-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a8556-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a8556-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a8556-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a8556-106">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a8556-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="a8556-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="a8556-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="a8556-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="a8556-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="a8556-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a8556-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="a8556-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQueries >**</span><span class="sxs-lookup"><span data-stu-id="a8556-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8556-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8556-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8556-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8556-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a8556-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8556-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8556-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8556-114">Attributes</span></span>  
 <span data-ttu-id="a8556-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="a8556-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a8556-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8556-116">Child Elements</span></span>  
  
|<span data-ttu-id="a8556-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8556-117">Element</span></span>|<span data-ttu-id="a8556-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8556-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8556-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="a8556-119">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="a8556-120">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="a8556-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8556-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8556-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a8556-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8556-122">Element</span></span>|<span data-ttu-id="a8556-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8556-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8556-124">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="a8556-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="a8556-125">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="a8556-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8556-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8556-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a8556-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a8556-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a8556-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a8556-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
