---
title: "&lt;Method&gt; Öğesi (.NET Yerel)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 74aa7a683c8cf4c5ec61dc48ead3ed0f5a780cd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmethodgt-element-net-native"></a><span data-ttu-id="cb932-102">&lt;Method&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="cb932-102">&lt;Method&gt; Element (.NET Native)</span></span>
<span data-ttu-id="cb932-103">Çalışma zamanı yansıma ilke oluşturucunun ya da yöntemi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cb932-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb932-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb932-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb932-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb932-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cb932-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb932-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb932-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cb932-107">Attributes</span></span>  
  
|<span data-ttu-id="cb932-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cb932-108">Attribute</span></span>|<span data-ttu-id="cb932-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="cb932-109">Attribute type</span></span>|<span data-ttu-id="cb932-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb932-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="cb932-111">Genel</span><span class="sxs-lookup"><span data-stu-id="cb932-111">General</span></span>|<span data-ttu-id="cb932-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="cb932-112">Required attribute.</span></span> <span data-ttu-id="cb932-113">Yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb932-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="cb932-114">Genel</span><span class="sxs-lookup"><span data-stu-id="cb932-114">General</span></span>|<span data-ttu-id="cb932-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="cb932-115">Optional attribute.</span></span> <span data-ttu-id="cb932-116">Yöntem imzası belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb932-116">Specifies the method signature.</span></span> <span data-ttu-id="cb932-117">Birden çok parametre varsa, bunların virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="cb932-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="cb932-118">Örneğin, aşağıdaki `<Method>` öğesi tanımlar için ilke <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cb932-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="cb932-119">Öznitelik olmazsa, çalışma zamanı yönerge yöntemi tüm aşırı yüklemeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cb932-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="cb932-120">Yansıma</span><span class="sxs-lookup"><span data-stu-id="cb932-120">Reflection</span></span>|<span data-ttu-id="cb932-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="cb932-121">Optional attribute.</span></span> <span data-ttu-id="cb932-122">Hakkında bilgi için sorgulama veya bir yöntem numaralandırma kontrol eder, ancak çalışma zamanında dinamik herhangi çağırma etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="cb932-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="cb932-123">Yansıma</span><span class="sxs-lookup"><span data-stu-id="cb932-123">Reflection</span></span>|<span data-ttu-id="cb932-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="cb932-124">Optional attribute.</span></span> <span data-ttu-id="cb932-125">Programlama Oluşturucusu veya dinamik etkinleştirmek için yöntemi çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="cb932-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="cb932-126">Bu ilke üyesi çalışma zamanında dinamik olarak çağrılabilir sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb932-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="cb932-127">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="cb932-127">Name attribute</span></span>  
  
|<span data-ttu-id="cb932-128">Değer</span><span class="sxs-lookup"><span data-stu-id="cb932-128">Value</span></span>|<span data-ttu-id="cb932-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb932-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb932-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="cb932-130">*method_name*</span></span>|<span data-ttu-id="cb932-131">Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="cb932-131">The method name.</span></span> <span data-ttu-id="cb932-132">Yöntem türü üst tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb932-132">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="cb932-133">İmza özniteliği</span><span class="sxs-lookup"><span data-stu-id="cb932-133">Signature attribute</span></span>  
  
|<span data-ttu-id="cb932-134">Değer</span><span class="sxs-lookup"><span data-stu-id="cb932-134">Value</span></span>|<span data-ttu-id="cb932-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb932-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb932-136">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="cb932-136">*method_signature*</span></span>|<span data-ttu-id="cb932-137">Yöntem imzası form parametre türleri.</span><span class="sxs-lookup"><span data-stu-id="cb932-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="cb932-138">Birden çok parametre, örneğin, virgülle ayrılır `"System.String,System.Int32,System.Int32)"`.</span><span class="sxs-lookup"><span data-stu-id="cb932-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="cb932-139">Parametre türü adları tam olarak nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb932-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="cb932-140">Tüm diğer özniteliklerle</span><span class="sxs-lookup"><span data-stu-id="cb932-140">All other attributes</span></span>  
  
|<span data-ttu-id="cb932-141">Değer</span><span class="sxs-lookup"><span data-stu-id="cb932-141">Value</span></span>|<span data-ttu-id="cb932-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb932-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb932-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="cb932-143">*policy_setting*</span></span>|<span data-ttu-id="cb932-144">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="cb932-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="cb932-145">Olası değerler şunlardır: `Auto`, `Excluded`, `Included`, ve `Required`.</span><span class="sxs-lookup"><span data-stu-id="cb932-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="cb932-146">Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="cb932-146">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb932-147">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb932-147">Child Elements</span></span>  
  
|<span data-ttu-id="cb932-148">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb932-148">Element</span></span>|<span data-ttu-id="cb932-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb932-149">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb932-150">\<Parametresi ></span><span class="sxs-lookup"><span data-stu-id="cb932-150">\<Parameter></span></span>](../../../docs/framework/net-native/parameter-element-net-native.md)|<span data-ttu-id="cb932-151">Bir yönteme geçirilen bağımsız değişken türü ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cb932-151">Applies policy to the type of the argument passed to a method.</span></span>|  
|[<span data-ttu-id="cb932-152">\<GenericParameter ></span><span class="sxs-lookup"><span data-stu-id="cb932-152">\<GenericParameter></span></span>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|<span data-ttu-id="cb932-153">İlke genel türü veya yöntemi parametresinin türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cb932-153">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[<span data-ttu-id="cb932-154">\<Impliestype ></span><span class="sxs-lookup"><span data-stu-id="cb932-154">\<ImpliesType></span></span>](../../../docs/framework/net-native/impliestype-element-net-native.md)|<span data-ttu-id="cb932-155">Bu ilkeyi içeren tarafından temsil edilen yöntem uygulandıysa İlkesi bir türü için geçerlidir `<Method>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb932-155">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[<span data-ttu-id="cb932-156">\<TypeParameter ></span><span class="sxs-lookup"><span data-stu-id="cb932-156">\<TypeParameter></span></span>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|<span data-ttu-id="cb932-157">Tarafından temsil edilen türü ilkenin uygulandığı bir <xref:System.Type> yöntemi için bağımsız değişken geçirildi.</span><span class="sxs-lookup"><span data-stu-id="cb932-157">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb932-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb932-158">Parent Elements</span></span>  
  
|<span data-ttu-id="cb932-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb932-159">Element</span></span>|<span data-ttu-id="cb932-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb932-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb932-161">\<Türü ></span><span class="sxs-lookup"><span data-stu-id="cb932-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="cb932-162">Yansıma ilke türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cb932-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="cb932-163">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="cb932-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="cb932-164">Yansıma İlkesi, yapılandırılmış bir genel tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cb932-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb932-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb932-165">Remarks</span></span>  
 <span data-ttu-id="cb932-166">A `<Method>` genel yöntem öğesinin kendi ilke olmayan tüm örneklemesi kendi ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cb932-166">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="cb932-167">Kullanabileceğiniz `Signature` belirli yöntemi aşırı yüklemesini ilkesini belirtmek için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="cb932-167">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="cb932-168">Aksi halde, eğer `Signature` özniteliği yoksa, çalışma zamanı yönerge yöntemi tüm aşırı yüklemeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cb932-168">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="cb932-169">Kullanarak bir oluşturucu için çalışma zamanı yansıma İlkesi tanımlayamazsınız `<Method>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb932-169">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="cb932-170">Bunun yerine, kullanın `Activate` özniteliği [ \<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md), veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb932-170">Instead, use the `Activate` attribute of the  [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md), [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md), [\<Type>](../../../docs/framework/net-native/type-element-net-native.md), or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb932-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb932-171">Example</span></span>  
 <span data-ttu-id="cb932-172">`Stringify` Yöntemidir aşağıdaki örnekte, dize gösterimi bir nesneyi dönüştürmek için yansıma kullanan genel amaçlı bir biçimlendirme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cb932-172">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="cb932-173">Nesnenin varsayılan çağıran yanı sıra `ToString` yöntemi, yöntem oluşturabilirsiniz biçimlendirilmiş Sonuç dizesini bir nesnenin geçirerek `ToString` yöntemi bir biçim dizesi bir <xref:System.IFormatProvider> uygulaması ya da her ikisini de.</span><span class="sxs-lookup"><span data-stu-id="cb932-173">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="cb932-174">Aşağıdakilerden birini de işleyememesi <xref:System.Convert.ToString%2A?displayProperty=nameWithType> bir sayı, ikili, onaltılık veya sekizlik gösterimine dönüştürür aşırı.</span><span class="sxs-lookup"><span data-stu-id="cb932-174">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="cb932-175">`Stringify` Yöntemi, aşağıdaki gibi kod tarafından çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="cb932-175">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="cb932-176">Ancak, .NET yerel ile derlendiğinde örnek bir özel durum sayısı çalışma zamanında atabilirsiniz dahil olmak üzere <xref:System.NullReferenceException> ve [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durumlar, bu oluşur çünkü `Stringify` yöntemi dinamik olarak .NET Framework Sınıf Kitaplığı'nda ilkel türler biçimlendirme öncelikle desteklemeye yönelik.</span><span class="sxs-lookup"><span data-stu-id="cb932-176">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="cb932-177">Ancak, bunların meta verilerini varsayılan yönergeleri dosyası tarafından kullanılabilir hale getirilir değil.</span><span class="sxs-lookup"><span data-stu-id="cb932-177">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="cb932-178">Hatta kendi meta veriler kullanılabilir olduğunda, ancak örnek oluşturur [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durumlar için uygun `ToString` uygulamaları sahip olan dahil yerel kodda.</span><span class="sxs-lookup"><span data-stu-id="cb932-178">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="cb932-179">Bu özel durumlar tüm kullanarak Kaldırılabilir [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) , meta verileri, mevcut ve ekleyerek olmalıdır türlerini tanımlamak üzere öğesi `<Method>` yöntemi aşırı uyarlamasını emin olmak için öğeleri çağrılabilir dinamik olarak da mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="cb932-179">These exceptions can all be eliminated by using the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="cb932-180">Bu özel durumları ortadan kaldırır ve hatasız yürütmek örnek sağlayan default.rd.xml dosya verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cb932-180">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb932-181">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb932-181">See Also</span></span>  
 [<span data-ttu-id="cb932-182">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cb932-182">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="cb932-183">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="cb932-183">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="cb932-184">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="cb932-184">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="cb932-185">\<Methodınstantiation > öğesi</span><span class="sxs-lookup"><span data-stu-id="cb932-185">\<MethodInstantiation> Element</span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)
