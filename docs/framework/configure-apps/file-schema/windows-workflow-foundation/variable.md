---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: e487e54ac5c70351d00df4275302bc9f4e92292c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270608"
---
# <a name="variable"></a><span data-ttu-id="25866-101">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="25866-101">\<variable></span></span>
<span data-ttu-id="25866-102">Bu etkinlik sorguyla ilişkilendirilen değişkeni koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="25866-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="25866-103">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="25866-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="25866-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="25866-104">\<system.serviceModel></span></span>  
<span data-ttu-id="25866-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="25866-105">\<tracking></span></span>  
<span data-ttu-id="25866-106">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="25866-106">\<profiles></span></span>  
<span data-ttu-id="25866-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="25866-107">\<trackingProfile></span></span>  
<span data-ttu-id="25866-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="25866-108">\<workflow></span></span>  
<span data-ttu-id="25866-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="25866-109">\<activityStateQueries></span></span>  
<span data-ttu-id="25866-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="25866-110">\<activityStateQuery></span></span>  
<span data-ttu-id="25866-111">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="25866-111">\<variables></span></span>  
<span data-ttu-id="25866-112">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="25866-112">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25866-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25866-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25866-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="25866-114">Attributes and Elements</span></span>  
 <span data-ttu-id="25866-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="25866-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25866-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="25866-116">Attributes</span></span>  
  
|<span data-ttu-id="25866-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="25866-117">Attribute</span></span>|<span data-ttu-id="25866-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25866-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="25866-119">name</span><span class="sxs-lookup"><span data-stu-id="25866-119">name</span></span>|<span data-ttu-id="25866-120">Değişkenin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="25866-120">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25866-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="25866-121">Child Elements</span></span>  
 <span data-ttu-id="25866-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="25866-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25866-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="25866-123">Parent Elements</span></span>  
  
|<span data-ttu-id="25866-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="25866-124">Element</span></span>|<span data-ttu-id="25866-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25866-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25866-126">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="25866-126">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="25866-127">Bir etkinlik durumu sorgusu ile ilişkili bir değişkeni.</span><span class="sxs-lookup"><span data-stu-id="25866-127">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25866-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25866-128">Remarks</span></span>  
 <span data-ttu-id="25866-129">Bir benzersiz bir ActivityStateQuery bir iş akışı yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="25866-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="25866-130">İzleme erişme post düzenlediğinizde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="25866-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="25866-131">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) öğeleri herhangi bir değişken veya bağımsız değişken ayıklamak için bir iş akışındaki herhangi bir etkinlikten.</span><span class="sxs-lookup"><span data-stu-id="25866-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="25866-132">Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgusu gösterir, etkinliğin `Closed` izleme kaydını yayılan.</span><span class="sxs-lookup"><span data-stu-id="25866-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="25866-133">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabileceği ve bu nedenle içinde bir izleme abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="25866-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="25866-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25866-134">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="25866-135">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="25866-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="25866-136">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="25866-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
