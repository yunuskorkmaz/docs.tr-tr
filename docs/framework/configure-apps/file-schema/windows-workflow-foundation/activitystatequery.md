---
title: <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 5d3c35589330ab5bed5f89c0dafac006b9e3af55
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398946"
---
# <a name="activitystatequery"></a><span data-ttu-id="015f4-101">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="015f4-101">\<activityStateQuery></span></span>
<span data-ttu-id="015f4-102">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="015f4-102">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="015f4-103">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="015f4-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="015f4-104">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="015f4-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="015f4-105">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="015f4-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="015f4-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="015f4-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="015f4-107">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="015f4-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="015f4-108">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="015f4-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="015f4-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="015f4-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="015f4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="015f4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="015f4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="015f4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="015f4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="015f4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="015f4-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQuery >**</span><span class="sxs-lookup"><span data-stu-id="015f4-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="015f4-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="015f4-114">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
        <states>
          <state name="String"/>
        </states>
        <variables>
          <variable name="String"/>
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="015f4-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="015f4-115">Attributes and Elements</span></span>  
 <span data-ttu-id="015f4-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="015f4-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="015f4-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="015f4-117">Attributes</span></span>  
  
|<span data-ttu-id="015f4-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="015f4-118">Attribute</span></span>|<span data-ttu-id="015f4-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="015f4-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="015f4-120">activityName</span><span class="sxs-lookup"><span data-stu-id="015f4-120">activityName</span></span>|<span data-ttu-id="015f4-121">Örnekleri filtreleyecek <xref:System.Activities.Tracking.ActivityStateRecord> etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="015f4-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="015f4-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="015f4-122">Child Elements</span></span>  
  
|<span data-ttu-id="015f4-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="015f4-123">Element</span></span>|<span data-ttu-id="015f4-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="015f4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="015f4-125">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="015f4-125">\<arguments></span></span>](arguments.md)|<span data-ttu-id="015f4-126">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="015f4-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="015f4-127">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="015f4-127">\<states></span></span>](states.md)|<span data-ttu-id="015f4-128">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren yapılandırma öğelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="015f4-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="015f4-129">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="015f4-129">\<states></span></span>](states.md)|<span data-ttu-id="015f4-130">Bu etkinlik sorguyla ilişkilendirilen değişkenlerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="015f4-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="015f4-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="015f4-131">Parent Elements</span></span>  
  
|<span data-ttu-id="015f4-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="015f4-132">Element</span></span>|<span data-ttu-id="015f4-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="015f4-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="015f4-134">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="015f4-134">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="015f4-135">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="015f4-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="015f4-136">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="015f4-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="015f4-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="015f4-137">Remarks</span></span>  
 <span data-ttu-id="015f4-138">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="015f4-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="015f4-139">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="015f4-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="015f4-140">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](states.md) ve [ \<durumlar >](states.md) öğeleri için [ \<bağımsız değişkenleri](arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="015f4-140">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="015f4-141">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="015f4-141">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="015f4-142">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="015f4-142">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="015f4-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="015f4-143">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="015f4-144">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="015f4-144">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="015f4-145">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="015f4-145">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
