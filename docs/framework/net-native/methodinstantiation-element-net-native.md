---
title: <MethodInstantiation>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
ms.openlocfilehash: f19bd3c20088431bcbbafac298398b82a664bee9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128322"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="c664c-102">\<MethodInstantiation>Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="c664c-102">\<MethodInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="c664c-103">Oluşturulmuş bir genel metoda çalışma zamanı yansıtma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="c664c-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c664c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c664c-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c664c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c664c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c664c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c664c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c664c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c664c-107">Attributes</span></span>  
  
|<span data-ttu-id="c664c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c664c-108">Attribute</span></span>|<span data-ttu-id="c664c-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="c664c-109">Attribute type</span></span>|<span data-ttu-id="c664c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c664c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="c664c-111">Genel</span><span class="sxs-lookup"><span data-stu-id="c664c-111">General</span></span>|<span data-ttu-id="c664c-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c664c-112">Required attribute.</span></span> <span data-ttu-id="c664c-113">Yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c664c-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="c664c-114">Genel</span><span class="sxs-lookup"><span data-stu-id="c664c-114">General</span></span>|<span data-ttu-id="c664c-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c664c-115">Optional attribute.</span></span> <span data-ttu-id="c664c-116">Metodun adlandırılmış parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c664c-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="c664c-117">Birden çok adlandırılmış parametre virgüller ile ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c664c-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="c664c-118">`Signature`Özniteliği, aşırı yüklenmiş yöntemleri ayırt etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c664c-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="c664c-119">Genel</span><span class="sxs-lookup"><span data-stu-id="c664c-119">General</span></span>|<span data-ttu-id="c664c-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c664c-120">Required attribute.</span></span> <span data-ttu-id="c664c-121">Genel tür bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c664c-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="c664c-122">Birden çok bağımsız değişken varsa, bunlar virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c664c-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="c664c-123">Yansıma</span><span class="sxs-lookup"><span data-stu-id="c664c-123">Reflection</span></span>|<span data-ttu-id="c664c-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c664c-124">Optional attribute.</span></span> <span data-ttu-id="c664c-125">Bir yöntem hakkında bilgi sorgulama veya bir yöntemi numaralandırma, ancak çalışma zamanında dinamik çağırma etkinleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="c664c-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="c664c-126">Yansıma</span><span class="sxs-lookup"><span data-stu-id="c664c-126">Reflection</span></span>|<span data-ttu-id="c664c-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c664c-127">Optional attribute.</span></span> <span data-ttu-id="c664c-128">Dinamik programlamayı etkinleştirmek için bir oluşturucuya veya yönteme çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="c664c-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="c664c-129">Bu ilke, bir üyenin çalışma zamanında dinamik olarak çağrılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c664c-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="c664c-130">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="c664c-130">Name attribute</span></span>  
  
|<span data-ttu-id="c664c-131">Değer</span><span class="sxs-lookup"><span data-stu-id="c664c-131">Value</span></span>|<span data-ttu-id="c664c-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c664c-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c664c-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="c664c-133">*method_name*</span></span>|<span data-ttu-id="c664c-134">Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="c664c-134">The method name.</span></span> <span data-ttu-id="c664c-135">Metodun türü üst [\<Type>](type-element-net-native.md) veya öğe tarafından tanımlanır [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="c664c-135">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="c664c-136">Signature özniteliği</span><span class="sxs-lookup"><span data-stu-id="c664c-136">Signature attribute</span></span>  
  
|<span data-ttu-id="c664c-137">Değer</span><span class="sxs-lookup"><span data-stu-id="c664c-137">Value</span></span>|<span data-ttu-id="c664c-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c664c-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c664c-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="c664c-139">*method_signature*</span></span>|<span data-ttu-id="c664c-140">Metodun adlandırılmış parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c664c-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="c664c-141">Birden çok parametre varsa, bunlar virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c664c-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="c664c-142">Arguments özniteliği</span><span class="sxs-lookup"><span data-stu-id="c664c-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="c664c-143">Değer</span><span class="sxs-lookup"><span data-stu-id="c664c-143">Value</span></span>|<span data-ttu-id="c664c-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c664c-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c664c-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="c664c-145">*method_arguments*</span></span>|<span data-ttu-id="c664c-146">Genel tür bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c664c-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="c664c-147">Birden çok bağımsız değişken varsa, bunlar virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c664c-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="c664c-148">Her bağımsız değişken tam nitelikli tür adından oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c664c-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="c664c-149">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c664c-149">All other attributes</span></span>  
  
|<span data-ttu-id="c664c-150">Değer</span><span class="sxs-lookup"><span data-stu-id="c664c-150">Value</span></span>|<span data-ttu-id="c664c-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c664c-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c664c-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="c664c-152">*policy_setting*</span></span>|<span data-ttu-id="c664c-153">Yöntemi için bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="c664c-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="c664c-154">Olası değerler şunlardır,, `Auto` `Excluded` `Included` ve `Required` .</span><span class="sxs-lookup"><span data-stu-id="c664c-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="c664c-155">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="c664c-155">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c664c-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c664c-156">Child Elements</span></span>  
 <span data-ttu-id="c664c-157">Yok.</span><span class="sxs-lookup"><span data-stu-id="c664c-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c664c-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c664c-158">Parent Elements</span></span>  
  
|<span data-ttu-id="c664c-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="c664c-159">Element</span></span>|<span data-ttu-id="c664c-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c664c-160">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="c664c-161">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="c664c-161">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="c664c-162">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="c664c-162">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c664c-163">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c664c-163">Remarks</span></span>  
 <span data-ttu-id="c664c-164">`<MethodInstantiation>`Öğesi, karşılık gelen açık genel yönteminin çalışma zamanı yansıma ilkesini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c664c-164">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c664c-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c664c-165">See also</span></span>

- [<span data-ttu-id="c664c-166">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c664c-166">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="c664c-167">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="c664c-167">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="c664c-168">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="c664c-168">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="c664c-169">\<Method>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="c664c-169">\<Method> Element</span></span>](method-element-net-native.md)
