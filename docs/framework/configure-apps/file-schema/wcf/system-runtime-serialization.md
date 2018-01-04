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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab66252ebc5b87c197b3e4ac7b6def9355e5f201
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="b46bf-102">&lt;System.Runtime.Serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="b46bf-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="b46bf-103">Kök öğe için temsil eden <xref:System.Runtime.Serialization> ad alanı bölüm ve seçenekleri ayarlamak için öğeleri içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b46bf-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="b46bf-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="b46bf-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b46bf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b46bf-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b46bf-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b46bf-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b46bf-107">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="b46bf-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b46bf-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b46bf-108">Attributes</span></span>  
 <span data-ttu-id="b46bf-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="b46bf-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b46bf-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b46bf-110">Child Elements</span></span>  
  
|<span data-ttu-id="b46bf-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="b46bf-111">Element</span></span>|<span data-ttu-id="b46bf-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b46bf-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b46bf-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="b46bf-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="b46bf-114">Kullanılacak bilinen türleri eklenmesini etkinleştirir zaman seri durumundan çıkarma.</span><span class="sxs-lookup"><span data-stu-id="b46bf-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b46bf-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b46bf-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b46bf-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="b46bf-116">Element</span></span>|<span data-ttu-id="b46bf-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b46bf-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b46bf-118">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="b46bf-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="b46bf-119">Yapılandırma için üst düzey öğesi.</span><span class="sxs-lookup"><span data-stu-id="b46bf-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b46bf-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b46bf-120">See Also</span></span>  
 <xref:System.Runtime.Serialization>  
 [<span data-ttu-id="b46bf-121">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="b46bf-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="b46bf-122">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="b46bf-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
