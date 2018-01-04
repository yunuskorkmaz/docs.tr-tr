---
title: '&lt;filterTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8cf87cc74c7bb5d495584407c803dacc7b94f195
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="0b28e-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="0b28e-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="0b28e-103">Filtre doğru olarak değerlendirilirse karşı iletileri ve istemci uç noktasına iletileri yönlendirmek için değerlendirilecek filtrelerin listesi içeren bir yönlendirme tablosu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0b28e-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="0b28e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="0b28e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0b28e-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="0b28e-105">\<routing></span></span>  
<span data-ttu-id="0b28e-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="0b28e-106">\<routingTables></span></span>  
<span data-ttu-id="0b28e-107">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="0b28e-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b28e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b28e-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0b28e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b28e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0b28e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b28e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b28e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0b28e-111">Attributes</span></span>  
  
|<span data-ttu-id="0b28e-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="0b28e-112">Element</span></span>|<span data-ttu-id="0b28e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b28e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b28e-114">name</span><span class="sxs-lookup"><span data-stu-id="0b28e-114">name</span></span>|<span data-ttu-id="0b28e-115">Bu yapılandırma öğesi benzersiz adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="0b28e-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b28e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b28e-116">Child Elements</span></span>  
  
|<span data-ttu-id="0b28e-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="0b28e-117">Element</span></span>|<span data-ttu-id="0b28e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b28e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b28e-119">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="0b28e-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="0b28e-120">Yönlendirme filtreleri ve ne zaman bir filtre ile eşleşen için iletileri göndermek için hedef uç noktaları arasındaki eşlemeleri.</span><span class="sxs-lookup"><span data-stu-id="0b28e-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0b28e-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b28e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0b28e-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="0b28e-122">Element</span></span>|<span data-ttu-id="0b28e-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b28e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b28e-124">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="0b28e-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="0b28e-125">Yönlendirme tabloları içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="0b28e-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b28e-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b28e-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
