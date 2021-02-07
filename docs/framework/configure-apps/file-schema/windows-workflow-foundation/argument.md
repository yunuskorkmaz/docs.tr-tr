---
description: 'Hakkında daha fazla bilgi edinin: <argument>'
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: 7ef91d78d5d4a56b7291a6443ee7e68fefe4f401
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748875"
---
# \<argument>

<span data-ttu-id="38361-102">Bir etkinlik durumu sorgusu ile ilişkili bir bağımsız değişken temsil eden bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="38361-102">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="38361-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="38361-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<arguments>**](arguments.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<argument>**  
  
## <a name="syntax"></a><span data-ttu-id="38361-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="38361-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38361-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="38361-105">Attributes and Elements</span></span>  

 <span data-ttu-id="38361-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="38361-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38361-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="38361-107">Attributes</span></span>  
  
|<span data-ttu-id="38361-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="38361-108">Attribute</span></span>|<span data-ttu-id="38361-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38361-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38361-110">name</span><span class="sxs-lookup"><span data-stu-id="38361-110">name</span></span>|<span data-ttu-id="38361-111">Bağımsız değişkenin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="38361-111">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38361-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="38361-112">Child Elements</span></span>  

 <span data-ttu-id="38361-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="38361-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38361-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="38361-114">Parent Elements</span></span>  
  
|<span data-ttu-id="38361-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="38361-115">Element</span></span>|<span data-ttu-id="38361-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38361-116">Description</span></span>|  
|-------------|-----------------|  
|[\<arguments>](arguments.md)|<span data-ttu-id="38361-117">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="38361-117">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38361-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38361-118">Remarks</span></span>  

 <span data-ttu-id="38361-119">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="38361-119">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="38361-120">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="38361-120">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="38361-121">[\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişken çıkarmak için ve öğelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38361-121">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="38361-122">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="38361-122">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="38361-123">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle kullanılarak bir izleme profili içinde abone olunmuş olur [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="38361-123">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38361-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38361-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="38361-125">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="38361-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="38361-126">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="38361-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
