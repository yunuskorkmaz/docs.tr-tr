---
title: <activityStateQuery>WCF
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: 49c507424e813067e1dad9b08167d9661acef36f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991224"
---
# <a name="activitystatequery-of-wcf"></a><span data-ttu-id="150c1-102">\<WCF > activityStateQuery</span><span class="sxs-lookup"><span data-stu-id="150c1-102">\<activityStateQuery> of WCF</span></span>

<span data-ttu-id="150c1-103">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="150c1-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="150c1-104">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="150c1-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="150c1-105">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="150c1-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="150c1-106">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="150c1-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="150c1-107">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="150c1-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="150c1-108">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="150c1-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="150c1-109">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="150c1-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="150c1-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="150c1-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="150c1-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="150c1-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="150c1-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="150c1-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="150c1-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="150c1-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="150c1-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="150c1-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries-of-wcf.md)</span></span>\
<span data-ttu-id="150c1-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQuery >**</span><span class="sxs-lookup"><span data-stu-id="150c1-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="150c1-116">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="150c1-116">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="150c1-117">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="150c1-117">Attributes and elements</span></span>  

<span data-ttu-id="150c1-118">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="150c1-118">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="150c1-119">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="150c1-119">Attributes</span></span>  
  
|<span data-ttu-id="150c1-120">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="150c1-120">Attribute</span></span>|<span data-ttu-id="150c1-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="150c1-121">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="150c1-122">activityName</span><span class="sxs-lookup"><span data-stu-id="150c1-122">activityName</span></span>|<span data-ttu-id="150c1-123">Örnekleri filtreleyecek <xref:System.Activities.Tracking.ActivityStateRecord> etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="150c1-123">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="150c1-124">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="150c1-124">Child elements</span></span>  
  
|<span data-ttu-id="150c1-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="150c1-125">Element</span></span>|<span data-ttu-id="150c1-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="150c1-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="150c1-127">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="150c1-127">\<arguments></span></span>](../windows-workflow-foundation/arguments.md)|<span data-ttu-id="150c1-128">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="150c1-128">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="150c1-129">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="150c1-129">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="150c1-130">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren yapılandırma öğelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="150c1-130">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="150c1-131">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="150c1-131">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="150c1-132">Bu etkinlik sorguyla ilişkilendirilen değişkenlerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="150c1-132">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="150c1-133">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="150c1-133">Parent elements</span></span>  
  
|<span data-ttu-id="150c1-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="150c1-134">Element</span></span>|<span data-ttu-id="150c1-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="150c1-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="150c1-136">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="150c1-136">\<faultPropagationQuery></span></span>](../windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="150c1-137">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="150c1-137">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="150c1-138">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="150c1-138">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="150c1-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="150c1-139">Remarks</span></span>

<span data-ttu-id="150c1-140">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="150c1-140">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="150c1-141">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="150c1-141">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="150c1-142">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](../windows-workflow-foundation/states.md) ve [ \<durumlar >](../windows-workflow-foundation/states.md) öğeleri için [ \<bağımsız değişkenleri](../windows-workflow-foundation/arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="150c1-142">You can use the [\<arguments>](../windows-workflow-foundation/arguments.md), [\<states>](../windows-workflow-foundation/states.md) and [\<states>](../windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="150c1-143">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="150c1-143">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="150c1-144">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](../windows-workflow-foundation/activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="150c1-144">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed" />
  </states>
  <variables>
    <variable name="FromAddress" />
  </variables>
  <arguments>
    <argument name="Result" />
  </arguments>
</activityStateQuery>
```  
  
## <a name="see-also"></a><span data-ttu-id="150c1-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="150c1-145">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="150c1-146">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="150c1-146">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="150c1-147">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="150c1-147">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
