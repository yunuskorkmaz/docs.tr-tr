---
title: <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 5d3c35589330ab5bed5f89c0dafac006b9e3af55
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398946"
---
# \<activityStateQuery>
<span data-ttu-id="d0996-101">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0996-101">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="d0996-102">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0996-102">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="d0996-103">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d0996-103">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="d0996-104">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d0996-104">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="d0996-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d0996-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="d0996-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0996-106">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
        <states>
          <state name="String"/>
        </states>
        <variables>
          <variable name="String"/>
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0996-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0996-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d0996-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0996-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0996-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d0996-109">Attributes</span></span>  
  
|<span data-ttu-id="d0996-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d0996-110">Attribute</span></span>|<span data-ttu-id="d0996-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0996-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0996-112">activityName</span><span class="sxs-lookup"><span data-stu-id="d0996-112">activityName</span></span>|<span data-ttu-id="d0996-113">Örnekleri filtreleyecek etkinliğin adını belirten bir dize <xref:System.Activities.Tracking.ActivityStateRecord> .</span><span class="sxs-lookup"><span data-stu-id="d0996-113">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0996-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0996-114">Child Elements</span></span>  
  
|<span data-ttu-id="d0996-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0996-115">Element</span></span>|<span data-ttu-id="d0996-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0996-116">Description</span></span>|  
|-------------|-----------------|  
|[\<arguments>](arguments.md)|<span data-ttu-id="d0996-117">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d0996-117">A collection of arguments associated with this activity query.</span></span>|  
|[\<states>](states.md)|<span data-ttu-id="d0996-118">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren yapılandırma öğelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d0996-118">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[\<states>](states.md)|<span data-ttu-id="d0996-119">Bu etkinlik sorguyla ilişkilendirilen değişkenlerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d0996-119">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0996-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0996-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d0996-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0996-121">Element</span></span>|<span data-ttu-id="d0996-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0996-122">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="d0996-123">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan yapılandırma öğelerinin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0996-123">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d0996-124">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d0996-124">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0996-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0996-125">Remarks</span></span>  
 <span data-ttu-id="d0996-126">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="d0996-126">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="d0996-127">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0996-127">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="d0996-128">[\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişken çıkarmak için ve öğelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0996-128">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="d0996-129">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d0996-129">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="d0996-130">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle kullanılarak bir izleme profili içinde abone olunmuş olur [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="d0996-130">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0996-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0996-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d0996-132">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="d0996-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d0996-133">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="d0996-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
