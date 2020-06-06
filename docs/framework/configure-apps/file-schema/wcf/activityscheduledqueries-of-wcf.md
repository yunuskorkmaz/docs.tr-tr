---
title: <activityScheduledQueries>WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: c2281a9027aabfc5255ef7b09176f60d1725b522
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850502"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="38c42-102">\<activityScheduledQueries>WCF</span><span class="sxs-lookup"><span data-stu-id="38c42-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="38c42-103">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="38c42-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="38c42-104">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="38c42-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="38c42-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="38c42-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="38c42-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38c42-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38c42-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="38c42-107">Attributes and elements</span></span>  

<span data-ttu-id="38c42-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="38c42-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38c42-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="38c42-109">Attributes</span></span>  

<span data-ttu-id="38c42-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="38c42-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="38c42-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="38c42-111">Child elements</span></span>  
  
|<span data-ttu-id="38c42-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="38c42-112">Element</span></span>|<span data-ttu-id="38c42-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38c42-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="38c42-114">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="38c42-114">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="38c42-115">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="38c42-115">Parent elements</span></span>  
  
|<span data-ttu-id="38c42-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="38c42-116">Element</span></span>|<span data-ttu-id="38c42-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38c42-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="38c42-118">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="38c42-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38c42-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38c42-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="38c42-120">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="38c42-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="38c42-121">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="38c42-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
