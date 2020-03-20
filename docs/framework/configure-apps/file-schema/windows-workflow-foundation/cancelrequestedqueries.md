---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 89297b3a7d64f4300a735d8512230d441836c634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152313"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="ffee0-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="ffee0-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="ffee0-102">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek için kullanılan sorgukoleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ffee0-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ffee0-103">Sorgu, bir izleme katılımcısının istek kayıt nesnelerini iptal etmek için abone olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ffee0-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="ffee0-104">Profil sorgularını izleme hakkında daha fazla bilgi için [bkz.](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ffee0-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ffee0-105">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ffee0-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ffee0-106">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ffee0-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="ffee0-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="ffee0-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="ffee0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<izlemeProfil>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="ffee0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="ffee0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<iş akışı>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ffee0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="ffee0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span><span class="sxs-lookup"><span data-stu-id="ffee0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffee0-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ffee0-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffee0-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ffee0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ffee0-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ffee0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffee0-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ffee0-114">Attributes</span></span>  
 <span data-ttu-id="ffee0-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="ffee0-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ffee0-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ffee0-116">Child Elements</span></span>  
  
|<span data-ttu-id="ffee0-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ffee0-117">Element</span></span>|<span data-ttu-id="ffee0-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffee0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ffee0-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="ffee0-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="ffee0-120">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri ni izlemek için kullanılan bir sorgu</span><span class="sxs-lookup"><span data-stu-id="ffee0-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ffee0-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ffee0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ffee0-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="ffee0-122">Element</span></span>|<span data-ttu-id="ffee0-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffee0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ffee0-124">\<iş akışı></span><span class="sxs-lookup"><span data-stu-id="ffee0-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="ffee0-125">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ffee0-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ffee0-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffee0-126">See also</span></span>

- [<span data-ttu-id="ffee0-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="ffee0-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ffee0-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="ffee0-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
