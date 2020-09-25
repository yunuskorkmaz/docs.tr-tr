---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 24e9136729df1352ebb1e665d1ebaf0ce9dc28a5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175843"
---
# \<faultPropagationQueries>

<span data-ttu-id="a42ef-101">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a42ef-101">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a42ef-102">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="a42ef-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="a42ef-103">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a42ef-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="a42ef-104">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a42ef-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="a42ef-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a42ef-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**
  
## <a name="syntax"></a><span data-ttu-id="a42ef-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a42ef-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a42ef-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a42ef-107">Attributes and Elements</span></span>  

 <span data-ttu-id="a42ef-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a42ef-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a42ef-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a42ef-109">Attributes</span></span>  

 <span data-ttu-id="a42ef-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="a42ef-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a42ef-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a42ef-111">Child Elements</span></span>  
  
|<span data-ttu-id="a42ef-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="a42ef-112">Element</span></span>|<span data-ttu-id="a42ef-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a42ef-113">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="a42ef-114">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="a42ef-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a42ef-115">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="a42ef-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a42ef-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a42ef-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a42ef-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="a42ef-117">Element</span></span>|<span data-ttu-id="a42ef-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a42ef-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="a42ef-119">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="a42ef-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a42ef-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a42ef-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a42ef-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a42ef-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a42ef-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a42ef-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
