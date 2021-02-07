---
description: 'Hakkında daha fazla bilgi edinin: <activityStateQueries>'
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: ad324d88c481016d85b8e58ccc0857b7773d8328
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748966"
---
# \<activityStateQueries>

<span data-ttu-id="cfdd2-102">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="cfdd2-103">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="cfdd2-104">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="cfdd2-105">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="cfdd2-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="cfdd2-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="cfdd2-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="cfdd2-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfdd2-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cfdd2-108">Attributes and Elements</span></span>  

 <span data-ttu-id="cfdd2-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfdd2-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cfdd2-110">Attributes</span></span>  

 <span data-ttu-id="cfdd2-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cfdd2-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cfdd2-112">Child Elements</span></span>  
  
|<span data-ttu-id="cfdd2-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="cfdd2-113">Element</span></span>|<span data-ttu-id="cfdd2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfdd2-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="cfdd2-115">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-115">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="cfdd2-116">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-116">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cfdd2-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cfdd2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cfdd2-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="cfdd2-118">Element</span></span>|<span data-ttu-id="cfdd2-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfdd2-119">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="cfdd2-120">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-120">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cfdd2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfdd2-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cfdd2-122">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="cfdd2-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cfdd2-123">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="cfdd2-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
