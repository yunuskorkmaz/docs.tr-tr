---
title: <faultPropagationQueries>WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 709c2c6907b4d0d28118f9de12edb047aa16d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855270"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="bbe2c-102">\<faultPropagationQueries>WCF</span><span class="sxs-lookup"><span data-stu-id="bbe2c-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="bbe2c-103">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bbe2c-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="bbe2c-104">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="bbe2c-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="bbe2c-105">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bbe2c-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="bbe2c-106">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bbe2c-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="bbe2c-107">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="bbe2c-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="bbe2c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbe2c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbe2c-109">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="bbe2c-109">Attributes and elements</span></span>

<span data-ttu-id="bbe2c-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbe2c-110">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="bbe2c-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bbe2c-111">Attributes</span></span>

<span data-ttu-id="bbe2c-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="bbe2c-112">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="bbe2c-113">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="bbe2c-113">Child elements</span></span>

|<span data-ttu-id="bbe2c-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="bbe2c-114">Element</span></span>|<span data-ttu-id="bbe2c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbe2c-115">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="bbe2c-116">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="bbe2c-116">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="bbe2c-117">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="bbe2c-117">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bbe2c-118">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="bbe2c-118">Parent elements</span></span>  
  
|<span data-ttu-id="bbe2c-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="bbe2c-119">Element</span></span>|<span data-ttu-id="bbe2c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbe2c-120">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="bbe2c-121">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="bbe2c-121">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bbe2c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbe2c-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bbe2c-123">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="bbe2c-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bbe2c-124">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="bbe2c-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
