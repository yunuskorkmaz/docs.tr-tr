---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: a0794314cfcb87df00d66b6832356fb130787eba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928863"
---
# <a name="knowntype"></a><span data-ttu-id="9c3dc-101">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="9c3dc-101">\<knownType></span></span>
<span data-ttu-id="9c3dc-102">Seri durumdan çıkarma sırasında tarafından <xref:System.Runtime.Serialization.DataContractSerializer> kullanılacak bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="9c3dc-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="9c3dc-103">Öğesi, bir "bildirildiği tür" alanı veya özelliği tarafından döndürülen bir "bilinen tür" belirtir.</span><span class="sxs-lookup"><span data-stu-id="9c3dc-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="9c3dc-104">Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="9c3dc-104">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="9c3dc-105">\<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="9c3dc-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="9c3dc-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="9c3dc-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="9c3dc-107">\<declaredTypes > öğesi</span><span class="sxs-lookup"><span data-stu-id="9c3dc-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="9c3dc-108">\<\<DeclaredTypes > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="9c3dc-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="9c3dc-109">\<knownType > öğesi</span><span class="sxs-lookup"><span data-stu-id="9c3dc-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c3dc-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c3dc-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="9c3dc-111">Tür</span><span class="sxs-lookup"><span data-stu-id="9c3dc-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c3dc-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9c3dc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9c3dc-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9c3dc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c3dc-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9c3dc-114">Attributes</span></span>  
  
|<span data-ttu-id="9c3dc-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9c3dc-115">Attribute</span></span>|<span data-ttu-id="9c3dc-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c3dc-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c3dc-117">türü</span><span class="sxs-lookup"><span data-stu-id="9c3dc-117">type</span></span>|<span data-ttu-id="9c3dc-118">Türü (ad uzayı dahil), derleme adı, sürüm, kültür ve ortak anahtar belirtecini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9c3dc-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c3dc-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9c3dc-119">Child Elements</span></span>  
  
|<span data-ttu-id="9c3dc-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="9c3dc-120">Element</span></span>|<span data-ttu-id="9c3dc-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c3dc-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c3dc-122">\<parametre ></span><span class="sxs-lookup"><span data-stu-id="9c3dc-122">\<parameter></span></span>](parameter.md)|<span data-ttu-id="9c3dc-123">Belirtilen tür genel bir tür olduğunda bir parametre dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9c3dc-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c3dc-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9c3dc-124">Parent Elements</span></span>  
  
|<span data-ttu-id="9c3dc-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="9c3dc-125">Element</span></span>|<span data-ttu-id="9c3dc-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c3dc-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c3dc-127">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="9c3dc-127">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="9c3dc-128">Tanımlı türler koleksiyonuna, belirtilen bir tür ekler.</span><span class="sxs-lookup"><span data-stu-id="9c3dc-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c3dc-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c3dc-129">Remarks</span></span>  
 <span data-ttu-id="9c3dc-130">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9c3dc-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="9c3dc-131">Bu öğenin kullanılmasıyla ilgili bir örnek için bkz. [ DataContractSerializer>.\<](datacontractserializer-element.md)</span><span class="sxs-lookup"><span data-stu-id="9c3dc-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c3dc-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c3dc-132">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c3dc-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c3dc-133">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="9c3dc-134">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="9c3dc-134">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="9c3dc-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="9c3dc-135">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="9c3dc-136">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="9c3dc-136">\<add></span></span>](add-of-declaredtypes-element.md)
