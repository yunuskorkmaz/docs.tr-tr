---
title: WCF &lt;activityStateQuery&gt;
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: 6d55a53a6344922cee0d42c26102d5f0bbf46f67
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151797"
---
# <a name="ltactivitystatequerygt-of-wcf"></a><span data-ttu-id="d1e43-102">WCF &lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="d1e43-102">&lt;activityStateQuery&gt; of WCF</span></span>

<span data-ttu-id="d1e43-103">Yaşam döngüsü değişiklikleri bir iş akışı örneği oluşturan etkinliklerinin izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d1e43-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="d1e43-104">Örneğin, "E-posta Gönder" etkinlik içinde bir iş akışı örneği tamamlanan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1e43-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="d1e43-105">Bu sorgu, etkinlik durumu kayıt nesnelerine abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d1e43-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="d1e43-106">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d1e43-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="d1e43-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d1e43-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="d1e43-108">\<system.serviceModel > \<İzleme ></span><span class="sxs-lookup"><span data-stu-id="d1e43-108">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="d1e43-109">\<profilleri > \<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="d1e43-109">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="d1e43-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="d1e43-110">\<workflow></span></span>  
<span data-ttu-id="d1e43-111">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="d1e43-111">\<activityStateQueries></span></span>  
<span data-ttu-id="d1e43-112">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="d1e43-112">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1e43-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1e43-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1e43-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="d1e43-114">Attributes and elements</span></span>  

<span data-ttu-id="d1e43-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1e43-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1e43-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d1e43-116">Attributes</span></span>  
  
|<span data-ttu-id="d1e43-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d1e43-117">Attribute</span></span>|<span data-ttu-id="d1e43-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1e43-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1e43-119">activityName</span><span class="sxs-lookup"><span data-stu-id="d1e43-119">activityName</span></span>|<span data-ttu-id="d1e43-120">Filtrelemek için etkinliğin adını belirten bir dize <xref:System.Activities.Tracking.ActivityStateRecord> üzerinde örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d1e43-120">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1e43-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d1e43-121">Child elements</span></span>  
  
|<span data-ttu-id="d1e43-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="d1e43-122">Element</span></span>|<span data-ttu-id="d1e43-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1e43-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1e43-124">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="d1e43-124">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="d1e43-125">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d1e43-125">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="d1e43-126">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="d1e43-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="d1e43-127">Kendisi için bir izleme kaydını yayılan abone olunan etkinliğin durumları içeren yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d1e43-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="d1e43-128">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="d1e43-128">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="d1e43-129">Bu etkinlik sorguyla ilişkilendirilen değişkenlerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d1e43-129">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1e43-130">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="d1e43-130">Parent elements</span></span>  
  
|<span data-ttu-id="d1e43-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="d1e43-131">Element</span></span>|<span data-ttu-id="d1e43-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1e43-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1e43-133">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="d1e43-133">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="d1e43-134">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d1e43-134">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d1e43-135">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d1e43-135">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1e43-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1e43-136">Remarks</span></span>

<span data-ttu-id="d1e43-137">Bir benzersiz bir ActivityStateQuery bir iş akışı yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="d1e43-137">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="d1e43-138">İzleme erişme post düzenlediğinizde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1e43-138">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="d1e43-139">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) öğeleri herhangi bir değişken veya bağımsız değişken ayıklamak için bir iş akışındaki herhangi bir etkinlikten. Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgusu gösterir, etkinliğin `Closed` izleme kaydını yayılan.</span><span class="sxs-lookup"><span data-stu-id="d1e43-139">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="d1e43-140">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabileceği ve bu nedenle içinde bir izleme abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="d1e43-140">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d1e43-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1e43-141">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="d1e43-142">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="d1e43-142">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d1e43-143">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="d1e43-143">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
