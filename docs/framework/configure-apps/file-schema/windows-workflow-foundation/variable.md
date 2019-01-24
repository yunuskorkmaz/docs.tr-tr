---
title: '&lt;Değişkeni&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 185e7e7196f6679ec3d1fae8a2a256b934022ca9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647887"
---
# <a name="ltvariablegt"></a><span data-ttu-id="ae0db-102">&lt;Değişkeni&gt;</span><span class="sxs-lookup"><span data-stu-id="ae0db-102">&lt;variable&gt;</span></span>
<span data-ttu-id="ae0db-103">Bu etkinlik sorguyla ilişkilendirilen değişkeni koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ae0db-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="ae0db-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ae0db-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ae0db-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ae0db-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ae0db-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="ae0db-106">\<tracking></span></span>  
<span data-ttu-id="ae0db-107">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="ae0db-107">\<profiles></span></span>  
<span data-ttu-id="ae0db-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ae0db-108">\<trackingProfile></span></span>  
<span data-ttu-id="ae0db-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="ae0db-109">\<workflow></span></span>  
<span data-ttu-id="ae0db-110">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="ae0db-110">\<activityStateQueries></span></span>  
<span data-ttu-id="ae0db-111">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="ae0db-111">\<activityStateQuery></span></span>  
<span data-ttu-id="ae0db-112">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="ae0db-112">\<variables></span></span>  
<span data-ttu-id="ae0db-113">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="ae0db-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae0db-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae0db-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae0db-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae0db-115">Attributes and Elements</span></span>  
 <span data-ttu-id="ae0db-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ae0db-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae0db-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ae0db-117">Attributes</span></span>  
  
|<span data-ttu-id="ae0db-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ae0db-118">Attribute</span></span>|<span data-ttu-id="ae0db-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae0db-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae0db-120">name</span><span class="sxs-lookup"><span data-stu-id="ae0db-120">name</span></span>|<span data-ttu-id="ae0db-121">Değişkenin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="ae0db-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae0db-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae0db-122">Child Elements</span></span>  
 <span data-ttu-id="ae0db-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="ae0db-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae0db-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae0db-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ae0db-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae0db-125">Element</span></span>|<span data-ttu-id="ae0db-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae0db-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae0db-127">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="ae0db-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="ae0db-128">Bir etkinlik durumu sorgusu ile ilişkili bir değişkeni.</span><span class="sxs-lookup"><span data-stu-id="ae0db-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae0db-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae0db-129">Remarks</span></span>  
 <span data-ttu-id="ae0db-130">Bir benzersiz bir ActivityStateQuery bir iş akışı yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="ae0db-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="ae0db-131">İzleme erişme post düzenlediğinizde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae0db-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="ae0db-132">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) öğeleri herhangi bir değişken veya bağımsız değişken ayıklamak için bir iş akışındaki herhangi bir etkinlikten.</span><span class="sxs-lookup"><span data-stu-id="ae0db-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="ae0db-133">Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgusu gösterir, etkinliğin `Closed` izleme kaydını yayılan.</span><span class="sxs-lookup"><span data-stu-id="ae0db-133">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="ae0db-134">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabileceği ve bu nedenle içinde bir izleme abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="ae0db-134">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ae0db-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae0db-135">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ae0db-136">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="ae0db-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ae0db-137">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="ae0db-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
