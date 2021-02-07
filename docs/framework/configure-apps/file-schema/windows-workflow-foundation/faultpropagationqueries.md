---
description: 'Hakkında daha fazla bilgi edinin: <faultPropagationQueries>'
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 13bd19a3673846bfbd641cd2f8eeafc20b8186f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719077"
---
# \<faultPropagationQueries>

<span data-ttu-id="f5190-102">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f5190-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f5190-103">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="f5190-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="f5190-104">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5190-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="f5190-105">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f5190-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="f5190-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f5190-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**
  
## <a name="syntax"></a><span data-ttu-id="f5190-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f5190-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5190-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5190-108">Attributes and Elements</span></span>  

 <span data-ttu-id="f5190-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5190-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5190-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f5190-110">Attributes</span></span>  

 <span data-ttu-id="f5190-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="f5190-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f5190-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5190-112">Child Elements</span></span>  
  
|<span data-ttu-id="f5190-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="f5190-113">Element</span></span>|<span data-ttu-id="f5190-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5190-114">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="f5190-115">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="f5190-115">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f5190-116">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="f5190-116">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f5190-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5190-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f5190-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="f5190-118">Element</span></span>|<span data-ttu-id="f5190-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5190-119">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="f5190-120">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="f5190-120">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5190-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5190-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f5190-122">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f5190-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f5190-123">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f5190-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
