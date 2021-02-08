---
description: 'Hakkında daha fazla bilgi edinin: <System. Runtime. Serialization>'
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: cf1d95c8650e4b6979d4f34b0bed1fa395911f2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786635"
---
# \<system.runtime.serialization>

<span data-ttu-id="fa95a-103">Ad alanı bölümünün kök öğesini temsil eder <xref:System.Runtime.Serialization> ve seçeneklerini ayarlamak için öğeleri içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="fa95a-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.serialization>**  
  
## <a name="syntax"></a><span data-ttu-id="fa95a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fa95a-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa95a-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa95a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="fa95a-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="fa95a-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa95a-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fa95a-107">Attributes</span></span>  

 <span data-ttu-id="fa95a-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="fa95a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fa95a-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa95a-109">Child Elements</span></span>  
  
|<span data-ttu-id="fa95a-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa95a-110">Element</span></span>|<span data-ttu-id="fa95a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa95a-111">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="fa95a-112">Seri durumdan çıkarma sırasında kullanılacak bilinen türlerin eklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa95a-112">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa95a-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa95a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="fa95a-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa95a-114">Element</span></span>|<span data-ttu-id="fa95a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa95a-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa95a-116">\<configuration> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="fa95a-116">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="fa95a-117">Yapılandırma için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="fa95a-117">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa95a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa95a-118">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="fa95a-119">Veri Sözleşmelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="fa95a-119">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="fa95a-120">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="fa95a-120">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
