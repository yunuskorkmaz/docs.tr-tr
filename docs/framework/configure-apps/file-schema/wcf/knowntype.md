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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ccb7152197a021821936e178e0de77b9dfabce45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltknowntypegt"></a><span data-ttu-id="7a372-102">&lt;knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="7a372-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="7a372-103">Tarafından kullanılmak üzere bir tür belirttiğinden <xref:System.Runtime.Serialization.DataContractSerializer> seri durumdan çıkarma sırasında.</span><span class="sxs-lookup"><span data-stu-id="7a372-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="7a372-104">"Bilinen bir türe" öğesi belirttiğinden bir alan veya "bildirilen türü." özelliği tarafından döndürülen</span><span class="sxs-lookup"><span data-stu-id="7a372-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="7a372-105">Daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="7a372-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="7a372-106">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="7a372-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="7a372-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="7a372-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="7a372-108">\<declaredTypes > öğesi</span><span class="sxs-lookup"><span data-stu-id="7a372-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="7a372-109">\<Ekle >, \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="7a372-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="7a372-110">\<knownType > öğesi</span><span class="sxs-lookup"><span data-stu-id="7a372-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a372-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a372-111">Syntax</span></span>  
  
```xml  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## <a name="type"></a><span data-ttu-id="7a372-112">Tür</span><span class="sxs-lookup"><span data-stu-id="7a372-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a372-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a372-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7a372-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7a372-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a372-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7a372-115">Attributes</span></span>  
  
|<span data-ttu-id="7a372-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7a372-116">Attribute</span></span>|<span data-ttu-id="7a372-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a372-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7a372-118">türü</span><span class="sxs-lookup"><span data-stu-id="7a372-118">type</span></span>|<span data-ttu-id="7a372-119">(Ad alanı dahil) türü, derleme adı, sürüm, kültür ve ortak anahtar belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a372-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a372-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a372-120">Child Elements</span></span>  
  
|<span data-ttu-id="7a372-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="7a372-121">Element</span></span>|<span data-ttu-id="7a372-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a372-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a372-123">\<parametresi ></span><span class="sxs-lookup"><span data-stu-id="7a372-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="7a372-124">Bildirilen tür genel bir tür olduğunda parametre dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a372-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7a372-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a372-125">Parent Elements</span></span>  
  
|<span data-ttu-id="7a372-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="7a372-126">Element</span></span>|<span data-ttu-id="7a372-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a372-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a372-128">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="7a372-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="7a372-129">Bildirilen bir türe bildirilen türleri koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="7a372-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a372-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a372-130">Remarks</span></span>  
 <span data-ttu-id="7a372-131">Bilinen türleri hakkında daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7a372-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="7a372-132">Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.</span><span class="sxs-lookup"><span data-stu-id="7a372-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a372-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a372-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a372-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a372-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="7a372-135">Veri sözleşmesi bilinen türler</span><span class="sxs-lookup"><span data-stu-id="7a372-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="7a372-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="7a372-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="7a372-137">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="7a372-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
