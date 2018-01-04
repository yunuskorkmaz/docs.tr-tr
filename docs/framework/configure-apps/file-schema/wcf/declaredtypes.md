---
title: '&lt;declaredTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3066ee9247e69c746c28251b975bb80425ccbc8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdeclaredtypesgt"></a><span data-ttu-id="9c2d7-102">&lt;declaredTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="9c2d7-102">&lt;declaredTypes&gt;</span></span>
<span data-ttu-id="9c2d7-103">İçeren bilinen türleri <xref:System.Runtime.Serialization.DataContractSerializer> çıkarılırken kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-103">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="9c2d7-104">Veri sözleşmeleri ve bilinen türleri hakkında daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="9c2d7-104">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="9c2d7-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="9c2d7-105">system.runtime.serialization</span></span>  
<span data-ttu-id="9c2d7-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="9c2d7-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="9c2d7-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="9c2d7-107">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c2d7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c2d7-108">Syntax</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c2d7-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9c2d7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9c2d7-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c2d7-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9c2d7-111">Attributes</span></span>  
 <span data-ttu-id="9c2d7-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9c2d7-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9c2d7-113">Child Elements</span></span>  
  
|<span data-ttu-id="9c2d7-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="9c2d7-114">Element</span></span>|<span data-ttu-id="9c2d7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c2d7-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c2d7-116">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="9c2d7-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="9c2d7-117">Bilinen türler gereksinim türlerini ekler.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-117">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c2d7-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9c2d7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9c2d7-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="9c2d7-119">Element</span></span>|<span data-ttu-id="9c2d7-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c2d7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c2d7-121">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="9c2d7-121">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="9c2d7-122">Yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-122">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c2d7-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c2d7-123">Remarks</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="9c2d7-124">bilinen türlerini, bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-124"> known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c2d7-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c2d7-125">Example</span></span>  
 <span data-ttu-id="9c2d7-126">Bildirilen türlerini ve bilinen türleri için eklenen aşağıdaki XML kodunu gösterir bir `DataContractSerializer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-126">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="9c2d7-127">Örnek eklenmekte olan üç tür gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-127">The example shows three types being added.</span></span> <span data-ttu-id="9c2d7-128">İlk "Öğesi" adlı bir bilinen türünü kullanan "Siparişler" adlı bir özel türüdür.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-128">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="9c2d7-129">İkinci bildirilmiş türü bir <xref:System.Collections.Generic.List%601> kullanan `Item` bilinen türü.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-129">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="9c2d7-130">Son olarak üçüncü türü bildirilen bir <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-130">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="9c2d7-131"><xref:System.Collections.Generic.Dictionary%602> Sınıf türüdür iki tür parametreleri ile genel bir tür.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-131">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="9c2d7-132">İlk anahtarı temsil eder ve ikinci değer temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-132">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="9c2d7-133">Aşağıdaki örnek, bir <xref:System.Collections.Generic.List%601> türünün ikinci (değer) listesine bilinen türler.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-133">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="9c2d7-134">Kullanmalısınız `index` özniteliği bilinen türünü kullanmak için hangi tür parametresi belirtin.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-134">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="9c2d7-135">Bu durumda, değer türü "1" dizini özniteliği belirttiği (sıfır tabanlı derlemedir).</span><span class="sxs-lookup"><span data-stu-id="9c2d7-135">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
            <parameter index="1"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c2d7-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9c2d7-136">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="9c2d7-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="9c2d7-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="9c2d7-138">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="9c2d7-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="9c2d7-139">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="9c2d7-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
