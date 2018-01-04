---
title: "&lt;Yönlendirme&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ef71753a4b0ff20a966842119adb6e637ded1f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltroutinggt"></a><span data-ttu-id="0bd29-102">&lt;Yönlendirme&gt;</span><span class="sxs-lookup"><span data-stu-id="0bd29-102">&lt;routing&gt;</span></span>

<span data-ttu-id="0bd29-103">Türünü belirleme yönlendirme bir filtre kümesi tanımlamak için yapılandırma bölümünü temsil eder [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için ne zaman iletileri göndermek için hedef uç nokta tanımlayan tabloları yapılırken kullanılacak bir Filtre eşleşir.</span><span class="sxs-lookup"><span data-stu-id="0bd29-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="0bd29-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="0bd29-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="0bd29-105">&nbsp;&nbsp;**\<Yönlendirme >**</span><span class="sxs-lookup"><span data-stu-id="0bd29-105">&nbsp;&nbsp;**\<routing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0bd29-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0bd29-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="0bd29-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="0bd29-107">Attributes and elements</span></span>

<span data-ttu-id="0bd29-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0bd29-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0bd29-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0bd29-109">Attributes</span></span>

<span data-ttu-id="0bd29-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="0bd29-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="0bd29-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="0bd29-111">Child elements</span></span>

|     | <span data-ttu-id="0bd29-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bd29-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0bd29-113">**\<filtreleri >**</span><span class="sxs-lookup"><span data-stu-id="0bd29-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="0bd29-114">Bir dizi türünü belirleme yönlendirme filtreleri içeren [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] gelen iletileri değerlendirirken MessageFilter kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0bd29-114">Contains a set of routing filters that determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="0bd29-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="0bd29-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="0bd29-116">Yönlendirme filtreleri ve filtre eşleştiğinde kullanmak için hangi uç noktaya belirtmek için hedef uç noktaları arasında eşlemeler içerir.</span><span class="sxs-lookup"><span data-stu-id="0bd29-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="0bd29-117">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="0bd29-117">Parent elements</span></span>

|     | <span data-ttu-id="0bd29-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bd29-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="0bd29-119">**\<Sistem. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="0bd29-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="0bd29-120">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="0bd29-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="0bd29-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bd29-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
