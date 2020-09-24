---
title: <state> / <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 058480c29d6c5b554d5187a1a12a0c2e54587428
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169758"
---
# <a name="state-of-states"></a><span data-ttu-id="6b312-102">\<state> / \<states></span><span class="sxs-lookup"><span data-stu-id="6b312-102">\<state> of \<states></span></span>

<span data-ttu-id="6b312-103">Bir izleme kaydının oluşturulması gereken abone olunan etkinliğin durumunu içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="6b312-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="6b312-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6b312-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="6b312-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6b312-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b312-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b312-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6b312-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b312-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b312-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6b312-108">Attributes</span></span>  
  
|<span data-ttu-id="6b312-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6b312-109">Attribute</span></span>|<span data-ttu-id="6b312-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b312-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b312-111">name</span><span class="sxs-lookup"><span data-stu-id="6b312-111">name</span></span>|<span data-ttu-id="6b312-112">Bir izleme kaydının Yayınlanma için abone olunan etkinlik durumunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="6b312-112">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b312-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b312-113">Child Elements</span></span>  

 <span data-ttu-id="6b312-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="6b312-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b312-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b312-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6b312-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b312-116">Element</span></span>|<span data-ttu-id="6b312-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b312-117">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-activitystatequery.md)|<span data-ttu-id="6b312-118">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren yapılandırma öğelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6b312-118">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b312-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b312-119">Remarks</span></span>  

 <span data-ttu-id="6b312-120">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="6b312-120">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="6b312-121">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b312-121">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="6b312-122">[\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişken çıkarmak için ve öğelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b312-122">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="6b312-123">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6b312-123">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="6b312-124">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle kullanılarak bir izleme profili içinde abone olunmuş olur [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="6b312-124">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b312-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b312-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6b312-126">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="6b312-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6b312-127">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="6b312-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
