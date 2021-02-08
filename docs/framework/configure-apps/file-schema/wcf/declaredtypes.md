---
description: 'Hakkında daha fazla bilgi edinin: <declaredTypes>'
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: e5f60209dd556edc7cf47b01b1a58c1f17d74eac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803938"
---
# \<declaredTypes>

<span data-ttu-id="b0875-102"><xref:System.Runtime.Serialization.DataContractSerializer>Seri durumdan çıkarılırken kullandığı bilinen türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b0875-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="b0875-103">Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="b0875-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="b0875-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b0875-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0875-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0875-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b0875-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0875-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0875-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0875-107">Attributes</span></span>  

 <span data-ttu-id="b0875-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="b0875-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b0875-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0875-109">Child Elements</span></span>  
  
|<span data-ttu-id="b0875-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0875-110">Element</span></span>|<span data-ttu-id="b0875-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0875-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="b0875-112">Bilinen türler gerektiren türler ekler.</span><span class="sxs-lookup"><span data-stu-id="b0875-112">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0875-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0875-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b0875-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0875-114">Element</span></span>|<span data-ttu-id="b0875-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0875-115">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="b0875-116">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="b0875-116">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0875-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0875-117">Remarks</span></span>  

 <span data-ttu-id="b0875-118">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="b0875-118">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0875-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0875-119">Example</span></span>  

 <span data-ttu-id="b0875-120">Aşağıdaki XML kodu, tanımlanmış türleri ve bir öğeye eklenen bilinen türleri gösterir `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="b0875-120">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="b0875-121">Örnek, eklenmekte olan üç tür gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0875-121">The example shows three types being added.</span></span> <span data-ttu-id="b0875-122">Birincisi, "Item" adlı bilinen bir tür kullanan "Orders" adlı özel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="b0875-122">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="b0875-123">Belirtilen ikinci tür, bilinen bir <xref:System.Collections.Generic.List%601> tür olarak kullanılan bir türüdür `Item` .</span><span class="sxs-lookup"><span data-stu-id="b0875-123">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="b0875-124">Son olarak, belirtilen üçüncü tür bir <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="b0875-124">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="b0875-125"><xref:System.Collections.Generic.Dictionary%602>Sınıf türü, iki tür parametresi olan genel bir türdür.</span><span class="sxs-lookup"><span data-stu-id="b0875-125">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="b0875-126">İlki anahtarı temsil eder ve ikincisi değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b0875-126">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="b0875-127">Aşağıdaki örnek, bir <xref:System.Collections.Generic.List%601> ikinci türü (değer) bilinen türler listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="b0875-127">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="b0875-128">`index`Bilinen türde kullanılacak tür parametresini belirtmek için özniteliğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0875-128">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="b0875-129">Bu durumda, değer türü "1" olarak ayarlanmış dizin özniteliği ile gösterilir (koleksiyon sıfır tabanlıdır).</span><span class="sxs-lookup"><span data-stu-id="b0875-129">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0875-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0875-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="b0875-131">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="b0875-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)
