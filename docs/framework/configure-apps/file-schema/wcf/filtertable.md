---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 7bdc76ba7a8e2927b93fa0207f48cc569279482f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747417"
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="9e275-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="9e275-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="9e275-103">Filtre doğru olarak değerlendirilirse karşı iletileri ve istemci uç noktasına iletileri yönlendirmek için değerlendirilecek filtrelerin listesi içeren bir yönlendirme tablosu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9e275-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="9e275-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9e275-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9e275-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="9e275-105">\<routing></span></span>  
<span data-ttu-id="9e275-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="9e275-106">\<routingTables></span></span>  
<span data-ttu-id="9e275-107">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="9e275-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e275-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e275-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9e275-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e275-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9e275-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9e275-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e275-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9e275-111">Attributes</span></span>  
  
|<span data-ttu-id="9e275-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="9e275-112">Element</span></span>|<span data-ttu-id="9e275-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e275-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e275-114">name</span><span class="sxs-lookup"><span data-stu-id="9e275-114">name</span></span>|<span data-ttu-id="9e275-115">Bu yapılandırma öğesi benzersiz adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="9e275-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e275-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e275-116">Child Elements</span></span>  
  
|<span data-ttu-id="9e275-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="9e275-117">Element</span></span>|<span data-ttu-id="9e275-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e275-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e275-119">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="9e275-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="9e275-120">Yönlendirme filtreleri ve ne zaman bir filtre ile eşleşen için iletileri göndermek için hedef uç noktaları arasındaki eşlemeleri.</span><span class="sxs-lookup"><span data-stu-id="9e275-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9e275-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e275-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9e275-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="9e275-122">Element</span></span>|<span data-ttu-id="9e275-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e275-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e275-124">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="9e275-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="9e275-125">Yönlendirme tabloları içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="9e275-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e275-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e275-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
