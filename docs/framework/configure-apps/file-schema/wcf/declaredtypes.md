---
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: 8919ee717012f8badcf7015bf8d850ed431c5943
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090283"
---
# <a name="declaredtypes"></a><span data-ttu-id="12d83-101">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="12d83-101">\<declaredTypes></span></span>
<span data-ttu-id="12d83-102">İçerir, bilinen türleri <xref:System.Runtime.Serialization.DataContractSerializer> işlenirken kullanır.</span><span class="sxs-lookup"><span data-stu-id="12d83-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="12d83-103">Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="12d83-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="12d83-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="12d83-104">system.runtime.serialization</span></span>  
<span data-ttu-id="12d83-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="12d83-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="12d83-106">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="12d83-106">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12d83-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12d83-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12d83-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="12d83-108">Attributes and Elements</span></span>  
 <span data-ttu-id="12d83-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="12d83-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12d83-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="12d83-110">Attributes</span></span>  
 <span data-ttu-id="12d83-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="12d83-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="12d83-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="12d83-112">Child Elements</span></span>  
  
|<span data-ttu-id="12d83-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="12d83-113">Element</span></span>|<span data-ttu-id="12d83-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12d83-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12d83-115">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="12d83-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="12d83-116">Bilinen türler gerektiren türleri ekler.</span><span class="sxs-lookup"><span data-stu-id="12d83-116">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12d83-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="12d83-117">Parent Elements</span></span>  
  
|<span data-ttu-id="12d83-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="12d83-118">Element</span></span>|<span data-ttu-id="12d83-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12d83-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12d83-120">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="12d83-120">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="12d83-121">İçin yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="12d83-121">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12d83-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12d83-122">Remarks</span></span>  
 <span data-ttu-id="12d83-123">Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="12d83-123">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12d83-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="12d83-124">Example</span></span>  
 <span data-ttu-id="12d83-125">Bildirilen türleri ve bilinen türler için eklenen aşağıdaki XML kodunu gösteren bir `DataContractSerializer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="12d83-125">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="12d83-126">Eklenen üç örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="12d83-126">The example shows three types being added.</span></span> <span data-ttu-id="12d83-127">İlk "Madde" adlı bir bilinen türünü kullanan "Siparişler" adlı bir özel türüdür.</span><span class="sxs-lookup"><span data-stu-id="12d83-127">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="12d83-128">İkinci bildirilen türü bir <xref:System.Collections.Generic.List%601> kullanan `Item` bilinen türü.</span><span class="sxs-lookup"><span data-stu-id="12d83-128">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="12d83-129">Son olarak üçüncü türü bildirilen bir <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="12d83-129">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="12d83-130"><xref:System.Collections.Generic.Dictionary%602> Sınıf türüdür, iki tür parametreleri ile genel tür.</span><span class="sxs-lookup"><span data-stu-id="12d83-130">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="12d83-131">İlk tuşunu temsil eder ve ikinci değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="12d83-131">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="12d83-132">Aşağıdaki örnek ekler bir <xref:System.Collections.Generic.List%601> türünün ikinci (değer) listeye bilinen türler.</span><span class="sxs-lookup"><span data-stu-id="12d83-132">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="12d83-133">Kullanmalısınız `index` bilinen türü kullanmak için hangi tür parametresi belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="12d83-133">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="12d83-134">Bu durumda, değer türü "1" dizini özniteliği tarafından belirtilen (koleksiyon sıfır tabanlı).</span><span class="sxs-lookup"><span data-stu-id="12d83-134">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12d83-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12d83-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="12d83-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="12d83-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="12d83-137">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="12d83-137">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="12d83-138">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="12d83-138">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
