---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 8b14dc1908ef3a06549154f70efb2d4e5cb10076
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289448"
---
# <a name="parameter"></a><span data-ttu-id="5ca5b-101">\<Parametresi ></span><span class="sxs-lookup"><span data-stu-id="5ca5b-101">\<parameter></span></span>
<span data-ttu-id="5ca5b-102">Bildirilen tür genel bir tür olduğunda genel parametre belirler.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="5ca5b-103">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="5ca5b-103">\<system.runtime.serialization></span></span>  
<span data-ttu-id="5ca5b-104">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="5ca5b-104">\<dataContractSerializer></span></span>  
<span data-ttu-id="5ca5b-105">\<declaredTypes > öğesi</span><span class="sxs-lookup"><span data-stu-id="5ca5b-105">\<declaredTypes> Element</span></span>  
<span data-ttu-id="5ca5b-106">\<Ekle > öğesi için \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="5ca5b-106">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="5ca5b-107">\<knownType > öğesi</span><span class="sxs-lookup"><span data-stu-id="5ca5b-107">\<knownType> Element</span></span>  
<span data-ttu-id="5ca5b-108">\<parametresi > öğesi</span><span class="sxs-lookup"><span data-stu-id="5ca5b-108">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ca5b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ca5b-109">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ca5b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ca5b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ca5b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ca5b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ca5b-112">Attributes</span></span>  
  
|<span data-ttu-id="5ca5b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ca5b-113">Attribute</span></span>|<span data-ttu-id="5ca5b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ca5b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ca5b-115">dizin</span><span class="sxs-lookup"><span data-stu-id="5ca5b-115">index</span></span>|<span data-ttu-id="5ca5b-116">Bildirilen tür genel bir tür olduğunda, bilinen türü döndüren genel parametre belirler.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-116">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="5ca5b-117">türü</span><span class="sxs-lookup"><span data-stu-id="5ca5b-117">type</span></span>|<span data-ttu-id="5ca5b-118">Serileştirme ve seri durumundan çıkarma için kullanılan bilinen türü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-118">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="5ca5b-119">Dizin öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ca5b-119">index Attribute</span></span>  
  
|<span data-ttu-id="5ca5b-120">Değer</span><span class="sxs-lookup"><span data-stu-id="5ca5b-120">Value</span></span>|<span data-ttu-id="5ca5b-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ca5b-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5ca5b-122">"0"</span><span class="sxs-lookup"><span data-stu-id="5ca5b-122">"0"</span></span>|<span data-ttu-id="5ca5b-123">İlk genel tür parametre.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-123">The first parameter in the generic type.</span></span> <span data-ttu-id="5ca5b-124">Örneğin, bir <xref:System.Collections.Generic.List%601> yalnızca bir parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-124">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="5ca5b-125">Bildirilen tür olarak kullanılıyorsa, dizin "0" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-125">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="5ca5b-126">"1"</span><span class="sxs-lookup"><span data-stu-id="5ca5b-126">"1"</span></span>|<span data-ttu-id="5ca5b-127">İkinci bir genel tür parametresi.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-127">The second parameter in a generic type.</span></span> <span data-ttu-id="5ca5b-128">Örneğin, bir <xref:System.Collections.Generic.Dictionary%602> iki parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-128">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="5ca5b-129">İkinci parametre tarafından döndürülen bilinen türü, "1" dizini özniteliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-129">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ca5b-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ca5b-130">Child Elements</span></span>  
 <span data-ttu-id="5ca5b-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ca5b-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ca5b-132">Parent Elements</span></span>  
  
|<span data-ttu-id="5ca5b-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ca5b-133">Element</span></span>|<span data-ttu-id="5ca5b-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ca5b-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ca5b-135">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="5ca5b-135">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="5ca5b-136">Bir alan veya özellik bildirilen türü tarafından döndürülen bilinen bir türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-136">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ca5b-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ca5b-137">Remarks</span></span>  
 <span data-ttu-id="5ca5b-138">Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-138">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="5ca5b-139">Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-139">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="5ca5b-140">Bu yapılandırma öğesi, her iki öznitelik aynı anda sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-140">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="5ca5b-141">Her iki öznitelik ayarlanırsa, bir <xref:System.Configuration.ConfigurationErrorsException> gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-141">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca5b-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-142">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="5ca5b-143">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="5ca5b-143">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="5ca5b-144">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="5ca5b-144">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="5ca5b-145">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="5ca5b-145">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
