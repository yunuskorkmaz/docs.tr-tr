---
description: 'Hakkında daha fazla bilgi edinin: <routing>'
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 62222b527a14310b66015d4fdc4503e6cff25c8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683352"
---
# \<routing>

<span data-ttu-id="94a29-102">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümünü temsil eder <xref:System.ServiceModel.Dispatcher.MessageFilter> . Ayrıca, bir filtre eşleştiğinde ileti göndermek için hedef uç noktalarını tanımlayan yönlendirme tablolarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="94a29-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**
  
## <a name="syntax"></a><span data-ttu-id="94a29-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="94a29-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String"
               filterName="String"
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94a29-104">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="94a29-104">Attributes and elements</span></span>

<span data-ttu-id="94a29-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="94a29-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="94a29-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="94a29-106">Attributes</span></span>

<span data-ttu-id="94a29-107">Yok</span><span class="sxs-lookup"><span data-stu-id="94a29-107">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="94a29-108">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="94a29-108">Child elements</span></span>

|     | <span data-ttu-id="94a29-109">Description</span><span class="sxs-lookup"><span data-stu-id="94a29-109">Description</span></span> |
| --- | ----------- |
| [**\<filters>**](filters-of-routing.md) | <span data-ttu-id="94a29-110">Gelen iletiler değerlendirilirken Windows Communication Foundation (WCF) MessageFilter türünü belirten bir yönlendirme filtreleri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="94a29-110">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [**\<filterTables>**](filtertables.md) | <span data-ttu-id="94a29-111">Filtre eşleştiğinde kullanılacak bitiş noktasını belirtmek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içerir.</span><span class="sxs-lookup"><span data-stu-id="94a29-111">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="94a29-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="94a29-112">Parent elements</span></span>

|     | <span data-ttu-id="94a29-113">Description</span><span class="sxs-lookup"><span data-stu-id="94a29-113">Description</span></span> |
| --- | ----------- |
| **\<system.ServiceModel>** | <span data-ttu-id="94a29-114">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="94a29-114">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="94a29-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94a29-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
