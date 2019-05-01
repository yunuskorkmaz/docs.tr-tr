---
title: <MethodInstantiation> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae15e6d61267feb0388170ee27dcd939035329b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61867087"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="a4a9d-102">\<Methodınstantiation > öğesi (.NET yerel)</span><span class="sxs-lookup"><span data-stu-id="a4a9d-102">\<MethodInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="a4a9d-103">Çalışma zamanı yansıma ilkesini oluşturulmuş bir genel yöntem için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4a9d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4a9d-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4a9d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4a9d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a4a9d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4a9d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a4a9d-107">Attributes</span></span>  
  
|<span data-ttu-id="a4a9d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a4a9d-108">Attribute</span></span>|<span data-ttu-id="a4a9d-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="a4a9d-109">Attribute type</span></span>|<span data-ttu-id="a4a9d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4a9d-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="a4a9d-111">Genel</span><span class="sxs-lookup"><span data-stu-id="a4a9d-111">General</span></span>|<span data-ttu-id="a4a9d-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-112">Required attribute.</span></span> <span data-ttu-id="a4a9d-113">Yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="a4a9d-114">Genel</span><span class="sxs-lookup"><span data-stu-id="a4a9d-114">General</span></span>|<span data-ttu-id="a4a9d-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-115">Optional attribute.</span></span> <span data-ttu-id="a4a9d-116">Yönteminin adlandırılmış parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="a4a9d-117">Birden fazla adlandırılmış parametreler virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="a4a9d-118">`Signature` Özniteliği, aşırı yüklenmiş yöntemler ayırt etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="a4a9d-119">Genel</span><span class="sxs-lookup"><span data-stu-id="a4a9d-119">General</span></span>|<span data-ttu-id="a4a9d-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-120">Required attribute.</span></span> <span data-ttu-id="a4a9d-121">Genel tür bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="a4a9d-122">Birden çok bağımsız değişkeni varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="a4a9d-123">Yansıma</span><span class="sxs-lookup"><span data-stu-id="a4a9d-123">Reflection</span></span>|<span data-ttu-id="a4a9d-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-124">Optional attribute.</span></span> <span data-ttu-id="a4a9d-125">Hakkında bilgi için sorgulama veya bir yöntem numaralandırma kontrol eder, ancak herhangi bir dinamik çağrı çalışma zamanında etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="a4a9d-126">Yansıma</span><span class="sxs-lookup"><span data-stu-id="a4a9d-126">Reflection</span></span>|<span data-ttu-id="a4a9d-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-127">Optional attribute.</span></span> <span data-ttu-id="a4a9d-128">Programlama. bir oluşturucu veya dinamik olarak etkinleştirme yöntemi çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="a4a9d-129">Bu ilke, çalışma zamanında dinamik olarak çağrılabilir üyesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="a4a9d-130">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="a4a9d-130">Name attribute</span></span>  
  
|<span data-ttu-id="a4a9d-131">Değer</span><span class="sxs-lookup"><span data-stu-id="a4a9d-131">Value</span></span>|<span data-ttu-id="a4a9d-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4a9d-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4a9d-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="a4a9d-133">*method_name*</span></span>|<span data-ttu-id="a4a9d-134">Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-134">The method name.</span></span> <span data-ttu-id="a4a9d-135">Yöntem türü üst öğe tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="a4a9d-136">İmza özniteliği</span><span class="sxs-lookup"><span data-stu-id="a4a9d-136">Signature attribute</span></span>  
  
|<span data-ttu-id="a4a9d-137">Değer</span><span class="sxs-lookup"><span data-stu-id="a4a9d-137">Value</span></span>|<span data-ttu-id="a4a9d-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4a9d-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4a9d-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="a4a9d-139">*method_signature*</span></span>|<span data-ttu-id="a4a9d-140">Yönteminin adlandırılmış parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="a4a9d-141">Birden çok parametre varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="a4a9d-142">Bağımsız değişkenler özniteliği</span><span class="sxs-lookup"><span data-stu-id="a4a9d-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="a4a9d-143">Değer</span><span class="sxs-lookup"><span data-stu-id="a4a9d-143">Value</span></span>|<span data-ttu-id="a4a9d-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4a9d-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4a9d-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="a4a9d-145">*method_arguments*</span></span>|<span data-ttu-id="a4a9d-146">Genel tür bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="a4a9d-147">Birden çok bağımsız değişkeni varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="a4a9d-148">Her bağımsız değişken tam olarak nitelenmiş tür adını oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="a4a9d-149">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a4a9d-149">All other attributes</span></span>  
  
|<span data-ttu-id="a4a9d-150">Değer</span><span class="sxs-lookup"><span data-stu-id="a4a9d-150">Value</span></span>|<span data-ttu-id="a4a9d-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4a9d-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4a9d-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="a4a9d-152">*policy_setting*</span></span>|<span data-ttu-id="a4a9d-153">Bu ilke türü yöntemi için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="a4a9d-154">Olası değerler `Auto`, `Excluded`, `Included`, ve `Required`.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="a4a9d-155">Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a4a9d-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4a9d-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4a9d-156">Child Elements</span></span>  
 <span data-ttu-id="a4a9d-157">Yok.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4a9d-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4a9d-158">Parent Elements</span></span>  
  
|<span data-ttu-id="a4a9d-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="a4a9d-159">Element</span></span>|<span data-ttu-id="a4a9d-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4a9d-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4a9d-161">\<türü ></span><span class="sxs-lookup"><span data-stu-id="a4a9d-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="a4a9d-162">Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="a4a9d-163">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="a4a9d-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="a4a9d-164">Yansıma ilkesini, oluşturulmuş bir genel türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4a9d-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4a9d-165">Remarks</span></span>  
 <span data-ttu-id="a4a9d-166">`<MethodInstantiation>` Öğesini karşılık gelen, açık genel yöntem, çalışma zamanı yansıma ilkesini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a9d-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4a9d-167">See also</span></span>

- [<span data-ttu-id="a4a9d-168">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a4a9d-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="a4a9d-169">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="a4a9d-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="a4a9d-170">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="a4a9d-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="a4a9d-171">\<Yöntem > öğesi</span><span class="sxs-lookup"><span data-stu-id="a4a9d-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
