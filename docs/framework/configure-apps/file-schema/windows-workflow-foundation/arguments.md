---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: f06a2188ea3561437c1453d3a1cb23d42d767f53
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398918"
---
# <a name="arguments"></a><span data-ttu-id="590f7-101">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="590f7-101">\<arguments></span></span>
<span data-ttu-id="590f7-102">Bir etkinlik durumu sorgusu ile ilişkili bağımsız değişkenler koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="590f7-102">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="590f7-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="590f7-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="590f7-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="590f7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="590f7-105">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="590f7-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="590f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="590f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="590f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="590f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="590f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="590f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="590f7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="590f7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="590f7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="590f7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="590f7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağımsız değişkenler >**</span><span class="sxs-lookup"><span data-stu-id="590f7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<arguments>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="590f7-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="590f7-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="590f7-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="590f7-113">Attributes and Elements</span></span>  
 <span data-ttu-id="590f7-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="590f7-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="590f7-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="590f7-115">Attributes</span></span>  
 <span data-ttu-id="590f7-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="590f7-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="590f7-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="590f7-117">Child Elements</span></span>  
  
|<span data-ttu-id="590f7-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="590f7-118">Element</span></span>|<span data-ttu-id="590f7-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="590f7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="590f7-120">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="590f7-120">\<argument></span></span>](argument.md)|<span data-ttu-id="590f7-121">Bir etkinlik durumu sorgusu ile ilişkili bir bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="590f7-121">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="590f7-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="590f7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="590f7-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="590f7-123">Element</span></span>|<span data-ttu-id="590f7-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="590f7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="590f7-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="590f7-125">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="590f7-126">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek için kullanılan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="590f7-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="590f7-127">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="590f7-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="590f7-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="590f7-128">Remarks</span></span>  
 <span data-ttu-id="590f7-129">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="590f7-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="590f7-130">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="590f7-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="590f7-131">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](states.md) ve [ \<durumlar >](states.md) öğeleri için [ \<bağımsız değişkenleri](arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="590f7-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="590f7-132">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="590f7-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="590f7-133">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="590f7-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="590f7-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="590f7-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="590f7-135">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="590f7-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="590f7-136">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="590f7-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
