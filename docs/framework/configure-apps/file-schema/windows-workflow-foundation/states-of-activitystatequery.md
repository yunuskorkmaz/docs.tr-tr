---
description: 'Hakkında daha fazla bilgi <states> edinin: <activityStateQuery>'
title: <states> / <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: 16a0af865508f0ebc50d16728c35188310c95043
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773283"
---
# <a name="states-of-activitystatequery"></a><span data-ttu-id="165fd-103">\<states> / \<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="165fd-103">\<states> of \<activityStateQuery></span></span>

<span data-ttu-id="165fd-104">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren yapılandırma öğelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="165fd-104">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="165fd-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="165fd-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="165fd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="165fd-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="165fd-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="165fd-107">Attributes and Elements</span></span>  

 <span data-ttu-id="165fd-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="165fd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="165fd-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="165fd-109">Attributes</span></span>  

 <span data-ttu-id="165fd-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="165fd-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="165fd-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="165fd-111">Child Elements</span></span>  
  
|<span data-ttu-id="165fd-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="165fd-112">Element</span></span>|<span data-ttu-id="165fd-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="165fd-113">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](state-of-states.md)|<span data-ttu-id="165fd-114">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="165fd-114">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="165fd-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="165fd-115">Parent Elements</span></span>  
  
|<span data-ttu-id="165fd-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="165fd-116">Element</span></span>|<span data-ttu-id="165fd-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="165fd-117">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="165fd-118">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek için kullanılan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="165fd-118">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="165fd-119">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="165fd-119">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="165fd-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="165fd-120">Remarks</span></span>  

 <span data-ttu-id="165fd-121">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="165fd-121">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="165fd-122">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="165fd-122">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="165fd-123">[\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişken çıkarmak için ve öğelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="165fd-123">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="165fd-124">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="165fd-124">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="165fd-125">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle kullanılarak bir izleme profili içinde abone olunmuş olur [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="165fd-125">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="165fd-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="165fd-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="165fd-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="165fd-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="165fd-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="165fd-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
