---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: 72a2d6f8439e720bb7bf236bd942552224e85501
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189736"
---
# \<argument>

<span data-ttu-id="840a0-101">Bir etkinlik durumu sorgusu ile ilişkili bir bağımsız değişken temsil eden bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="840a0-101">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="840a0-102">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="840a0-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<arguments>**](arguments.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<argument>**  
  
## <a name="syntax"></a><span data-ttu-id="840a0-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="840a0-103">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="840a0-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="840a0-104">Attributes and Elements</span></span>  

 <span data-ttu-id="840a0-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="840a0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="840a0-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="840a0-106">Attributes</span></span>  
  
|<span data-ttu-id="840a0-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="840a0-107">Attribute</span></span>|<span data-ttu-id="840a0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="840a0-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="840a0-109">name</span><span class="sxs-lookup"><span data-stu-id="840a0-109">name</span></span>|<span data-ttu-id="840a0-110">Bağımsız değişkenin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="840a0-110">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="840a0-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="840a0-111">Child Elements</span></span>  

 <span data-ttu-id="840a0-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="840a0-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="840a0-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="840a0-113">Parent Elements</span></span>  
  
|<span data-ttu-id="840a0-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="840a0-114">Element</span></span>|<span data-ttu-id="840a0-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="840a0-115">Description</span></span>|  
|-------------|-----------------|  
|[\<arguments>](arguments.md)|<span data-ttu-id="840a0-116">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="840a0-116">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="840a0-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="840a0-117">Remarks</span></span>  

 <span data-ttu-id="840a0-118">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="840a0-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="840a0-119">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="840a0-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="840a0-120">[\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişken çıkarmak için ve öğelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="840a0-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="840a0-121">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="840a0-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="840a0-122">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle kullanılarak bir izleme profili içinde abone olunmuş olur [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="840a0-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="840a0-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="840a0-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="840a0-124">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="840a0-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="840a0-125">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="840a0-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
