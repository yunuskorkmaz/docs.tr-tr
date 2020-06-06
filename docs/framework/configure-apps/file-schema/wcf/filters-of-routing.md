---
title: <filters> / <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855243"
---
# <a name="filters-of-routing"></a><span data-ttu-id="f983d-102">\<filters> / \<routing></span><span class="sxs-lookup"><span data-stu-id="f983d-102">\<filters> of \<routing></span></span>

<span data-ttu-id="f983d-103">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümünü temsil eder <xref:System.ServiceModel.Dispatcher.MessageFilter> .</span><span class="sxs-lookup"><span data-stu-id="f983d-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**  
  
## <a name="syntax"></a><span data-ttu-id="f983d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f983d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f983d-105">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="f983d-105">Attributes and elements</span></span>

<span data-ttu-id="f983d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f983d-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f983d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f983d-107">Attributes</span></span>

<span data-ttu-id="f983d-108">Yok</span><span class="sxs-lookup"><span data-stu-id="f983d-108">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="f983d-109">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="f983d-109">Child elements</span></span>

|     | <span data-ttu-id="f983d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f983d-110">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="f983d-111">Gelen iletiler değerlendirilirken Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi içerir <xref:System.ServiceModel.Dispatcher.MessageFilter> .</span><span class="sxs-lookup"><span data-stu-id="f983d-111">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="f983d-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="f983d-112">Parent elements</span></span>

|     | <span data-ttu-id="f983d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f983d-113">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="f983d-114">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümünü temsil eder <xref:System.ServiceModel.Dispatcher.MessageFilter> . Ayrıca, bir filtre eşleştiğinde ileti göndermek için hedef uç noktalarını tanımlayan yönlendirme tablolarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f983d-114">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f983d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f983d-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
