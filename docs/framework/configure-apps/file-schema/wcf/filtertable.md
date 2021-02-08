---
description: 'Hakkında daha fazla bilgi edinin: <filterTable>'
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 2051bb0e778e5676f39d91b7d7ba415fd7e523af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782045"
---
# \<filterTable>

<span data-ttu-id="573a2-102">Filtrenin, filtre true olarak değerlendirilirse, iletileri yönlendirmek için bir filtre listesi ve istemci uç noktası içeren bir yönlendirme tablosunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="573a2-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**  
  
## <a name="syntax"></a><span data-ttu-id="573a2-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="573a2-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="573a2-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="573a2-104">Attributes and Elements</span></span>  

 <span data-ttu-id="573a2-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="573a2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="573a2-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="573a2-106">Attributes</span></span>  
  
|<span data-ttu-id="573a2-107">Öğe</span><span class="sxs-lookup"><span data-stu-id="573a2-107">Element</span></span>|<span data-ttu-id="573a2-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="573a2-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="573a2-109">name</span><span class="sxs-lookup"><span data-stu-id="573a2-109">name</span></span>|<span data-ttu-id="573a2-110">Bu yapılandırma öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="573a2-110">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="573a2-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="573a2-111">Child Elements</span></span>  
  
|<span data-ttu-id="573a2-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="573a2-112">Element</span></span>|<span data-ttu-id="573a2-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="573a2-113">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="573a2-114">Filtre eşleştiğinde ileti göndermek için yönlendirme filtreleri ve hedef uç noktalar arasındaki eşlemeler.</span><span class="sxs-lookup"><span data-stu-id="573a2-114">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="573a2-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="573a2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="573a2-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="573a2-116">Element</span></span>|<span data-ttu-id="573a2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="573a2-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="573a2-118">Yönlendirme tablolarını içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="573a2-118">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="573a2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="573a2-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
