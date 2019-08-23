---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 3c7e9cb1284ab55c8dd199d9fb47a223698814f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934134"
---
# <a name="routing"></a><span data-ttu-id="d3100-101">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="d3100-101">\<routing></span></span>

<span data-ttu-id="d3100-102">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> türünü ve hedef bitiş noktalarını tanımlayan yönlendirme tablolarını belirleyen bir yönlendirme filtreleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder. Filtre eşleştiğinde iletileri gönder.</span><span class="sxs-lookup"><span data-stu-id="d3100-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="d3100-103">[ **\<System. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="d3100-103">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="d3100-104">&nbsp;&nbsp; **\<Yönlendirme >**</span><span class="sxs-lookup"><span data-stu-id="d3100-104">&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="d3100-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3100-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3100-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="d3100-106">Attributes and elements</span></span>

<span data-ttu-id="d3100-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d3100-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d3100-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d3100-108">Attributes</span></span>

<span data-ttu-id="d3100-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="d3100-109">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="d3100-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d3100-110">Child elements</span></span>

|     | <span data-ttu-id="d3100-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3100-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d3100-112"> **\<Filtreler >** </span><span class="sxs-lookup"><span data-stu-id="d3100-112">**\<filters>**</span></span>](filters-of-routing.md) | <span data-ttu-id="d3100-113">Gelen iletiler değerlendirilirken Windows Communication Foundation (WCF) MessageFilter türünü belirten bir yönlendirme filtreleri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="d3100-113">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="d3100-114"> **\<filterTables >** </span><span class="sxs-lookup"><span data-stu-id="d3100-114">**\<filterTables>**</span></span>](filtertables.md) | <span data-ttu-id="d3100-115">Filtre eşleştiğinde kullanılacak bitiş noktasını belirtmek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içerir.</span><span class="sxs-lookup"><span data-stu-id="d3100-115">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="d3100-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="d3100-116">Parent elements</span></span>

|     | <span data-ttu-id="d3100-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3100-117">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="d3100-118">**\<sistemin. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="d3100-118">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="d3100-119">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="d3100-119">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="d3100-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3100-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
