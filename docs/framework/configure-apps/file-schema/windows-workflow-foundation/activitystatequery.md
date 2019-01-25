---
title: '&lt;activityStateQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 7b872d933d07af329601063b3d769bc43a22007c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568679"
---
# <a name="ltactivitystatequerygt"></a><span data-ttu-id="12a4f-102">&lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="12a4f-102">&lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="12a4f-103">Yaşam döngüsü değişiklikleri bir iş akışı örneği oluşturan etkinliklerinin izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="12a4f-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="12a4f-104">Örneğin, "E-posta Gönder" etkinlik içinde bir iş akışı örneği tamamlanan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12a4f-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="12a4f-105">Bu sorgu, etkinlik durumu kayıt nesnelerine abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="12a4f-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="12a4f-106">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="12a4f-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="12a4f-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="12a4f-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="12a4f-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="12a4f-108">\<system.serviceModel></span></span>  
<span data-ttu-id="12a4f-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="12a4f-109">\<tracking></span></span>  
<span data-ttu-id="12a4f-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="12a4f-110">\<trackingProfile></span></span>  
<span data-ttu-id="12a4f-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="12a4f-111">\<workflow></span></span>  
<span data-ttu-id="12a4f-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="12a4f-112">\<activityStateQueries></span></span>  
<span data-ttu-id="12a4f-113">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="12a4f-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12a4f-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12a4f-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12a4f-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="12a4f-115">Attributes and Elements</span></span>  
 <span data-ttu-id="12a4f-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="12a4f-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12a4f-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="12a4f-117">Attributes</span></span>  
  
|<span data-ttu-id="12a4f-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="12a4f-118">Attribute</span></span>|<span data-ttu-id="12a4f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12a4f-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12a4f-120">activityName</span><span class="sxs-lookup"><span data-stu-id="12a4f-120">activityName</span></span>|<span data-ttu-id="12a4f-121">Filtrelemek için etkinliğin adını belirten bir dize <xref:System.Activities.Tracking.ActivityStateRecord> üzerinde örnekleri.</span><span class="sxs-lookup"><span data-stu-id="12a4f-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12a4f-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="12a4f-122">Child Elements</span></span>  
  
|<span data-ttu-id="12a4f-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="12a4f-123">Element</span></span>|<span data-ttu-id="12a4f-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12a4f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12a4f-125">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="12a4f-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="12a4f-126">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="12a4f-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="12a4f-127">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="12a4f-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="12a4f-128">Kendisi için bir izleme kaydını yayılan abone olunan etkinliğin durumları içeren yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="12a4f-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="12a4f-129">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="12a4f-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="12a4f-130">Bu etkinlik sorguyla ilişkilendirilen değişkenlerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="12a4f-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12a4f-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="12a4f-131">Parent Elements</span></span>  
  
|<span data-ttu-id="12a4f-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="12a4f-132">Element</span></span>|<span data-ttu-id="12a4f-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12a4f-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12a4f-134">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="12a4f-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="12a4f-135">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="12a4f-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="12a4f-136">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="12a4f-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12a4f-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12a4f-137">Remarks</span></span>  
 <span data-ttu-id="12a4f-138">Bir benzersiz bir ActivityStateQuery bir iş akışı yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="12a4f-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="12a4f-139">İzleme erişme post düzenlediğinizde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="12a4f-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="12a4f-140">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) öğeleri herhangi bir değişken veya bağımsız değişken ayıklamak için bir iş akışındaki herhangi bir etkinlikten.</span><span class="sxs-lookup"><span data-stu-id="12a4f-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="12a4f-141">Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgusu gösterir, etkinliğin `Closed` izleme kaydını yayılan.</span><span class="sxs-lookup"><span data-stu-id="12a4f-141">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="12a4f-142">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabileceği ve bu nedenle içinde bir izleme abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="12a4f-142">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12a4f-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12a4f-143">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="12a4f-144">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="12a4f-144">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="12a4f-145">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="12a4f-145">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
