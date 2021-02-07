---
description: WCF hakkında daha fazla bilgi edinin <faultPropagationQueries>
title: <faultPropagationQueries> WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: e3ed504b3aada87246fabe54c0b32ef5ad60b34b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684444"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="807a3-103">\<faultPropagationQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="807a3-103">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="807a3-104">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="807a3-104">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="807a3-105">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="807a3-105">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="807a3-106">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="807a3-106">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="807a3-107">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="807a3-107">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="807a3-108">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="807a3-108">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="807a3-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="807a3-109">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="807a3-110">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="807a3-110">Attributes and elements</span></span>

<span data-ttu-id="807a3-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="807a3-111">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="807a3-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="807a3-112">Attributes</span></span>

<span data-ttu-id="807a3-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="807a3-113">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="807a3-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="807a3-114">Child elements</span></span>

|<span data-ttu-id="807a3-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="807a3-115">Element</span></span>|<span data-ttu-id="807a3-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="807a3-116">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="807a3-117">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="807a3-117">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="807a3-118">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="807a3-118">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="807a3-119">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="807a3-119">Parent elements</span></span>  
  
|<span data-ttu-id="807a3-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="807a3-120">Element</span></span>|<span data-ttu-id="807a3-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="807a3-121">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="807a3-122">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="807a3-122">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="807a3-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="807a3-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="807a3-124">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="807a3-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="807a3-125">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="807a3-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
