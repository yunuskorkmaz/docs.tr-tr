---
title: '&lt;filterTables&gt;'
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: 966556a1a8bde72e33640dcc6fd37ae7a044ceef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753420"
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="d81b2-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="d81b2-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="d81b2-103">Yönlendirme filtreleri ve filtre eşleştiğinde ileti göndermek için hedef uç noktaları arasındaki eşlemeleri içeren yönlendirme tablolarını tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d81b2-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="d81b2-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d81b2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d81b2-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="d81b2-105">\<routing></span></span>  
<span data-ttu-id="d81b2-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="d81b2-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d81b2-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d81b2-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d81b2-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d81b2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d81b2-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d81b2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d81b2-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d81b2-110">Attributes</span></span>  
 <span data-ttu-id="d81b2-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="d81b2-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d81b2-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d81b2-112">Child Elements</span></span>  
  
|<span data-ttu-id="d81b2-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="d81b2-113">Element</span></span>|<span data-ttu-id="d81b2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d81b2-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d81b2-115">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="d81b2-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="d81b2-116">Yönlendirme filtreleri ve ne zaman bir filtre ile eşleşen için iletileri göndermek için hedef uç noktaları arasındaki eşlemeleri içeren bir yönlendirme tablosu.</span><span class="sxs-lookup"><span data-stu-id="d81b2-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d81b2-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d81b2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d81b2-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="d81b2-118">Element</span></span>|<span data-ttu-id="d81b2-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d81b2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d81b2-120">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="d81b2-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="d81b2-121">Yönlendirme filtreleri ve yönlendirme tabloları içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="d81b2-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d81b2-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d81b2-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
