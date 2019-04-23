---
title: <MethodInstantiation> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae15e6d61267feb0388170ee27dcd939035329b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121699"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="ce2e1-102">\<Methodınstantiation > öğesi (.NET yerel)</span><span class="sxs-lookup"><span data-stu-id="ce2e1-102">\<MethodInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="ce2e1-103">Çalışma zamanı yansıma ilkesini oluşturulmuş bir genel yöntem için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce2e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce2e1-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce2e1-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce2e1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ce2e1-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce2e1-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ce2e1-107">Attributes</span></span>  
  
|<span data-ttu-id="ce2e1-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ce2e1-108">Attribute</span></span>|<span data-ttu-id="ce2e1-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="ce2e1-109">Attribute type</span></span>|<span data-ttu-id="ce2e1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce2e1-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="ce2e1-111">Genel</span><span class="sxs-lookup"><span data-stu-id="ce2e1-111">General</span></span>|<span data-ttu-id="ce2e1-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-112">Required attribute.</span></span> <span data-ttu-id="ce2e1-113">Yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="ce2e1-114">Genel</span><span class="sxs-lookup"><span data-stu-id="ce2e1-114">General</span></span>|<span data-ttu-id="ce2e1-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-115">Optional attribute.</span></span> <span data-ttu-id="ce2e1-116">Yönteminin adlandırılmış parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="ce2e1-117">Birden fazla adlandırılmış parametreler virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="ce2e1-118">`Signature` Özniteliği, aşırı yüklenmiş yöntemler ayırt etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="ce2e1-119">Genel</span><span class="sxs-lookup"><span data-stu-id="ce2e1-119">General</span></span>|<span data-ttu-id="ce2e1-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-120">Required attribute.</span></span> <span data-ttu-id="ce2e1-121">Genel tür bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="ce2e1-122">Birden çok bağımsız değişkeni varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="ce2e1-123">Yansıma</span><span class="sxs-lookup"><span data-stu-id="ce2e1-123">Reflection</span></span>|<span data-ttu-id="ce2e1-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-124">Optional attribute.</span></span> <span data-ttu-id="ce2e1-125">Hakkında bilgi için sorgulama veya bir yöntem numaralandırma kontrol eder, ancak herhangi bir dinamik çağrı çalışma zamanında etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="ce2e1-126">Yansıma</span><span class="sxs-lookup"><span data-stu-id="ce2e1-126">Reflection</span></span>|<span data-ttu-id="ce2e1-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-127">Optional attribute.</span></span> <span data-ttu-id="ce2e1-128">Programlama. bir oluşturucu veya dinamik olarak etkinleştirme yöntemi çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="ce2e1-129">Bu ilke, çalışma zamanında dinamik olarak çağrılabilir üyesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="ce2e1-130">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="ce2e1-130">Name attribute</span></span>  
  
|<span data-ttu-id="ce2e1-131">Değer</span><span class="sxs-lookup"><span data-stu-id="ce2e1-131">Value</span></span>|<span data-ttu-id="ce2e1-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce2e1-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ce2e1-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="ce2e1-133">*method_name*</span></span>|<span data-ttu-id="ce2e1-134">Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-134">The method name.</span></span> <span data-ttu-id="ce2e1-135">Yöntem türü üst öğe tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="ce2e1-136">İmza özniteliği</span><span class="sxs-lookup"><span data-stu-id="ce2e1-136">Signature attribute</span></span>  
  
|<span data-ttu-id="ce2e1-137">Değer</span><span class="sxs-lookup"><span data-stu-id="ce2e1-137">Value</span></span>|<span data-ttu-id="ce2e1-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce2e1-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ce2e1-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="ce2e1-139">*method_signature*</span></span>|<span data-ttu-id="ce2e1-140">Yönteminin adlandırılmış parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="ce2e1-141">Birden çok parametre varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="ce2e1-142">Bağımsız değişkenler özniteliği</span><span class="sxs-lookup"><span data-stu-id="ce2e1-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="ce2e1-143">Değer</span><span class="sxs-lookup"><span data-stu-id="ce2e1-143">Value</span></span>|<span data-ttu-id="ce2e1-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce2e1-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ce2e1-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="ce2e1-145">*method_arguments*</span></span>|<span data-ttu-id="ce2e1-146">Genel tür bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="ce2e1-147">Birden çok bağımsız değişkeni varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="ce2e1-148">Her bağımsız değişken tam olarak nitelenmiş tür adını oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="ce2e1-149">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ce2e1-149">All other attributes</span></span>  
  
|<span data-ttu-id="ce2e1-150">Değer</span><span class="sxs-lookup"><span data-stu-id="ce2e1-150">Value</span></span>|<span data-ttu-id="ce2e1-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce2e1-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ce2e1-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="ce2e1-152">*policy_setting*</span></span>|<span data-ttu-id="ce2e1-153">Bu ilke türü yöntemi için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="ce2e1-154">Olası değerler `Auto`, `Excluded`, `Included`, ve `Required`.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="ce2e1-155">Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="ce2e1-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce2e1-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce2e1-156">Child Elements</span></span>  
 <span data-ttu-id="ce2e1-157">Yok.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce2e1-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce2e1-158">Parent Elements</span></span>  
  
|<span data-ttu-id="ce2e1-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="ce2e1-159">Element</span></span>|<span data-ttu-id="ce2e1-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce2e1-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce2e1-161">\<türü ></span><span class="sxs-lookup"><span data-stu-id="ce2e1-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="ce2e1-162">Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="ce2e1-163">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="ce2e1-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="ce2e1-164">Yansıma ilkesini, oluşturulmuş bir genel türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce2e1-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce2e1-165">Remarks</span></span>  
 <span data-ttu-id="ce2e1-166">`<MethodInstantiation>` Öğesini karşılık gelen, açık genel yöntem, çalışma zamanı yansıma ilkesini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce2e1-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce2e1-167">See also</span></span>

- [<span data-ttu-id="ce2e1-168">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ce2e1-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="ce2e1-169">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="ce2e1-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="ce2e1-170">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="ce2e1-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="ce2e1-171">\<Yöntem > öğesi</span><span class="sxs-lookup"><span data-stu-id="ce2e1-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
