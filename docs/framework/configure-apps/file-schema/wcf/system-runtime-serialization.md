---
title: '&lt;System.Runtime.Serialization&gt;'
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 6ffd4057028adcd123086173a05164eb5d2622f3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="ba838-102">&lt;System.Runtime.Serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="ba838-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="ba838-103">Kök öğe için temsil eden <xref:System.Runtime.Serialization> ad alanı bölüm ve seçenekleri ayarlamak için öğeleri içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ba838-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="ba838-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="ba838-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba838-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba838-105">Syntax</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer">  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
             <parameter index="Integer"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba838-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba838-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ba838-107">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="ba838-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba838-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ba838-108">Attributes</span></span>  
 <span data-ttu-id="ba838-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="ba838-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ba838-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba838-110">Child Elements</span></span>  
  
|<span data-ttu-id="ba838-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="ba838-111">Element</span></span>|<span data-ttu-id="ba838-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba838-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba838-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="ba838-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="ba838-114">Kullanılacak bilinen türleri eklenmesini etkinleştirir zaman seri durumundan çıkarma.</span><span class="sxs-lookup"><span data-stu-id="ba838-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ba838-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba838-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ba838-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="ba838-116">Element</span></span>|<span data-ttu-id="ba838-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba838-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba838-118">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="ba838-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="ba838-119">Yapılandırma için üst düzey öğesi.</span><span class="sxs-lookup"><span data-stu-id="ba838-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba838-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba838-120">See Also</span></span>  
 <xref:System.Runtime.Serialization>  
 [<span data-ttu-id="ba838-121">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="ba838-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="ba838-122">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="ba838-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
