---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: b67f51e634d1294830690dad8c8cffb1fc9a6cd2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399458"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="85e64-102">\<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="85e64-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="85e64-103"><xref:System.Runtime.Serialization> Ad alanı bölümünün kök öğesini temsil eder ve seçeneklerini <xref:System.Runtime.Serialization.DataContractSerializer>ayarlamak için öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="85e64-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

<span data-ttu-id="85e64-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="85e64-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="85e64-105">&nbsp;&nbsp; **\<System. Runtime. Serialization >**</span><span class="sxs-lookup"><span data-stu-id="85e64-105">&nbsp;&nbsp;**\<system.runtime.serialization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85e64-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85e64-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85e64-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="85e64-107">Attributes and Elements</span></span>  
 <span data-ttu-id="85e64-108">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="85e64-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85e64-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="85e64-109">Attributes</span></span>  
 <span data-ttu-id="85e64-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="85e64-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="85e64-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="85e64-111">Child Elements</span></span>  
  
|<span data-ttu-id="85e64-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="85e64-112">Element</span></span>|<span data-ttu-id="85e64-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85e64-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85e64-114">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="85e64-114">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="85e64-115">Seri durumdan çıkarma sırasında kullanılacak bilinen türlerin eklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="85e64-115">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85e64-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="85e64-116">Parent Elements</span></span>  
  
|<span data-ttu-id="85e64-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="85e64-117">Element</span></span>|<span data-ttu-id="85e64-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85e64-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85e64-119">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="85e64-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="85e64-120">Yapılandırma için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="85e64-120">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85e64-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85e64-121">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="85e64-122">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="85e64-122">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="85e64-123">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="85e64-123">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
 