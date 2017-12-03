---
title: '&lt;knownType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bedebb98e5fc48292c503eef30cee30c8d29c41c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltknowntypegt"></a><span data-ttu-id="d8a9f-102">&lt;knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="d8a9f-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="d8a9f-103">Tarafından kullanılmak üzere bir tür belirttiğinden <xref:System.Runtime.Serialization.DataContractSerializer> seri durumdan çıkarma sırasında.</span><span class="sxs-lookup"><span data-stu-id="d8a9f-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="d8a9f-104">"Bilinen bir türe" öğesi belirttiğinden bir alan veya "bildirilen türü." özelliği tarafından döndürülen</span><span class="sxs-lookup"><span data-stu-id="d8a9f-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="d8a9f-105">Daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="d8a9f-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="d8a9f-106">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="d8a9f-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="d8a9f-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="d8a9f-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="d8a9f-108">\<declaredTypes > öğesi</span><span class="sxs-lookup"><span data-stu-id="d8a9f-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="d8a9f-109">\<Ekle >, \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="d8a9f-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="d8a9f-110">\<knownType > öğesi</span><span class="sxs-lookup"><span data-stu-id="d8a9f-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8a9f-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8a9f-111">Syntax</span></span>  
  
```xml  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## <a name="type"></a><span data-ttu-id="d8a9f-112">Tür</span><span class="sxs-lookup"><span data-stu-id="d8a9f-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8a9f-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8a9f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d8a9f-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8a9f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8a9f-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d8a9f-115">Attributes</span></span>  
  
|<span data-ttu-id="d8a9f-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d8a9f-116">Attribute</span></span>|<span data-ttu-id="d8a9f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8a9f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8a9f-118">türü</span><span class="sxs-lookup"><span data-stu-id="d8a9f-118">type</span></span>|<span data-ttu-id="d8a9f-119">(Ad alanı dahil) türü, derleme adı, sürüm, kültür ve ortak anahtar belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8a9f-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8a9f-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8a9f-120">Child Elements</span></span>  
  
|<span data-ttu-id="d8a9f-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="d8a9f-121">Element</span></span>|<span data-ttu-id="d8a9f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8a9f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8a9f-123">\<parametresi ></span><span class="sxs-lookup"><span data-stu-id="d8a9f-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="d8a9f-124">Bildirilen tür genel bir tür olduğunda parametre dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8a9f-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8a9f-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8a9f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d8a9f-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="d8a9f-126">Element</span></span>|<span data-ttu-id="d8a9f-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8a9f-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8a9f-128">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="d8a9f-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="d8a9f-129">Bildirilen bir türe bildirilen türleri koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="d8a9f-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8a9f-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8a9f-130">Remarks</span></span>  
 <span data-ttu-id="d8a9f-131">Bilinen türleri hakkında daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d8a9f-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="d8a9f-132">Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.</span><span class="sxs-lookup"><span data-stu-id="d8a9f-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8a9f-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8a9f-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8a9f-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8a9f-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="d8a9f-135">Veri sözleşmesi bilinen türler</span><span class="sxs-lookup"><span data-stu-id="d8a9f-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="d8a9f-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="d8a9f-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="d8a9f-137">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="d8a9f-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
