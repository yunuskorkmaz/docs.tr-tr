---
title: '&lt;System.Runtime.Serialization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5a47417ded6e0917fadf2134eed5997d9d3b3d74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="6b2c1-102">&lt;System.Runtime.Serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="6b2c1-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="6b2c1-103">Kök öğe için temsil eden <xref:System.Runtime.Serialization> ad alanı bölüm ve seçenekleri ayarlamak için öğeleri içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6b2c1-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="6b2c1-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="6b2c1-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b2c1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b2c1-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b2c1-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b2c1-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6b2c1-107">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="6b2c1-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b2c1-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6b2c1-108">Attributes</span></span>  
 <span data-ttu-id="6b2c1-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="6b2c1-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6b2c1-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b2c1-110">Child Elements</span></span>  
  
|<span data-ttu-id="6b2c1-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b2c1-111">Element</span></span>|<span data-ttu-id="6b2c1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b2c1-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b2c1-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="6b2c1-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="6b2c1-114">Kullanılacak bilinen türleri eklenmesini etkinleştirir zaman seri durumundan çıkarma.</span><span class="sxs-lookup"><span data-stu-id="6b2c1-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b2c1-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b2c1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6b2c1-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b2c1-116">Element</span></span>|<span data-ttu-id="6b2c1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b2c1-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b2c1-118">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="6b2c1-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="6b2c1-119">Yapılandırma için üst düzey öğesi.</span><span class="sxs-lookup"><span data-stu-id="6b2c1-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b2c1-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b2c1-120">See Also</span></span>  
 <xref:System.Runtime.Serialization>  
 [<span data-ttu-id="6b2c1-121">Veri sözleşmelerini kullanma</span><span class="sxs-lookup"><span data-stu-id="6b2c1-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="6b2c1-122">Veri sözleşmesi bilinen türler</span><span class="sxs-lookup"><span data-stu-id="6b2c1-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
