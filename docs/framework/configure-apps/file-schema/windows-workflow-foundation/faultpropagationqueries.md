---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 3d6d03638ec5806448a16cc32b37e630d6198624
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152137"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="e0d4e-101">\<hata YayılımSorgular></span><span class="sxs-lookup"><span data-stu-id="e0d4e-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="e0d4e-102">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan sorgukoleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e0d4e-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e0d4e-103">Bu olay, bir Hata Handler bir hatayı her işlerde oluşur.</span><span class="sxs-lookup"><span data-stu-id="e0d4e-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e0d4e-104">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için bu tür sorguyu kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="e0d4e-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e0d4e-105">Sorgu, bir izleme katılımcısının hata yayma kayıtlarına abone olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e0d4e-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="e0d4e-106">Profil sorgularını izleme hakkında daha fazla bilgi için [bkz.](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e0d4e-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e0d4e-107">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e0d4e-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e0d4e-108">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e0d4e-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="e0d4e-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="e0d4e-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="e0d4e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<izlemeProfil>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="e0d4e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="e0d4e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<iş akışı>**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e0d4e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="e0d4e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<hata YayılımSorgular>**</span><span class="sxs-lookup"><span data-stu-id="e0d4e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="e0d4e-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0d4e-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0d4e-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0d4e-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e0d4e-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0d4e-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0d4e-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e0d4e-116">Attributes</span></span>  
 <span data-ttu-id="e0d4e-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0d4e-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e0d4e-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0d4e-118">Child Elements</span></span>  
  
|<span data-ttu-id="e0d4e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0d4e-119">Element</span></span>|<span data-ttu-id="e0d4e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0d4e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0d4e-121">\<hataPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="e0d4e-121">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="e0d4e-122">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="e0d4e-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e0d4e-123">Bu olay, bir Hata Handler bir hatayı her işlerde oluşur.</span><span class="sxs-lookup"><span data-stu-id="e0d4e-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e0d4e-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0d4e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e0d4e-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0d4e-125">Element</span></span>|<span data-ttu-id="e0d4e-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0d4e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0d4e-127">\<iş akışı></span><span class="sxs-lookup"><span data-stu-id="e0d4e-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="e0d4e-128">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="e0d4e-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0d4e-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0d4e-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e0d4e-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="e0d4e-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e0d4e-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="e0d4e-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
