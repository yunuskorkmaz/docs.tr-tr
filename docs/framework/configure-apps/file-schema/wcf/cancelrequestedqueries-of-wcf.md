---
title: <cancelRequestedQueries> WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 205399330c1aa69b332c2149ee32d9b6098ccdbe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151174"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="2bffa-102">\<cancelRequestedQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="2bffa-102">\<cancelRequestedQueries> of WCF</span></span>

<span data-ttu-id="2bffa-103">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2bffa-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="2bffa-104">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2bffa-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="2bffa-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2bffa-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="2bffa-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2bffa-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bffa-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="2bffa-107">Attributes and elements</span></span>  

<span data-ttu-id="2bffa-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2bffa-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bffa-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2bffa-109">Attributes</span></span>

<span data-ttu-id="2bffa-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="2bffa-110">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="2bffa-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="2bffa-111">Child elements</span></span>
  
|<span data-ttu-id="2bffa-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="2bffa-112">Element</span></span>|<span data-ttu-id="2bffa-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bffa-113">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="2bffa-114">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan sorgu</span><span class="sxs-lookup"><span data-stu-id="2bffa-114">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2bffa-115">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="2bffa-115">Parent elements</span></span>  
  
|<span data-ttu-id="2bffa-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="2bffa-116">Element</span></span>|<span data-ttu-id="2bffa-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bffa-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="2bffa-118">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2bffa-118">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2bffa-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bffa-119">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="2bffa-120">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="2bffa-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2bffa-121">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="2bffa-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
