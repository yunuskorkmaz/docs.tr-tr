---
description: 'Hakkında daha fazla bilgi edinin: <customTrackingQueries>'
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 3601950742eb002f43969bea4612e830d8365509
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719076"
---
# \<customTrackingQueries>

<span data-ttu-id="a53ed-102">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a53ed-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="a53ed-103">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a53ed-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="a53ed-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a53ed-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="a53ed-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a53ed-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String"
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a53ed-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a53ed-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a53ed-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a53ed-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a53ed-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a53ed-108">Attributes</span></span>  

 <span data-ttu-id="a53ed-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="a53ed-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a53ed-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a53ed-110">Child Elements</span></span>  
  
|<span data-ttu-id="a53ed-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="a53ed-111">Element</span></span>|<span data-ttu-id="a53ed-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a53ed-112">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="a53ed-113">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="a53ed-113">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a53ed-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a53ed-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a53ed-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="a53ed-115">Element</span></span>|<span data-ttu-id="a53ed-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a53ed-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="a53ed-117">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="a53ed-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a53ed-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a53ed-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a53ed-119">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a53ed-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a53ed-120">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a53ed-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
