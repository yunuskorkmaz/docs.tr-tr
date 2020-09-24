---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 84ced06691ce3b3c9c9573fc9d114335096a849d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157115"
---
# \<system.runtime.serialization>

<span data-ttu-id="d9b9b-102">Ad alanı bölümünün kök öğesini temsil eder <xref:System.Runtime.Serialization> ve seçeneklerini ayarlamak için öğeleri içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="d9b9b-102">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.serialization>**  
  
## <a name="syntax"></a><span data-ttu-id="d9b9b-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="d9b9b-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9b9b-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9b9b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d9b9b-105">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="d9b9b-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9b9b-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d9b9b-106">Attributes</span></span>  

 <span data-ttu-id="d9b9b-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="d9b9b-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d9b9b-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9b9b-108">Child Elements</span></span>  
  
|<span data-ttu-id="d9b9b-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9b9b-109">Element</span></span>|<span data-ttu-id="d9b9b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9b9b-110">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="d9b9b-111">Seri durumdan çıkarma sırasında kullanılacak bilinen türlerin eklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9b9b-111">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9b9b-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9b9b-112">Parent Elements</span></span>  
  
|<span data-ttu-id="d9b9b-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9b9b-113">Element</span></span>|<span data-ttu-id="d9b9b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9b9b-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9b9b-115">\<configuration> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="d9b9b-115">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="d9b9b-116">Yapılandırma için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="d9b9b-116">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9b9b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9b9b-117">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="d9b9b-118">Veri Sözleşmelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="d9b9b-118">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="d9b9b-119">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="d9b9b-119">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
