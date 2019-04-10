---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 4e5c7d56e35afe3001f4c70064adbfef7702c720
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229283"
---
# <a name="filtertable"></a><span data-ttu-id="3898b-101">\<filterTable ></span><span class="sxs-lookup"><span data-stu-id="3898b-101">\<filterTable></span></span>
<span data-ttu-id="3898b-102">Filtrenin true olarak değerlendirilirse karşı iletileri ve istemci uç noktasına iletileri yönlendirmek için değerlendirilecek filtrelerin listesini içeren bir yönlendirme tablosu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3898b-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="3898b-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3898b-103">\<system.serviceModel></span></span>  
<span data-ttu-id="3898b-104">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="3898b-104">\<routing></span></span>  
<span data-ttu-id="3898b-105">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="3898b-105">\<routingTables></span></span>  
<span data-ttu-id="3898b-106">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="3898b-106">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3898b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3898b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3898b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3898b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3898b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3898b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3898b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3898b-110">Attributes</span></span>  
  
|<span data-ttu-id="3898b-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="3898b-111">Element</span></span>|<span data-ttu-id="3898b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3898b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3898b-113">name</span><span class="sxs-lookup"><span data-stu-id="3898b-113">name</span></span>|<span data-ttu-id="3898b-114">Bu yapılandırma öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="3898b-114">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3898b-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3898b-115">Child Elements</span></span>  
  
|<span data-ttu-id="3898b-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="3898b-116">Element</span></span>|<span data-ttu-id="3898b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3898b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3898b-118">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="3898b-118">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="3898b-119">Ne zaman eşleşen filtre ileti göndermek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri.</span><span class="sxs-lookup"><span data-stu-id="3898b-119">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3898b-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3898b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3898b-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="3898b-121">Element</span></span>|<span data-ttu-id="3898b-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3898b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3898b-123">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="3898b-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="3898b-124">Yönlendirme tabloları içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="3898b-124">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3898b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3898b-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
