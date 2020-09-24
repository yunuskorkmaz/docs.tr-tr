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
ms.openlocfilehash: 281d9d7d7e51a837de4f86f85472815956a20319
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153917"
---
# \<declaredTypes>

<span data-ttu-id="b153d-101"><xref:System.Runtime.Serialization.DataContractSerializer>Seri durumdan çıkarılırken kullandığı bilinen türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b153d-101">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="b153d-102">Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="b153d-102">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="b153d-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="b153d-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b153d-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b153d-104">Attributes and Elements</span></span>  

 <span data-ttu-id="b153d-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b153d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b153d-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b153d-106">Attributes</span></span>  

 <span data-ttu-id="b153d-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="b153d-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b153d-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b153d-108">Child Elements</span></span>  
  
|<span data-ttu-id="b153d-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="b153d-109">Element</span></span>|<span data-ttu-id="b153d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b153d-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="b153d-111">Bilinen türler gerektiren türler ekler.</span><span class="sxs-lookup"><span data-stu-id="b153d-111">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b153d-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b153d-112">Parent Elements</span></span>  
  
|<span data-ttu-id="b153d-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="b153d-113">Element</span></span>|<span data-ttu-id="b153d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b153d-114">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="b153d-115">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="b153d-115">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b153d-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b153d-116">Remarks</span></span>  

 <span data-ttu-id="b153d-117">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="b153d-117">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b153d-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="b153d-118">Example</span></span>  

 <span data-ttu-id="b153d-119">Aşağıdaki XML kodu, tanımlanmış türleri ve bir öğeye eklenen bilinen türleri gösterir `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="b153d-119">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="b153d-120">Örnek, eklenmekte olan üç tür gösterir.</span><span class="sxs-lookup"><span data-stu-id="b153d-120">The example shows three types being added.</span></span> <span data-ttu-id="b153d-121">Birincisi, "Item" adlı bilinen bir tür kullanan "Orders" adlı özel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="b153d-121">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="b153d-122">Belirtilen ikinci tür, bilinen bir <xref:System.Collections.Generic.List%601> tür olarak kullanılan bir türüdür `Item` .</span><span class="sxs-lookup"><span data-stu-id="b153d-122">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="b153d-123">Son olarak, belirtilen üçüncü tür bir <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="b153d-123">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="b153d-124"><xref:System.Collections.Generic.Dictionary%602>Sınıf türü, iki tür parametresi olan genel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="b153d-124">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="b153d-125">İlki anahtarı temsil eder ve ikincisi değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b153d-125">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="b153d-126">Aşağıdaki örnek, bir <xref:System.Collections.Generic.List%601> ikinci türü (değer) bilinen türler listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="b153d-126">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="b153d-127">`index`Bilinen türde kullanılacak tür parametresini belirtmek için özniteliğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b153d-127">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="b153d-128">Bu durumda, değer türü "1" olarak ayarlanmış dizin özniteliği ile gösterilir (koleksiyon sıfır tabanlıdır).</span><span class="sxs-lookup"><span data-stu-id="b153d-128">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b153d-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b153d-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="b153d-130">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="b153d-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)
