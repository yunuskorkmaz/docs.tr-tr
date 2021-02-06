---
description: 'Hakkında daha fazla bilgi edinin: <cancelRequestedQuery>'
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: efd908fb52d2bc32bf05fce9099c7105abdc9b1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652646"
---
# \<cancelRequestedQuery>

<span data-ttu-id="30e79-102">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="30e79-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="30e79-103">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="30e79-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="30e79-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="30e79-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="30e79-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="30e79-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30e79-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="30e79-106">Attributes and Elements</span></span>  

 <span data-ttu-id="30e79-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30e79-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30e79-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="30e79-108">Attributes</span></span>  
  
|<span data-ttu-id="30e79-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="30e79-109">Attribute</span></span>|<span data-ttu-id="30e79-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30e79-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30e79-111">activityName</span><span class="sxs-lookup"><span data-stu-id="30e79-111">activityName</span></span>|<span data-ttu-id="30e79-112">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="30e79-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="30e79-113">childActivityName</span><span class="sxs-lookup"><span data-stu-id="30e79-113">childActivityName</span></span>|<span data-ttu-id="30e79-114">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="30e79-114">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30e79-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="30e79-115">Child Elements</span></span>  

 <span data-ttu-id="30e79-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="30e79-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30e79-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="30e79-117">Parent Elements</span></span>  
  
|<span data-ttu-id="30e79-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="30e79-118">Element</span></span>|<span data-ttu-id="30e79-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30e79-119">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="30e79-120">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="30e79-120">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="30e79-121">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="30e79-121">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30e79-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30e79-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="30e79-123">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="30e79-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="30e79-124">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="30e79-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
