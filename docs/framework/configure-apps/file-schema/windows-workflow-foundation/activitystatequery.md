---
title: <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 539ce0ba72ae7a8d568cdea3a1a3aab3eec1001b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220740"
---
# <a name="activitystatequery"></a><span data-ttu-id="cc345-101">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="cc345-101">\<activityStateQuery></span></span>
<span data-ttu-id="cc345-102">Yaşam döngüsü değişiklikleri bir iş akışı örneği oluşturan etkinliklerinin izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cc345-102">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="cc345-103">Örneğin, "E-posta Gönder" etkinlik içinde bir iş akışı örneği tamamlanan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc345-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="cc345-104">Bu sorgu, etkinlik durumu kayıt nesnelerine abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cc345-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="cc345-105">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="cc345-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="cc345-106">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="cc345-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="cc345-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cc345-107">\<system.serviceModel></span></span>  
<span data-ttu-id="cc345-108">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="cc345-108">\<tracking></span></span>  
<span data-ttu-id="cc345-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="cc345-109">\<trackingProfile></span></span>  
<span data-ttu-id="cc345-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="cc345-110">\<workflow></span></span>  
<span data-ttu-id="cc345-111">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="cc345-111">\<activityStateQueries></span></span>  
<span data-ttu-id="cc345-112">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="cc345-112">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc345-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc345-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc345-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc345-114">Attributes and Elements</span></span>  
 <span data-ttu-id="cc345-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cc345-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc345-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cc345-116">Attributes</span></span>  
  
|<span data-ttu-id="cc345-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cc345-117">Attribute</span></span>|<span data-ttu-id="cc345-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc345-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc345-119">activityName</span><span class="sxs-lookup"><span data-stu-id="cc345-119">activityName</span></span>|<span data-ttu-id="cc345-120">Filtrelemek için etkinliğin adını belirten bir dize <xref:System.Activities.Tracking.ActivityStateRecord> üzerinde örnekleri.</span><span class="sxs-lookup"><span data-stu-id="cc345-120">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc345-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc345-121">Child Elements</span></span>  
  
|<span data-ttu-id="cc345-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="cc345-122">Element</span></span>|<span data-ttu-id="cc345-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc345-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc345-124">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="cc345-124">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="cc345-125">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="cc345-125">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="cc345-126">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="cc345-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="cc345-127">Kendisi için bir izleme kaydını yayılan abone olunan etkinliğin durumları içeren yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="cc345-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="cc345-128">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="cc345-128">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="cc345-129">Bu etkinlik sorguyla ilişkilendirilen değişkenlerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="cc345-129">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc345-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc345-130">Parent Elements</span></span>  
  
|<span data-ttu-id="cc345-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="cc345-131">Element</span></span>|<span data-ttu-id="cc345-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc345-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc345-133">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="cc345-133">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="cc345-134">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cc345-134">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="cc345-135">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cc345-135">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc345-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc345-136">Remarks</span></span>  
 <span data-ttu-id="cc345-137">Bir benzersiz bir ActivityStateQuery bir iş akışı yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="cc345-137">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="cc345-138">İzleme erişme post düzenlediğinizde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc345-138">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="cc345-139">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) öğeleri herhangi bir değişken veya bağımsız değişken ayıklamak için bir iş akışındaki herhangi bir etkinlikten.</span><span class="sxs-lookup"><span data-stu-id="cc345-139">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="cc345-140">Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgusu gösterir, etkinliğin `Closed` izleme kaydını yayılan.</span><span class="sxs-lookup"><span data-stu-id="cc345-140">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="cc345-141">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabileceği ve bu nedenle içinde bir izleme abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="cc345-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cc345-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc345-142">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cc345-143">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="cc345-143">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cc345-144">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="cc345-144">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
