---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: 3e9fc4f286e7aba6406ce61910da9e614e13ffca
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368096"
---
# <a name="arguments"></a><span data-ttu-id="7f0e3-101">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="7f0e3-101">\<arguments></span></span>
<span data-ttu-id="7f0e3-102">Bir etkinlik durumu sorgusu ile ilişkili bağımsız değişkenler koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7f0e3-102">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="7f0e3-103">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="7f0e3-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="7f0e3-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7f0e3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7f0e3-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="7f0e3-105">\<tracking></span></span>  
<span data-ttu-id="7f0e3-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7f0e3-106">\<trackingProfile></span></span>  
<span data-ttu-id="7f0e3-107">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="7f0e3-107">\<workflow></span></span>  
<span data-ttu-id="7f0e3-108">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="7f0e3-108">\<activityStateQueries></span></span>  
<span data-ttu-id="7f0e3-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="7f0e3-109">\<activityStateQuery></span></span>  
<span data-ttu-id="7f0e3-110">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="7f0e3-110">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f0e3-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f0e3-111">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f0e3-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f0e3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7f0e3-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7f0e3-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f0e3-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7f0e3-114">Attributes</span></span>  
 <span data-ttu-id="7f0e3-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="7f0e3-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7f0e3-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f0e3-116">Child Elements</span></span>  
  
|<span data-ttu-id="7f0e3-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="7f0e3-117">Element</span></span>|<span data-ttu-id="7f0e3-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f0e3-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f0e3-119">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="7f0e3-119">\<argument></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|<span data-ttu-id="7f0e3-120">Bir etkinlik durumu sorgusu ile ilişkili bir bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="7f0e3-120">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f0e3-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f0e3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7f0e3-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="7f0e3-122">Element</span></span>|<span data-ttu-id="7f0e3-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f0e3-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f0e3-124">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="7f0e3-124">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="7f0e3-125">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7f0e3-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7f0e3-126">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7f0e3-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f0e3-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f0e3-127">Remarks</span></span>  
 <span data-ttu-id="7f0e3-128">Bir benzersiz bir ActivityStateQuery bir iş akışı yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="7f0e3-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="7f0e3-129">İzleme erişme post düzenlediğinizde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f0e3-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="7f0e3-130">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) öğeleri herhangi bir değişken veya bağımsız değişken ayıklamak için bir iş akışındaki herhangi bir etkinlikten.</span><span class="sxs-lookup"><span data-stu-id="7f0e3-130">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="7f0e3-131">Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgusu gösterir, etkinliğin `Closed` izleme kaydını yayılan.</span><span class="sxs-lookup"><span data-stu-id="7f0e3-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="7f0e3-132">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabileceği ve bu nedenle içinde bir izleme abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="7f0e3-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f0e3-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f0e3-133">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7f0e3-134">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="7f0e3-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7f0e3-135">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="7f0e3-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
