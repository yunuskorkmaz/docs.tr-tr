---
description: 'Hakkında daha fazla bilgi edinin: <customTrackingQuery>'
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 24857aca39aad825a3dd4eca83fa3a51ec440b25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795098"
---
# \<customTrackingQuery>

<span data-ttu-id="0c0b8-102">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0c0b8-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="0c0b8-103">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0c0b8-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="0c0b8-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="0c0b8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="0c0b8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0c0b8-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c0b8-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c0b8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0c0b8-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0c0b8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c0b8-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0c0b8-108">Attributes</span></span>  
  
|<span data-ttu-id="0c0b8-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0c0b8-109">Attribute</span></span>|<span data-ttu-id="0c0b8-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c0b8-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c0b8-111">activityName</span><span class="sxs-lookup"><span data-stu-id="0c0b8-111">activityName</span></span>|<span data-ttu-id="0c0b8-112">İzleme kaydını oluşturan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="0c0b8-112">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="0c0b8-113">name</span><span class="sxs-lookup"><span data-stu-id="0c0b8-113">name</span></span>|<span data-ttu-id="0c0b8-114">Yayılan özel izleme kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="0c0b8-114">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c0b8-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c0b8-115">Child Elements</span></span>  

 <span data-ttu-id="0c0b8-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="0c0b8-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c0b8-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c0b8-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0c0b8-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c0b8-118">Element</span></span>|<span data-ttu-id="0c0b8-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c0b8-119">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="0c0b8-120">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="0c0b8-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c0b8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c0b8-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0c0b8-122">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="0c0b8-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0c0b8-123">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="0c0b8-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
