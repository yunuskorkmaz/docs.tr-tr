---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c34eba2614a354f1753d8da077f8653f2c260a97
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757917"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="213f9-102">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="213f9-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="213f9-103">İçin olan kök öğesini temsil eden <xref:System.Runtime.Serialization> ad uzayı bölümü ve seçeneklerini ayarlamak için öğeleri içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="213f9-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="213f9-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="213f9-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="213f9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="213f9-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="213f9-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="213f9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="213f9-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="213f9-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="213f9-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="213f9-108">Attributes</span></span>  
 <span data-ttu-id="213f9-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="213f9-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="213f9-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="213f9-110">Child Elements</span></span>  
  
|<span data-ttu-id="213f9-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="213f9-111">Element</span></span>|<span data-ttu-id="213f9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="213f9-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="213f9-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="213f9-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="213f9-114">Kullanılacak bilinen türlerinin eklenmesi sağlar, seri durumdan çıkarma.</span><span class="sxs-lookup"><span data-stu-id="213f9-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="213f9-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="213f9-115">Parent Elements</span></span>  
  
|<span data-ttu-id="213f9-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="213f9-116">Element</span></span>|<span data-ttu-id="213f9-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="213f9-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="213f9-118">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="213f9-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="213f9-119">Yapılandırma için üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="213f9-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="213f9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="213f9-120">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="213f9-121">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="213f9-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="213f9-122">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="213f9-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
