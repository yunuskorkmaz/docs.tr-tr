---
description: 'Hakkında daha fazla bilgi edinin: <cancelRequestedQueries>'
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: a508de97bce604284d9af00a3344fe5f35dc8bea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698082"
---
# \<cancelRequestedQueries>

<span data-ttu-id="23fc9-102">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="23fc9-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="23fc9-103">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="23fc9-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="23fc9-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="23fc9-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="23fc9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="23fc9-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String"
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23fc9-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="23fc9-106">Attributes and Elements</span></span>  

 <span data-ttu-id="23fc9-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="23fc9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23fc9-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="23fc9-108">Attributes</span></span>  

 <span data-ttu-id="23fc9-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="23fc9-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="23fc9-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="23fc9-110">Child Elements</span></span>  
  
|<span data-ttu-id="23fc9-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="23fc9-111">Element</span></span>|<span data-ttu-id="23fc9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23fc9-112">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery.md)|<span data-ttu-id="23fc9-113">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan sorgu</span><span class="sxs-lookup"><span data-stu-id="23fc9-113">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23fc9-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="23fc9-114">Parent Elements</span></span>  
  
|<span data-ttu-id="23fc9-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="23fc9-115">Element</span></span>|<span data-ttu-id="23fc9-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23fc9-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="23fc9-117">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="23fc9-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23fc9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23fc9-118">See also</span></span>

- [<span data-ttu-id="23fc9-119">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="23fc9-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="23fc9-120">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="23fc9-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
