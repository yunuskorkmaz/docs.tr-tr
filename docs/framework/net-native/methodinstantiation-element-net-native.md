---
title: '&lt;MethodInstantiation&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d741e8df8f2b8c6d90a1d867c73495a2ffd1304
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397799"
---
# <a name="ltmethodinstantiationgt-element-net-native"></a><span data-ttu-id="7174c-102">&lt;MethodInstantiation&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="7174c-102">&lt;MethodInstantiation&gt; Element (.NET Native)</span></span>
<span data-ttu-id="7174c-103">Çalışma zamanı yansıma İlkesi oluşturulan genel yöntem için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7174c-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7174c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7174c-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7174c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7174c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7174c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7174c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7174c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7174c-107">Attributes</span></span>  
  
|<span data-ttu-id="7174c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7174c-108">Attribute</span></span>|<span data-ttu-id="7174c-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="7174c-109">Attribute type</span></span>|<span data-ttu-id="7174c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7174c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="7174c-111">Genel</span><span class="sxs-lookup"><span data-stu-id="7174c-111">General</span></span>|<span data-ttu-id="7174c-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7174c-112">Required attribute.</span></span> <span data-ttu-id="7174c-113">Yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7174c-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="7174c-114">Genel</span><span class="sxs-lookup"><span data-stu-id="7174c-114">General</span></span>|<span data-ttu-id="7174c-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7174c-115">Optional attribute.</span></span> <span data-ttu-id="7174c-116">Yönteminin adlandırılmış parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7174c-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="7174c-117">Birden çok adlandırılmış parametreleri virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="7174c-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="7174c-118">`Signature` Özniteliği aşırı yüklenmiş yöntemler ayırt etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7174c-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="7174c-119">Genel</span><span class="sxs-lookup"><span data-stu-id="7174c-119">General</span></span>|<span data-ttu-id="7174c-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7174c-120">Required attribute.</span></span> <span data-ttu-id="7174c-121">Genel tür bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7174c-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="7174c-122">Birden fazla bağımsız değişken varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="7174c-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="7174c-123">Yansıma</span><span class="sxs-lookup"><span data-stu-id="7174c-123">Reflection</span></span>|<span data-ttu-id="7174c-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7174c-124">Optional attribute.</span></span> <span data-ttu-id="7174c-125">Hakkında bilgi için sorgulama veya bir yöntem numaralandırma kontrol eder, ancak çalışma zamanında dinamik herhangi çağırma etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="7174c-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="7174c-126">Yansıma</span><span class="sxs-lookup"><span data-stu-id="7174c-126">Reflection</span></span>|<span data-ttu-id="7174c-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7174c-127">Optional attribute.</span></span> <span data-ttu-id="7174c-128">Programlama Oluşturucusu veya dinamik etkinleştirmek için yöntemi çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="7174c-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="7174c-129">Bu ilke üyesi çalışma zamanında dinamik olarak çağrılabilir sağlar.</span><span class="sxs-lookup"><span data-stu-id="7174c-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="7174c-130">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="7174c-130">Name attribute</span></span>  
  
|<span data-ttu-id="7174c-131">Değer</span><span class="sxs-lookup"><span data-stu-id="7174c-131">Value</span></span>|<span data-ttu-id="7174c-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7174c-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7174c-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="7174c-133">*method_name*</span></span>|<span data-ttu-id="7174c-134">Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="7174c-134">The method name.</span></span> <span data-ttu-id="7174c-135">Yöntem türü üst tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="7174c-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="7174c-136">İmza özniteliği</span><span class="sxs-lookup"><span data-stu-id="7174c-136">Signature attribute</span></span>  
  
|<span data-ttu-id="7174c-137">Değer</span><span class="sxs-lookup"><span data-stu-id="7174c-137">Value</span></span>|<span data-ttu-id="7174c-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7174c-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7174c-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="7174c-139">*method_signature*</span></span>|<span data-ttu-id="7174c-140">Yöntem adlandırılmış parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7174c-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="7174c-141">Birden çok parametre varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="7174c-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="7174c-142">Bağımsız değişkenler özniteliği</span><span class="sxs-lookup"><span data-stu-id="7174c-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="7174c-143">Değer</span><span class="sxs-lookup"><span data-stu-id="7174c-143">Value</span></span>|<span data-ttu-id="7174c-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7174c-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7174c-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="7174c-145">*method_arguments*</span></span>|<span data-ttu-id="7174c-146">Genel tür bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7174c-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="7174c-147">Birden fazla bağımsız değişken varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="7174c-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="7174c-148">Her bağımsız değişken tam olarak nitelenmiş tür adını oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7174c-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="7174c-149">Tüm diğer özniteliklerle</span><span class="sxs-lookup"><span data-stu-id="7174c-149">All other attributes</span></span>  
  
|<span data-ttu-id="7174c-150">Değer</span><span class="sxs-lookup"><span data-stu-id="7174c-150">Value</span></span>|<span data-ttu-id="7174c-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7174c-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7174c-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="7174c-152">*policy_setting*</span></span>|<span data-ttu-id="7174c-153">Bu ilke türü yöntemi için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="7174c-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="7174c-154">Olası değerler şunlardır: `Auto`, `Excluded`, `Included`, ve `Required`.</span><span class="sxs-lookup"><span data-stu-id="7174c-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="7174c-155">Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="7174c-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7174c-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7174c-156">Child Elements</span></span>  
 <span data-ttu-id="7174c-157">Yok.</span><span class="sxs-lookup"><span data-stu-id="7174c-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7174c-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7174c-158">Parent Elements</span></span>  
  
|<span data-ttu-id="7174c-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="7174c-159">Element</span></span>|<span data-ttu-id="7174c-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7174c-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7174c-161">\<türü ></span><span class="sxs-lookup"><span data-stu-id="7174c-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="7174c-162">Yansıma ilke türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7174c-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="7174c-163">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="7174c-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="7174c-164">Yansıma İlkesi, yapılandırılmış bir genel tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7174c-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7174c-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7174c-165">Remarks</span></span>  
 <span data-ttu-id="7174c-166">`<MethodInstantiation>` Öğesi kendi karşılık gelen açık genel yöntem çalışma zamanı yansıma ilkesini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="7174c-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7174c-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7174c-167">See Also</span></span>  
 [<span data-ttu-id="7174c-168">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7174c-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="7174c-169">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="7174c-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="7174c-170">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="7174c-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="7174c-171">\<Yöntem > öğesi</span><span class="sxs-lookup"><span data-stu-id="7174c-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
