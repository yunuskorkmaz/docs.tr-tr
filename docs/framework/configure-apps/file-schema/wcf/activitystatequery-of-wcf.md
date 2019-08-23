---
title: <activityStateQuery>WCF
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: ce7505896b9c5bb605bb0f67d735cb324f4fd493
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926907"
---
# <a name="activitystatequery-of-wcf"></a><span data-ttu-id="4fb4a-102">\<WCF > activityStateQuery</span><span class="sxs-lookup"><span data-stu-id="4fb4a-102">\<activityStateQuery> of WCF</span></span>

<span data-ttu-id="4fb4a-103">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="4fb4a-104">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="4fb4a-105">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="4fb4a-106">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="4fb4a-107">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4fb4a-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="4fb4a-108">\<System. ServiceModel > \<izleme ></span><span class="sxs-lookup"><span data-stu-id="4fb4a-108">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="4fb4a-109">\<> \<TrackingProfile > profilleri</span><span class="sxs-lookup"><span data-stu-id="4fb4a-109">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="4fb4a-110">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="4fb4a-110">\<workflow></span></span>  
<span data-ttu-id="4fb4a-111">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="4fb4a-111">\<activityStateQueries></span></span>  
<span data-ttu-id="4fb4a-112">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="4fb4a-112">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fb4a-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4fb4a-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fb4a-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="4fb4a-114">Attributes and elements</span></span>  

<span data-ttu-id="4fb4a-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fb4a-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4fb4a-116">Attributes</span></span>  
  
|<span data-ttu-id="4fb4a-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4fb4a-117">Attribute</span></span>|<span data-ttu-id="4fb4a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fb4a-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fb4a-119">activityName</span><span class="sxs-lookup"><span data-stu-id="4fb4a-119">activityName</span></span>|<span data-ttu-id="4fb4a-120">Örnekleri filtreleyecek <xref:System.Activities.Tracking.ActivityStateRecord> etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-120">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fb4a-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="4fb4a-121">Child elements</span></span>  
  
|<span data-ttu-id="4fb4a-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="4fb4a-122">Element</span></span>|<span data-ttu-id="4fb4a-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fb4a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fb4a-124">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="4fb4a-124">\<arguments></span></span>](../windows-workflow-foundation/arguments.md)|<span data-ttu-id="4fb4a-125">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-125">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="4fb4a-126">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="4fb4a-126">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="4fb4a-127">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren yapılandırma öğelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="4fb4a-128">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="4fb4a-128">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="4fb4a-129">Bu etkinlik sorguyla ilişkilendirilen değişkenlerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-129">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4fb4a-130">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="4fb4a-130">Parent elements</span></span>  
  
|<span data-ttu-id="4fb4a-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="4fb4a-131">Element</span></span>|<span data-ttu-id="4fb4a-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fb4a-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fb4a-133">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="4fb4a-133">\<faultPropagationQuery></span></span>](../windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="4fb4a-134">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-134">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="4fb4a-135">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-135">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fb4a-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4fb4a-136">Remarks</span></span>

<span data-ttu-id="4fb4a-137">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-137">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="4fb4a-138">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-138">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="4fb4a-139">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](../windows-workflow-foundation/states.md) ve [ \<durumlar >](../windows-workflow-foundation/states.md) öğeleri için [ \<bağımsız değişkenleri](../windows-workflow-foundation/arguments.md)kullanabilirsiniz. Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-139">You can use the [\<arguments>](../windows-workflow-foundation/arguments.md), [\<states>](../windows-workflow-foundation/states.md) and [\<states>](../windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="4fb4a-140">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](../windows-workflow-foundation/activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-140">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4fb4a-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fb4a-141">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="4fb4a-142">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="4fb4a-142">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4fb4a-143">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="4fb4a-143">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
