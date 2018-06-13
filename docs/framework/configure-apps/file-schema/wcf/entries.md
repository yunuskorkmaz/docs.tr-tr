---
title: '&lt;Girdileri&gt;'
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: b9cc7f7736ffefaca68a0f197bd064a99c4dca9a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746715"
---
# <a name="ltentriesgt"></a><span data-ttu-id="d85a7-102">&lt;Girdileri&gt;</span><span class="sxs-lookup"><span data-stu-id="d85a7-102">&lt;entries&gt;</span></span>
<span data-ttu-id="d85a7-103">Yönlendirme filtreleri ve ne zaman bir filtre ile eşleşen için iletileri göndermek için hedef uç noktaları arasındaki eşlemeleri içeren bir yönlendirme girişi.</span><span class="sxs-lookup"><span data-stu-id="d85a7-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="d85a7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d85a7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d85a7-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="d85a7-105">\<routing></span></span>  
<span data-ttu-id="d85a7-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="d85a7-106">\<routingTables></span></span>  
<span data-ttu-id="d85a7-107">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="d85a7-107">\<table></span></span>  
<span data-ttu-id="d85a7-108">\<girişleri ></span><span class="sxs-lookup"><span data-stu-id="d85a7-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d85a7-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d85a7-109">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d85a7-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d85a7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d85a7-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d85a7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d85a7-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d85a7-112">Attributes</span></span>  
 <span data-ttu-id="d85a7-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="d85a7-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d85a7-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d85a7-114">Child Elements</span></span>  
  
|<span data-ttu-id="d85a7-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="d85a7-115">Element</span></span>|<span data-ttu-id="d85a7-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d85a7-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d85a7-117">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="d85a7-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="d85a7-118">Bir filtre önceden tanımlanmış bir istemci uç noktası eşler.</span><span class="sxs-lookup"><span data-stu-id="d85a7-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="d85a7-119">Bu filtre ile eşleşen iletileri bu hedefe gönderilir.</span><span class="sxs-lookup"><span data-stu-id="d85a7-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d85a7-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d85a7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d85a7-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="d85a7-121">Element</span></span>|<span data-ttu-id="d85a7-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d85a7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d85a7-123">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="d85a7-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="d85a7-124">Bir yönlendirme tablosu içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="d85a7-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d85a7-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d85a7-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
