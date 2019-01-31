---
title: <MethodInstantiation> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccc8cd22c3175a2b6456f71d9dc773ce85848949
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275074"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="c4da7-102">\<Methodınstantiation > öğesi (.NET yerel)</span><span class="sxs-lookup"><span data-stu-id="c4da7-102">\<MethodInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="c4da7-103">Çalışma zamanı yansıma ilkesini oluşturulmuş bir genel yöntem için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c4da7-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4da7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4da7-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4da7-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4da7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c4da7-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4da7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4da7-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c4da7-107">Attributes</span></span>  
  
|<span data-ttu-id="c4da7-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c4da7-108">Attribute</span></span>|<span data-ttu-id="c4da7-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="c4da7-109">Attribute type</span></span>|<span data-ttu-id="c4da7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4da7-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="c4da7-111">Genel</span><span class="sxs-lookup"><span data-stu-id="c4da7-111">General</span></span>|<span data-ttu-id="c4da7-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c4da7-112">Required attribute.</span></span> <span data-ttu-id="c4da7-113">Yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4da7-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="c4da7-114">Genel</span><span class="sxs-lookup"><span data-stu-id="c4da7-114">General</span></span>|<span data-ttu-id="c4da7-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c4da7-115">Optional attribute.</span></span> <span data-ttu-id="c4da7-116">Yönteminin adlandırılmış parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4da7-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="c4da7-117">Birden fazla adlandırılmış parametreler virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c4da7-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="c4da7-118">`Signature` Özniteliği, aşırı yüklenmiş yöntemler ayırt etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4da7-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="c4da7-119">Genel</span><span class="sxs-lookup"><span data-stu-id="c4da7-119">General</span></span>|<span data-ttu-id="c4da7-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c4da7-120">Required attribute.</span></span> <span data-ttu-id="c4da7-121">Genel tür bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4da7-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="c4da7-122">Birden çok bağımsız değişkeni varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c4da7-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="c4da7-123">Yansıma</span><span class="sxs-lookup"><span data-stu-id="c4da7-123">Reflection</span></span>|<span data-ttu-id="c4da7-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c4da7-124">Optional attribute.</span></span> <span data-ttu-id="c4da7-125">Hakkında bilgi için sorgulama veya bir yöntem numaralandırma kontrol eder, ancak herhangi bir dinamik çağrı çalışma zamanında etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="c4da7-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="c4da7-126">Yansıma</span><span class="sxs-lookup"><span data-stu-id="c4da7-126">Reflection</span></span>|<span data-ttu-id="c4da7-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c4da7-127">Optional attribute.</span></span> <span data-ttu-id="c4da7-128">Programlama. bir oluşturucu veya dinamik olarak etkinleştirme yöntemi çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="c4da7-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="c4da7-129">Bu ilke, çalışma zamanında dinamik olarak çağrılabilir üyesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4da7-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="c4da7-130">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="c4da7-130">Name attribute</span></span>  
  
|<span data-ttu-id="c4da7-131">Değer</span><span class="sxs-lookup"><span data-stu-id="c4da7-131">Value</span></span>|<span data-ttu-id="c4da7-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4da7-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c4da7-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="c4da7-133">*method_name*</span></span>|<span data-ttu-id="c4da7-134">Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="c4da7-134">The method name.</span></span> <span data-ttu-id="c4da7-135">Yöntem türü üst öğe tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="c4da7-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="c4da7-136">İmza özniteliği</span><span class="sxs-lookup"><span data-stu-id="c4da7-136">Signature attribute</span></span>  
  
|<span data-ttu-id="c4da7-137">Değer</span><span class="sxs-lookup"><span data-stu-id="c4da7-137">Value</span></span>|<span data-ttu-id="c4da7-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4da7-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c4da7-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="c4da7-139">*method_signature*</span></span>|<span data-ttu-id="c4da7-140">Yönteminin adlandırılmış parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4da7-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="c4da7-141">Birden çok parametre varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c4da7-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="c4da7-142">Bağımsız değişkenler özniteliği</span><span class="sxs-lookup"><span data-stu-id="c4da7-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="c4da7-143">Değer</span><span class="sxs-lookup"><span data-stu-id="c4da7-143">Value</span></span>|<span data-ttu-id="c4da7-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4da7-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c4da7-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="c4da7-145">*method_arguments*</span></span>|<span data-ttu-id="c4da7-146">Genel tür bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4da7-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="c4da7-147">Birden çok bağımsız değişkeni varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c4da7-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="c4da7-148">Her bağımsız değişken tam olarak nitelenmiş tür adını oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4da7-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="c4da7-149">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c4da7-149">All other attributes</span></span>  
  
|<span data-ttu-id="c4da7-150">Değer</span><span class="sxs-lookup"><span data-stu-id="c4da7-150">Value</span></span>|<span data-ttu-id="c4da7-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4da7-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c4da7-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="c4da7-152">*policy_setting*</span></span>|<span data-ttu-id="c4da7-153">Bu ilke türü yöntemi için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="c4da7-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="c4da7-154">Olası değerler `Auto`, `Excluded`, `Included`, ve `Required`.</span><span class="sxs-lookup"><span data-stu-id="c4da7-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="c4da7-155">Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="c4da7-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4da7-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4da7-156">Child Elements</span></span>  
 <span data-ttu-id="c4da7-157">Yok.</span><span class="sxs-lookup"><span data-stu-id="c4da7-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4da7-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4da7-158">Parent Elements</span></span>  
  
|<span data-ttu-id="c4da7-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="c4da7-159">Element</span></span>|<span data-ttu-id="c4da7-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4da7-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4da7-161">\<türü ></span><span class="sxs-lookup"><span data-stu-id="c4da7-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="c4da7-162">Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c4da7-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="c4da7-163">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="c4da7-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="c4da7-164">Yansıma ilkesini, oluşturulmuş bir genel türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c4da7-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4da7-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4da7-165">Remarks</span></span>  
 <span data-ttu-id="c4da7-166">`<MethodInstantiation>` Öğesini karşılık gelen, açık genel yöntem, çalışma zamanı yansıma ilkesini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c4da7-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4da7-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4da7-167">See also</span></span>
- [<span data-ttu-id="c4da7-168">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c4da7-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="c4da7-169">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="c4da7-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="c4da7-170">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="c4da7-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="c4da7-171">\<Yöntem > öğesi</span><span class="sxs-lookup"><span data-stu-id="c4da7-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
