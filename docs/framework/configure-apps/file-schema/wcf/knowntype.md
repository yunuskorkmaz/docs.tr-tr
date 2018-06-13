---
title: '&lt;knownType&gt;'
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: b2445f12f1eaac03b3f3ab66f3d13a5f465a1133
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753332"
---
# <a name="ltknowntypegt"></a><span data-ttu-id="15fea-102">&lt;knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="15fea-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="15fea-103">Tarafından kullanılmak üzere bir tür belirttiğinden <xref:System.Runtime.Serialization.DataContractSerializer> seri durumdan çıkarma sırasında.</span><span class="sxs-lookup"><span data-stu-id="15fea-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="15fea-104">"Bilinen bir türe" öğesi belirttiğinden bir alan veya "bildirilen türü." özelliği tarafından döndürülen</span><span class="sxs-lookup"><span data-stu-id="15fea-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="15fea-105">Daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="15fea-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="15fea-106">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="15fea-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="15fea-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="15fea-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="15fea-108">\<declaredTypes > öğesi</span><span class="sxs-lookup"><span data-stu-id="15fea-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="15fea-109">\<Ekle >, \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="15fea-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="15fea-110">\<knownType > öğesi</span><span class="sxs-lookup"><span data-stu-id="15fea-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15fea-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15fea-111">Syntax</span></span>  
  
```xml  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## <a name="type"></a><span data-ttu-id="15fea-112">Tür</span><span class="sxs-lookup"><span data-stu-id="15fea-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15fea-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="15fea-113">Attributes and Elements</span></span>  
 <span data-ttu-id="15fea-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15fea-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15fea-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="15fea-115">Attributes</span></span>  
  
|<span data-ttu-id="15fea-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="15fea-116">Attribute</span></span>|<span data-ttu-id="15fea-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15fea-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="15fea-118">türü</span><span class="sxs-lookup"><span data-stu-id="15fea-118">type</span></span>|<span data-ttu-id="15fea-119">(Ad alanı dahil) türü, derleme adı, sürüm, kültür ve ortak anahtar belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="15fea-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15fea-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="15fea-120">Child Elements</span></span>  
  
|<span data-ttu-id="15fea-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="15fea-121">Element</span></span>|<span data-ttu-id="15fea-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15fea-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15fea-123">\<Parametresi ></span><span class="sxs-lookup"><span data-stu-id="15fea-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="15fea-124">Bildirilen tür genel bir tür olduğunda parametre dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="15fea-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15fea-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="15fea-125">Parent Elements</span></span>  
  
|<span data-ttu-id="15fea-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="15fea-126">Element</span></span>|<span data-ttu-id="15fea-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15fea-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15fea-128">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="15fea-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="15fea-129">Bildirilen bir türe bildirilen türleri koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="15fea-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15fea-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15fea-130">Remarks</span></span>  
 <span data-ttu-id="15fea-131">Bilinen türleri hakkında daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="15fea-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="15fea-132">Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.</span><span class="sxs-lookup"><span data-stu-id="15fea-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15fea-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="15fea-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="15fea-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15fea-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="15fea-135">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="15fea-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="15fea-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="15fea-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="15fea-137">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="15fea-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
