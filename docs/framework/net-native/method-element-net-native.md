---
title: <Method>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 8db32c660846b4f4071fff2a40c760a3d1ef2489
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180985"
---
# <a name="method-element-net-native"></a><span data-ttu-id="62391-102">\<Method>Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="62391-102">\<Method> Element (.NET Native)</span></span>
<span data-ttu-id="62391-103">Çalışma zamanı yansıtma ilkesini bir oluşturucuya veya yöntemine uygular.</span><span class="sxs-lookup"><span data-stu-id="62391-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62391-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62391-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62391-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="62391-105">Attributes and Elements</span></span>  
 <span data-ttu-id="62391-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="62391-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62391-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="62391-107">Attributes</span></span>  
  
|<span data-ttu-id="62391-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="62391-108">Attribute</span></span>|<span data-ttu-id="62391-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="62391-109">Attribute type</span></span>|<span data-ttu-id="62391-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62391-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="62391-111">Genel</span><span class="sxs-lookup"><span data-stu-id="62391-111">General</span></span>|<span data-ttu-id="62391-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="62391-112">Required attribute.</span></span> <span data-ttu-id="62391-113">Yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="62391-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="62391-114">Genel</span><span class="sxs-lookup"><span data-stu-id="62391-114">General</span></span>|<span data-ttu-id="62391-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="62391-115">Optional attribute.</span></span> <span data-ttu-id="62391-116">Yöntem imzasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="62391-116">Specifies the method signature.</span></span> <span data-ttu-id="62391-117">Birden çok parametre varsa, bunlar virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="62391-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="62391-118">Örneğin, aşağıdaki `<Method>` öğe yöntemi için ilkeyi tanımlar <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> .</span><span class="sxs-lookup"><span data-stu-id="62391-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="62391-119">Öznitelik yoksa, çalışma zamanı yönergesi metodun tüm aşırı yüklemeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="62391-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="62391-120">Yansıma</span><span class="sxs-lookup"><span data-stu-id="62391-120">Reflection</span></span>|<span data-ttu-id="62391-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="62391-121">Optional attribute.</span></span> <span data-ttu-id="62391-122">Bir yöntem hakkında bilgi sorgulama veya bir yöntemi numaralandırma, ancak çalışma zamanında dinamik çağırma etkinleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="62391-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="62391-123">Yansıma</span><span class="sxs-lookup"><span data-stu-id="62391-123">Reflection</span></span>|<span data-ttu-id="62391-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="62391-124">Optional attribute.</span></span> <span data-ttu-id="62391-125">Dinamik programlamayı etkinleştirmek için bir oluşturucuya veya yönteme çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="62391-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="62391-126">Bu ilke, bir üyenin çalışma zamanında dinamik olarak çağrılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="62391-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="62391-127">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="62391-127">Name attribute</span></span>  
  
|<span data-ttu-id="62391-128">Değer</span><span class="sxs-lookup"><span data-stu-id="62391-128">Value</span></span>|<span data-ttu-id="62391-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62391-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="62391-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="62391-130">*method_name*</span></span>|<span data-ttu-id="62391-131">Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="62391-131">The method name.</span></span> <span data-ttu-id="62391-132">Metodun türü üst [\<Type>](type-element-net-native.md) veya öğe tarafından tanımlanır [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="62391-132">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="62391-133">Signature özniteliği</span><span class="sxs-lookup"><span data-stu-id="62391-133">Signature attribute</span></span>  
  
|<span data-ttu-id="62391-134">Değer</span><span class="sxs-lookup"><span data-stu-id="62391-134">Value</span></span>|<span data-ttu-id="62391-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62391-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="62391-136">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="62391-136">*method_signature*</span></span>|<span data-ttu-id="62391-137">Yöntem imzasını oluşturan parametre türleri.</span><span class="sxs-lookup"><span data-stu-id="62391-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="62391-138">Birden çok parametre virgüllerle ayrılır, örneğin, `"System.String,System.Int32,System.Int32)"` .</span><span class="sxs-lookup"><span data-stu-id="62391-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="62391-139">Parametre türü adları tam olarak nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="62391-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="62391-140">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="62391-140">All other attributes</span></span>  
  
|<span data-ttu-id="62391-141">Değer</span><span class="sxs-lookup"><span data-stu-id="62391-141">Value</span></span>|<span data-ttu-id="62391-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62391-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="62391-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="62391-143">*policy_setting*</span></span>|<span data-ttu-id="62391-144">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="62391-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="62391-145">Olası değerler şunlardır,, `Auto` `Excluded` `Included` ve `Required` .</span><span class="sxs-lookup"><span data-stu-id="62391-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="62391-146">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="62391-146">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62391-147">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="62391-147">Child Elements</span></span>  
  
|<span data-ttu-id="62391-148">Öğe</span><span class="sxs-lookup"><span data-stu-id="62391-148">Element</span></span>|<span data-ttu-id="62391-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62391-149">Description</span></span>|  
|-------------|-----------------|  
|[\<Parameter>](parameter-element-net-native.md)|<span data-ttu-id="62391-150">Bir yönteme geçirilen bağımsız değişkenin türüne ilke uygular.</span><span class="sxs-lookup"><span data-stu-id="62391-150">Applies policy to the type of the argument passed to a method.</span></span>|  
|[\<GenericParameter>](genericparameter-element-net-native.md)|<span data-ttu-id="62391-151">İlkeyi genel bir türün veya yöntemin parametre türüne uygular.</span><span class="sxs-lookup"><span data-stu-id="62391-151">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="62391-152">İlke, kapsayan öğe tarafından temsil edilen yönteme uygulanmışsa, ilkeyi bir türe uygular `<Method>` .</span><span class="sxs-lookup"><span data-stu-id="62391-152">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[\<TypeParameter>](typeparameter-element-net-native.md)|<span data-ttu-id="62391-153"><xref:System.Type>Bir yönteme geçirilen bağımsız değişkenle temsil edilen türe ilke uygular.</span><span class="sxs-lookup"><span data-stu-id="62391-153">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62391-154">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="62391-154">Parent Elements</span></span>  
  
|<span data-ttu-id="62391-155">Öğe</span><span class="sxs-lookup"><span data-stu-id="62391-155">Element</span></span>|<span data-ttu-id="62391-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62391-156">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="62391-157">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="62391-157">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="62391-158">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="62391-158">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62391-159">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62391-159">Remarks</span></span>  
 <span data-ttu-id="62391-160">`<Method>`Genel yöntemin bir öğesi, kendi ilkesi olmayan tüm örneklemelerde ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="62391-160">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="62391-161">`Signature`Belirli bir yöntem aşırı yüklemesi için ilkeyi belirtmek üzere özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62391-161">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="62391-162">Aksi halde, `Signature` özniteliği yoksa, çalışma zamanı yönergesi metodun tüm aşırı yüklemeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="62391-162">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="62391-163">Öğesini kullanarak bir Oluşturucu için çalışma zamanı yansıtma ilkesini tanımlayamazsınız `<Method>` .</span><span class="sxs-lookup"><span data-stu-id="62391-163">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="62391-164">Bunun yerine,,, `Activate` [\<Assembly>](assembly-element-net-native.md) [\<Namespace>](namespace-element-net-native.md) [\<Type>](type-element-net-native.md) veya öğesinin özniteliğini kullanın [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="62391-164">Instead, use the `Activate` attribute of the  [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), [\<Type>](type-element-net-native.md), or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62391-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="62391-165">Example</span></span>  
 <span data-ttu-id="62391-166">`Stringify`Aşağıdaki örnekteki yöntem, bir nesneyi dize gösterimine dönüştürmek için yansıma kullanan genel amaçlı bir biçimlendirme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="62391-166">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="62391-167">Nesnenin varsayılan metodunu çağırmanın yanı sıra `ToString` , yöntemi bir nesnenin `ToString` yöntemini bir biçim dizesi, bir <xref:System.IFormatProvider> uygulama veya her ikisi geçirerek, biçimlendirilen bir sonuç dizesi üretebilir.</span><span class="sxs-lookup"><span data-stu-id="62391-167">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="62391-168">Ayrıca <xref:System.Convert.ToString%2A?displayProperty=nameWithType> , bir sayıyı ikili, onaltılı veya sekizli gösterimine dönüştüren aşırı yüklemelerin birini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="62391-168">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="62391-169">`Stringify`Yöntemi, aşağıdaki gibi kodla çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="62391-169">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="62391-170">Ancak, .NET Native ile derlendiğinde, örnek çalışma zamanında, <xref:System.NullReferenceException> ve [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumları dahil olmak üzere bir dizi özel durum oluşturabilir, bu durum, `Stringify` yöntemin öncelikle .NET Framework sınıf kitaplığındaki temel türleri dinamik olarak biçimlendirmeyi desteklemesi amaçlanan için oluşur.</span><span class="sxs-lookup"><span data-stu-id="62391-170">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="62391-171">Ancak, meta verileri varsayılan yönergeler dosyası tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="62391-171">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="62391-172">Ancak meta verileri kullanılabilir duruma getirilse de, uygun uygulamalar yerel koda dahil olmadığından, örnek [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumları oluşturur `ToString` .</span><span class="sxs-lookup"><span data-stu-id="62391-172">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="62391-173">Bu özel durumlar [\<Type>](type-element-net-native.md) , meta verileri bulunması gereken türleri tanımlamak için öğesini kullanarak ve `<Method>` dinamik olarak çağrılabilen yöntem aşırı yüklemelerinin uygulanmasını sağlamak için öğe ekleyerek ortadan kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="62391-173">These exceptions can all be eliminated by using the [\<Type>](type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="62391-174">Aşağıda, bu özel durumları ortadan kaldıran ve örneğin hatasız yürütülmesine izin veren default. RD. xml dosyası verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="62391-174">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="62391-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62391-175">See also</span></span>

- [<span data-ttu-id="62391-176">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="62391-176">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="62391-177">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="62391-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="62391-178">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="62391-178">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="62391-179">\<MethodInstantiation>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="62391-179">\<MethodInstantiation> Element</span></span>](methodinstantiation-element-net-native.md)
