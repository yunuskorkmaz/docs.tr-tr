---
title: <customTrackingQueries>WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 2c4bd74ae346c536e8bc0ae454e638b7c76a40fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855437"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="b4c1d-102">\<customTrackingQueries>WCF</span><span class="sxs-lookup"><span data-stu-id="b4c1d-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="b4c1d-103">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="b4c1d-104">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="b4c1d-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b4c1d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  

## <a name="syntax"></a><span data-ttu-id="b4c1d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4c1d-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4c1d-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="b4c1d-107">Attributes and elements</span></span>

<span data-ttu-id="b4c1d-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4c1d-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b4c1d-109">Attributes</span></span>

<span data-ttu-id="b4c1d-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-110">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="b4c1d-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b4c1d-111">Child elements</span></span>
  
|<span data-ttu-id="b4c1d-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="b4c1d-112">Element</span></span>|<span data-ttu-id="b4c1d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4c1d-113">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery-of-wcf.md)|<span data-ttu-id="b4c1d-114">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-114">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4c1d-115">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="b4c1d-115">Parent elements</span></span>  
  
|<span data-ttu-id="b4c1d-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="b4c1d-116">Element</span></span>|<span data-ttu-id="b4c1d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4c1d-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="b4c1d-118">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4c1d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4c1d-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b4c1d-120">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="b4c1d-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b4c1d-121">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="b4c1d-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
