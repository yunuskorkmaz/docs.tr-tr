---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 4d3dd9042951ffb46b8e0a3f7bb7bcdee23fd58b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148843"
---
# <a name="knowntype"></a><span data-ttu-id="cb379-101">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="cb379-101">\<knownType></span></span>
<span data-ttu-id="cb379-102">Tarafından kullanılacak bir tür belirttiğinden <xref:System.Runtime.Serialization.DataContractSerializer> seri durumundan çıkarma sırasında.</span><span class="sxs-lookup"><span data-stu-id="cb379-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="cb379-103">"Bilinen türü" olan öğeyi belirten bir alan veya özellik "bildirilen türü." tarafından döndürülen</span><span class="sxs-lookup"><span data-stu-id="cb379-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="cb379-104">Daha fazla bilgi için [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="cb379-104">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="cb379-105">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="cb379-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="cb379-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="cb379-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="cb379-107">\<declaredTypes > öğesi</span><span class="sxs-lookup"><span data-stu-id="cb379-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="cb379-108">\<Ekle >, \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="cb379-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="cb379-109">\<knownType > öğesi</span><span class="sxs-lookup"><span data-stu-id="cb379-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb379-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb379-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="cb379-111">Tür</span><span class="sxs-lookup"><span data-stu-id="cb379-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb379-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb379-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cb379-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb379-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb379-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cb379-114">Attributes</span></span>  
  
|<span data-ttu-id="cb379-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cb379-115">Attribute</span></span>|<span data-ttu-id="cb379-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb379-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb379-117"> türü</span><span class="sxs-lookup"><span data-stu-id="cb379-117">type</span></span>|<span data-ttu-id="cb379-118">Türü (ad uzayı dahil), derleme adı, sürüm, kültür ve ortak anahtar belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb379-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb379-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb379-119">Child Elements</span></span>  
  
|<span data-ttu-id="cb379-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb379-120">Element</span></span>|<span data-ttu-id="cb379-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb379-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb379-122">\<Parametresi ></span><span class="sxs-lookup"><span data-stu-id="cb379-122">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="cb379-123">Bildirilen tür genel bir tür olduğunda, bir parametre dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb379-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb379-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb379-124">Parent Elements</span></span>  
  
|<span data-ttu-id="cb379-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb379-125">Element</span></span>|<span data-ttu-id="cb379-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb379-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb379-127">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="cb379-127">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="cb379-128">Bildirilen tür bildirilen tür koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="cb379-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb379-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb379-129">Remarks</span></span>  
 <span data-ttu-id="cb379-130">Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="cb379-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="cb379-131">Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.</span><span class="sxs-lookup"><span data-stu-id="cb379-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb379-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb379-132">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb379-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb379-133">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="cb379-134">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="cb379-134">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="cb379-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="cb379-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="cb379-136">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="cb379-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
