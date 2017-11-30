---
title: "&lt;MethodInstantiation&gt; Öğesi (.NET Yerel)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 37e3ff3e792b8067b6d9409d799cf6e30350606a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmethodinstantiationgt-element-net-native"></a><span data-ttu-id="10e0f-102">&lt;MethodInstantiation&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="10e0f-102">&lt;MethodInstantiation&gt; Element (.NET Native)</span></span>
<span data-ttu-id="10e0f-103">Çalışma zamanı yansıma İlkesi oluşturulan genel yöntem için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="10e0f-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10e0f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10e0f-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10e0f-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="10e0f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="10e0f-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10e0f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10e0f-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10e0f-107">Attributes</span></span>  
  
|<span data-ttu-id="10e0f-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="10e0f-108">Attribute</span></span>|<span data-ttu-id="10e0f-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="10e0f-109">Attribute type</span></span>|<span data-ttu-id="10e0f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10e0f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="10e0f-111">Genel</span><span class="sxs-lookup"><span data-stu-id="10e0f-111">General</span></span>|<span data-ttu-id="10e0f-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="10e0f-112">Required attribute.</span></span> <span data-ttu-id="10e0f-113">Yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="10e0f-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="10e0f-114">Genel</span><span class="sxs-lookup"><span data-stu-id="10e0f-114">General</span></span>|<span data-ttu-id="10e0f-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="10e0f-115">Optional attribute.</span></span> <span data-ttu-id="10e0f-116">Yönteminin adlandırılmış parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="10e0f-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="10e0f-117">Birden çok adlandırılmış parametreleri virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="10e0f-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="10e0f-118">`Signature` Özniteliği aşırı yüklenmiş yöntemler ayırt etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="10e0f-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="10e0f-119">Genel</span><span class="sxs-lookup"><span data-stu-id="10e0f-119">General</span></span>|<span data-ttu-id="10e0f-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="10e0f-120">Required attribute.</span></span> <span data-ttu-id="10e0f-121">Genel tür bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="10e0f-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="10e0f-122">Birden fazla bağımsız değişken varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="10e0f-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="10e0f-123">Yansıma</span><span class="sxs-lookup"><span data-stu-id="10e0f-123">Reflection</span></span>|<span data-ttu-id="10e0f-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="10e0f-124">Optional attribute.</span></span> <span data-ttu-id="10e0f-125">Hakkında bilgi için sorgulama veya bir yöntem numaralandırma kontrol eder, ancak çalışma zamanında dinamik herhangi çağırma etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="10e0f-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="10e0f-126">Yansıma</span><span class="sxs-lookup"><span data-stu-id="10e0f-126">Reflection</span></span>|<span data-ttu-id="10e0f-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="10e0f-127">Optional attribute.</span></span> <span data-ttu-id="10e0f-128">Programlama Oluşturucusu veya dinamik etkinleştirmek için yöntemi çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="10e0f-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="10e0f-129">Bu ilke üyesi çalışma zamanında dinamik olarak çağrılabilir sağlar.</span><span class="sxs-lookup"><span data-stu-id="10e0f-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="10e0f-130">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="10e0f-130">Name attribute</span></span>  
  
|<span data-ttu-id="10e0f-131">Değer</span><span class="sxs-lookup"><span data-stu-id="10e0f-131">Value</span></span>|<span data-ttu-id="10e0f-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10e0f-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10e0f-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="10e0f-133">*method_name*</span></span>|<span data-ttu-id="10e0f-134">Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="10e0f-134">The method name.</span></span> <span data-ttu-id="10e0f-135">Yöntem türü üst tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="10e0f-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="10e0f-136">İmza özniteliği</span><span class="sxs-lookup"><span data-stu-id="10e0f-136">Signature attribute</span></span>  
  
|<span data-ttu-id="10e0f-137">Değer</span><span class="sxs-lookup"><span data-stu-id="10e0f-137">Value</span></span>|<span data-ttu-id="10e0f-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10e0f-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10e0f-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="10e0f-139">*method_signature*</span></span>|<span data-ttu-id="10e0f-140">Yöntem adlandırılmış parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="10e0f-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="10e0f-141">Birden çok parametre varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="10e0f-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="10e0f-142">Bağımsız değişkenler özniteliği</span><span class="sxs-lookup"><span data-stu-id="10e0f-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="10e0f-143">Değer</span><span class="sxs-lookup"><span data-stu-id="10e0f-143">Value</span></span>|<span data-ttu-id="10e0f-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10e0f-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10e0f-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="10e0f-145">*method_arguments*</span></span>|<span data-ttu-id="10e0f-146">Genel tür bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="10e0f-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="10e0f-147">Birden fazla bağımsız değişken varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="10e0f-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="10e0f-148">Her bağımsız değişken tam olarak nitelenmiş tür adını oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="10e0f-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="10e0f-149">Tüm diğer özniteliklerle</span><span class="sxs-lookup"><span data-stu-id="10e0f-149">All other attributes</span></span>  
  
|<span data-ttu-id="10e0f-150">Değer</span><span class="sxs-lookup"><span data-stu-id="10e0f-150">Value</span></span>|<span data-ttu-id="10e0f-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10e0f-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10e0f-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="10e0f-152">*policy_setting*</span></span>|<span data-ttu-id="10e0f-153">Bu ilke türü yöntemi için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="10e0f-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="10e0f-154">Olası değerler şunlardır: `Auto`, `Excluded`, `Included`, ve `Required`.</span><span class="sxs-lookup"><span data-stu-id="10e0f-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="10e0f-155">Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="10e0f-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10e0f-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="10e0f-156">Child Elements</span></span>  
 <span data-ttu-id="10e0f-157">Yok.</span><span class="sxs-lookup"><span data-stu-id="10e0f-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10e0f-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="10e0f-158">Parent Elements</span></span>  
  
|<span data-ttu-id="10e0f-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="10e0f-159">Element</span></span>|<span data-ttu-id="10e0f-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10e0f-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10e0f-161">\<Türü ></span><span class="sxs-lookup"><span data-stu-id="10e0f-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="10e0f-162">Yansıma ilke türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="10e0f-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="10e0f-163">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="10e0f-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="10e0f-164">Yansıma İlkesi, yapılandırılmış bir genel tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="10e0f-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10e0f-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10e0f-165">Remarks</span></span>  
 <span data-ttu-id="10e0f-166">`<MethodInstantiation>` Öğesi kendi karşılık gelen açık genel yöntem çalışma zamanı yansıma ilkesini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="10e0f-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10e0f-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10e0f-167">See Also</span></span>  
 [<span data-ttu-id="10e0f-168">Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu</span><span class="sxs-lookup"><span data-stu-id="10e0f-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="10e0f-169">Çalışma zamanı yönerge öğeleri</span><span class="sxs-lookup"><span data-stu-id="10e0f-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="10e0f-170">Çalışma zamanı yönerge İlkesi ayarları</span><span class="sxs-lookup"><span data-stu-id="10e0f-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="10e0f-171">\<Yöntem > öğesi</span><span class="sxs-lookup"><span data-stu-id="10e0f-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
