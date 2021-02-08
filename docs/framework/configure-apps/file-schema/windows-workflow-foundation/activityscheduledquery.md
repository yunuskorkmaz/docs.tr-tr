---
description: 'Hakkında daha fazla bilgi edinin: <activityScheduledQuery>'
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 72aa9c2d3480488d4468d008fa8a4306929c190d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802118"
---
# \<activityScheduledQuery>

<span data-ttu-id="80293-102">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="80293-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="80293-103">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="80293-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="80293-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="80293-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="80293-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="80293-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80293-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="80293-106">Attributes and Elements</span></span>  

 <span data-ttu-id="80293-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80293-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80293-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="80293-108">Attributes</span></span>  
  
|<span data-ttu-id="80293-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="80293-109">Attribute</span></span>|<span data-ttu-id="80293-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80293-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80293-111">activityName</span><span class="sxs-lookup"><span data-stu-id="80293-111">activityName</span></span>|<span data-ttu-id="80293-112">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="80293-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="80293-113">childActivityName</span><span class="sxs-lookup"><span data-stu-id="80293-113">childActivityName</span></span>|<span data-ttu-id="80293-114">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="80293-114">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80293-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="80293-115">Child Elements</span></span>  

 <span data-ttu-id="80293-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="80293-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80293-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="80293-117">Parent Elements</span></span>  
  
|<span data-ttu-id="80293-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="80293-118">Element</span></span>|<span data-ttu-id="80293-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80293-119">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="80293-120">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="80293-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80293-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80293-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="80293-122">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="80293-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="80293-123">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="80293-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
