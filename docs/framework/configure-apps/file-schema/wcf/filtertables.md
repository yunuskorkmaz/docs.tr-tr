---
title: '&lt;filterTables&gt;'
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: d73a3c25dbb4d2de41007149ef5864fcf37ad883
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573065"
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="5c95e-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="5c95e-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="5c95e-103">Filtreler eşleştiğinde ileti göndermek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri içeren yönlendirme tablosunun tanımı için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5c95e-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="5c95e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5c95e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5c95e-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="5c95e-105">\<routing></span></span>  
<span data-ttu-id="5c95e-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="5c95e-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c95e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c95e-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c95e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c95e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5c95e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5c95e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c95e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5c95e-110">Attributes</span></span>  
 <span data-ttu-id="5c95e-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="5c95e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5c95e-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c95e-112">Child Elements</span></span>  
  
|<span data-ttu-id="5c95e-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="5c95e-113">Element</span></span>|<span data-ttu-id="5c95e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c95e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c95e-115">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="5c95e-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="5c95e-116">Bir yönlendirme tablosu, ne zaman eşleşen filtre ileti göndermek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5c95e-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5c95e-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c95e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5c95e-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="5c95e-118">Element</span></span>|<span data-ttu-id="5c95e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c95e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c95e-120">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="5c95e-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="5c95e-121">Yönlendirme filtreleri ve yönlendirme tablolarını içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="5c95e-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c95e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c95e-122">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
