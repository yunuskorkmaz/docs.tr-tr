---
description: 'Hakkında daha fazla bilgi <filters> edinin: <routing>'
title: <filters> / <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 41b51453f53fca042f53ca1ee8372413b8478ecd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782058"
---
# <a name="filters-of-routing"></a><span data-ttu-id="4c899-103">\<filters> / \<routing></span><span class="sxs-lookup"><span data-stu-id="4c899-103">\<filters> of \<routing></span></span>

<span data-ttu-id="4c899-104">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümünü temsil eder <xref:System.ServiceModel.Dispatcher.MessageFilter> .</span><span class="sxs-lookup"><span data-stu-id="4c899-104">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**  
  
## <a name="syntax"></a><span data-ttu-id="4c899-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4c899-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c899-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="4c899-106">Attributes and elements</span></span>

<span data-ttu-id="4c899-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c899-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4c899-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4c899-108">Attributes</span></span>

<span data-ttu-id="4c899-109">Yok</span><span class="sxs-lookup"><span data-stu-id="4c899-109">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="4c899-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="4c899-110">Child elements</span></span>

|     | <span data-ttu-id="4c899-111">Description</span><span class="sxs-lookup"><span data-stu-id="4c899-111">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="4c899-112">Gelen iletiler değerlendirilirken Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi içerir <xref:System.ServiceModel.Dispatcher.MessageFilter> .</span><span class="sxs-lookup"><span data-stu-id="4c899-112">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="4c899-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="4c899-113">Parent elements</span></span>

|     | <span data-ttu-id="4c899-114">Description</span><span class="sxs-lookup"><span data-stu-id="4c899-114">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="4c899-115">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümünü temsil eder <xref:System.ServiceModel.Dispatcher.MessageFilter> . Ayrıca, bir filtre eşleştiğinde ileti göndermek için hedef uç noktalarını tanımlayan yönlendirme tablolarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4c899-115">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="4c899-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c899-116">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
