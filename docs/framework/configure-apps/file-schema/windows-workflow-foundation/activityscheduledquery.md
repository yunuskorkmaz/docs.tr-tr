---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 207931f68303883c29161cc28a5fc1974d01b6b8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148743"
---
# \<activityScheduledQuery>

<span data-ttu-id="e398b-101">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e398b-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="e398b-102">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e398b-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="e398b-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e398b-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="e398b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e398b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e398b-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e398b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e398b-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e398b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e398b-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e398b-107">Attributes</span></span>  
  
|<span data-ttu-id="e398b-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e398b-108">Attribute</span></span>|<span data-ttu-id="e398b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e398b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e398b-110">activityName</span><span class="sxs-lookup"><span data-stu-id="e398b-110">activityName</span></span>|<span data-ttu-id="e398b-111">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e398b-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="e398b-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="e398b-112">childActivityName</span></span>|<span data-ttu-id="e398b-113">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e398b-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e398b-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e398b-114">Child Elements</span></span>  

 <span data-ttu-id="e398b-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="e398b-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e398b-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e398b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e398b-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="e398b-117">Element</span></span>|<span data-ttu-id="e398b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e398b-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="e398b-119">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="e398b-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e398b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e398b-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e398b-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="e398b-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e398b-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="e398b-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
