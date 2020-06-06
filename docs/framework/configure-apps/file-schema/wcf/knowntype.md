---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 61f51b2ecd572ba254317a01e0f514503c7cc9e4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397879"
---
# \<knownType>
<span data-ttu-id="d9d92-101">Seri durumdan çıkarma sırasında tarafından kullanılacak bir tür belirtir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="d9d92-101">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="d9d92-102">Öğesi, bir "bildirildiği tür" alanı veya özelliği tarafından döndürülen bir "bilinen tür" belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9d92-102">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="d9d92-103">Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="d9d92-103">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**  
  
## <a name="syntax"></a><span data-ttu-id="d9d92-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9d92-104">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="d9d92-105">Tür</span><span class="sxs-lookup"><span data-stu-id="d9d92-105">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9d92-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9d92-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d9d92-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d9d92-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9d92-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d9d92-108">Attributes</span></span>  
  
|<span data-ttu-id="d9d92-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d9d92-109">Attribute</span></span>|<span data-ttu-id="d9d92-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9d92-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9d92-111">tür</span><span class="sxs-lookup"><span data-stu-id="d9d92-111">type</span></span>|<span data-ttu-id="d9d92-112">Türü (ad uzayı dahil), derleme adı, sürüm, kültür ve ortak anahtar belirtecini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9d92-112">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9d92-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9d92-113">Child Elements</span></span>  
  
|<span data-ttu-id="d9d92-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9d92-114">Element</span></span>|<span data-ttu-id="d9d92-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9d92-115">Description</span></span>|  
|-------------|-----------------|  
|[\<parameter>](parameter.md)|<span data-ttu-id="d9d92-116">Belirtilen tür genel bir tür olduğunda bir parametre dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9d92-116">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9d92-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9d92-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d9d92-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9d92-118">Element</span></span>|<span data-ttu-id="d9d92-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9d92-119">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="d9d92-120">Tanımlı türler koleksiyonuna, belirtilen bir tür ekler.</span><span class="sxs-lookup"><span data-stu-id="d9d92-120">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9d92-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9d92-121">Remarks</span></span>  
 <span data-ttu-id="d9d92-122">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="d9d92-122">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="d9d92-123">[\<dataContractSerializer>](datacontractserializer-element.md)Bu öğenin kullanımıyla ilgili bir örnek için bkz..</span><span class="sxs-lookup"><span data-stu-id="d9d92-123">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9d92-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9d92-124">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d9d92-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9d92-125">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="d9d92-126">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="d9d92-126">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
