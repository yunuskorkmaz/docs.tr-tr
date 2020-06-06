---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 09cbc43ae4db82dc80e6985131f8d6cc0c24b2ac
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152417"
---
# \<activityScheduledQuery>
<span data-ttu-id="a50d6-101">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a50d6-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="a50d6-102">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a50d6-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="a50d6-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a50d6-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="a50d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a50d6-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a50d6-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a50d6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a50d6-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a50d6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a50d6-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a50d6-107">Attributes</span></span>  
  
|<span data-ttu-id="a50d6-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a50d6-108">Attribute</span></span>|<span data-ttu-id="a50d6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a50d6-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a50d6-110">activityName</span><span class="sxs-lookup"><span data-stu-id="a50d6-110">activityName</span></span>|<span data-ttu-id="a50d6-111">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a50d6-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="a50d6-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="a50d6-112">childActivityName</span></span>|<span data-ttu-id="a50d6-113">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a50d6-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a50d6-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a50d6-114">Child Elements</span></span>  
 <span data-ttu-id="a50d6-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="a50d6-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a50d6-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a50d6-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a50d6-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="a50d6-117">Element</span></span>|<span data-ttu-id="a50d6-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a50d6-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="a50d6-119">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="a50d6-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a50d6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a50d6-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a50d6-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a50d6-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a50d6-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a50d6-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
