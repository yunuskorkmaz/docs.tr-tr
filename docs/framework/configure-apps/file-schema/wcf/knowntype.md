---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 61f51b2ecd572ba254317a01e0f514503c7cc9e4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397879"
---
# <a name="knowntype"></a><span data-ttu-id="c6c92-101">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="c6c92-101">\<knownType></span></span>
<span data-ttu-id="c6c92-102">Seri durumdan çıkarma sırasında tarafından <xref:System.Runtime.Serialization.DataContractSerializer> kullanılacak bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6c92-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="c6c92-103">Öğesi, bir "bildirildiği tür" alanı veya özelliği tarafından döndürülen bir "bilinen tür" belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6c92-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="c6c92-104">Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="c6c92-104">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
<span data-ttu-id="c6c92-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c6c92-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c6c92-106">&nbsp;&nbsp;[ **\<System. Runtime. Serialization >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="c6c92-106">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="c6c92-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dataContractSerializer >** ](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="c6c92-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="c6c92-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="c6c92-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="c6c92-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> Ekle**](add-of-declaredtypes-element.md)</span><span class="sxs-lookup"><span data-stu-id="c6c92-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)</span></span>\
<span data-ttu-id="c6c92-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<knownType >**</span><span class="sxs-lookup"><span data-stu-id="c6c92-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6c92-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6c92-111">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="c6c92-112">Tür</span><span class="sxs-lookup"><span data-stu-id="c6c92-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6c92-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6c92-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c6c92-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6c92-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6c92-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c6c92-115">Attributes</span></span>  
  
|<span data-ttu-id="c6c92-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c6c92-116">Attribute</span></span>|<span data-ttu-id="c6c92-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6c92-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6c92-118">türü</span><span class="sxs-lookup"><span data-stu-id="c6c92-118">type</span></span>|<span data-ttu-id="c6c92-119">Türü (ad uzayı dahil), derleme adı, sürüm, kültür ve ortak anahtar belirtecini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6c92-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6c92-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6c92-120">Child Elements</span></span>  
  
|<span data-ttu-id="c6c92-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6c92-121">Element</span></span>|<span data-ttu-id="c6c92-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6c92-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6c92-123">\<parametre ></span><span class="sxs-lookup"><span data-stu-id="c6c92-123">\<parameter></span></span>](parameter.md)|<span data-ttu-id="c6c92-124">Belirtilen tür genel bir tür olduğunda bir parametre dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6c92-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6c92-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6c92-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c6c92-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6c92-126">Element</span></span>|<span data-ttu-id="c6c92-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6c92-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6c92-128">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="c6c92-128">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="c6c92-129">Tanımlı türler koleksiyonuna, belirtilen bir tür ekler.</span><span class="sxs-lookup"><span data-stu-id="c6c92-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6c92-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6c92-130">Remarks</span></span>  
 <span data-ttu-id="c6c92-131">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="c6c92-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="c6c92-132">Bu öğenin kullanılmasıyla ilgili bir örnek için bkz. [ DataContractSerializer>.\<](datacontractserializer-element.md)</span><span class="sxs-lookup"><span data-stu-id="c6c92-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6c92-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6c92-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c6c92-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6c92-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="c6c92-135">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="c6c92-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="c6c92-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="c6c92-136">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="c6c92-137">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="c6c92-137">\<add></span></span>](add-of-declaredtypes-element.md)
