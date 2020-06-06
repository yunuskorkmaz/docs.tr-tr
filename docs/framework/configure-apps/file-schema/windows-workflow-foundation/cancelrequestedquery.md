---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e6840ce647625c36356cccd4651f17de32777e2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152293"
---
# \<cancelRequestedQuery>
<span data-ttu-id="00061-101">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00061-101">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="00061-102">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="00061-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="00061-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="00061-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="00061-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00061-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String"
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00061-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="00061-105">Attributes and Elements</span></span>  
 <span data-ttu-id="00061-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="00061-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00061-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="00061-107">Attributes</span></span>  
  
|<span data-ttu-id="00061-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="00061-108">Attribute</span></span>|<span data-ttu-id="00061-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00061-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00061-110">activityName</span><span class="sxs-lookup"><span data-stu-id="00061-110">activityName</span></span>|<span data-ttu-id="00061-111">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="00061-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="00061-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="00061-112">childActivityName</span></span>|<span data-ttu-id="00061-113">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="00061-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00061-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="00061-114">Child Elements</span></span>  
 <span data-ttu-id="00061-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="00061-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00061-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="00061-116">Parent Elements</span></span>  
  
|<span data-ttu-id="00061-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="00061-117">Element</span></span>|<span data-ttu-id="00061-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00061-118">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="00061-119">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00061-119">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="00061-120">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="00061-120">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00061-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00061-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="00061-122">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="00061-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="00061-123">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="00061-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
