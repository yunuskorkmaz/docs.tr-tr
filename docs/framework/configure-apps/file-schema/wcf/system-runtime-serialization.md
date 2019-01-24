---
title: '&lt;System.Runtime.Serialization&gt;'
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 6321ab192161468142a4cd4d2155d3f787bb0165
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600267"
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="6a2b2-102">&lt;System.Runtime.Serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="6a2b2-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="6a2b2-103">İçin olan kök öğesini temsil eden <xref:System.Runtime.Serialization> ad uzayı bölümü ve seçeneklerini ayarlamak için öğeleri içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6a2b2-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="6a2b2-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="6a2b2-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a2b2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a2b2-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a2b2-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a2b2-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6a2b2-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6a2b2-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a2b2-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6a2b2-108">Attributes</span></span>  
 <span data-ttu-id="6a2b2-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="6a2b2-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6a2b2-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a2b2-110">Child Elements</span></span>  
  
|<span data-ttu-id="6a2b2-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a2b2-111">Element</span></span>|<span data-ttu-id="6a2b2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a2b2-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a2b2-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="6a2b2-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="6a2b2-114">Kullanılacak bilinen türlerinin eklenmesi sağlar, seri durumdan çıkarma.</span><span class="sxs-lookup"><span data-stu-id="6a2b2-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6a2b2-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a2b2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6a2b2-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a2b2-116">Element</span></span>|<span data-ttu-id="6a2b2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a2b2-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a2b2-118">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="6a2b2-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="6a2b2-119">Yapılandırma için üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="6a2b2-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a2b2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a2b2-120">See also</span></span>
- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="6a2b2-121">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="6a2b2-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="6a2b2-122">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="6a2b2-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
