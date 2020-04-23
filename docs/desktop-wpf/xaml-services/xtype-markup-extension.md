---
title: x:Type İşaretleme Uzantısı
ms.date: 03/30/2017
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
ms.openlocfilehash: f75d4e30dc41bbce995e466466c96c1a2830949b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071362"
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="318bc-102">x:Type İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="318bc-102">x:Type Markup Extension</span></span>

<span data-ttu-id="318bc-103">Belirli bir <xref:System.Type> XAML türü için altta yatan türdeki CLR nesnesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="318bc-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="318bc-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="318bc-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Type prefix:typeNameValue}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="318bc-105">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="318bc-105">XAML Object Element Usage</span></span>

```xaml
<x:Type TypeName="prefix:typeNameValue"/>
```

## <a name="xaml-values"></a><span data-ttu-id="318bc-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="318bc-106">XAML Values</span></span>

|||
|-|-|
|`prefix`|<span data-ttu-id="318bc-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="318bc-107">Optional.</span></span> <span data-ttu-id="318bc-108">Varsayılan olmayan bir XAML ad alanını eşleyen bir önek.</span><span class="sxs-lookup"><span data-stu-id="318bc-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="318bc-109">Önek belirtmek sık sık gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="318bc-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="318bc-110">Bkz. Açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="318bc-110">See Remarks.</span></span>|
|`typeNameValue`|<span data-ttu-id="318bc-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="318bc-111">Required.</span></span> <span data-ttu-id="318bc-112">Geçerli varsayılan XAML ad alanına çözülebilen bir tür adı; veya sağlanırsa `prefix` belirtilen eşlenen önek.</span><span class="sxs-lookup"><span data-stu-id="318bc-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|

## <a name="remarks"></a><span data-ttu-id="318bc-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="318bc-113">Remarks</span></span>

<span data-ttu-id="318bc-114">Biçimlendirme uzantısı, `x:Type` C#'daki `typeof()` işleçle veya `GetType` Microsoft Visual Basic'teki işleçle benzer bir işleve sahiptir.</span><span class="sxs-lookup"><span data-stu-id="318bc-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in C# or the `GetType` operator in Microsoft Visual Basic.</span></span>

<span data-ttu-id="318bc-115">`x:Type` Biçimlendirme uzantısı, türü <xref:System.Type>alan özellikler için dize dışından dönüştürme davranışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="318bc-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="318bc-116">Giriş bir XAML türüdür.</span><span class="sxs-lookup"><span data-stu-id="318bc-116">The input is a XAML type.</span></span> <span data-ttu-id="318bc-117">Giriş XAML türü ve çıkış <xref:System.Type> CLR arasındaki ilişki, <xref:System.Type> çıkış <xref:System.Xaml.XamlType.UnderlyingType%2A> girişin <xref:System.Xaml.XamlType>, XAML <xref:System.Xaml.XamlType> şema bağlamı ve bağlam ın <xref:System.Windows.Markup.IXamlTypeResolver> sağladığı hizmete dayalı gerekli baktıktan sonra olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="318bc-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="318bc-118">.NET XAML Hizmetleri'nde, bu biçimlendirme uzantısı <xref:System.Windows.Markup.TypeExtension> için işleme sınıf tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="318bc-118">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>

<span data-ttu-id="318bc-119">Belirli çerçeve uygulamalarında, değer <xref:System.Type> olarak kabul eden bazı özellikler doğrudan türün adını (türün `Name`dize değeri) kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="318bc-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="318bc-120">Ancak, bu davranışı uygulamak karmaşık bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="318bc-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="318bc-121">Örneğin, aşağıdaki "WPF Kullanım Notları" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="318bc-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>

<span data-ttu-id="318bc-122">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="318bc-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="318bc-123">Tanımlayıcı dizesonra sağlanan `x:Type` dize belirteci alttaki <xref:System.Windows.Markup.TypeExtension.TypeName%2A> <xref:System.Windows.Markup.TypeExtension> uzantı sınıfının değeri olarak atanır.</span><span class="sxs-lookup"><span data-stu-id="318bc-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="318bc-124">CLR türlerini temel alan .NET XAML Hizmetleri için varsayılan XAML şeması bağlamında, bu özniteliğin değeri istenen <xref:System.Reflection.MemberInfo.Name%2A> türdeki veya varsayılan olmayan xaml ad alanı eşlemi için bir önek önce gelen içerir. <xref:System.Reflection.MemberInfo.Name%2A></span><span class="sxs-lookup"><span data-stu-id="318bc-124">Under the default XAML schema context for .NET XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>

<span data-ttu-id="318bc-125">`x:Type` Biçimlendirme uzantısı nesne öğesi sözdiziminde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="318bc-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="318bc-126">Bu durumda, uzantıyı düzgün <xref:System.Windows.Markup.TypeExtension.TypeName%2A> bir şekilde başlatmanın özelliğinin değerini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="318bc-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>

<span data-ttu-id="318bc-127">`x:Type` Biçimlendirme uzantısı ayrıntılı bir öznitelik olarak da kullanılabilir; ancak bu kullanım tipik değildir:`<object property="{x:Type TypeName=typeNameValue}" .../>`</span><span class="sxs-lookup"><span data-stu-id="318bc-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<object property="{x:Type TypeName=typeNameValue}" .../>`</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="318bc-128">WPF Kullanım Notları</span><span class="sxs-lookup"><span data-stu-id="318bc-128">WPF Usage Notes</span></span>

### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="318bc-129">Varsayılan XAML Ad Alanı ve Tür Eşleme</span><span class="sxs-lookup"><span data-stu-id="318bc-129">Default XAML Namespace and Type Mapping</span></span>

<span data-ttu-id="318bc-130">WPF programlama için varsayılan XAML ad alanı, tipik XAML senaryoları için gereken XAML türlerinin çoğunu içerir; bu nedenle, XAML türü değerlerine başvururken genellikle önekleri önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="318bc-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="318bc-131">Özel bir derlemeden veya WPF derlemesinde var olan ancak varsayılan XAML ad alanına eşlenmemiş bir CLR ad alanından gelen türler için bir türe başvuruyorsanız önek eşlemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="318bc-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="318bc-132">Önekler, XAML ad alanları ve CLR ad alanlarını eşleme hakkında daha fazla bilgi için [WPF XAML için XAML Ad Alanları ve Ad Alanı Eşleme'ye](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="318bc-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>

### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="318bc-133">Dize Olarak Tür Adı Destekleyen Özellikler Yazın</span><span class="sxs-lookup"><span data-stu-id="318bc-133">Type Properties That Support Typename-as-String</span></span>

<span data-ttu-id="318bc-134">WPF, `x:Type` biçimlendirme uzantısı kullanımı gerektirmeden bazı <xref:System.Type> tür özelliklerinin değerini belirtmeyi sağlayan teknikleri destekler.</span><span class="sxs-lookup"><span data-stu-id="318bc-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="318bc-135">Bunun yerine, değeri türü adlayan bir dize olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="318bc-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="318bc-136">Buna örnek <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> olarak <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>verilebilir ve .</span><span class="sxs-lookup"><span data-stu-id="318bc-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="318bc-137">Bu davranış için destek tür dönüştürücüler veya biçimlendirme uzantıları aracılığıyla sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="318bc-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="318bc-138">Bunun yerine, bu aracılığıyla <xref:System.Windows.FrameworkElementFactory>uygulanan bir erteleme davranışıdır.</span><span class="sxs-lookup"><span data-stu-id="318bc-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>

<span data-ttu-id="318bc-139">Silverlight da benzer bir kongreyi destekliyor.</span><span class="sxs-lookup"><span data-stu-id="318bc-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="318bc-140">Aslında, Silverlight şu anda XAML dil desteğini `{x:Type}` desteklemez `{x:Type}` ve WPF-Silverlight XAML geçişini desteklemek için tasarlanmış birkaç durum dışında kullanımları kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="318bc-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="318bc-141">Bu nedenle, dize olarak dize olarak dakti-as-davranış bir <xref:System.Type> değer olduğu tüm Silverlight yerel özellik değerlendirme yerleşiktir.</span><span class="sxs-lookup"><span data-stu-id="318bc-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>

## <a name="xaml-2009"></a><span data-ttu-id="318bc-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="318bc-142">XAML 2009</span></span>

<span data-ttu-id="318bc-143">XAML 2009 genel türleri için ek destek sağlar `x:TypeArguments` ve `x:Type` özellik davranışını değiştirir ve bu desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="318bc-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>

- <span data-ttu-id="318bc-144">`x:TypeArguments`ve genel bir nesne anlık için ilişkili nesne öğesi kök dışındaki öğeler üzerinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="318bc-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="318bc-145">Daha fazla bilgi için [x:TypeArguments](xtypearguments-directive.md)Yönergesi'nin "XAML 2009" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="318bc-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](xtypearguments-directive.md).</span></span>

- <span data-ttu-id="318bc-146">XAML 2009, biçimlendirmede genel bir tür kısıtlamasını belirtmek için bir sözdizimini destekler.</span><span class="sxs-lookup"><span data-stu-id="318bc-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="318bc-147">Bu, iki `x:TypeArguments`özellik `x:Type`tarafından veya birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="318bc-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>

- <span data-ttu-id="318bc-148">WPF XAML uygulaması yük için XAML 2009 işlenirken de türü <xref:System.Type>kullanan belirli çerçeve özellikleri için örtük tür dönüştürme davranışı bu yeteneği ekler.</span><span class="sxs-lookup"><span data-stu-id="318bc-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>

<span data-ttu-id="318bc-149">WPF'de XAML 2009 özelliklerini ancak yalnızca gevşek XAML (biçimlendirme derlememiş XAML) için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="318bc-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="318bc-150">WPF için biçimlendirmeyle derlenen XAML ve XAML'nin BAML formu şu anda XAML 2009 anahtar kelimelerini ve özelliklerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="318bc-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="318bc-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="318bc-151">See also</span></span>

- <xref:System.Windows.Style>
- [<span data-ttu-id="318bc-152">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="318bc-152">Styling and Templating</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="318bc-153">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="318bc-153">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="318bc-154">Biçimlendirme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="318bc-154">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
