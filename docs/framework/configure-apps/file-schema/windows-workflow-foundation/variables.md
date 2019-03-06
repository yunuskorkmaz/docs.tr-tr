---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 3ff568c267331538fb9be0e6cb40eebbca44d882
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375668"
---
# <a name="variables"></a><span data-ttu-id="80053-101">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="80053-101">\<variables></span></span>
<span data-ttu-id="80053-102">Bu etkinlik sorguyla ilişkilendirilen değişkeni koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="80053-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="80053-103">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="80053-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="80053-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="80053-104">\<system.serviceModel></span></span>  
<span data-ttu-id="80053-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="80053-105">\<tracking></span></span>  
<span data-ttu-id="80053-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="80053-106">\<trackingProfile></span></span>  
<span data-ttu-id="80053-107">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="80053-107">\<workflow></span></span>  
<span data-ttu-id="80053-108">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="80053-108">\<activityStateQueries></span></span>  
<span data-ttu-id="80053-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="80053-109">\<activityStateQuery></span></span>  
<span data-ttu-id="80053-110">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="80053-110">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80053-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80053-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80053-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="80053-112">Attributes and Elements</span></span>  
 <span data-ttu-id="80053-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80053-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80053-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="80053-114">Attributes</span></span>  
 <span data-ttu-id="80053-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="80053-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="80053-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="80053-116">Child Elements</span></span>  
  
|<span data-ttu-id="80053-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="80053-117">Element</span></span>|<span data-ttu-id="80053-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80053-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80053-119">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="80053-119">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="80053-120">Bir etkinlik durumu sorgusu ile ilişkili bir değişkeni.</span><span class="sxs-lookup"><span data-stu-id="80053-120">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80053-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="80053-121">Parent Elements</span></span>  
  
|<span data-ttu-id="80053-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="80053-122">Element</span></span>|<span data-ttu-id="80053-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80053-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80053-124">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="80053-124">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="80053-125">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="80053-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="80053-126">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="80053-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80053-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80053-127">Remarks</span></span>  
 <span data-ttu-id="80053-128">Bir benzersiz bir ActivityStateQuery bir iş akışı yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="80053-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="80053-129">İzleme erişme post düzenlediğinizde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="80053-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="80053-130">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) öğeleri herhangi bir değişken veya bağımsız değişken ayıklamak için bir iş akışındaki herhangi bir etkinlikten.</span><span class="sxs-lookup"><span data-stu-id="80053-130">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="80053-131">Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgusu gösterir, etkinliğin `Closed` izleme kaydını yayılan.</span><span class="sxs-lookup"><span data-stu-id="80053-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="80053-132">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabileceği ve bu nedenle içinde bir izleme abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="80053-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="80053-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80053-133">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="80053-134">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="80053-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="80053-135">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="80053-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
