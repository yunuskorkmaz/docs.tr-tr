---
title: "x:Type İşaretleme Uzantısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4d645d5c953c0ff33435a5648024ace099455e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="c947f-102">x:Type İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="c947f-102">x:Type Markup Extension</span></span>
<span data-ttu-id="c947f-103">CLR sağlayan <xref:System.Type> belirtilen bir XAML tür için temel alınan tür nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c947f-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c947f-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="c947f-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="c947f-105">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="c947f-105">XAML Object Element Usage</span></span>  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c947f-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="c947f-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`prefix`|<span data-ttu-id="c947f-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c947f-107">Optional.</span></span> <span data-ttu-id="c947f-108">Varsayılan olmayan XAML ad uzayı eşleyen bir önek.</span><span class="sxs-lookup"><span data-stu-id="c947f-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="c947f-109">Bir önek belirtme sık gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c947f-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="c947f-110">Açıklamalar bakın.</span><span class="sxs-lookup"><span data-stu-id="c947f-110">See Remarks.</span></span>|  
|`typeNameValue`|<span data-ttu-id="c947f-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c947f-111">Required.</span></span> <span data-ttu-id="c947f-112">Tür adı için geçerli varsayılan XAML ad uzayı çözümlenebilir; veya belirtilen eşlenmiş öneki varsa `prefix` sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c947f-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c947f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c947f-113">Remarks</span></span>  
 <span data-ttu-id="c947f-114">`x:Type` Biçimlendirme uzantısı benzer bir işlevi olan `typeof()` işlecinde [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] veya `GetType` işlecinde [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c947f-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] or the `GetType` operator in [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)].</span></span>  
  
 <span data-ttu-id="c947f-115">`x:Type` Biçimlendirme uzantısı türü ele özellikleri için bir dize öğesinden dönüştürme davranış sağlayan <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="c947f-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="c947f-116">Giriş XAML türüdür.</span><span class="sxs-lookup"><span data-stu-id="c947f-116">The input is a XAML type.</span></span> <span data-ttu-id="c947f-117">Giriş XAML türü ve CLR çıkış arasındaki ilişkiyi <xref:System.Type> çıkış olan <xref:System.Type> olan <xref:System.Xaml.XamlType.UnderlyingType%2A> giriş <xref:System.Xaml.XamlType>, gerekli bakan sonra <xref:System.Xaml.XamlType> XAML şema içeriği ve göre<xref:System.Windows.Markup.IXamlTypeResolver>Hizmet bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c947f-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="c947f-118">.NET Framework XAML hizmetlerinde bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.TypeExtension> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c947f-118">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>  
  
 <span data-ttu-id="c947f-119">Bazı özellikler belirli framework uygulamalarında alın <xref:System.Type> değeri doğrudan türünün adını kabul (tür dizesi değerini `Name`).</span><span class="sxs-lookup"><span data-stu-id="c947f-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="c947f-120">Ancak, bu davranış uygulama karmaşık bir senaryo değildir.</span><span class="sxs-lookup"><span data-stu-id="c947f-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="c947f-121">Örnekler için aşağıdaki "WPF kullanım notları" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c947f-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>  
  
 <span data-ttu-id="c947f-122">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="c947f-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="c947f-123">Sonra sağlanan dize belirteci `x:Type` kimlik dizesi olarak atandığı <xref:System.Windows.Markup.TypeExtension.TypeName%2A> temel değer <xref:System.Windows.Markup.TypeExtension> uzantısı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c947f-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="c947f-124">CLR türlerine dayanarak, .NET Framework XAML hizmetlerinde, varsayılan XAML şema içeriği bu özniteliğin değeri ya da altındadır <xref:System.Reflection.MemberInfo.Name%2A> istenen türde veya içeren <xref:System.Reflection.MemberInfo.Name%2A> varsayılan olmayan XAML ad uzayı için bir önek öncesinde eşleme.</span><span class="sxs-lookup"><span data-stu-id="c947f-124">Under the default XAML schema context for .NET Framework XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>  
  
 <span data-ttu-id="c947f-125">`x:Type` Biçimlendirme uzantısı nesne öğesi sözdiziminde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c947f-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="c947f-126">Bu durumda, değerini belirten <xref:System.Windows.Markup.TypeExtension.TypeName%2A> özelliği uzantıyı düzgün başlatmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c947f-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="c947f-127">`x:Type` Biçimlendirme uzantısı olarak ayrıntılı bir özniteliği de kullanılabilir; ancak bu kullanım tipik: `<``object``property``="{x:Type TypeName=``typeNameValue``}" .../>`</span><span class="sxs-lookup"><span data-stu-id="c947f-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<``object` `property``="{x:Type TypeName=``typeNameValue``}" .../>`</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="c947f-128">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="c947f-128">WPF Usage Notes</span></span>  
  
### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="c947f-129">Varsayılan XAML Namespace ve tür eşlemesi</span><span class="sxs-lookup"><span data-stu-id="c947f-129">Default XAML Namespace and Type Mapping</span></span>  
 <span data-ttu-id="c947f-130">Varsayılan XAML ad uzayı WPF programlama için tipik XAML senaryoları için gereksinim duyduğunuz XAML türlerinin çoğu içerir; Bu nedenle, genellikle önekleri XAML tür değerleri başvururken önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c947f-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="c947f-131">Özel bir derlemeyi ya da bir WPF derlemede var, ancak varsayılan XAML ad alanına eşlenmeyen bir CLR ad alanından olan türleri için bir tür başvuran varsa bir önek eşleme gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c947f-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="c947f-132">Önekleri, XAML ad uzayları ve eşleme CLR ad alanları hakkında daha fazla bilgi için bkz: [XAML ad uzayları ve WPF XAML için Namespace eşleme](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="c947f-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>  
  
### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="c947f-133">Özellikler bu destek Typename olarak-dizesi yazın</span><span class="sxs-lookup"><span data-stu-id="c947f-133">Type Properties That Support Typename-as-String</span></span>  
 <span data-ttu-id="c947f-134">WPF destekleyen türünün bazı özellikleri değerini belirten etkinleştirmek teknikleri <xref:System.Type> gerektirmeden bir `x:Type` biçimlendirme uzantısı kullanımı.</span><span class="sxs-lookup"><span data-stu-id="c947f-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="c947f-135">Bunun yerine, değer türü adları bir dize olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c947f-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="c947f-136">Bu öğeler örnekleri <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> ve <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c947f-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c947f-137">Bu davranış desteği tür dönüştürücüleri veya işaretleme uzantıları aracılığıyla sağlanmadı.</span><span class="sxs-lookup"><span data-stu-id="c947f-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="c947f-138">Bunun yerine, bu aracılığıyla uygulanan bir erteleme davranıştır <xref:System.Windows.FrameworkElementFactory>.</span><span class="sxs-lookup"><span data-stu-id="c947f-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>  
  
 <span data-ttu-id="c947f-139">Silverlight benzer bir kuralı destekler.</span><span class="sxs-lookup"><span data-stu-id="c947f-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="c947f-140">Aslında, Silverlight şu anda desteklemediği `{x:Type}` kendi XAML dil desteği ve kabul etmediği `{x:Type}` kullanımları Silverlight WPF XAML geçişi desteklemek için tasarlanmıştır birkaç durumlar dışında.</span><span class="sxs-lookup"><span data-stu-id="c947f-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="c947f-141">Bu nedenle, dize olarak typename tüm Silverlight yerel özellik değerlendirmesi için yerleşik bir davranıştır burada bir <xref:System.Type> değerdir.</span><span class="sxs-lookup"><span data-stu-id="c947f-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="c947f-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="c947f-142">XAML 2009</span></span>  
 <span data-ttu-id="c947f-143">XAML 2009 desteği sağlar. ek genel türleri ve özellik davranışını değiştiren `x:TypeArguments` ve `x:Type` bu desteği sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="c947f-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>  
  
-   <span data-ttu-id="c947f-144">`x:TypeArguments`ve ilişkili nesne öğesi genel nesne örneğini oluşturmada için kök başka öğelerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="c947f-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="c947f-145">Daha fazla bilgi için "XAML 2009" bölümüne bakın [x: TypeArguments yönergesi](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span><span class="sxs-lookup"><span data-stu-id="c947f-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span></span>  
  
-   <span data-ttu-id="c947f-146">XAML 2009 genel tür kısıtlaması biçimlendirmede belirtmek için bir söz dizimi destekler.</span><span class="sxs-lookup"><span data-stu-id="c947f-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="c947f-147">Bu tarafından kullanılabilir `x:TypeArguments`, göre `x:Type`, veya iki özellik birlikte.</span><span class="sxs-lookup"><span data-stu-id="c947f-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>  
  
-   <span data-ttu-id="c947f-148">Yük türünü kullanan belirli framework özellikleri örtük tür dönüştürme davranışını bu özelliği de ekler için XAML 2009 işlerken WPF XAML uygulama <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="c947f-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="c947f-149">WPF'de, ancak yalnızca gevşek XAML için (biçimlendirme-derlenmemiş XAML) XAML 2009 özellikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c947f-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="c947f-150">XAML biçimlendirme derlenmiş WPF ve XAML BAML form için şu anda desteklemediği XAML 2009 anahtar sözcükleri ve özellikler.</span><span class="sxs-lookup"><span data-stu-id="c947f-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c947f-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c947f-151">See Also</span></span>  
 <xref:System.Windows.Style>  
 [<span data-ttu-id="c947f-152">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c947f-152">Styling and Templating</span></span>](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="c947f-153">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="c947f-153">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="c947f-154">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="c947f-154">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
