---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 4663ccedcafb6b151de75568afd3743c83c75224
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189831"
---
# \<activityStateQueries>

<span data-ttu-id="63048-101">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="63048-101">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="63048-102">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63048-102">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="63048-103">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="63048-103">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="63048-104">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="63048-104">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="63048-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="63048-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="63048-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="63048-106">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63048-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="63048-107">Attributes and Elements</span></span>  

 <span data-ttu-id="63048-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="63048-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63048-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="63048-109">Attributes</span></span>  

 <span data-ttu-id="63048-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="63048-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="63048-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="63048-111">Child Elements</span></span>  
  
|<span data-ttu-id="63048-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="63048-112">Element</span></span>|<span data-ttu-id="63048-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63048-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="63048-114">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="63048-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="63048-115">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="63048-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63048-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="63048-116">Parent Elements</span></span>  
  
|<span data-ttu-id="63048-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="63048-117">Element</span></span>|<span data-ttu-id="63048-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63048-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="63048-119">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="63048-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63048-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63048-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="63048-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="63048-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="63048-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="63048-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
