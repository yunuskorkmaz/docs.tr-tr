---
title: '&lt;Parametre&gt;'
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: a68fdecaba6ad4e64e4d3a4161d9fef6c099d60a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690741"
---
# <a name="ltparametergt"></a><span data-ttu-id="15354-102">&lt;Parametre&gt;</span><span class="sxs-lookup"><span data-stu-id="15354-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="15354-103">Bildirilen tür genel bir tür olduğunda genel parametre belirler.</span><span class="sxs-lookup"><span data-stu-id="15354-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="15354-104">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="15354-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="15354-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="15354-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="15354-106">\<declaredTypes > öğesi</span><span class="sxs-lookup"><span data-stu-id="15354-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="15354-107">\<Ekle > öğesi için \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="15354-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="15354-108">\<knownType > öğesi</span><span class="sxs-lookup"><span data-stu-id="15354-108">\<knownType> Element</span></span>  
<span data-ttu-id="15354-109">\<parametresi > öğesi</span><span class="sxs-lookup"><span data-stu-id="15354-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15354-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15354-110">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15354-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="15354-111">Attributes and Elements</span></span>  
 <span data-ttu-id="15354-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15354-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15354-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="15354-113">Attributes</span></span>  
  
|<span data-ttu-id="15354-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="15354-114">Attribute</span></span>|<span data-ttu-id="15354-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15354-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="15354-116">dizin</span><span class="sxs-lookup"><span data-stu-id="15354-116">index</span></span>|<span data-ttu-id="15354-117">Bildirilen tür genel bir tür olduğunda, bilinen türü döndüren genel parametre belirler.</span><span class="sxs-lookup"><span data-stu-id="15354-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="15354-118">türü</span><span class="sxs-lookup"><span data-stu-id="15354-118">type</span></span>|<span data-ttu-id="15354-119">Serileştirme ve seri durumundan çıkarma için kullanılan bilinen türü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="15354-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="15354-120">Dizin öznitelik</span><span class="sxs-lookup"><span data-stu-id="15354-120">index Attribute</span></span>  
  
|<span data-ttu-id="15354-121">Değer</span><span class="sxs-lookup"><span data-stu-id="15354-121">Value</span></span>|<span data-ttu-id="15354-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15354-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15354-123">"0"</span><span class="sxs-lookup"><span data-stu-id="15354-123">"0"</span></span>|<span data-ttu-id="15354-124">İlk genel tür parametre.</span><span class="sxs-lookup"><span data-stu-id="15354-124">The first parameter in the generic type.</span></span> <span data-ttu-id="15354-125">Örneğin, bir <xref:System.Collections.Generic.List%601> yalnızca bir parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="15354-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="15354-126">Bildirilen tür olarak kullanılıyorsa, dizin "0" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="15354-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="15354-127">"1"</span><span class="sxs-lookup"><span data-stu-id="15354-127">"1"</span></span>|<span data-ttu-id="15354-128">İkinci bir genel tür parametresi.</span><span class="sxs-lookup"><span data-stu-id="15354-128">The second parameter in a generic type.</span></span> <span data-ttu-id="15354-129">Örneğin, bir <xref:System.Collections.Generic.Dictionary%602> iki parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="15354-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="15354-130">İkinci parametre tarafından döndürülen bilinen türü, "1" dizini özniteliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="15354-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15354-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="15354-131">Child Elements</span></span>  
 <span data-ttu-id="15354-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="15354-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15354-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="15354-133">Parent Elements</span></span>  
  
|<span data-ttu-id="15354-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="15354-134">Element</span></span>|<span data-ttu-id="15354-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15354-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15354-136">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="15354-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="15354-137">Bir alan veya özellik bildirilen türü tarafından döndürülen bilinen bir türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="15354-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15354-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15354-138">Remarks</span></span>  
 <span data-ttu-id="15354-139">Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="15354-139">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="15354-140">Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.</span><span class="sxs-lookup"><span data-stu-id="15354-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="15354-141">Bu yapılandırma öğesi, her iki öznitelik aynı anda sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="15354-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="15354-142">Her iki öznitelik ayarlanırsa, bir <xref:System.Configuration.ConfigurationErrorsException> gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="15354-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15354-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15354-143">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="15354-144">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="15354-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="15354-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="15354-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="15354-146">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="15354-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
