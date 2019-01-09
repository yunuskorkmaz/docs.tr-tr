---
title: '&lt;filterTables&gt;'
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: 2b537619a276f32c50576561aea03b5fbbb58e7d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147791"
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="fe1e4-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="fe1e4-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="fe1e4-103">Filtreler eşleştiğinde ileti göndermek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri içeren yönlendirme tablosunun tanımı için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fe1e4-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="fe1e4-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fe1e4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fe1e4-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="fe1e4-105">\<routing></span></span>  
<span data-ttu-id="fe1e4-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="fe1e4-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe1e4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe1e4-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe1e4-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe1e4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fe1e4-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe1e4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe1e4-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fe1e4-110">Attributes</span></span>  
 <span data-ttu-id="fe1e4-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe1e4-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fe1e4-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe1e4-112">Child Elements</span></span>  
  
|<span data-ttu-id="fe1e4-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe1e4-113">Element</span></span>|<span data-ttu-id="fe1e4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe1e4-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe1e4-115">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="fe1e4-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="fe1e4-116">Bir yönlendirme tablosu, ne zaman eşleşen filtre ileti göndermek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fe1e4-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe1e4-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe1e4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="fe1e4-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe1e4-118">Element</span></span>|<span data-ttu-id="fe1e4-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe1e4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe1e4-120">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="fe1e4-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="fe1e4-121">Yönlendirme filtreleri ve yönlendirme tablolarını içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="fe1e4-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe1e4-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe1e4-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
