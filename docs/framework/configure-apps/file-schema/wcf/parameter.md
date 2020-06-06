---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 07fa410109a7bd2fa315132c4737301698bb3a93
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400106"
---
# \<parameter>
<span data-ttu-id="ca8b6-101">Tanımlanmış bir tür genel bir tür olduğunda genel parametreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-101">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**  
  
## <a name="syntax"></a><span data-ttu-id="ca8b6-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca8b6-102">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca8b6-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca8b6-103">Attributes and Elements</span></span>  
 <span data-ttu-id="ca8b6-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca8b6-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ca8b6-105">Attributes</span></span>  
  
|<span data-ttu-id="ca8b6-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ca8b6-106">Attribute</span></span>|<span data-ttu-id="ca8b6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca8b6-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ca8b6-108">dizin</span><span class="sxs-lookup"><span data-stu-id="ca8b6-108">index</span></span>|<span data-ttu-id="ca8b6-109">Belirtilen tür genel bir tür olduğunda, bilinen türü döndürecek genel parametreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-109">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="ca8b6-110">tür</span><span class="sxs-lookup"><span data-stu-id="ca8b6-110">type</span></span>|<span data-ttu-id="ca8b6-111">Serileştirme ve seri durumdan çıkarma için kullanılan bilinen türü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-111">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="ca8b6-112">Index özniteliği</span><span class="sxs-lookup"><span data-stu-id="ca8b6-112">index Attribute</span></span>  
  
|<span data-ttu-id="ca8b6-113">Değer</span><span class="sxs-lookup"><span data-stu-id="ca8b6-113">Value</span></span>|<span data-ttu-id="ca8b6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca8b6-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ca8b6-115">"0"</span><span class="sxs-lookup"><span data-stu-id="ca8b6-115">"0"</span></span>|<span data-ttu-id="ca8b6-116">Genel türdeki ilk parametre.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-116">The first parameter in the generic type.</span></span> <span data-ttu-id="ca8b6-117">Örneğin, a <xref:System.Collections.Generic.List%601> yalnızca bir parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-117">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="ca8b6-118">Belirtilen tür olarak kullanılırsa, Dizin "0" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-118">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="ca8b6-119">"1"</span><span class="sxs-lookup"><span data-stu-id="ca8b6-119">"1"</span></span>|<span data-ttu-id="ca8b6-120">Genel türde ikinci parametre.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-120">The second parameter in a generic type.</span></span> <span data-ttu-id="ca8b6-121">Örneğin, bir <xref:System.Collections.Generic.Dictionary%602> iki parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-121">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="ca8b6-122">Bilinen tür ikinci parametre tarafından döndürülürse, Dizin özniteliğini "1" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-122">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca8b6-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca8b6-123">Child Elements</span></span>  
 <span data-ttu-id="ca8b6-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca8b6-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca8b6-125">Parent Elements</span></span>  
  
|<span data-ttu-id="ca8b6-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca8b6-126">Element</span></span>|<span data-ttu-id="ca8b6-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca8b6-127">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="ca8b6-128">Tanımlı türün bir alanı veya özelliği tarafından döndürülebilecek bilinen bir türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-128">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca8b6-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca8b6-129">Remarks</span></span>  
 <span data-ttu-id="ca8b6-130">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="ca8b6-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="ca8b6-131">[\<dataContractSerializer>](datacontractserializer-element.md)Bu öğenin kullanımıyla ilgili bir örnek için bkz..</span><span class="sxs-lookup"><span data-stu-id="ca8b6-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="ca8b6-132">Bu yapılandırma öğesinin her iki özniteliği de aynı anda olamaz.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-132">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="ca8b6-133">Her iki öznitelik de ayarlanırsa, bir <xref:System.Configuration.ConfigurationErrorsException> gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-133">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca8b6-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca8b6-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="ca8b6-135">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="ca8b6-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
