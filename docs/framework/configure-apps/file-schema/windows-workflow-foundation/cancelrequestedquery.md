---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 5de459717fdc0dbf946f12dceda18dce79ca4b06
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398811"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="d654c-101">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="d654c-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="d654c-102">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d654c-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d654c-103">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d654c-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="d654c-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d654c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="d654c-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d654c-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d654c-106">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d654c-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="d654c-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="d654c-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="d654c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="d654c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="d654c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d654c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="d654c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cancelRequestedQueries >** ](cancelrequestedqueries.md)</span><span class="sxs-lookup"><span data-stu-id="d654c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)</span></span>\
<span data-ttu-id="d654c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQuery >**</span><span class="sxs-lookup"><span data-stu-id="d654c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d654c-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d654c-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d654c-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d654c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d654c-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d654c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d654c-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d654c-115">Attributes</span></span>  
  
|<span data-ttu-id="d654c-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d654c-116">Attribute</span></span>|<span data-ttu-id="d654c-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d654c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d654c-118">activityName</span><span class="sxs-lookup"><span data-stu-id="d654c-118">activityName</span></span>|<span data-ttu-id="d654c-119">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d654c-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="d654c-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="d654c-120">childActivityName</span></span>|<span data-ttu-id="d654c-121">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d654c-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d654c-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d654c-122">Child Elements</span></span>  
 <span data-ttu-id="d654c-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="d654c-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d654c-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d654c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d654c-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="d654c-125">Element</span></span>|<span data-ttu-id="d654c-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d654c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d654c-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="d654c-127">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="d654c-128">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d654c-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d654c-129">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d654c-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d654c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d654c-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d654c-131">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="d654c-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d654c-132">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="d654c-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
