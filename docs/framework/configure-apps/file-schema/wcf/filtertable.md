---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: f790e294b832f43a595d0636c60a8a67da5ad56a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147895"
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="a51dc-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="a51dc-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="a51dc-103">Filtrenin true olarak değerlendirilirse karşı iletileri ve istemci uç noktasına iletileri yönlendirmek için değerlendirilecek filtrelerin listesini içeren bir yönlendirme tablosu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a51dc-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="a51dc-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a51dc-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a51dc-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="a51dc-105">\<routing></span></span>  
<span data-ttu-id="a51dc-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="a51dc-106">\<routingTables></span></span>  
<span data-ttu-id="a51dc-107">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="a51dc-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a51dc-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a51dc-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a51dc-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a51dc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a51dc-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a51dc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a51dc-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a51dc-111">Attributes</span></span>  
  
|<span data-ttu-id="a51dc-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="a51dc-112">Element</span></span>|<span data-ttu-id="a51dc-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a51dc-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a51dc-114">name</span><span class="sxs-lookup"><span data-stu-id="a51dc-114">name</span></span>|<span data-ttu-id="a51dc-115">Bu yapılandırma öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="a51dc-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a51dc-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a51dc-116">Child Elements</span></span>  
  
|<span data-ttu-id="a51dc-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="a51dc-117">Element</span></span>|<span data-ttu-id="a51dc-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a51dc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a51dc-119">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="a51dc-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="a51dc-120">Ne zaman eşleşen filtre ileti göndermek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri.</span><span class="sxs-lookup"><span data-stu-id="a51dc-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a51dc-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a51dc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a51dc-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="a51dc-122">Element</span></span>|<span data-ttu-id="a51dc-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a51dc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a51dc-124">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="a51dc-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="a51dc-125">Yönlendirme tabloları içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="a51dc-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a51dc-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a51dc-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
