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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75e06b0258f2e4f65d441c25b5081cf7a6627518
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="34237-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="34237-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="34237-103">Yönlendirme filtreleri ve filtre eşleştiğinde ileti göndermek için hedef uç noktaları arasındaki eşlemeleri içeren yönlendirme tablolarını tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="34237-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="34237-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="34237-104">\<system.serviceModel></span></span>  
<span data-ttu-id="34237-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="34237-105">\<routing></span></span>  
<span data-ttu-id="34237-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="34237-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34237-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34237-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34237-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="34237-108">Attributes and Elements</span></span>  
 <span data-ttu-id="34237-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="34237-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34237-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="34237-110">Attributes</span></span>  
 <span data-ttu-id="34237-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="34237-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="34237-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="34237-112">Child Elements</span></span>  
  
|<span data-ttu-id="34237-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="34237-113">Element</span></span>|<span data-ttu-id="34237-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34237-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34237-115">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="34237-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="34237-116">Yönlendirme filtreleri ve ne zaman bir filtre ile eşleşen için iletileri göndermek için hedef uç noktaları arasındaki eşlemeleri içeren bir yönlendirme tablosu.</span><span class="sxs-lookup"><span data-stu-id="34237-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34237-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="34237-117">Parent Elements</span></span>  
  
|<span data-ttu-id="34237-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="34237-118">Element</span></span>|<span data-ttu-id="34237-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34237-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34237-120">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="34237-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="34237-121">Yönlendirme filtreleri ve yönlendirme tabloları içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="34237-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34237-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34237-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
