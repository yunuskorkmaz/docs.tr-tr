---
title: <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 560df771b44fc8ba8d192657677bf0496283b539
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945423"
---
# <a name="activitystatequery"></a><span data-ttu-id="ecda7-101">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="ecda7-101">\<activityStateQuery></span></span>
<span data-ttu-id="ecda7-102">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ecda7-102">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="ecda7-103">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecda7-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="ecda7-104">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ecda7-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="ecda7-105">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ecda7-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="ecda7-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ecda7-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ecda7-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ecda7-107">\<system.serviceModel></span></span>  
<span data-ttu-id="ecda7-108">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="ecda7-108">\<tracking></span></span>  
<span data-ttu-id="ecda7-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ecda7-109">\<trackingProfile></span></span>  
<span data-ttu-id="ecda7-110">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="ecda7-110">\<workflow></span></span>  
<span data-ttu-id="ecda7-111">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="ecda7-111">\<activityStateQueries></span></span>  
<span data-ttu-id="ecda7-112">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="ecda7-112">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecda7-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ecda7-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecda7-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ecda7-114">Attributes and Elements</span></span>  
 <span data-ttu-id="ecda7-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ecda7-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecda7-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ecda7-116">Attributes</span></span>  
  
|<span data-ttu-id="ecda7-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ecda7-117">Attribute</span></span>|<span data-ttu-id="ecda7-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecda7-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ecda7-119">activityName</span><span class="sxs-lookup"><span data-stu-id="ecda7-119">activityName</span></span>|<span data-ttu-id="ecda7-120">Örnekleri filtreleyecek <xref:System.Activities.Tracking.ActivityStateRecord> etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ecda7-120">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecda7-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ecda7-121">Child Elements</span></span>  
  
|<span data-ttu-id="ecda7-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="ecda7-122">Element</span></span>|<span data-ttu-id="ecda7-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecda7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecda7-124">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="ecda7-124">\<arguments></span></span>](arguments.md)|<span data-ttu-id="ecda7-125">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ecda7-125">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="ecda7-126">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="ecda7-126">\<states></span></span>](states.md)|<span data-ttu-id="ecda7-127">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren yapılandırma öğelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ecda7-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="ecda7-128">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="ecda7-128">\<states></span></span>](states.md)|<span data-ttu-id="ecda7-129">Bu etkinlik sorguyla ilişkilendirilen değişkenlerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ecda7-129">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ecda7-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ecda7-130">Parent Elements</span></span>  
  
|<span data-ttu-id="ecda7-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="ecda7-131">Element</span></span>|<span data-ttu-id="ecda7-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecda7-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecda7-133">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="ecda7-133">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="ecda7-134">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ecda7-134">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ecda7-135">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ecda7-135">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecda7-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ecda7-136">Remarks</span></span>  
 <span data-ttu-id="ecda7-137">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="ecda7-137">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="ecda7-138">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecda7-138">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="ecda7-139">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](states.md) ve [ \<durumlar >](states.md) öğeleri için [ \<bağımsız değişkenleri](arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecda7-139">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="ecda7-140">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ecda7-140">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="ecda7-141">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="ecda7-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ecda7-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecda7-142">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ecda7-143">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="ecda7-143">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ecda7-144">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="ecda7-144">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
