---
title: '&lt;parametre&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9db1921e2a6ee1ae2780f744c45fdb25efbf797
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltparametergt"></a><span data-ttu-id="efd75-102">&lt;parametre&gt;</span><span class="sxs-lookup"><span data-stu-id="efd75-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="efd75-103">Bildirilen bir türe genel bir tür olduğunda genel parametresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="efd75-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="efd75-104">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="efd75-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="efd75-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="efd75-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="efd75-106">\<declaredTypes > öğesi</span><span class="sxs-lookup"><span data-stu-id="efd75-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="efd75-107">\<Ekle > öğesi için \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="efd75-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="efd75-108">\<knownType > öğesi</span><span class="sxs-lookup"><span data-stu-id="efd75-108">\<knownType> Element</span></span>  
<span data-ttu-id="efd75-109">\<parametresi > öğesi</span><span class="sxs-lookup"><span data-stu-id="efd75-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efd75-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="efd75-110">Syntax</span></span>  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efd75-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="efd75-111">Attributes and Elements</span></span>  
 <span data-ttu-id="efd75-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="efd75-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efd75-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="efd75-113">Attributes</span></span>  
  
|<span data-ttu-id="efd75-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="efd75-114">Attribute</span></span>|<span data-ttu-id="efd75-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efd75-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="efd75-116">dizin</span><span class="sxs-lookup"><span data-stu-id="efd75-116">index</span></span>|<span data-ttu-id="efd75-117">Bildirilen genel bir tür olduğunda, bilinen bir tür döndürür genel parametresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="efd75-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="efd75-118">türü</span><span class="sxs-lookup"><span data-stu-id="efd75-118">type</span></span>|<span data-ttu-id="efd75-119">Serileştirme ve seri durumundan çıkarma için kullanılan bilinen türünü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="efd75-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="efd75-120">Dizin özniteliği</span><span class="sxs-lookup"><span data-stu-id="efd75-120">index Attribute</span></span>  
  
|<span data-ttu-id="efd75-121">Değer</span><span class="sxs-lookup"><span data-stu-id="efd75-121">Value</span></span>|<span data-ttu-id="efd75-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efd75-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="efd75-123">"0"</span><span class="sxs-lookup"><span data-stu-id="efd75-123">"0"</span></span>|<span data-ttu-id="efd75-124">Genel tür ilk parametre.</span><span class="sxs-lookup"><span data-stu-id="efd75-124">The first parameter in the generic type.</span></span> <span data-ttu-id="efd75-125">Örneğin, bir <xref:System.Collections.Generic.List%601> yalnızca bir parametre içeriyor.</span><span class="sxs-lookup"><span data-stu-id="efd75-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="efd75-126">Bildirilen türü olarak kullanılıyorsa, dizin "0" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="efd75-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="efd75-127">"1"</span><span class="sxs-lookup"><span data-stu-id="efd75-127">"1"</span></span>|<span data-ttu-id="efd75-128">Genel bir tür ikinci bir parametre.</span><span class="sxs-lookup"><span data-stu-id="efd75-128">The second parameter in a generic type.</span></span> <span data-ttu-id="efd75-129">Örneğin, bir <xref:System.Collections.Generic.Dictionary%602> iki parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="efd75-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="efd75-130">İkinci parametresi tarafından bilinen türü döndürülürse, "1" dizini özniteliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="efd75-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efd75-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="efd75-131">Child Elements</span></span>  
 <span data-ttu-id="efd75-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="efd75-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="efd75-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="efd75-133">Parent Elements</span></span>  
  
|<span data-ttu-id="efd75-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="efd75-134">Element</span></span>|<span data-ttu-id="efd75-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efd75-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efd75-136">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="efd75-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="efd75-137">Bir alan veya türü, özellik tarafından döndürülen bilinen bir türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="efd75-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efd75-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="efd75-138">Remarks</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="efd75-139">bilinen türlerini, bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="efd75-139"> known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="efd75-140">Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.</span><span class="sxs-lookup"><span data-stu-id="efd75-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="efd75-141">Bu yapılandırma öğesi her iki öznitelik aynı anda sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="efd75-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="efd75-142">Her iki öznitelik ayarlanırsa, bir <xref:System.Configuration.ConfigurationErrorsException> oluşur.</span><span class="sxs-lookup"><span data-stu-id="efd75-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd75-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="efd75-143">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="efd75-144">Veri sözleşmesi bilinen türler</span><span class="sxs-lookup"><span data-stu-id="efd75-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="efd75-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="efd75-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="efd75-146">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="efd75-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
