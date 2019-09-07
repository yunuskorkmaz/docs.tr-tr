---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: ed08f5533cd6b3839775d061452cb17110cc627e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398902"
---
# <a name="argument"></a><span data-ttu-id="ced1d-101">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="ced1d-101">\<argument></span></span>
<span data-ttu-id="ced1d-102">Bir etkinlik durumu sorgusu ile ilişkili bir bağımsız değişken temsil eden bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ced1d-102">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="ced1d-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ced1d-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ced1d-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ced1d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ced1d-105">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ced1d-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="ced1d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="ced1d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="ced1d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="ced1d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="ced1d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ced1d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="ced1d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="ced1d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="ced1d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="ced1d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="ced1d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağımsız değişkenler >** ](arguments.md)</span><span class="sxs-lookup"><span data-stu-id="ced1d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<arguments>**](arguments.md)</span></span>\
<span data-ttu-id="ced1d-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağımsız değişken >**</span><span class="sxs-lookup"><span data-stu-id="ced1d-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<argument>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ced1d-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ced1d-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ced1d-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ced1d-114">Attributes and Elements</span></span>  
 <span data-ttu-id="ced1d-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ced1d-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ced1d-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ced1d-116">Attributes</span></span>  
  
|<span data-ttu-id="ced1d-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ced1d-117">Attribute</span></span>|<span data-ttu-id="ced1d-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ced1d-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ced1d-119">name</span><span class="sxs-lookup"><span data-stu-id="ced1d-119">name</span></span>|<span data-ttu-id="ced1d-120">Bağımsız değişkenin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ced1d-120">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ced1d-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ced1d-121">Child Elements</span></span>  
 <span data-ttu-id="ced1d-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="ced1d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ced1d-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ced1d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ced1d-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="ced1d-124">Element</span></span>|<span data-ttu-id="ced1d-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ced1d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ced1d-126">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="ced1d-126">\<arguments></span></span>](arguments.md)|<span data-ttu-id="ced1d-127">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ced1d-127">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ced1d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ced1d-128">Remarks</span></span>  
 <span data-ttu-id="ced1d-129">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="ced1d-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="ced1d-130">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="ced1d-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="ced1d-131">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](states.md) ve [ \<durumlar >](states.md) öğeleri için [ \<bağımsız değişkenleri](arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ced1d-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="ced1d-132">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ced1d-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="ced1d-133">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="ced1d-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ced1d-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ced1d-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ced1d-135">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="ced1d-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ced1d-136">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="ced1d-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
