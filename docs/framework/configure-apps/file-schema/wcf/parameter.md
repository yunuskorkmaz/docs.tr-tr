---
description: 'Hakkında daha fazla bilgi edinin: <parameter>'
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: fb04cfb5bf451cdb99c23ae41ea8fafeb13f0d11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683820"
---
# \<parameter>

<span data-ttu-id="e5a64-102">Tanımlanmış bir tür genel bir tür olduğunda genel parametreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**  
  
## <a name="syntax"></a><span data-ttu-id="e5a64-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5a64-103">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5a64-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5a64-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e5a64-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5a64-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5a64-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e5a64-106">Attributes</span></span>  
  
|<span data-ttu-id="e5a64-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e5a64-107">Attribute</span></span>|<span data-ttu-id="e5a64-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5a64-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5a64-109">dizin</span><span class="sxs-lookup"><span data-stu-id="e5a64-109">index</span></span>|<span data-ttu-id="e5a64-110">Belirtilen tür genel bir tür olduğunda, bilinen türü döndürecek genel parametreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-110">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="e5a64-111">tür</span><span class="sxs-lookup"><span data-stu-id="e5a64-111">type</span></span>|<span data-ttu-id="e5a64-112">Serileştirme ve seri durumdan çıkarma için kullanılan bilinen türü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="e5a64-112">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="e5a64-113">Index özniteliği</span><span class="sxs-lookup"><span data-stu-id="e5a64-113">index Attribute</span></span>  
  
|<span data-ttu-id="e5a64-114">Değer</span><span class="sxs-lookup"><span data-stu-id="e5a64-114">Value</span></span>|<span data-ttu-id="e5a64-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5a64-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e5a64-116">"0"</span><span class="sxs-lookup"><span data-stu-id="e5a64-116">"0"</span></span>|<span data-ttu-id="e5a64-117">Genel türdeki ilk parametre.</span><span class="sxs-lookup"><span data-stu-id="e5a64-117">The first parameter in the generic type.</span></span> <span data-ttu-id="e5a64-118">Örneğin, a <xref:System.Collections.Generic.List%601> yalnızca bir parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-118">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="e5a64-119">Belirtilen tür olarak kullanılırsa, Dizin "0" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e5a64-119">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="e5a64-120">"1"</span><span class="sxs-lookup"><span data-stu-id="e5a64-120">"1"</span></span>|<span data-ttu-id="e5a64-121">Genel türde ikinci parametre.</span><span class="sxs-lookup"><span data-stu-id="e5a64-121">The second parameter in a generic type.</span></span> <span data-ttu-id="e5a64-122">Örneğin, bir <xref:System.Collections.Generic.Dictionary%602> iki parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-122">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="e5a64-123">Bilinen tür ikinci parametre tarafından döndürülürse, Dizin özniteliğini "1" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e5a64-123">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5a64-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5a64-124">Child Elements</span></span>  

 <span data-ttu-id="e5a64-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5a64-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5a64-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5a64-126">Parent Elements</span></span>  
  
|<span data-ttu-id="e5a64-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5a64-127">Element</span></span>|<span data-ttu-id="e5a64-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5a64-128">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="e5a64-129">Tanımlı türün bir alanı veya özelliği tarafından döndürülebilecek bilinen bir türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-129">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5a64-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5a64-130">Remarks</span></span>  

 <span data-ttu-id="e5a64-131">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="e5a64-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="e5a64-132">[\<dataContractSerializer>](datacontractserializer-element.md)Bu öğenin kullanımıyla ilgili bir örnek için bkz..</span><span class="sxs-lookup"><span data-stu-id="e5a64-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="e5a64-133">Bu yapılandırma öğesinin her iki özniteliği de aynı anda olamaz.</span><span class="sxs-lookup"><span data-stu-id="e5a64-133">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="e5a64-134">Her iki öznitelik de ayarlanırsa, bir <xref:System.Configuration.ConfigurationErrorsException> gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-134">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a64-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5a64-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="e5a64-136">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="e5a64-136">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
