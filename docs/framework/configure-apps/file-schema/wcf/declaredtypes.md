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
ms.openlocfilehash: cef34a8836c7b17fe9a85cac190090f42653df14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919247"
---
# <a name="declaredtypes"></a><span data-ttu-id="f7576-101">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="f7576-101">\<declaredTypes></span></span>
<span data-ttu-id="f7576-102">Seri durumdan çıkarılırken <xref:System.Runtime.Serialization.DataContractSerializer> kullandığı bilinen türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f7576-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="f7576-103">Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="f7576-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="f7576-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="f7576-104">system.runtime.serialization</span></span>  
<span data-ttu-id="f7576-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="f7576-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="f7576-106">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="f7576-106">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7576-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7576-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7576-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7576-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f7576-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f7576-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7576-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f7576-110">Attributes</span></span>  
 <span data-ttu-id="f7576-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="f7576-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f7576-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7576-112">Child Elements</span></span>  
  
|<span data-ttu-id="f7576-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="f7576-113">Element</span></span>|<span data-ttu-id="f7576-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7576-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7576-115">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="f7576-115">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="f7576-116">Bilinen türler gerektiren türler ekler.</span><span class="sxs-lookup"><span data-stu-id="f7576-116">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f7576-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7576-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f7576-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="f7576-118">Element</span></span>|<span data-ttu-id="f7576-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7576-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7576-120">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="f7576-120">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="f7576-121">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f7576-121">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7576-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7576-122">Remarks</span></span>  
 <span data-ttu-id="f7576-123">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f7576-123">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7576-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7576-124">Example</span></span>  
 <span data-ttu-id="f7576-125">Aşağıdaki XML kodu, tanımlanmış türleri ve bir `DataContractSerializer` öğeye eklenen bilinen türleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7576-125">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="f7576-126">Örnek, eklenmekte olan üç tür gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7576-126">The example shows three types being added.</span></span> <span data-ttu-id="f7576-127">Birincisi, "Item" adlı bilinen bir tür kullanan "Orders" adlı özel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="f7576-127">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="f7576-128">Belirtilen ikinci tür, bilinen bir <xref:System.Collections.Generic.List%601> tür olarak `Item` kullanılan bir türüdür.</span><span class="sxs-lookup"><span data-stu-id="f7576-128">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="f7576-129">Son olarak, belirtilen üçüncü tür bir <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="f7576-129">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="f7576-130"><xref:System.Collections.Generic.Dictionary%602> Sınıf türü, iki tür parametresi olan genel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="f7576-130">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="f7576-131">İlki anahtarı temsil eder ve ikincisi değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f7576-131">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="f7576-132">Aşağıdaki örnek, bir <xref:System.Collections.Generic.List%601> ikinci türü (değer) bilinen türler listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="f7576-132">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="f7576-133">Bilinen türde kullanılacak tür `index` parametresini belirtmek için özniteliğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7576-133">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="f7576-134">Bu durumda, değer türü "1" olarak ayarlanmış dizin özniteliği ile gösterilir (koleksiyon sıfır tabanlıdır).</span><span class="sxs-lookup"><span data-stu-id="f7576-134">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f7576-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7576-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="f7576-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="f7576-136">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="f7576-137">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="f7576-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="f7576-138">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="f7576-138">\<add></span></span>](add-of-declaredtypes-element.md)
