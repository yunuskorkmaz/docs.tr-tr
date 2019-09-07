---
title: <state> / <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 391e552bce34d637a324c78702cb0e7121f2c999
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398659"
---
# <a name="state-of-states"></a><span data-ttu-id="14c48-102">\<\<durumların durum > ></span><span class="sxs-lookup"><span data-stu-id="14c48-102">\<state> of \<states></span></span>
<span data-ttu-id="14c48-103">Bir izleme kaydının oluşturulması gereken abone olunan etkinliğin durumunu içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="14c48-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="14c48-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="14c48-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="14c48-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="14c48-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="14c48-106">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="14c48-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="14c48-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="14c48-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="14c48-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="14c48-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="14c48-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="14c48-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="14c48-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="14c48-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="14c48-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="14c48-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="14c48-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<durumlar >** ](states-of-activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="14c48-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-activitystatequery.md)</span></span>\
<span data-ttu-id="14c48-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<durum >**</span><span class="sxs-lookup"><span data-stu-id="14c48-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14c48-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14c48-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14c48-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="14c48-115">Attributes and Elements</span></span>  
 <span data-ttu-id="14c48-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="14c48-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14c48-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="14c48-117">Attributes</span></span>  
  
|<span data-ttu-id="14c48-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="14c48-118">Attribute</span></span>|<span data-ttu-id="14c48-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14c48-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="14c48-120">name</span><span class="sxs-lookup"><span data-stu-id="14c48-120">name</span></span>|<span data-ttu-id="14c48-121">Bir izleme kaydının Yayınlanma için abone olunan etkinlik durumunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="14c48-121">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14c48-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="14c48-122">Child Elements</span></span>  
 <span data-ttu-id="14c48-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="14c48-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14c48-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="14c48-124">Parent Elements</span></span>  
  
|<span data-ttu-id="14c48-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="14c48-125">Element</span></span>|<span data-ttu-id="14c48-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14c48-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14c48-127">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="14c48-127">\<states></span></span>](states-of-activitystatequery.md)|<span data-ttu-id="14c48-128">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren yapılandırma öğelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="14c48-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14c48-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14c48-129">Remarks</span></span>  
 <span data-ttu-id="14c48-130">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="14c48-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="14c48-131">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="14c48-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="14c48-132">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](states.md) ve [ \<durumlar >](states.md) öğeleri için [ \<bağımsız değişkenleri](arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14c48-132">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="14c48-133">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="14c48-133">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="14c48-134">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="14c48-134">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="14c48-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14c48-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="14c48-136">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="14c48-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="14c48-137">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="14c48-137">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
