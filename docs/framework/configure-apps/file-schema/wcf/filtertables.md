---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: b0a344aa69085d50087eefc746236bc8ceacadaa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918850"
---
# <a name="filtertables"></a><span data-ttu-id="c55ce-101">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="c55ce-101">\<filterTables></span></span>
<span data-ttu-id="c55ce-102">Filtre eşleştiğinde iletileri göndermek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içeren yönlendirme tablolarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c55ce-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="c55ce-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c55ce-103">\<system.serviceModel></span></span>  
<span data-ttu-id="c55ce-104">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="c55ce-104">\<routing></span></span>  
<span data-ttu-id="c55ce-105">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="c55ce-105">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c55ce-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c55ce-106">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c55ce-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c55ce-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c55ce-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c55ce-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c55ce-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c55ce-109">Attributes</span></span>  
 <span data-ttu-id="c55ce-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="c55ce-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c55ce-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c55ce-111">Child Elements</span></span>  
  
|<span data-ttu-id="c55ce-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="c55ce-112">Element</span></span>|<span data-ttu-id="c55ce-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c55ce-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c55ce-114">\<Filtreler ></span><span class="sxs-lookup"><span data-stu-id="c55ce-114">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="c55ce-115">Filtre eşleştiğinde iletileri göndermek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içeren bir yönlendirme tablosu.</span><span class="sxs-lookup"><span data-stu-id="c55ce-115">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c55ce-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c55ce-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c55ce-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="c55ce-117">Element</span></span>|<span data-ttu-id="c55ce-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c55ce-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c55ce-119">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="c55ce-119">\<routing></span></span>](routing.md)|<span data-ttu-id="c55ce-120">Yönlendirme filtrelerini ve yönlendirme tablolarını içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="c55ce-120">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c55ce-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c55ce-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
