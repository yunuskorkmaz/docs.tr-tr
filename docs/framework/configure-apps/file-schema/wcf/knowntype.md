---
description: 'Hakkında daha fazla bilgi edinin: <knownType>'
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 205f799c81263be3dd08aae9efefb975b06a0cc7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725512"
---
# \<knownType>

<span data-ttu-id="4f0cd-102">Seri durumdan çıkarma sırasında tarafından kullanılacak bir tür belirtir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="4f0cd-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="4f0cd-103">Öğesi, bir "bildirildiği tür" alanı veya özelliği tarafından döndürülen bir "bilinen tür" belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f0cd-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="4f0cd-104">Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="4f0cd-104">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**  
  
## <a name="syntax"></a><span data-ttu-id="4f0cd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4f0cd-105">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="4f0cd-106">Tür</span><span class="sxs-lookup"><span data-stu-id="4f0cd-106">Type</span></span>  

 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f0cd-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f0cd-107">Attributes and Elements</span></span>  

 <span data-ttu-id="4f0cd-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f0cd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f0cd-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4f0cd-109">Attributes</span></span>  
  
|<span data-ttu-id="4f0cd-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4f0cd-110">Attribute</span></span>|<span data-ttu-id="4f0cd-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f0cd-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f0cd-112">tür</span><span class="sxs-lookup"><span data-stu-id="4f0cd-112">type</span></span>|<span data-ttu-id="4f0cd-113">Türü (ad uzayı dahil), derleme adı, sürüm, kültür ve ortak anahtar belirtecini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f0cd-113">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f0cd-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f0cd-114">Child Elements</span></span>  
  
|<span data-ttu-id="4f0cd-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="4f0cd-115">Element</span></span>|<span data-ttu-id="4f0cd-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f0cd-116">Description</span></span>|  
|-------------|-----------------|  
|[\<parameter>](parameter.md)|<span data-ttu-id="4f0cd-117">Belirtilen tür genel bir tür olduğunda bir parametre dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f0cd-117">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f0cd-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f0cd-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4f0cd-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="4f0cd-119">Element</span></span>|<span data-ttu-id="4f0cd-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f0cd-120">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="4f0cd-121">Tanımlı türler koleksiyonuna, belirtilen bir tür ekler.</span><span class="sxs-lookup"><span data-stu-id="4f0cd-121">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f0cd-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f0cd-122">Remarks</span></span>  

 <span data-ttu-id="4f0cd-123">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="4f0cd-123">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="4f0cd-124">[\<dataContractSerializer>](datacontractserializer-element.md)Bu öğenin kullanımıyla ilgili bir örnek için bkz..</span><span class="sxs-lookup"><span data-stu-id="4f0cd-124">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f0cd-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f0cd-125">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f0cd-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f0cd-126">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="4f0cd-127">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="4f0cd-127">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
