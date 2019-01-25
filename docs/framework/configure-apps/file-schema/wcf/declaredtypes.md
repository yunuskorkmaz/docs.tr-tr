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
ms.openlocfilehash: 405a6f21af1cb3508b7b88625101ed75f198bbaa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682673"
---
# <a name="ltdeclaredtypesgt"></a><span data-ttu-id="1946c-102">&lt;declaredTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="1946c-102">&lt;declaredTypes&gt;</span></span>
<span data-ttu-id="1946c-103">İçerir, bilinen türleri <xref:System.Runtime.Serialization.DataContractSerializer> işlenirken kullanır.</span><span class="sxs-lookup"><span data-stu-id="1946c-103">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="1946c-104">Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="1946c-104">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="1946c-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="1946c-105">system.runtime.serialization</span></span>  
<span data-ttu-id="1946c-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="1946c-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="1946c-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="1946c-107">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1946c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1946c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1946c-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1946c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1946c-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1946c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1946c-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1946c-111">Attributes</span></span>  
 <span data-ttu-id="1946c-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="1946c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1946c-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1946c-113">Child Elements</span></span>  
  
|<span data-ttu-id="1946c-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="1946c-114">Element</span></span>|<span data-ttu-id="1946c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1946c-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1946c-116">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="1946c-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="1946c-117">Bilinen türler gerektiren türleri ekler.</span><span class="sxs-lookup"><span data-stu-id="1946c-117">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1946c-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1946c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1946c-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="1946c-119">Element</span></span>|<span data-ttu-id="1946c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1946c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1946c-121">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="1946c-121">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="1946c-122">İçin yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1946c-122">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1946c-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1946c-123">Remarks</span></span>  
 <span data-ttu-id="1946c-124">Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1946c-124">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1946c-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="1946c-125">Example</span></span>  
 <span data-ttu-id="1946c-126">Bildirilen türleri ve bilinen türler için eklenen aşağıdaki XML kodunu gösteren bir `DataContractSerializer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="1946c-126">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="1946c-127">Eklenen üç örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="1946c-127">The example shows three types being added.</span></span> <span data-ttu-id="1946c-128">İlk "Madde" adlı bir bilinen türünü kullanan "Siparişler" adlı bir özel türüdür.</span><span class="sxs-lookup"><span data-stu-id="1946c-128">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="1946c-129">İkinci bildirilen türü bir <xref:System.Collections.Generic.List%601> kullanan `Item` bilinen türü.</span><span class="sxs-lookup"><span data-stu-id="1946c-129">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="1946c-130">Son olarak üçüncü türü bildirilen bir <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="1946c-130">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="1946c-131"><xref:System.Collections.Generic.Dictionary%602> Sınıf türüdür, iki tür parametreleri ile genel tür.</span><span class="sxs-lookup"><span data-stu-id="1946c-131">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="1946c-132">İlk tuşunu temsil eder ve ikinci değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1946c-132">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="1946c-133">Aşağıdaki örnek ekler bir <xref:System.Collections.Generic.List%601> türünün ikinci (değer) listeye bilinen türler.</span><span class="sxs-lookup"><span data-stu-id="1946c-133">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="1946c-134">Kullanmalısınız `index` bilinen türü kullanmak için hangi tür parametresi belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1946c-134">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="1946c-135">Bu durumda, değer türü "1" dizini özniteliği tarafından belirtilen (koleksiyon sıfır tabanlı).</span><span class="sxs-lookup"><span data-stu-id="1946c-135">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1946c-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1946c-136">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="1946c-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="1946c-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="1946c-138">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="1946c-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="1946c-139">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="1946c-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
