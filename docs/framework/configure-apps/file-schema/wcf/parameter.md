---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: c3f2179835ad1232e115cad0decdd3d41bbdc160
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932842"
---
# <a name="parameter"></a><span data-ttu-id="4b3d5-101">\<parametre ></span><span class="sxs-lookup"><span data-stu-id="4b3d5-101">\<parameter></span></span>
<span data-ttu-id="4b3d5-102">Tanımlanmış bir tür genel bir tür olduğunda genel parametreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="4b3d5-103">\<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="4b3d5-103">\<system.runtime.serialization></span></span>  
<span data-ttu-id="4b3d5-104">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="4b3d5-104">\<dataContractSerializer></span></span>  
<span data-ttu-id="4b3d5-105">\<declaredTypes > öğesi</span><span class="sxs-lookup"><span data-stu-id="4b3d5-105">\<declaredTypes> Element</span></span>  
<span data-ttu-id="4b3d5-106">\<DeclaredTypes > için \<> öğesi ekleme</span><span class="sxs-lookup"><span data-stu-id="4b3d5-106">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="4b3d5-107">\<knownType > öğesi</span><span class="sxs-lookup"><span data-stu-id="4b3d5-107">\<knownType> Element</span></span>  
<span data-ttu-id="4b3d5-108">\<Parameter > öğesi</span><span class="sxs-lookup"><span data-stu-id="4b3d5-108">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b3d5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b3d5-109">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b3d5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b3d5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4b3d5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b3d5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4b3d5-112">Attributes</span></span>  
  
|<span data-ttu-id="4b3d5-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4b3d5-113">Attribute</span></span>|<span data-ttu-id="4b3d5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b3d5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b3d5-115">dizin</span><span class="sxs-lookup"><span data-stu-id="4b3d5-115">index</span></span>|<span data-ttu-id="4b3d5-116">Belirtilen tür genel bir tür olduğunda, bilinen türü döndürecek genel parametreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-116">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="4b3d5-117">türü</span><span class="sxs-lookup"><span data-stu-id="4b3d5-117">type</span></span>|<span data-ttu-id="4b3d5-118">Serileştirme ve seri durumdan çıkarma için kullanılan bilinen türü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-118">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="4b3d5-119">Index özniteliği</span><span class="sxs-lookup"><span data-stu-id="4b3d5-119">index Attribute</span></span>  
  
|<span data-ttu-id="4b3d5-120">Değer</span><span class="sxs-lookup"><span data-stu-id="4b3d5-120">Value</span></span>|<span data-ttu-id="4b3d5-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b3d5-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4b3d5-122">"0"</span><span class="sxs-lookup"><span data-stu-id="4b3d5-122">"0"</span></span>|<span data-ttu-id="4b3d5-123">Genel türdeki ilk parametre.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-123">The first parameter in the generic type.</span></span> <span data-ttu-id="4b3d5-124">Örneğin, a <xref:System.Collections.Generic.List%601> yalnızca bir parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-124">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="4b3d5-125">Belirtilen tür olarak kullanılırsa, Dizin "0" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-125">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="4b3d5-126">"1"</span><span class="sxs-lookup"><span data-stu-id="4b3d5-126">"1"</span></span>|<span data-ttu-id="4b3d5-127">Genel türde ikinci parametre.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-127">The second parameter in a generic type.</span></span> <span data-ttu-id="4b3d5-128">Örneğin, bir <xref:System.Collections.Generic.Dictionary%602> iki parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-128">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="4b3d5-129">Bilinen tür ikinci parametre tarafından döndürülürse, Dizin özniteliğini "1" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-129">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b3d5-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b3d5-130">Child Elements</span></span>  
 <span data-ttu-id="4b3d5-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b3d5-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b3d5-132">Parent Elements</span></span>  
  
|<span data-ttu-id="4b3d5-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="4b3d5-133">Element</span></span>|<span data-ttu-id="4b3d5-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b3d5-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b3d5-135">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="4b3d5-135">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="4b3d5-136">Tanımlı türün bir alanı veya özelliği tarafından döndürülebilecek bilinen bir türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-136">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b3d5-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b3d5-137">Remarks</span></span>  
 <span data-ttu-id="4b3d5-138">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-138">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="4b3d5-139">Bu öğenin kullanılmasıyla ilgili bir örnek için bkz. [ DataContractSerializer>.\<](datacontractserializer-element.md)</span><span class="sxs-lookup"><span data-stu-id="4b3d5-139">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="4b3d5-140">Bu yapılandırma öğesinin her iki özniteliği de aynı anda olamaz.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-140">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="4b3d5-141">Her iki öznitelik de ayarlanırsa, bir <xref:System.Configuration.ConfigurationErrorsException> gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-141">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b3d5-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b3d5-142">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="4b3d5-143">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="4b3d5-143">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="4b3d5-144">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="4b3d5-144">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="4b3d5-145">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="4b3d5-145">\<add></span></span>](add-of-declaredtypes-element.md)
