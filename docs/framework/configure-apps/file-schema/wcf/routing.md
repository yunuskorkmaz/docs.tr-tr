---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: cc7c1a64f9481a7ab41cf35241ade04bd690dae0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786392"
---
# <a name="routing"></a><span data-ttu-id="46d4e-101">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="46d4e-101">\<routing></span></span>

<span data-ttu-id="46d4e-102">Windows Communication Foundation (WCF) türünü belirleyen ve yönlendirme süzgeçleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için hedef bitiş noktalarını tanımlayan tabloları yapılırken kullanılacak ne zaman eşleşen bir filtre, iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="46d4e-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="46d4e-103">[**\<system.serviceModel>**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="46d4e-103">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="46d4e-104">&nbsp;&nbsp;**\<Yönlendirme >**</span><span class="sxs-lookup"><span data-stu-id="46d4e-104">&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="46d4e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46d4e-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46d4e-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="46d4e-106">Attributes and elements</span></span>

<span data-ttu-id="46d4e-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46d4e-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="46d4e-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="46d4e-108">Attributes</span></span>

<span data-ttu-id="46d4e-109">None</span><span class="sxs-lookup"><span data-stu-id="46d4e-109">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="46d4e-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="46d4e-110">Child elements</span></span>

|     | <span data-ttu-id="46d4e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46d4e-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="46d4e-112">**\<filtreleri >**</span><span class="sxs-lookup"><span data-stu-id="46d4e-112">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="46d4e-113">Windows Communication Foundation (WCF) MessageFilter türünü gelen iletileri değerlendirmek kullanılacağını belirlemek yönlendirme süzgeçleri kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="46d4e-113">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="46d4e-114">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="46d4e-114">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="46d4e-115">Filtreler eşleştiğinde kullanmak için hangi uç noktaya belirtmek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="46d4e-115">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="46d4e-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="46d4e-116">Parent elements</span></span>

|     | <span data-ttu-id="46d4e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46d4e-117">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="46d4e-118">**\<sistemi. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="46d4e-118">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="46d4e-119">Tüm WCF yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="46d4e-119">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="46d4e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46d4e-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
