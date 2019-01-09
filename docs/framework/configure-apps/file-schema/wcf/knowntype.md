---
title: '&lt;knownType&gt;'
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 6156f102573333ec0d5533b8f1a8506d91215f47
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151936"
---
# <a name="ltknowntypegt"></a><span data-ttu-id="46086-102">&lt;knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="46086-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="46086-103">Tarafından kullanılacak bir tür belirttiğinden <xref:System.Runtime.Serialization.DataContractSerializer> seri durumundan çıkarma sırasında.</span><span class="sxs-lookup"><span data-stu-id="46086-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="46086-104">"Bilinen türü" olan öğeyi belirten bir alan veya özellik "bildirilen türü." tarafından döndürülen</span><span class="sxs-lookup"><span data-stu-id="46086-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="46086-105">Daha fazla bilgi için [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="46086-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="46086-106">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="46086-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="46086-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="46086-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="46086-108">\<declaredTypes > öğesi</span><span class="sxs-lookup"><span data-stu-id="46086-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="46086-109">\<Ekle >, \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="46086-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="46086-110">\<knownType > öğesi</span><span class="sxs-lookup"><span data-stu-id="46086-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46086-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46086-111">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="46086-112">Tür</span><span class="sxs-lookup"><span data-stu-id="46086-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46086-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="46086-113">Attributes and Elements</span></span>  
 <span data-ttu-id="46086-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46086-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46086-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="46086-115">Attributes</span></span>  
  
|<span data-ttu-id="46086-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="46086-116">Attribute</span></span>|<span data-ttu-id="46086-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46086-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46086-118">türü</span><span class="sxs-lookup"><span data-stu-id="46086-118">type</span></span>|<span data-ttu-id="46086-119">Türü (ad uzayı dahil), derleme adı, sürüm, kültür ve ortak anahtar belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="46086-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46086-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="46086-120">Child Elements</span></span>  
  
|<span data-ttu-id="46086-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="46086-121">Element</span></span>|<span data-ttu-id="46086-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46086-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46086-123">\<Parametresi ></span><span class="sxs-lookup"><span data-stu-id="46086-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="46086-124">Bildirilen tür genel bir tür olduğunda, bir parametre dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="46086-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="46086-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="46086-125">Parent Elements</span></span>  
  
|<span data-ttu-id="46086-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="46086-126">Element</span></span>|<span data-ttu-id="46086-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46086-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46086-128">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="46086-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="46086-129">Bildirilen tür bildirilen tür koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="46086-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46086-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46086-130">Remarks</span></span>  
 <span data-ttu-id="46086-131">Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="46086-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="46086-132">Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.</span><span class="sxs-lookup"><span data-stu-id="46086-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46086-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="46086-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="46086-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46086-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="46086-135">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="46086-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="46086-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="46086-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="46086-137">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="46086-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
