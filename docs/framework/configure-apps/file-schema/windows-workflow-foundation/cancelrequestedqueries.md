---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 89297b3a7d64f4300a735d8512230d441836c634
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152313"
---
# \<cancelRequestedQueries>
<span data-ttu-id="1f3e8-101">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1f3e8-101">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="1f3e8-102">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1f3e8-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="1f3e8-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1f3e8-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="1f3e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f3e8-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f3e8-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f3e8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1f3e8-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f3e8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f3e8-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1f3e8-107">Attributes</span></span>  
 <span data-ttu-id="1f3e8-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="1f3e8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1f3e8-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f3e8-109">Child Elements</span></span>  
  
|<span data-ttu-id="1f3e8-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="1f3e8-110">Element</span></span>|<span data-ttu-id="1f3e8-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f3e8-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery.md)|<span data-ttu-id="1f3e8-112">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan sorgu</span><span class="sxs-lookup"><span data-stu-id="1f3e8-112">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f3e8-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f3e8-113">Parent Elements</span></span>  
  
|<span data-ttu-id="1f3e8-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="1f3e8-114">Element</span></span>|<span data-ttu-id="1f3e8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f3e8-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="1f3e8-116">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="1f3e8-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f3e8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f3e8-117">See also</span></span>

- [<span data-ttu-id="1f3e8-118">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="1f3e8-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1f3e8-119">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="1f3e8-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
