---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 4d3dd9042951ffb46b8e0a3f7bb7bcdee23fd58b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148843"
---
# <a name="knowntype"></a><span data-ttu-id="e7abd-101">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="e7abd-101">\<knownType></span></span>
<span data-ttu-id="e7abd-102">Tarafından kullanılacak bir tür belirttiğinden <xref:System.Runtime.Serialization.DataContractSerializer> seri durumundan çıkarma sırasında.</span><span class="sxs-lookup"><span data-stu-id="e7abd-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="e7abd-103">"Bilinen türü" olan öğeyi belirten bir alan veya özellik "bildirilen türü." tarafından döndürülen</span><span class="sxs-lookup"><span data-stu-id="e7abd-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="e7abd-104">Daha fazla bilgi için [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="e7abd-104">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="e7abd-105">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="e7abd-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="e7abd-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="e7abd-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="e7abd-107">\<declaredTypes > öğesi</span><span class="sxs-lookup"><span data-stu-id="e7abd-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="e7abd-108">\<Ekle >, \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="e7abd-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="e7abd-109">\<knownType > öğesi</span><span class="sxs-lookup"><span data-stu-id="e7abd-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7abd-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7abd-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="e7abd-111">Tür</span><span class="sxs-lookup"><span data-stu-id="e7abd-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7abd-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7abd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e7abd-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7abd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7abd-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e7abd-114">Attributes</span></span>  
  
|<span data-ttu-id="e7abd-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e7abd-115">Attribute</span></span>|<span data-ttu-id="e7abd-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7abd-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7abd-117">türü</span><span class="sxs-lookup"><span data-stu-id="e7abd-117">type</span></span>|<span data-ttu-id="e7abd-118">Türü (ad uzayı dahil), derleme adı, sürüm, kültür ve ortak anahtar belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7abd-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7abd-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7abd-119">Child Elements</span></span>  
  
|<span data-ttu-id="e7abd-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="e7abd-120">Element</span></span>|<span data-ttu-id="e7abd-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7abd-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7abd-122">\<Parametresi ></span><span class="sxs-lookup"><span data-stu-id="e7abd-122">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="e7abd-123">Bildirilen tür genel bir tür olduğunda, bir parametre dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7abd-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7abd-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7abd-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e7abd-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="e7abd-125">Element</span></span>|<span data-ttu-id="e7abd-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7abd-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7abd-127">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="e7abd-127">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="e7abd-128">Bildirilen tür bildirilen tür koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="e7abd-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7abd-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7abd-129">Remarks</span></span>  
 <span data-ttu-id="e7abd-130">Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e7abd-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="e7abd-131">Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.</span><span class="sxs-lookup"><span data-stu-id="e7abd-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7abd-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7abd-132">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e7abd-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7abd-133">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="e7abd-134">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="e7abd-134">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="e7abd-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="e7abd-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="e7abd-136">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="e7abd-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
