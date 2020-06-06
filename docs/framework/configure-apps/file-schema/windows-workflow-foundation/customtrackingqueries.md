---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 6901244009956a499458858bf73f8fd83ec52e13
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152267"
---
# \<customTrackingQueries>
<span data-ttu-id="c5ec2-101">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c5ec2-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="c5ec2-102">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c5ec2-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="c5ec2-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c5ec2-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="c5ec2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5ec2-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5ec2-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5ec2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c5ec2-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5ec2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5ec2-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5ec2-107">Attributes</span></span>  
 <span data-ttu-id="c5ec2-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="c5ec2-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c5ec2-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5ec2-109">Child Elements</span></span>  
  
|<span data-ttu-id="c5ec2-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5ec2-110">Element</span></span>|<span data-ttu-id="c5ec2-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5ec2-111">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="c5ec2-112">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="c5ec2-112">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5ec2-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5ec2-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c5ec2-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5ec2-114">Element</span></span>|<span data-ttu-id="c5ec2-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5ec2-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="c5ec2-116">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="c5ec2-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5ec2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5ec2-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c5ec2-118">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c5ec2-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c5ec2-119">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c5ec2-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
