---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 5878720f51f4b5cfe3163abf316a867ccda31342
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397774"
---
# <a name="variable"></a><span data-ttu-id="421a6-101">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="421a6-101">\<variable></span></span>
<span data-ttu-id="421a6-102">Bu etkinlik sorguyla ilişkilendirilen değişkeni koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="421a6-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="421a6-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="421a6-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="421a6-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="421a6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="421a6-105">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="421a6-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="421a6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="421a6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="421a6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="421a6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="421a6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="421a6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="421a6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="421a6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="421a6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="421a6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="421a6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<değişkenler >** ](variables.md)</span><span class="sxs-lookup"><span data-stu-id="421a6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<variables>**](variables.md)</span></span>\
<span data-ttu-id="421a6-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<değişken >**</span><span class="sxs-lookup"><span data-stu-id="421a6-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="421a6-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="421a6-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="421a6-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="421a6-114">Attributes and Elements</span></span>  
 <span data-ttu-id="421a6-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="421a6-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="421a6-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="421a6-116">Attributes</span></span>  
  
|<span data-ttu-id="421a6-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="421a6-117">Attribute</span></span>|<span data-ttu-id="421a6-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="421a6-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="421a6-119">name</span><span class="sxs-lookup"><span data-stu-id="421a6-119">name</span></span>|<span data-ttu-id="421a6-120">Değişkenin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="421a6-120">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="421a6-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="421a6-121">Child Elements</span></span>  
 <span data-ttu-id="421a6-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="421a6-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="421a6-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="421a6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="421a6-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="421a6-124">Element</span></span>|<span data-ttu-id="421a6-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="421a6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="421a6-126">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="421a6-126">\<variable></span></span>](variable.md)|<span data-ttu-id="421a6-127">Bir etkinlik durumu sorgusu ile ilişkili bir değişkeni.</span><span class="sxs-lookup"><span data-stu-id="421a6-127">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="421a6-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="421a6-128">Remarks</span></span>  
 <span data-ttu-id="421a6-129">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="421a6-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="421a6-130">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="421a6-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="421a6-131">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](states.md) ve [ \<durumlar >](states.md) öğeleri için [ \<bağımsız değişkenleri](arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="421a6-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="421a6-132">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="421a6-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="421a6-133">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="421a6-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="421a6-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="421a6-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="421a6-135">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="421a6-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="421a6-136">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="421a6-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
