---
description: WCF hakkında daha fazla bilgi edinin <activityStateQuery>
title: <activityStateQuery> WCF
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: fff8f6ac793df9b0a355dfbed859b3a88178002a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725928"
---
# <a name="activitystatequery-of-wcf"></a><span data-ttu-id="5caf4-103">\<activityStateQuery> WCF</span><span class="sxs-lookup"><span data-stu-id="5caf4-103">\<activityStateQuery> of WCF</span></span>

<span data-ttu-id="5caf4-104">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5caf4-104">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="5caf4-105">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5caf4-105">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="5caf4-106">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5caf4-106">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="5caf4-107">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5caf4-107">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="5caf4-108">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5caf4-108">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="5caf4-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="5caf4-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5caf4-110">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="5caf4-110">Attributes and elements</span></span>  

<span data-ttu-id="5caf4-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5caf4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5caf4-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5caf4-112">Attributes</span></span>  
  
|<span data-ttu-id="5caf4-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5caf4-113">Attribute</span></span>|<span data-ttu-id="5caf4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5caf4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5caf4-115">activityName</span><span class="sxs-lookup"><span data-stu-id="5caf4-115">activityName</span></span>|<span data-ttu-id="5caf4-116">Örnekleri filtreleyecek etkinliğin adını belirten bir dize <xref:System.Activities.Tracking.ActivityStateRecord> .</span><span class="sxs-lookup"><span data-stu-id="5caf4-116">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5caf4-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="5caf4-117">Child elements</span></span>  
  
|<span data-ttu-id="5caf4-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="5caf4-118">Element</span></span>|<span data-ttu-id="5caf4-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5caf4-119">Description</span></span>|  
|-------------|-----------------|  
|[\<arguments>](../windows-workflow-foundation/arguments.md)|<span data-ttu-id="5caf4-120">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5caf4-120">A collection of arguments associated with this activity query.</span></span>|  
|[\<states>](../windows-workflow-foundation/states.md)|<span data-ttu-id="5caf4-121">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren yapılandırma öğelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5caf4-121">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[\<states>](../windows-workflow-foundation/states.md)|<span data-ttu-id="5caf4-122">Bu etkinlik sorguyla ilişkilendirilen değişkenlerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5caf4-122">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5caf4-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="5caf4-123">Parent elements</span></span>  
  
|<span data-ttu-id="5caf4-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="5caf4-124">Element</span></span>|<span data-ttu-id="5caf4-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5caf4-125">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](../windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="5caf4-126">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5caf4-126">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5caf4-127">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5caf4-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5caf4-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5caf4-128">Remarks</span></span>

<span data-ttu-id="5caf4-129">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="5caf4-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="5caf4-130">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="5caf4-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="5caf4-131">[\<arguments>](../windows-workflow-foundation/arguments.md) [\<states>](../windows-workflow-foundation/states.md) [\<states>](../windows-workflow-foundation/states.md) Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişken çıkarmak için ve öğelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5caf4-131">You can use the [\<arguments>](../windows-workflow-foundation/arguments.md), [\<states>](../windows-workflow-foundation/states.md) and [\<states>](../windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="5caf4-132">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5caf4-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="5caf4-133">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle kullanılarak bir izleme profili içinde abone olunmuş olur [\<activityStateQuery>](../windows-workflow-foundation/activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="5caf4-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5caf4-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5caf4-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="5caf4-135">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="5caf4-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5caf4-136">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="5caf4-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
