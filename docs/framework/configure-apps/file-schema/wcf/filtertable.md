---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 918a365004efea82f4ef4c8868f6821d4bb6da18
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855185"
---
# \<filterTable>
<span data-ttu-id="aec6d-101">Filtrenin, filtre true olarak değerlendirilirse, iletileri yönlendirmek için bir filtre listesi ve istemci uç noktası içeren bir yönlendirme tablosunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aec6d-101">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**  
  
## <a name="syntax"></a><span data-ttu-id="aec6d-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aec6d-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aec6d-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aec6d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="aec6d-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aec6d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aec6d-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aec6d-105">Attributes</span></span>  
  
|<span data-ttu-id="aec6d-106">Öğe</span><span class="sxs-lookup"><span data-stu-id="aec6d-106">Element</span></span>|<span data-ttu-id="aec6d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aec6d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aec6d-108">name</span><span class="sxs-lookup"><span data-stu-id="aec6d-108">name</span></span>|<span data-ttu-id="aec6d-109">Bu yapılandırma öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="aec6d-109">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aec6d-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aec6d-110">Child Elements</span></span>  
  
|<span data-ttu-id="aec6d-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="aec6d-111">Element</span></span>|<span data-ttu-id="aec6d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aec6d-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="aec6d-113">Filtre eşleştiğinde ileti göndermek için yönlendirme filtreleri ve hedef uç noktalar arasındaki eşlemeler.</span><span class="sxs-lookup"><span data-stu-id="aec6d-113">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aec6d-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aec6d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="aec6d-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="aec6d-115">Element</span></span>|<span data-ttu-id="aec6d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aec6d-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="aec6d-117">Yönlendirme tablolarını içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="aec6d-117">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aec6d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aec6d-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
