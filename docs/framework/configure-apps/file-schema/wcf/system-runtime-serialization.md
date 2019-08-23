---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 4ec5cd19ccdc5c21a3caf426520d51442dc5ab3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938931"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="e4317-102">\<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="e4317-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="e4317-103"><xref:System.Runtime.Serialization> Ad alanı bölümünün kök öğesini temsil eder ve seçeneklerini <xref:System.Runtime.Serialization.DataContractSerializer>ayarlamak için öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e4317-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="e4317-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="e4317-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4317-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4317-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4317-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4317-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e4317-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="e4317-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4317-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e4317-108">Attributes</span></span>  
 <span data-ttu-id="e4317-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="e4317-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e4317-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4317-110">Child Elements</span></span>  
  
|<span data-ttu-id="e4317-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4317-111">Element</span></span>|<span data-ttu-id="e4317-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4317-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4317-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="e4317-113">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="e4317-114">Seri durumdan çıkarma sırasında kullanılacak bilinen türlerin eklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4317-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4317-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4317-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e4317-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4317-116">Element</span></span>|<span data-ttu-id="e4317-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4317-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4317-118">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="e4317-118">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="e4317-119">Yapılandırma için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="e4317-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4317-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4317-120">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="e4317-121">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="e4317-121">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="e4317-122">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="e4317-122">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
