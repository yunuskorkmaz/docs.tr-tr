---
title: '&lt;declaredTypes&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: d6690722f743c74ee9909f029133f506e05ecb1d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltdeclaredtypesgt"></a><span data-ttu-id="c0e7a-102">&lt;declaredTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="c0e7a-102">&lt;declaredTypes&gt;</span></span>
<span data-ttu-id="c0e7a-103">İçeren bilinen türleri <xref:System.Runtime.Serialization.DataContractSerializer> çıkarılırken kullanır.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-103">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="c0e7a-104">Veri sözleşmeleri ve bilinen türleri hakkında daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="c0e7a-104">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="c0e7a-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="c0e7a-105">system.runtime.serialization</span></span>  
<span data-ttu-id="c0e7a-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="c0e7a-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="c0e7a-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="c0e7a-107">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0e7a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0e7a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0e7a-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0e7a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c0e7a-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0e7a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c0e7a-111">Attributes</span></span>  
 <span data-ttu-id="c0e7a-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c0e7a-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0e7a-113">Child Elements</span></span>  
  
|<span data-ttu-id="c0e7a-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="c0e7a-114">Element</span></span>|<span data-ttu-id="c0e7a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0e7a-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0e7a-116">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="c0e7a-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="c0e7a-117">Bilinen türler gereksinim türlerini ekler.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-117">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0e7a-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0e7a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c0e7a-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="c0e7a-119">Element</span></span>|<span data-ttu-id="c0e7a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0e7a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0e7a-121">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="c0e7a-121">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="c0e7a-122">Yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-122">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0e7a-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0e7a-123">Remarks</span></span>  
 <span data-ttu-id="c0e7a-124">Bilinen türleri hakkında daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-124">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0e7a-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0e7a-125">Example</span></span>  
 <span data-ttu-id="c0e7a-126">Bildirilen türlerini ve bilinen türleri için eklenen aşağıdaki XML kodunu gösterir bir `DataContractSerializer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-126">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="c0e7a-127">Örnek eklenmekte olan üç tür gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-127">The example shows three types being added.</span></span> <span data-ttu-id="c0e7a-128">İlk "Öğesi" adlı bir bilinen türünü kullanan "Siparişler" adlı bir özel türüdür.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-128">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="c0e7a-129">İkinci bildirilmiş türü bir <xref:System.Collections.Generic.List%601> kullanan `Item` bilinen türü.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-129">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="c0e7a-130">Son olarak üçüncü türü bildirilen bir <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-130">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="c0e7a-131"><xref:System.Collections.Generic.Dictionary%602> Sınıf türüdür iki tür parametreleri ile genel bir tür.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-131">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="c0e7a-132">İlk anahtarı temsil eder ve ikinci değer temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-132">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="c0e7a-133">Aşağıdaki örnek, bir <xref:System.Collections.Generic.List%601> türünün ikinci (değer) listesine bilinen türler.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-133">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="c0e7a-134">Kullanmalısınız `index` özniteliği bilinen türünü kullanmak için hangi tür parametresi belirtin.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-134">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="c0e7a-135">Bu durumda, değer türü "1" dizini özniteliği belirttiği (sıfır tabanlı derlemedir).</span><span class="sxs-lookup"><span data-stu-id="c0e7a-135">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0e7a-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c0e7a-136">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="c0e7a-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="c0e7a-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="c0e7a-138">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="c0e7a-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="c0e7a-139">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="c0e7a-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
