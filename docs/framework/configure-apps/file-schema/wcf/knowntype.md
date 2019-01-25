---
title: '&lt;knownType&gt;'
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: cb36a0d1d1ceb13a6db902904783ee15b14e673b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541072"
---
# <a name="ltknowntypegt"></a><span data-ttu-id="32123-102">&lt;knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="32123-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="32123-103">Tarafından kullanılacak bir tür belirttiğinden <xref:System.Runtime.Serialization.DataContractSerializer> seri durumundan çıkarma sırasında.</span><span class="sxs-lookup"><span data-stu-id="32123-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="32123-104">"Bilinen türü" olan öğeyi belirten bir alan veya özellik "bildirilen türü." tarafından döndürülen</span><span class="sxs-lookup"><span data-stu-id="32123-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="32123-105">Daha fazla bilgi için [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="32123-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="32123-106">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="32123-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="32123-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="32123-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="32123-108">\<declaredTypes > öğesi</span><span class="sxs-lookup"><span data-stu-id="32123-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="32123-109">\<Ekle >, \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="32123-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="32123-110">\<knownType > öğesi</span><span class="sxs-lookup"><span data-stu-id="32123-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32123-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32123-111">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="32123-112">Tür</span><span class="sxs-lookup"><span data-stu-id="32123-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32123-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="32123-113">Attributes and Elements</span></span>  
 <span data-ttu-id="32123-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="32123-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32123-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="32123-115">Attributes</span></span>  
  
|<span data-ttu-id="32123-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="32123-116">Attribute</span></span>|<span data-ttu-id="32123-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32123-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32123-118">türü</span><span class="sxs-lookup"><span data-stu-id="32123-118">type</span></span>|<span data-ttu-id="32123-119">Türü (ad uzayı dahil), derleme adı, sürüm, kültür ve ortak anahtar belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="32123-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32123-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="32123-120">Child Elements</span></span>  
  
|<span data-ttu-id="32123-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="32123-121">Element</span></span>|<span data-ttu-id="32123-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32123-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32123-123">\<Parametresi ></span><span class="sxs-lookup"><span data-stu-id="32123-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="32123-124">Bildirilen tür genel bir tür olduğunda, bir parametre dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="32123-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32123-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="32123-125">Parent Elements</span></span>  
  
|<span data-ttu-id="32123-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="32123-126">Element</span></span>|<span data-ttu-id="32123-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32123-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32123-128">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="32123-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="32123-129">Bildirilen tür bildirilen tür koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="32123-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32123-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32123-130">Remarks</span></span>  
 <span data-ttu-id="32123-131">Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="32123-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="32123-132">Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.</span><span class="sxs-lookup"><span data-stu-id="32123-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32123-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="32123-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32123-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32123-134">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="32123-135">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="32123-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="32123-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="32123-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="32123-137">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="32123-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
