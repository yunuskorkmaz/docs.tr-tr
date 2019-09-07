---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 07fa410109a7bd2fa315132c4737301698bb3a93
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400106"
---
# <a name="parameter"></a><span data-ttu-id="3eaee-101">\<parametre ></span><span class="sxs-lookup"><span data-stu-id="3eaee-101">\<parameter></span></span>
<span data-ttu-id="3eaee-102">Tanımlanmış bir tür genel bir tür olduğunda genel parametreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3eaee-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
<span data-ttu-id="3eaee-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3eaee-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3eaee-104">&nbsp;&nbsp;[ **\<System. Runtime. Serialization >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="3eaee-104">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="3eaee-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dataContractSerializer >** ](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="3eaee-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="3eaee-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="3eaee-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="3eaee-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> Ekle**](add-of-declaredtypes-element.md)</span><span class="sxs-lookup"><span data-stu-id="3eaee-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)</span></span>\
<span data-ttu-id="3eaee-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<knownType >** ](knowntype.md)</span><span class="sxs-lookup"><span data-stu-id="3eaee-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)</span></span>\
<span data-ttu-id="3eaee-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<parametre >**</span><span class="sxs-lookup"><span data-stu-id="3eaee-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eaee-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3eaee-110">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3eaee-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3eaee-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3eaee-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3eaee-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3eaee-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3eaee-113">Attributes</span></span>  
  
|<span data-ttu-id="3eaee-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3eaee-114">Attribute</span></span>|<span data-ttu-id="3eaee-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3eaee-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3eaee-116">dizin</span><span class="sxs-lookup"><span data-stu-id="3eaee-116">index</span></span>|<span data-ttu-id="3eaee-117">Belirtilen tür genel bir tür olduğunda, bilinen türü döndürecek genel parametreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3eaee-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="3eaee-118">türü</span><span class="sxs-lookup"><span data-stu-id="3eaee-118">type</span></span>|<span data-ttu-id="3eaee-119">Serileştirme ve seri durumdan çıkarma için kullanılan bilinen türü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="3eaee-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="3eaee-120">Index özniteliği</span><span class="sxs-lookup"><span data-stu-id="3eaee-120">index Attribute</span></span>  
  
|<span data-ttu-id="3eaee-121">Değer</span><span class="sxs-lookup"><span data-stu-id="3eaee-121">Value</span></span>|<span data-ttu-id="3eaee-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3eaee-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3eaee-123">"0"</span><span class="sxs-lookup"><span data-stu-id="3eaee-123">"0"</span></span>|<span data-ttu-id="3eaee-124">Genel türdeki ilk parametre.</span><span class="sxs-lookup"><span data-stu-id="3eaee-124">The first parameter in the generic type.</span></span> <span data-ttu-id="3eaee-125">Örneğin, a <xref:System.Collections.Generic.List%601> yalnızca bir parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3eaee-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="3eaee-126">Belirtilen tür olarak kullanılırsa, Dizin "0" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3eaee-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="3eaee-127">"1"</span><span class="sxs-lookup"><span data-stu-id="3eaee-127">"1"</span></span>|<span data-ttu-id="3eaee-128">Genel türde ikinci parametre.</span><span class="sxs-lookup"><span data-stu-id="3eaee-128">The second parameter in a generic type.</span></span> <span data-ttu-id="3eaee-129">Örneğin, bir <xref:System.Collections.Generic.Dictionary%602> iki parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3eaee-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="3eaee-130">Bilinen tür ikinci parametre tarafından döndürülürse, Dizin özniteliğini "1" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3eaee-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3eaee-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3eaee-131">Child Elements</span></span>  
 <span data-ttu-id="3eaee-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="3eaee-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3eaee-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3eaee-133">Parent Elements</span></span>  
  
|<span data-ttu-id="3eaee-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="3eaee-134">Element</span></span>|<span data-ttu-id="3eaee-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3eaee-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3eaee-136">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="3eaee-136">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="3eaee-137">Tanımlı türün bir alanı veya özelliği tarafından döndürülebilecek bilinen bir türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3eaee-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3eaee-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3eaee-138">Remarks</span></span>  
 <span data-ttu-id="3eaee-139">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="3eaee-139">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="3eaee-140">Bu öğenin kullanılmasıyla ilgili bir örnek için bkz. [ DataContractSerializer>.\<](datacontractserializer-element.md)</span><span class="sxs-lookup"><span data-stu-id="3eaee-140">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="3eaee-141">Bu yapılandırma öğesinin her iki özniteliği de aynı anda olamaz.</span><span class="sxs-lookup"><span data-stu-id="3eaee-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="3eaee-142">Her iki öznitelik de ayarlanırsa, bir <xref:System.Configuration.ConfigurationErrorsException> gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="3eaee-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eaee-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3eaee-143">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="3eaee-144">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="3eaee-144">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="3eaee-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="3eaee-145">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="3eaee-146">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="3eaee-146">\<add></span></span>](add-of-declaredtypes-element.md)
