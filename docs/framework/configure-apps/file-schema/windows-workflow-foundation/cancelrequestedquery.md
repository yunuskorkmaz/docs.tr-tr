---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: a50e9965a595fce64c383313091334e883dcfbfa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189493"
---
# \<cancelRequestedQuery>

<span data-ttu-id="3062b-101">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3062b-101">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="3062b-102">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3062b-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="3062b-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="3062b-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="3062b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3062b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3062b-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3062b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3062b-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3062b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3062b-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3062b-107">Attributes</span></span>  
  
|<span data-ttu-id="3062b-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3062b-108">Attribute</span></span>|<span data-ttu-id="3062b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3062b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3062b-110">activityName</span><span class="sxs-lookup"><span data-stu-id="3062b-110">activityName</span></span>|<span data-ttu-id="3062b-111">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3062b-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="3062b-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="3062b-112">childActivityName</span></span>|<span data-ttu-id="3062b-113">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3062b-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3062b-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3062b-114">Child Elements</span></span>  

 <span data-ttu-id="3062b-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="3062b-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3062b-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3062b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3062b-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="3062b-117">Element</span></span>|<span data-ttu-id="3062b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3062b-118">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="3062b-119">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3062b-119">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="3062b-120">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3062b-120">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3062b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3062b-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3062b-122">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="3062b-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3062b-123">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="3062b-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
