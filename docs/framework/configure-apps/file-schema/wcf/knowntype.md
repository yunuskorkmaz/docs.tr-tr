---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 6bb6a419d863172951d82a67de044cb8cfc30f49
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183799"
---
# \<knownType>

<span data-ttu-id="9bf37-101">Seri durumdan çıkarma sırasında tarafından kullanılacak bir tür belirtir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="9bf37-101">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="9bf37-102">Öğesi, bir "bildirildiği tür" alanı veya özelliği tarafından döndürülen bir "bilinen tür" belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bf37-102">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="9bf37-103">Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="9bf37-103">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**  
  
## <a name="syntax"></a><span data-ttu-id="9bf37-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9bf37-104">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="9bf37-105">Tür</span><span class="sxs-lookup"><span data-stu-id="9bf37-105">Type</span></span>  

 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bf37-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bf37-106">Attributes and Elements</span></span>  

 <span data-ttu-id="9bf37-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9bf37-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bf37-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9bf37-108">Attributes</span></span>  
  
|<span data-ttu-id="9bf37-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9bf37-109">Attribute</span></span>|<span data-ttu-id="9bf37-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bf37-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9bf37-111">tür</span><span class="sxs-lookup"><span data-stu-id="9bf37-111">type</span></span>|<span data-ttu-id="9bf37-112">Türü (ad uzayı dahil), derleme adı, sürüm, kültür ve ortak anahtar belirtecini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bf37-112">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bf37-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bf37-113">Child Elements</span></span>  
  
|<span data-ttu-id="9bf37-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="9bf37-114">Element</span></span>|<span data-ttu-id="9bf37-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bf37-115">Description</span></span>|  
|-------------|-----------------|  
|[\<parameter>](parameter.md)|<span data-ttu-id="9bf37-116">Belirtilen tür genel bir tür olduğunda bir parametre dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bf37-116">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9bf37-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bf37-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9bf37-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="9bf37-118">Element</span></span>|<span data-ttu-id="9bf37-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bf37-119">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="9bf37-120">Tanımlı türler koleksiyonuna, belirtilen bir tür ekler.</span><span class="sxs-lookup"><span data-stu-id="9bf37-120">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bf37-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9bf37-121">Remarks</span></span>  

 <span data-ttu-id="9bf37-122">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="9bf37-122">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="9bf37-123">[\<dataContractSerializer>](datacontractserializer-element.md)Bu öğenin kullanımıyla ilgili bir örnek için bkz..</span><span class="sxs-lookup"><span data-stu-id="9bf37-123">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bf37-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="9bf37-124">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL"/>
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="9bf37-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bf37-125">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="9bf37-126">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="9bf37-126">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
