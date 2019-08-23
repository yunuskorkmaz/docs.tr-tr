---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: f9e64e667befb70d617574b2a03c3e6bebb2a143
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925599"
---
# <a name="filtertable"></a><span data-ttu-id="adf57-101">\<Filtretablo ></span><span class="sxs-lookup"><span data-stu-id="adf57-101">\<filterTable></span></span>
<span data-ttu-id="adf57-102">Filtrenin, filtre true olarak değerlendirilirse, iletileri yönlendirmek için bir filtre listesi ve istemci uç noktası içeren bir yönlendirme tablosunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="adf57-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="adf57-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="adf57-103">\<system.serviceModel></span></span>  
<span data-ttu-id="adf57-104">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="adf57-104">\<routing></span></span>  
<span data-ttu-id="adf57-105">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="adf57-105">\<routingTables></span></span>  
<span data-ttu-id="adf57-106">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="adf57-106">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adf57-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="adf57-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adf57-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="adf57-108">Attributes and Elements</span></span>  
 <span data-ttu-id="adf57-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="adf57-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adf57-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="adf57-110">Attributes</span></span>  
  
|<span data-ttu-id="adf57-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="adf57-111">Element</span></span>|<span data-ttu-id="adf57-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adf57-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="adf57-113">name</span><span class="sxs-lookup"><span data-stu-id="adf57-113">name</span></span>|<span data-ttu-id="adf57-114">Bu yapılandırma öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="adf57-114">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adf57-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="adf57-115">Child Elements</span></span>  
  
|<span data-ttu-id="adf57-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="adf57-116">Element</span></span>|<span data-ttu-id="adf57-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adf57-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adf57-118">\<Filtreler ></span><span class="sxs-lookup"><span data-stu-id="adf57-118">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="adf57-119">Filtre eşleştiğinde ileti göndermek için yönlendirme filtreleri ve hedef uç noktalar arasındaki eşlemeler.</span><span class="sxs-lookup"><span data-stu-id="adf57-119">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="adf57-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="adf57-120">Parent Elements</span></span>  
  
|<span data-ttu-id="adf57-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="adf57-121">Element</span></span>|<span data-ttu-id="adf57-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adf57-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adf57-123">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="adf57-123">\<routing></span></span>](routing.md)|<span data-ttu-id="adf57-124">Yönlendirme tablolarını içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="adf57-124">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="adf57-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adf57-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
