---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 4e5c7d56e35afe3001f4c70064adbfef7702c720
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673218"
---
# <a name="filtertable"></a><span data-ttu-id="581e6-101">\<filterTable ></span><span class="sxs-lookup"><span data-stu-id="581e6-101">\<filterTable></span></span>
<span data-ttu-id="581e6-102">Filtrenin true olarak değerlendirilirse karşı iletileri ve istemci uç noktasına iletileri yönlendirmek için değerlendirilecek filtrelerin listesini içeren bir yönlendirme tablosu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="581e6-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="581e6-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="581e6-103">\<system.serviceModel></span></span>  
<span data-ttu-id="581e6-104">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="581e6-104">\<routing></span></span>  
<span data-ttu-id="581e6-105">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="581e6-105">\<routingTables></span></span>  
<span data-ttu-id="581e6-106">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="581e6-106">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="581e6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="581e6-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="581e6-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="581e6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="581e6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="581e6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="581e6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="581e6-110">Attributes</span></span>  
  
|<span data-ttu-id="581e6-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="581e6-111">Element</span></span>|<span data-ttu-id="581e6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="581e6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="581e6-113">name</span><span class="sxs-lookup"><span data-stu-id="581e6-113">name</span></span>|<span data-ttu-id="581e6-114">Bu yapılandırma öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="581e6-114">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="581e6-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="581e6-115">Child Elements</span></span>  
  
|<span data-ttu-id="581e6-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="581e6-116">Element</span></span>|<span data-ttu-id="581e6-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="581e6-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="581e6-118">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="581e6-118">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="581e6-119">Ne zaman eşleşen filtre ileti göndermek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri.</span><span class="sxs-lookup"><span data-stu-id="581e6-119">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="581e6-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="581e6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="581e6-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="581e6-121">Element</span></span>|<span data-ttu-id="581e6-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="581e6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="581e6-123">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="581e6-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="581e6-124">Yönlendirme tabloları içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="581e6-124">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="581e6-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="581e6-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
