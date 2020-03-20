---
title: <Method>Eleman (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 8db32c660846b4f4071fff2a40c760a3d1ef2489
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180985"
---
# <a name="method-element-net-native"></a><span data-ttu-id="40d6d-102">\<Yöntem> Elemanı (.NET Yerli)</span><span class="sxs-lookup"><span data-stu-id="40d6d-102">\<Method> Element (.NET Native)</span></span>
<span data-ttu-id="40d6d-103">Bir oluşturucuya veya yönteme çalışma zamanı yansıtma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="40d6d-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40d6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40d6d-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40d6d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="40d6d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="40d6d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40d6d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40d6d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="40d6d-107">Attributes</span></span>  
  
|<span data-ttu-id="40d6d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="40d6d-108">Attribute</span></span>|<span data-ttu-id="40d6d-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="40d6d-109">Attribute type</span></span>|<span data-ttu-id="40d6d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40d6d-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="40d6d-111">Genel</span><span class="sxs-lookup"><span data-stu-id="40d6d-111">General</span></span>|<span data-ttu-id="40d6d-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="40d6d-112">Required attribute.</span></span> <span data-ttu-id="40d6d-113">Yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="40d6d-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="40d6d-114">Genel</span><span class="sxs-lookup"><span data-stu-id="40d6d-114">General</span></span>|<span data-ttu-id="40d6d-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="40d6d-115">Optional attribute.</span></span> <span data-ttu-id="40d6d-116">Yöntem imzasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="40d6d-116">Specifies the method signature.</span></span> <span data-ttu-id="40d6d-117">Birden çok parametre varsa, virgülle ayrılırlar.</span><span class="sxs-lookup"><span data-stu-id="40d6d-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="40d6d-118">Örneğin, aşağıdaki `<Method>` öğe <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> yöntem için ilke tanımlar.</span><span class="sxs-lookup"><span data-stu-id="40d6d-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="40d6d-119">Öznitelik yoksa, çalışma zamanı yönergesi yöntemin tüm aşırı yükleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="40d6d-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="40d6d-120">Yansıma</span><span class="sxs-lookup"><span data-stu-id="40d6d-120">Reflection</span></span>|<span data-ttu-id="40d6d-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="40d6d-121">Optional attribute.</span></span> <span data-ttu-id="40d6d-122">Bir yöntem hakkında bilgi için sorgulamayı veya bir yöntemin sayısalasını denetler, ancak çalışma zamanında dinamik bir çağrıyı etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="40d6d-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="40d6d-123">Yansıma</span><span class="sxs-lookup"><span data-stu-id="40d6d-123">Reflection</span></span>|<span data-ttu-id="40d6d-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="40d6d-124">Optional attribute.</span></span> <span data-ttu-id="40d6d-125">Dinamik programlamayı etkinleştirmek için bir oluşturucuya veya yönteme çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="40d6d-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="40d6d-126">Bu ilke, bir üyenin çalışma zamanında dinamik olarak çağrılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="40d6d-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="40d6d-127">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="40d6d-127">Name attribute</span></span>  
  
|<span data-ttu-id="40d6d-128">Değer</span><span class="sxs-lookup"><span data-stu-id="40d6d-128">Value</span></span>|<span data-ttu-id="40d6d-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40d6d-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40d6d-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="40d6d-130">*method_name*</span></span>|<span data-ttu-id="40d6d-131">Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="40d6d-131">The method name.</span></span> <span data-ttu-id="40d6d-132">Yöntemin türü ana [ \<Type>](type-element-net-native.md) veya [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) öğesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="40d6d-132">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="40d6d-133">İmza özniteliği</span><span class="sxs-lookup"><span data-stu-id="40d6d-133">Signature attribute</span></span>  
  
|<span data-ttu-id="40d6d-134">Değer</span><span class="sxs-lookup"><span data-stu-id="40d6d-134">Value</span></span>|<span data-ttu-id="40d6d-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40d6d-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40d6d-136">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="40d6d-136">*method_signature*</span></span>|<span data-ttu-id="40d6d-137">Yöntem imzasını oluşturan parametre türleri.</span><span class="sxs-lookup"><span data-stu-id="40d6d-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="40d6d-138">Birden çok parametre virgülle `"System.String,System.Int32,System.Int32)"`ayrılır, örneğin.</span><span class="sxs-lookup"><span data-stu-id="40d6d-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="40d6d-139">Parametre türü adları tam nitelikli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40d6d-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="40d6d-140">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="40d6d-140">All other attributes</span></span>  
  
|<span data-ttu-id="40d6d-141">Değer</span><span class="sxs-lookup"><span data-stu-id="40d6d-141">Value</span></span>|<span data-ttu-id="40d6d-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40d6d-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="40d6d-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="40d6d-143">*policy_setting*</span></span>|<span data-ttu-id="40d6d-144">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="40d6d-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="40d6d-145">Olası değerler `Auto` `Excluded`, `Included`, `Required`, ve .</span><span class="sxs-lookup"><span data-stu-id="40d6d-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="40d6d-146">Daha fazla bilgi için [Runtime Yönergesi İlke Ayarları'na](runtime-directive-policy-settings.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="40d6d-146">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40d6d-147">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="40d6d-147">Child Elements</span></span>  
  
|<span data-ttu-id="40d6d-148">Öğe</span><span class="sxs-lookup"><span data-stu-id="40d6d-148">Element</span></span>|<span data-ttu-id="40d6d-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40d6d-149">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40d6d-150">\<Parametre></span><span class="sxs-lookup"><span data-stu-id="40d6d-150">\<Parameter></span></span>](parameter-element-net-native.md)|<span data-ttu-id="40d6d-151">Bir yönteme geçirilen bağımsız değişken türüne ilke uygular.</span><span class="sxs-lookup"><span data-stu-id="40d6d-151">Applies policy to the type of the argument passed to a method.</span></span>|  
|[<span data-ttu-id="40d6d-152">\<Genel Parametre></span><span class="sxs-lookup"><span data-stu-id="40d6d-152">\<GenericParameter></span></span>](genericparameter-element-net-native.md)|<span data-ttu-id="40d6d-153">Genel bir tür veya yöntemin parametre türüne ilke uygular.</span><span class="sxs-lookup"><span data-stu-id="40d6d-153">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[<span data-ttu-id="40d6d-154">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="40d6d-154">\<ImpliesType></span></span>](impliestype-element-net-native.md)|<span data-ttu-id="40d6d-155">Bu ilke, içeren `<Method>` öğe tarafından temsil edilen yönteme uygulanmışsa, bir türe ilke uygular.</span><span class="sxs-lookup"><span data-stu-id="40d6d-155">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[<span data-ttu-id="40d6d-156">\<TipParametre></span><span class="sxs-lookup"><span data-stu-id="40d6d-156">\<TypeParameter></span></span>](typeparameter-element-net-native.md)|<span data-ttu-id="40d6d-157">Bir yönteme geçirilen bir <xref:System.Type> bağımsız değişken tarafından temsil edilen türe ilke uygular.</span><span class="sxs-lookup"><span data-stu-id="40d6d-157">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40d6d-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="40d6d-158">Parent Elements</span></span>  
  
|<span data-ttu-id="40d6d-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="40d6d-159">Element</span></span>|<span data-ttu-id="40d6d-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40d6d-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40d6d-161">\<Tip></span><span class="sxs-lookup"><span data-stu-id="40d6d-161">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="40d6d-162">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="40d6d-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="40d6d-163">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="40d6d-163">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="40d6d-164">Yapılı genel bir türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="40d6d-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40d6d-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40d6d-165">Remarks</span></span>  
 <span data-ttu-id="40d6d-166">Genel `<Method>` bir yöntemin bir öğesi, ilkesini kendi ilkesi olmayan tüm anlık iletilere uygular.</span><span class="sxs-lookup"><span data-stu-id="40d6d-166">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="40d6d-167">Belirli bir `Signature` yöntem aşırı yüklemesi için ilke belirtmek için öznitelik kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40d6d-167">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="40d6d-168">Aksi takdirde, `Signature` öznitelik yoksa, çalışma zamanı yönergesi yöntemin tüm aşırı yükleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="40d6d-168">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="40d6d-169">`<Method>` Öğeyi kullanarak bir oluşturucu için çalışma zamanı yansıtma ilkesini tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="40d6d-169">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="40d6d-170">Bunun yerine, `Activate` [ \<Derleme>, ](assembly-element-net-native.md) [ \<Namespace>, ](namespace-element-net-native.md) [ \<Type>](type-element-net-native.md)veya [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) öğesiözeğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="40d6d-170">Instead, use the `Activate` attribute of the  [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), [\<Type>](type-element-net-native.md), or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40d6d-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="40d6d-171">Example</span></span>  
 <span data-ttu-id="40d6d-172">Aşağıdaki `Stringify` örnekteki yöntem, bir nesneyi dize gösterimine dönüştürmek için yansımayı kullanan genel amaçlı bir biçimlendirme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="40d6d-172">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="40d6d-173">Nesnenin varsayılan `ToString` yöntemini çağırmaya ek olarak, yöntem, nesnenin `ToString` yöntemini biçimlendirme dizesi, <xref:System.IFormatProvider> uygulama veya her ikisini birden geçirerek biçimlendirilmiş bir sonuç dizesi üretebilir.</span><span class="sxs-lookup"><span data-stu-id="40d6d-173">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="40d6d-174">Ayrıca, bir sayıyı <xref:System.Convert.ToString%2A?displayProperty=nameWithType> ikili, heksadesibel veya sekizli gösterimine dönüştüren aşırı yüklerden birini de çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="40d6d-174">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="40d6d-175">Yöntem `Stringify` aşağıdaki gibi kod la çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="40d6d-175">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="40d6d-176">Ancak, .NET Native ile derlendiğinde, örnek çalışma zamanında bir dizi özel <xref:System.NullReferenceException> durum atabilir, ve [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumlar da dahil olmak üzere, yöntem öncelikle .NET Framework Class Kitaplığı'ndaki ilkel türleri dinamik olarak biçimlendirmeyi desteklemek için tasarlandığından bu `Stringify` oluşur.</span><span class="sxs-lookup"><span data-stu-id="40d6d-176">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="40d6d-177">Ancak, meta verileri varsayılan yönergeler dosyası tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="40d6d-177">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="40d6d-178">Ancak, meta verileri kullanılabilir hale getirilse bile, uygun `ToString` uygulamalar yerel koda dahil edilmediğinden, örnek Eksik [RuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumlarını atar.</span><span class="sxs-lookup"><span data-stu-id="40d6d-178">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="40d6d-179">Bu özel durumlar, meta verileri bulunması gereken türleri tanımlamak için [ \<Type>](type-element-net-native.md) öğesi kullanılarak `<Method>` ve dinamik olarak çağrılabilen yöntem aşırı yüklemelerinin uygulanmasının da mevcut olduğundan emin olmak için öğeler eklenerek ortadan kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="40d6d-179">These exceptions can all be eliminated by using the [\<Type>](type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="40d6d-180">Aşağıda, bu özel durumları ortadan kaldıran ve örneğin hatasız yürütülmesine izin veren default.rd.xml dosyası verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="40d6d-180">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="40d6d-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40d6d-181">See also</span></span>

- [<span data-ttu-id="40d6d-182">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="40d6d-182">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="40d6d-183">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="40d6d-183">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="40d6d-184">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="40d6d-184">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="40d6d-185">\<MethodInstantiation> Elementi</span><span class="sxs-lookup"><span data-stu-id="40d6d-185">\<MethodInstantiation> Element</span></span>](methodinstantiation-element-net-native.md)
