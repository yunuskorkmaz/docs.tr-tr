---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399968"
---
# <a name="routing"></a><span data-ttu-id="263c3-101">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="263c3-101">\<routing></span></span>

<span data-ttu-id="263c3-102">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> türünü ve hedef bitiş noktalarını tanımlayan yönlendirme tablolarını belirleyen bir yönlendirme filtreleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder. Filtre eşleştiğinde iletileri gönder.</span><span class="sxs-lookup"><span data-stu-id="263c3-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="263c3-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="263c3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="263c3-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="263c3-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="263c3-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<Yönlendirme >**</span><span class="sxs-lookup"><span data-stu-id="263c3-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="263c3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="263c3-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="263c3-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="263c3-107">Attributes and elements</span></span>

<span data-ttu-id="263c3-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="263c3-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="263c3-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="263c3-109">Attributes</span></span>

<span data-ttu-id="263c3-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="263c3-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="263c3-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="263c3-111">Child elements</span></span>

|     | <span data-ttu-id="263c3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="263c3-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="263c3-113"> **\<Filtreler >** </span><span class="sxs-lookup"><span data-stu-id="263c3-113">**\<filters>**</span></span>](filters-of-routing.md) | <span data-ttu-id="263c3-114">Gelen iletiler değerlendirilirken Windows Communication Foundation (WCF) MessageFilter türünü belirten bir yönlendirme filtreleri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="263c3-114">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="263c3-115"> **\<filterTables >** </span><span class="sxs-lookup"><span data-stu-id="263c3-115">**\<filterTables>**</span></span>](filtertables.md) | <span data-ttu-id="263c3-116">Filtre eşleştiğinde kullanılacak bitiş noktasını belirtmek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içerir.</span><span class="sxs-lookup"><span data-stu-id="263c3-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="263c3-117">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="263c3-117">Parent elements</span></span>

|     | <span data-ttu-id="263c3-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="263c3-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="263c3-119">**\<sistemin. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="263c3-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="263c3-120">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="263c3-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="263c3-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="263c3-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
