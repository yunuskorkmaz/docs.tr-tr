---
description: 'Daha fazla bilgi edinin: <MethodInstantiation> öğesi (.NET Native)'
title: <MethodInstantiation> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
ms.openlocfilehash: 985d522a559dbbce936a2f29a9983c89ebd18a48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747497"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="4c804-103">\<MethodInstantiation> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="4c804-103">\<MethodInstantiation> Element (.NET Native)</span></span>

<span data-ttu-id="4c804-104">Oluşturulmuş bir genel metoda çalışma zamanı yansıtma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="4c804-104">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c804-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4c804-105">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c804-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c804-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4c804-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c804-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c804-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4c804-108">Attributes</span></span>  
  
|<span data-ttu-id="4c804-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4c804-109">Attribute</span></span>|<span data-ttu-id="4c804-110">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="4c804-110">Attribute type</span></span>|<span data-ttu-id="4c804-111">Description</span><span class="sxs-lookup"><span data-stu-id="4c804-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="4c804-112">Genel</span><span class="sxs-lookup"><span data-stu-id="4c804-112">General</span></span>|<span data-ttu-id="4c804-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4c804-113">Required attribute.</span></span> <span data-ttu-id="4c804-114">Yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c804-114">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="4c804-115">Genel</span><span class="sxs-lookup"><span data-stu-id="4c804-115">General</span></span>|<span data-ttu-id="4c804-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4c804-116">Optional attribute.</span></span> <span data-ttu-id="4c804-117">Metodun adlandırılmış parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c804-117">Specifies named parameters of the method.</span></span> <span data-ttu-id="4c804-118">Birden çok adlandırılmış parametre virgüller ile ayrılır.</span><span class="sxs-lookup"><span data-stu-id="4c804-118">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="4c804-119">`Signature`Özniteliği, aşırı yüklenmiş yöntemleri ayırt etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c804-119">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="4c804-120">Genel</span><span class="sxs-lookup"><span data-stu-id="4c804-120">General</span></span>|<span data-ttu-id="4c804-121">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4c804-121">Required attribute.</span></span> <span data-ttu-id="4c804-122">Genel tür bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c804-122">Specifies the generic type arguments.</span></span> <span data-ttu-id="4c804-123">Birden çok bağımsız değişken varsa, bunlar virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="4c804-123">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="4c804-124">Yansıma</span><span class="sxs-lookup"><span data-stu-id="4c804-124">Reflection</span></span>|<span data-ttu-id="4c804-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4c804-125">Optional attribute.</span></span> <span data-ttu-id="4c804-126">Bir yöntem hakkında bilgi sorgulama veya bir yöntemi numaralandırma, ancak çalışma zamanında dinamik çağırma etkinleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="4c804-126">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="4c804-127">Yansıma</span><span class="sxs-lookup"><span data-stu-id="4c804-127">Reflection</span></span>|<span data-ttu-id="4c804-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4c804-128">Optional attribute.</span></span> <span data-ttu-id="4c804-129">Dinamik programlamayı etkinleştirmek için bir oluşturucuya veya yönteme çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="4c804-129">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="4c804-130">Bu ilke, bir üyenin çalışma zamanında dinamik olarak çağrılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c804-130">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="4c804-131">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="4c804-131">Name attribute</span></span>  
  
|<span data-ttu-id="4c804-132">Değer</span><span class="sxs-lookup"><span data-stu-id="4c804-132">Value</span></span>|<span data-ttu-id="4c804-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c804-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4c804-134">*method_name*</span><span class="sxs-lookup"><span data-stu-id="4c804-134">*method_name*</span></span>|<span data-ttu-id="4c804-135">Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="4c804-135">The method name.</span></span> <span data-ttu-id="4c804-136">Metodun türü üst [\<Type>](type-element-net-native.md) veya öğe tarafından tanımlanır [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="4c804-136">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="4c804-137">Signature özniteliği</span><span class="sxs-lookup"><span data-stu-id="4c804-137">Signature attribute</span></span>  
  
|<span data-ttu-id="4c804-138">Değer</span><span class="sxs-lookup"><span data-stu-id="4c804-138">Value</span></span>|<span data-ttu-id="4c804-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c804-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4c804-140">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="4c804-140">*method_signature*</span></span>|<span data-ttu-id="4c804-141">Metodun adlandırılmış parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c804-141">Specifies the named parameters of the method.</span></span> <span data-ttu-id="4c804-142">Birden çok parametre varsa, bunlar virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="4c804-142">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="4c804-143">Arguments özniteliği</span><span class="sxs-lookup"><span data-stu-id="4c804-143">Arguments attribute</span></span>  
  
|<span data-ttu-id="4c804-144">Değer</span><span class="sxs-lookup"><span data-stu-id="4c804-144">Value</span></span>|<span data-ttu-id="4c804-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c804-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4c804-146">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="4c804-146">*method_arguments*</span></span>|<span data-ttu-id="4c804-147">Genel tür bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c804-147">Specifies the generic type arguments.</span></span> <span data-ttu-id="4c804-148">Birden çok bağımsız değişken varsa, bunlar virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="4c804-148">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="4c804-149">Her bağımsız değişken tam nitelikli tür adından oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c804-149">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="4c804-150">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4c804-150">All other attributes</span></span>  
  
|<span data-ttu-id="4c804-151">Değer</span><span class="sxs-lookup"><span data-stu-id="4c804-151">Value</span></span>|<span data-ttu-id="4c804-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c804-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4c804-153">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="4c804-153">*policy_setting*</span></span>|<span data-ttu-id="4c804-154">Yöntemi için bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="4c804-154">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="4c804-155">Olası değerler şunlardır,, `Auto` `Excluded` `Included` ve `Required` .</span><span class="sxs-lookup"><span data-stu-id="4c804-155">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="4c804-156">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="4c804-156">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c804-157">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c804-157">Child Elements</span></span>  

 <span data-ttu-id="4c804-158">Yok.</span><span class="sxs-lookup"><span data-stu-id="4c804-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c804-159">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c804-159">Parent Elements</span></span>  
  
|<span data-ttu-id="4c804-160">Öğe</span><span class="sxs-lookup"><span data-stu-id="4c804-160">Element</span></span>|<span data-ttu-id="4c804-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c804-161">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="4c804-162">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="4c804-162">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="4c804-163">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="4c804-163">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c804-164">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c804-164">Remarks</span></span>  

 <span data-ttu-id="4c804-165">`<MethodInstantiation>`Öğesi, karşılık gelen açık genel yönteminin çalışma zamanı yansıma ilkesini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="4c804-165">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c804-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c804-166">See also</span></span>

- [<span data-ttu-id="4c804-167">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4c804-167">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="4c804-168">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="4c804-168">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="4c804-169">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="4c804-169">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="4c804-170">\<Method> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="4c804-170">\<Method> Element</span></span>](method-element-net-native.md)
