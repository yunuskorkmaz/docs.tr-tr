---
description: 'Hakkında daha fazla bilgi <state> edinin: <states>'
title: <state> / <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 748044986143f182faa0edafb0cfe299a79a704e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781993"
---
# <a name="state-of-states"></a><span data-ttu-id="1f2bd-103">\<state> / \<states></span><span class="sxs-lookup"><span data-stu-id="1f2bd-103">\<state> of \<states></span></span>

<span data-ttu-id="1f2bd-104">Bir izleme kaydının oluşturulması gereken abone olunan etkinliğin durumunu içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-104">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="1f2bd-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1f2bd-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="1f2bd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1f2bd-106">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f2bd-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f2bd-107">Attributes and Elements</span></span>  

 <span data-ttu-id="1f2bd-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f2bd-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1f2bd-109">Attributes</span></span>  
  
|<span data-ttu-id="1f2bd-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1f2bd-110">Attribute</span></span>|<span data-ttu-id="1f2bd-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f2bd-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f2bd-112">name</span><span class="sxs-lookup"><span data-stu-id="1f2bd-112">name</span></span>|<span data-ttu-id="1f2bd-113">Bir izleme kaydının Yayınlanma için abone olunan etkinlik durumunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-113">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f2bd-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f2bd-114">Child Elements</span></span>  

 <span data-ttu-id="1f2bd-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f2bd-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f2bd-116">Parent Elements</span></span>  
  
|<span data-ttu-id="1f2bd-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="1f2bd-117">Element</span></span>|<span data-ttu-id="1f2bd-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f2bd-118">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-activitystatequery.md)|<span data-ttu-id="1f2bd-119">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren yapılandırma öğelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-119">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f2bd-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f2bd-120">Remarks</span></span>  

 <span data-ttu-id="1f2bd-121">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-121">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="1f2bd-122">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-122">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="1f2bd-123">[\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişken çıkarmak için ve öğelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-123">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="1f2bd-124">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-124">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="1f2bd-125">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle kullanılarak bir izleme profili içinde abone olunmuş olur [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="1f2bd-125">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1f2bd-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f2bd-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1f2bd-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="1f2bd-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1f2bd-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="1f2bd-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
