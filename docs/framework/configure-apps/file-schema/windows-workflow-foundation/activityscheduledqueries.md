---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 763754b95a7f39c7f35e05df28589b69352168e6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152430"
---
# \<activityScheduledQueries>
<span data-ttu-id="21a60-101">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="21a60-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="21a60-102">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="21a60-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="21a60-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="21a60-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="21a60-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21a60-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21a60-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="21a60-105">Attributes and Elements</span></span>  
 <span data-ttu-id="21a60-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21a60-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21a60-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="21a60-107">Attributes</span></span>  
 <span data-ttu-id="21a60-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="21a60-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="21a60-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="21a60-109">Child Elements</span></span>  
  
|<span data-ttu-id="21a60-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="21a60-110">Element</span></span>|<span data-ttu-id="21a60-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21a60-111">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="21a60-112">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="21a60-112">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21a60-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="21a60-113">Parent Elements</span></span>  
  
|<span data-ttu-id="21a60-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="21a60-114">Element</span></span>|<span data-ttu-id="21a60-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21a60-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="21a60-116">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="21a60-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21a60-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21a60-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="21a60-118">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="21a60-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="21a60-119">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="21a60-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
