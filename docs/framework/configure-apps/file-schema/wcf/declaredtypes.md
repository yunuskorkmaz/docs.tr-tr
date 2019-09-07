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
ms.openlocfilehash: c45a4e67d0a2d98c0e9c1a91e07f25b81370244c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398058"
---
# <a name="declaredtypes"></a><span data-ttu-id="ef4f4-101">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="ef4f4-101">\<declaredTypes></span></span>
<span data-ttu-id="ef4f4-102">Seri durumdan çıkarılırken <xref:System.Runtime.Serialization.DataContractSerializer> kullandığı bilinen türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="ef4f4-103">Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="ef4f4-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
<span data-ttu-id="ef4f4-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ef4f4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ef4f4-105">&nbsp;&nbsp;[ **\<System. Runtime. Serialization >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="ef4f4-105">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="ef4f4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dataContractSerializer >** ](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="ef4f4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="ef4f4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<declaredTypes >**</span><span class="sxs-lookup"><span data-stu-id="ef4f4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef4f4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef4f4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef4f4-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef4f4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ef4f4-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef4f4-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ef4f4-111">Attributes</span></span>  
 <span data-ttu-id="ef4f4-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ef4f4-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef4f4-113">Child Elements</span></span>  
  
|<span data-ttu-id="ef4f4-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef4f4-114">Element</span></span>|<span data-ttu-id="ef4f4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef4f4-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef4f4-116">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="ef4f4-116">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="ef4f4-117">Bilinen türler gerektiren türler ekler.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-117">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ef4f4-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef4f4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ef4f4-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef4f4-119">Element</span></span>|<span data-ttu-id="ef4f4-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef4f4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef4f4-121">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="ef4f4-121">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="ef4f4-122">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-122">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef4f4-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef4f4-123">Remarks</span></span>  
 <span data-ttu-id="ef4f4-124">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-124">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef4f4-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef4f4-125">Example</span></span>  
 <span data-ttu-id="ef4f4-126">Aşağıdaki XML kodu, tanımlanmış türleri ve bir `DataContractSerializer` öğeye eklenen bilinen türleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-126">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="ef4f4-127">Örnek, eklenmekte olan üç tür gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-127">The example shows three types being added.</span></span> <span data-ttu-id="ef4f4-128">Birincisi, "Item" adlı bilinen bir tür kullanan "Orders" adlı özel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-128">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="ef4f4-129">Belirtilen ikinci tür, bilinen bir <xref:System.Collections.Generic.List%601> tür olarak `Item` kullanılan bir türüdür.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-129">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="ef4f4-130">Son olarak, belirtilen üçüncü tür bir <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-130">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="ef4f4-131"><xref:System.Collections.Generic.Dictionary%602> Sınıf türü, iki tür parametresi olan genel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-131">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="ef4f4-132">İlki anahtarı temsil eder ve ikincisi değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-132">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="ef4f4-133">Aşağıdaki örnek, bir <xref:System.Collections.Generic.List%601> ikinci türü (değer) bilinen türler listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-133">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="ef4f4-134">Bilinen türde kullanılacak tür `index` parametresini belirtmek için özniteliğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-134">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="ef4f4-135">Bu durumda, değer türü "1" olarak ayarlanmış dizin özniteliği ile gösterilir (koleksiyon sıfır tabanlıdır).</span><span class="sxs-lookup"><span data-stu-id="ef4f4-135">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ef4f4-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef4f4-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="ef4f4-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="ef4f4-137">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="ef4f4-138">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="ef4f4-138">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="ef4f4-139">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="ef4f4-139">\<add></span></span>](add-of-declaredtypes-element.md)
