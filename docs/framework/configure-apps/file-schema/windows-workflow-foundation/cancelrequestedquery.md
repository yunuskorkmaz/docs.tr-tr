---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e6840ce647625c36356cccd4651f17de32777e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152293"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="7d3ab-101">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="7d3ab-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="7d3ab-102">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri ni izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7d3ab-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7d3ab-103">Sorgu, bir izleme katılımcısının istek kayıt nesnelerini iptal etmek için abone olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7d3ab-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="7d3ab-104">Profil sorgularını izleme hakkında daha fazla bilgi için [bkz.](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7d3ab-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="7d3ab-105">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7d3ab-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7d3ab-106">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7d3ab-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="7d3ab-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="7d3ab-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="7d3ab-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<izlemeProfil>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="7d3ab-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="7d3ab-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<iş akışı>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7d3ab-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="7d3ab-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)</span><span class="sxs-lookup"><span data-stu-id="7d3ab-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)</span></span>\
<span data-ttu-id="7d3ab-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span><span class="sxs-lookup"><span data-stu-id="7d3ab-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d3ab-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d3ab-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d3ab-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d3ab-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7d3ab-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d3ab-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d3ab-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7d3ab-115">Attributes</span></span>  
  
|<span data-ttu-id="7d3ab-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7d3ab-116">Attribute</span></span>|<span data-ttu-id="7d3ab-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d3ab-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d3ab-118">activityName</span><span class="sxs-lookup"><span data-stu-id="7d3ab-118">activityName</span></span>|<span data-ttu-id="7d3ab-119">İptal isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7d3ab-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="7d3ab-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="7d3ab-120">childActivityName</span></span>|<span data-ttu-id="7d3ab-121">İptal inistendiği alt etkinliğin in adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7d3ab-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d3ab-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d3ab-122">Child Elements</span></span>  
 <span data-ttu-id="7d3ab-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="7d3ab-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d3ab-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d3ab-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7d3ab-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d3ab-125">Element</span></span>|<span data-ttu-id="7d3ab-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d3ab-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d3ab-127">\<hataPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="7d3ab-127">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="7d3ab-128">Alt etkinliği üst etkinlik tarafından iptal etmek için istekleri ni izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7d3ab-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7d3ab-129">Sorgu, bir izleme katılımcısının istek kayıt nesnelerini iptal etmek için abone olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7d3ab-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d3ab-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d3ab-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7d3ab-131">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="7d3ab-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7d3ab-132">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="7d3ab-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
