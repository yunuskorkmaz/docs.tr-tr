---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 83339eebef9a4f1b7f69e0bd1dd16b8278a68258
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534611"
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="80695-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="80695-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="80695-103">Filtrenin true olarak değerlendirilirse karşı iletileri ve istemci uç noktasına iletileri yönlendirmek için değerlendirilecek filtrelerin listesini içeren bir yönlendirme tablosu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="80695-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="80695-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="80695-104">\<system.serviceModel></span></span>  
<span data-ttu-id="80695-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="80695-105">\<routing></span></span>  
<span data-ttu-id="80695-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="80695-106">\<routingTables></span></span>  
<span data-ttu-id="80695-107">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="80695-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80695-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80695-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80695-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="80695-109">Attributes and Elements</span></span>  
 <span data-ttu-id="80695-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80695-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80695-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="80695-111">Attributes</span></span>  
  
|<span data-ttu-id="80695-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="80695-112">Element</span></span>|<span data-ttu-id="80695-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80695-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80695-114">name</span><span class="sxs-lookup"><span data-stu-id="80695-114">name</span></span>|<span data-ttu-id="80695-115">Bu yapılandırma öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="80695-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80695-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="80695-116">Child Elements</span></span>  
  
|<span data-ttu-id="80695-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="80695-117">Element</span></span>|<span data-ttu-id="80695-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80695-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80695-119">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="80695-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="80695-120">Ne zaman eşleşen filtre ileti göndermek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri.</span><span class="sxs-lookup"><span data-stu-id="80695-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80695-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="80695-121">Parent Elements</span></span>  
  
|<span data-ttu-id="80695-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="80695-122">Element</span></span>|<span data-ttu-id="80695-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80695-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80695-124">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="80695-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="80695-125">Yönlendirme tabloları içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="80695-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80695-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80695-126">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
