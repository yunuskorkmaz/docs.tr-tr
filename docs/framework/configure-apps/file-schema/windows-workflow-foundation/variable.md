---
description: 'Hakkında daha fazla bilgi edinin: <variable>'
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 187aa0b1ab0494a9bad759c504b804580a60553e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698004"
---
# \<variable>

<span data-ttu-id="2d86d-102">Bu etkinlik sorguyla ilişkilendirilen değişkeni koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2d86d-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="2d86d-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2d86d-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<variables>**](variables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variable>**  
  
## <a name="syntax"></a><span data-ttu-id="2d86d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2d86d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d86d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d86d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="2d86d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2d86d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d86d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2d86d-107">Attributes</span></span>  
  
|<span data-ttu-id="2d86d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2d86d-108">Attribute</span></span>|<span data-ttu-id="2d86d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d86d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d86d-110">name</span><span class="sxs-lookup"><span data-stu-id="2d86d-110">name</span></span>|<span data-ttu-id="2d86d-111">Değişkenin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2d86d-111">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d86d-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d86d-112">Child Elements</span></span>  

 <span data-ttu-id="2d86d-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="2d86d-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d86d-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d86d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="2d86d-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="2d86d-115">Element</span></span>|<span data-ttu-id="2d86d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d86d-116">Description</span></span>|  
|-------------|-----------------|  
|[\<variable>](variable.md)|<span data-ttu-id="2d86d-117">Bir etkinlik durumu sorgusu ile ilişkili bir değişkeni.</span><span class="sxs-lookup"><span data-stu-id="2d86d-117">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d86d-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d86d-118">Remarks</span></span>  

 <span data-ttu-id="2d86d-119">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="2d86d-119">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="2d86d-120">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d86d-120">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="2d86d-121">[\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişken çıkarmak için ve öğelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d86d-121">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="2d86d-122">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2d86d-122">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="2d86d-123">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle kullanılarak bir izleme profili içinde abone olunmuş olur [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="2d86d-123">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2d86d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d86d-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2d86d-125">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="2d86d-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2d86d-126">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="2d86d-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
