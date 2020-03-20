---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c93a1f482882cc8cd9d229d82597efa64ba209bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152976"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="e956a-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="e956a-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="e956a-103">Ad alanı bölümünün <xref:System.Runtime.Serialization> kök öğesini temsil eder ve <xref:System.Runtime.Serialization.DataContractSerializer>'nin seçeneklerini ayarlamak için öğeler içerir.</span><span class="sxs-lookup"><span data-stu-id="e956a-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

<span data-ttu-id="e956a-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e956a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e956a-105">&nbsp;&nbsp;**\<system.runtime.serialization>**</span><span class="sxs-lookup"><span data-stu-id="e956a-105">&nbsp;&nbsp;**\<system.runtime.serialization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e956a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e956a-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e956a-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e956a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e956a-108">Aşağıdaki bölümlerde öznitelikleri, alt öğeleri ve üst öğeleri açıklar</span><span class="sxs-lookup"><span data-stu-id="e956a-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e956a-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e956a-109">Attributes</span></span>  
 <span data-ttu-id="e956a-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="e956a-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e956a-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e956a-111">Child Elements</span></span>  
  
|<span data-ttu-id="e956a-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="e956a-112">Element</span></span>|<span data-ttu-id="e956a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e956a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e956a-114">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="e956a-114">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="e956a-115">Deserialization zaman kullanılacak bilinen türlerin eklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e956a-115">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e956a-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e956a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e956a-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="e956a-117">Element</span></span>|<span data-ttu-id="e956a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e956a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e956a-119">\<yapılandırma> Element</span><span class="sxs-lookup"><span data-stu-id="e956a-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="e956a-120">Yapılandırma için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="e956a-120">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e956a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e956a-121">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="e956a-122">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="e956a-122">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="e956a-123">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="e956a-123">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
