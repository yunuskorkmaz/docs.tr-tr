---
title: <Method>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d741f51abf02f4bfda2b007efd4c859027e54d9b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049586"
---
# <a name="method-element-net-native"></a><span data-ttu-id="55229-102">\<Metot > öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="55229-102">\<Method> Element (.NET Native)</span></span>
<span data-ttu-id="55229-103">Çalışma zamanı yansıtma ilkesini bir oluşturucuya veya yöntemine uygular.</span><span class="sxs-lookup"><span data-stu-id="55229-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55229-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55229-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55229-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55229-105">Attributes and Elements</span></span>  
 <span data-ttu-id="55229-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55229-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55229-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55229-107">Attributes</span></span>  
  
|<span data-ttu-id="55229-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55229-108">Attribute</span></span>|<span data-ttu-id="55229-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="55229-109">Attribute type</span></span>|<span data-ttu-id="55229-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55229-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="55229-111">Genel</span><span class="sxs-lookup"><span data-stu-id="55229-111">General</span></span>|<span data-ttu-id="55229-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="55229-112">Required attribute.</span></span> <span data-ttu-id="55229-113">Yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="55229-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="55229-114">Genel</span><span class="sxs-lookup"><span data-stu-id="55229-114">General</span></span>|<span data-ttu-id="55229-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="55229-115">Optional attribute.</span></span> <span data-ttu-id="55229-116">Yöntem imzasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="55229-116">Specifies the method signature.</span></span> <span data-ttu-id="55229-117">Birden çok parametre varsa, bunlar virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="55229-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="55229-118">Örneğin, aşağıdaki `<Method>` öğe <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemi için ilkeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="55229-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="55229-119">Öznitelik yoksa, çalışma zamanı yönergesi metodun tüm aşırı yüklemeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="55229-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="55229-120">Yansıma</span><span class="sxs-lookup"><span data-stu-id="55229-120">Reflection</span></span>|<span data-ttu-id="55229-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="55229-121">Optional attribute.</span></span> <span data-ttu-id="55229-122">Bir yöntem hakkında bilgi sorgulama veya bir yöntemi numaralandırma, ancak çalışma zamanında dinamik çağırma etkinleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="55229-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="55229-123">Yansıma</span><span class="sxs-lookup"><span data-stu-id="55229-123">Reflection</span></span>|<span data-ttu-id="55229-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="55229-124">Optional attribute.</span></span> <span data-ttu-id="55229-125">Dinamik programlamayı etkinleştirmek için bir oluşturucuya veya yönteme çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="55229-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="55229-126">Bu ilke, bir üyenin çalışma zamanında dinamik olarak çağrılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="55229-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="55229-127">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="55229-127">Name attribute</span></span>  
  
|<span data-ttu-id="55229-128">Değer</span><span class="sxs-lookup"><span data-stu-id="55229-128">Value</span></span>|<span data-ttu-id="55229-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55229-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="55229-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="55229-130">*method_name*</span></span>|<span data-ttu-id="55229-131">Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="55229-131">The method name.</span></span> <span data-ttu-id="55229-132">Metodun türü, üst [ \<tür >](type-element-net-native.md) veya [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="55229-132">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="55229-133">Signature özniteliği</span><span class="sxs-lookup"><span data-stu-id="55229-133">Signature attribute</span></span>  
  
|<span data-ttu-id="55229-134">Değer</span><span class="sxs-lookup"><span data-stu-id="55229-134">Value</span></span>|<span data-ttu-id="55229-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55229-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="55229-136">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="55229-136">*method_signature*</span></span>|<span data-ttu-id="55229-137">Yöntem imzasını oluşturan parametre türleri.</span><span class="sxs-lookup"><span data-stu-id="55229-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="55229-138">Birden çok parametre virgüllerle ayrılır, örneğin, `"System.String,System.Int32,System.Int32)"`.</span><span class="sxs-lookup"><span data-stu-id="55229-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="55229-139">Parametre türü adları tam olarak nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="55229-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="55229-140">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55229-140">All other attributes</span></span>  
  
|<span data-ttu-id="55229-141">Değer</span><span class="sxs-lookup"><span data-stu-id="55229-141">Value</span></span>|<span data-ttu-id="55229-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55229-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="55229-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="55229-143">*policy_setting*</span></span>|<span data-ttu-id="55229-144">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="55229-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="55229-145">Olası değerler şunlardır `Auto` `Excluded` `Required`, ,ve.`Included`</span><span class="sxs-lookup"><span data-stu-id="55229-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="55229-146">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="55229-146">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55229-147">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55229-147">Child Elements</span></span>  
  
|<span data-ttu-id="55229-148">Öğe</span><span class="sxs-lookup"><span data-stu-id="55229-148">Element</span></span>|<span data-ttu-id="55229-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55229-149">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55229-150">\<Parametre ></span><span class="sxs-lookup"><span data-stu-id="55229-150">\<Parameter></span></span>](parameter-element-net-native.md)|<span data-ttu-id="55229-151">Bir yönteme geçirilen bağımsız değişkenin türüne ilke uygular.</span><span class="sxs-lookup"><span data-stu-id="55229-151">Applies policy to the type of the argument passed to a method.</span></span>|  
|[<span data-ttu-id="55229-152">\<GenericParameter ></span><span class="sxs-lookup"><span data-stu-id="55229-152">\<GenericParameter></span></span>](genericparameter-element-net-native.md)|<span data-ttu-id="55229-153">İlkeyi genel bir türün veya yöntemin parametre türüne uygular.</span><span class="sxs-lookup"><span data-stu-id="55229-153">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[<span data-ttu-id="55229-154">\<Impliestype ></span><span class="sxs-lookup"><span data-stu-id="55229-154">\<ImpliesType></span></span>](impliestype-element-net-native.md)|<span data-ttu-id="55229-155">İlke, kapsayan `<Method>` öğe tarafından temsil edilen yönteme uygulanmışsa, ilkeyi bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="55229-155">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[<span data-ttu-id="55229-156">\<TypeParameter ></span><span class="sxs-lookup"><span data-stu-id="55229-156">\<TypeParameter></span></span>](typeparameter-element-net-native.md)|<span data-ttu-id="55229-157">Bir yönteme geçirilen <xref:System.Type> bağımsız değişkenle temsil edilen türe ilke uygular.</span><span class="sxs-lookup"><span data-stu-id="55229-157">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="55229-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55229-158">Parent Elements</span></span>  
  
|<span data-ttu-id="55229-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="55229-159">Element</span></span>|<span data-ttu-id="55229-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55229-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55229-161">\<Tür ></span><span class="sxs-lookup"><span data-stu-id="55229-161">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="55229-162">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="55229-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="55229-163">\<Typeörneklemesi ></span><span class="sxs-lookup"><span data-stu-id="55229-163">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="55229-164">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="55229-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55229-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55229-165">Remarks</span></span>  
 <span data-ttu-id="55229-166">Genel `<Method>` yöntemin bir öğesi, kendi ilkesi olmayan tüm örneklemelerde ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="55229-166">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="55229-167">Belirli bir yöntem aşırı `Signature` yüklemesi için ilkeyi belirtmek üzere özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55229-167">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="55229-168">Aksi halde, özniteliği yoksa, çalışma zamanı yönergesi metodun tüm aşırı yüklemeleri için geçerlidir. `Signature`</span><span class="sxs-lookup"><span data-stu-id="55229-168">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="55229-169">`<Method>` Öğesini kullanarak bir Oluşturucu için çalışma zamanı yansıtma ilkesini tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="55229-169">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="55229-170">`Activate` Bunun yerine, [ \<derleme >](assembly-element-net-native.md), [ \<ad alanı >](namespace-element-net-native.md), [ \<tür >](type-element-net-native.md)veya [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğesi özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="55229-170">Instead, use the `Activate` attribute of the  [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), [\<Type>](type-element-net-native.md), or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55229-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="55229-171">Example</span></span>  
 <span data-ttu-id="55229-172">Aşağıdaki `Stringify` örnekteki yöntem, bir nesneyi dize gösterimine dönüştürmek için yansıma kullanan genel amaçlı bir biçimlendirme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="55229-172">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="55229-173">Nesnenin varsayılan `ToString` metodunu çağırmanın yanı sıra, yöntemi bir `ToString` nesnenin yöntemini bir biçim dizesi, bir <xref:System.IFormatProvider> uygulama veya her ikisi geçirerek, biçimlendirilen bir sonuç dizesi üretebilir.</span><span class="sxs-lookup"><span data-stu-id="55229-173">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="55229-174">Ayrıca, bir sayıyı ikili, onaltılı <xref:System.Convert.ToString%2A?displayProperty=nameWithType> veya sekizli gösterimine dönüştüren aşırı yüklemelerin birini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="55229-174">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="55229-175">`Stringify` Yöntemi, aşağıdaki gibi kodla çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="55229-175">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="55229-176">Ancak, .NET Native ile derlendiğinde, örnek, çalışma zamanında, ve [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumları dahil <xref:System.NullReferenceException> olmak üzere bir dizi özel durum oluşturabilir, `Stringify` bunun nedeni yöntemin öncelikle .NET Framework sınıf kitaplığındaki temel türleri dinamik olarak biçimlendirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="55229-176">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="55229-177">Ancak, meta verileri varsayılan yönergeler dosyası tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="55229-177">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="55229-178">Ancak meta verileri kullanılabilir duruma getirilse de, uygun `ToString` uygulamalar yerel koda dahil olmadığından, örnek [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="55229-178">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="55229-179">Bu özel durumlar, meta verileri bulunması gereken türleri tanımlamak için [ \<tür >](type-element-net-native.md) öğesi kullanılarak ve çağrılabilir yöntem aşırı yüklemelerinin uygulanmasını sağlamak için öğe ekleyerek `<Method>` ortadan kaldırılabilir. dinamik olarak da mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="55229-179">These exceptions can all be eliminated by using the [\<Type>](type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="55229-180">Aşağıda, bu özel durumları ortadan kaldıran ve örneğin hatasız yürütülmesine izin veren default. RD. xml dosyası verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="55229-180">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="55229-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55229-181">See also</span></span>

- [<span data-ttu-id="55229-182">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="55229-182">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="55229-183">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="55229-183">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="55229-184">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="55229-184">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="55229-185">\<Methodörneklemesi > öğesi</span><span class="sxs-lookup"><span data-stu-id="55229-185">\<MethodInstantiation> Element</span></span>](methodinstantiation-element-net-native.md)
