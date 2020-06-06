---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 3d6d03638ec5806448a16cc32b37e630d6198624
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152137"
---
# \<faultPropagationQueries>
<span data-ttu-id="1dcf4-101">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-101">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="1dcf4-102">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="1dcf4-103">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="1dcf4-104">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="1dcf4-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1dcf4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**
  
## <a name="syntax"></a><span data-ttu-id="1dcf4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1dcf4-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1dcf4-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1dcf4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1dcf4-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1dcf4-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1dcf4-109">Attributes</span></span>  
 <span data-ttu-id="1dcf4-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1dcf4-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1dcf4-111">Child Elements</span></span>  
  
|<span data-ttu-id="1dcf4-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="1dcf4-112">Element</span></span>|<span data-ttu-id="1dcf4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1dcf4-113">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="1dcf4-114">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="1dcf4-115">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1dcf4-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1dcf4-116">Parent Elements</span></span>  
  
|<span data-ttu-id="1dcf4-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="1dcf4-117">Element</span></span>|<span data-ttu-id="1dcf4-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1dcf4-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="1dcf4-119">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1dcf4-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1dcf4-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="1dcf4-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1dcf4-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="1dcf4-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
