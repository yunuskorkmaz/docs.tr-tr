---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: fb36feedc5fb2cbdf3827cbe44242c7ac6ab8a9b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185697"
---
# \<filterTable>

<span data-ttu-id="29a64-101">Filtrenin, filtre true olarak değerlendirilirse, iletileri yönlendirmek için bir filtre listesi ve istemci uç noktası içeren bir yönlendirme tablosunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="29a64-101">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**  
  
## <a name="syntax"></a><span data-ttu-id="29a64-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="29a64-102">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
     name="String">
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29a64-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="29a64-103">Attributes and Elements</span></span>  

 <span data-ttu-id="29a64-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="29a64-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29a64-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="29a64-105">Attributes</span></span>  
  
|<span data-ttu-id="29a64-106">Öğe</span><span class="sxs-lookup"><span data-stu-id="29a64-106">Element</span></span>|<span data-ttu-id="29a64-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29a64-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29a64-108">name</span><span class="sxs-lookup"><span data-stu-id="29a64-108">name</span></span>|<span data-ttu-id="29a64-109">Bu yapılandırma öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="29a64-109">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29a64-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="29a64-110">Child Elements</span></span>  
  
|<span data-ttu-id="29a64-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="29a64-111">Element</span></span>|<span data-ttu-id="29a64-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29a64-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="29a64-113">Filtre eşleştiğinde ileti göndermek için yönlendirme filtreleri ve hedef uç noktalar arasındaki eşlemeler.</span><span class="sxs-lookup"><span data-stu-id="29a64-113">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29a64-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="29a64-114">Parent Elements</span></span>  
  
|<span data-ttu-id="29a64-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="29a64-115">Element</span></span>|<span data-ttu-id="29a64-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29a64-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="29a64-117">Yönlendirme tablolarını içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="29a64-117">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29a64-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29a64-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
