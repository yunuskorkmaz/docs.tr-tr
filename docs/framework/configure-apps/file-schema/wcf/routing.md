---
title: '&lt;Yönlendirme&gt;'
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 1771d8a2603a8f61af6ba6e2acf6243d2fd073f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747734"
---
# <a name="ltroutinggt"></a><span data-ttu-id="a80d1-102">&lt;Yönlendirme&gt;</span><span class="sxs-lookup"><span data-stu-id="a80d1-102">&lt;routing&gt;</span></span>

<span data-ttu-id="a80d1-103">Windows Communication Foundation (WCF) türü belirlenemiyor yönlendirme bir filtre kümesi tanımlamak için yapılandırma bölümünü temsil eder <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için hedef uç nokta tanımlayan tabloları yapılırken kullanılacak ne zaman bir filtre ile eşleşen için iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="a80d1-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="a80d1-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="a80d1-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="a80d1-105">&nbsp;&nbsp;**\<Yönlendirme >**</span><span class="sxs-lookup"><span data-stu-id="a80d1-105">&nbsp;&nbsp;**\<routing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a80d1-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a80d1-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="a80d1-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="a80d1-107">Attributes and elements</span></span>

<span data-ttu-id="a80d1-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a80d1-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a80d1-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a80d1-109">Attributes</span></span>

<span data-ttu-id="a80d1-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="a80d1-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="a80d1-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a80d1-111">Child elements</span></span>

|     | <span data-ttu-id="a80d1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a80d1-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a80d1-113">**\<filtreleri >**</span><span class="sxs-lookup"><span data-stu-id="a80d1-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="a80d1-114">Windows Communication Foundation (WCF) MessageFilter türünü gelen iletileri hesaplanırken kullanılacak belirlemek yönlendirme filtreleri kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="a80d1-114">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="a80d1-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="a80d1-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="a80d1-116">Yönlendirme filtreleri ve filtre eşleştiğinde kullanmak için hangi uç noktaya belirtmek için hedef uç noktaları arasında eşlemeler içerir.</span><span class="sxs-lookup"><span data-stu-id="a80d1-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="a80d1-117">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="a80d1-117">Parent elements</span></span>

|     | <span data-ttu-id="a80d1-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a80d1-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="a80d1-119">**\<Sistem. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="a80d1-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="a80d1-120">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="a80d1-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="a80d1-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a80d1-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
