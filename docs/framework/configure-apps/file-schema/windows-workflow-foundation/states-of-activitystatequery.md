---
title: <states> / <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: 0c8bf5b793684d3e6076114ce9eda7ffe1ef7a81
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398625"
---
# <a name="states-of-activitystatequery"></a><span data-ttu-id="8bf9b-102">\<\<etkinlik statequery > durumlar ></span><span class="sxs-lookup"><span data-stu-id="8bf9b-102">\<states> of \<activityStateQuery></span></span>
<span data-ttu-id="8bf9b-103">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren yapılandırma öğelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8bf9b-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="8bf9b-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8bf9b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="8bf9b-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8bf9b-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8bf9b-106">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="8bf9b-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="8bf9b-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="8bf9b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="8bf9b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="8bf9b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="8bf9b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="8bf9b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="8bf9b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="8bf9b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="8bf9b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="8bf9b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="8bf9b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<durumlar >**</span><span class="sxs-lookup"><span data-stu-id="8bf9b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bf9b-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8bf9b-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bf9b-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8bf9b-114">Attributes and Elements</span></span>  
 <span data-ttu-id="8bf9b-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8bf9b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bf9b-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8bf9b-116">Attributes</span></span>  
 <span data-ttu-id="8bf9b-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="8bf9b-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8bf9b-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8bf9b-118">Child Elements</span></span>  
  
|<span data-ttu-id="8bf9b-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="8bf9b-119">Element</span></span>|<span data-ttu-id="8bf9b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bf9b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8bf9b-121">\<durum ></span><span class="sxs-lookup"><span data-stu-id="8bf9b-121">\<state></span></span>](state-of-states.md)|<span data-ttu-id="8bf9b-122">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="8bf9b-122">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8bf9b-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8bf9b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8bf9b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="8bf9b-124">Element</span></span>|<span data-ttu-id="8bf9b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bf9b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8bf9b-126">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="8bf9b-126">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="8bf9b-127">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek için kullanılan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8bf9b-127">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="8bf9b-128">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8bf9b-128">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bf9b-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bf9b-129">Remarks</span></span>  
 <span data-ttu-id="8bf9b-130">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="8bf9b-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="8bf9b-131">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bf9b-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="8bf9b-132">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](states.md) ve [ \<durumlar >](states.md) öğeleri için [ \<bağımsız değişkenleri](arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bf9b-132">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="8bf9b-133">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8bf9b-133">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="8bf9b-134">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="8bf9b-134">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bf9b-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bf9b-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8bf9b-136">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="8bf9b-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8bf9b-137">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="8bf9b-137">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
