---
title: '&lt;filterTables&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 028681acffcd93633807bdb1c6fa78aab98011c4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="e4eba-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="e4eba-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="e4eba-103">Yönlendirme filtreleri ve filtre eşleştiğinde ileti göndermek için hedef uç noktaları arasındaki eşlemeleri içeren yönlendirme tablolarını tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e4eba-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="e4eba-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e4eba-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e4eba-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="e4eba-105">\<routing></span></span>  
<span data-ttu-id="e4eba-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="e4eba-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4eba-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4eba-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e4eba-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4eba-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e4eba-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4eba-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4eba-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e4eba-110">Attributes</span></span>  
 <span data-ttu-id="e4eba-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="e4eba-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e4eba-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4eba-112">Child Elements</span></span>  
  
|<span data-ttu-id="e4eba-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4eba-113">Element</span></span>|<span data-ttu-id="e4eba-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4eba-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4eba-115">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="e4eba-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="e4eba-116">Yönlendirme filtreleri ve ne zaman bir filtre ile eşleşen için iletileri göndermek için hedef uç noktaları arasındaki eşlemeleri içeren bir yönlendirme tablosu.</span><span class="sxs-lookup"><span data-stu-id="e4eba-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4eba-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4eba-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e4eba-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4eba-118">Element</span></span>|<span data-ttu-id="e4eba-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4eba-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4eba-120">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="e4eba-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="e4eba-121">Yönlendirme filtreleri ve yönlendirme tabloları içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="e4eba-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4eba-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4eba-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
