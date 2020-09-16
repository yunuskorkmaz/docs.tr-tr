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
ms.openlocfilehash: 00e6684f6ad1eb8d96f72f49bd5e0d211c8166c3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559076"
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="7ab65-102">x:Type İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="7ab65-102">x:Type Markup Extension</span></span>

<span data-ttu-id="7ab65-103"><xref:System.Type>BELIRTILEN xaml türü için temeldeki tür olan CLR nesnesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ab65-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="7ab65-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="7ab65-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Type prefix:typeNameValue}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="7ab65-105">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="7ab65-105">XAML Object Element Usage</span></span>

```xaml
<x:Type TypeName="prefix:typeNameValue"/>
```

## <a name="xaml-values"></a><span data-ttu-id="7ab65-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="7ab65-106">XAML Values</span></span>

|||
|-|-|
|`prefix`|<span data-ttu-id="7ab65-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7ab65-107">Optional.</span></span> <span data-ttu-id="7ab65-108">Varsayılan olmayan XAML ad alanını eşleyen bir ön ek.</span><span class="sxs-lookup"><span data-stu-id="7ab65-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="7ab65-109">Ön ek belirtmek genellikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="7ab65-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="7ab65-110">Bkz. açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="7ab65-110">See Remarks.</span></span>|
|`typeNameValue`|<span data-ttu-id="7ab65-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7ab65-111">Required.</span></span> <span data-ttu-id="7ab65-112">Geçerli varsayılan XAML ad alanına çözümlenebilen bir tür adı; veya belirtilmişse belirtilen eşlenmiş ön ek `prefix` .</span><span class="sxs-lookup"><span data-stu-id="7ab65-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7ab65-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ab65-113">Remarks</span></span>

<span data-ttu-id="7ab65-114">`x:Type`Biçimlendirme uzantısı, `typeof()` C# ' deki Işlece veya `GetType` Microsoft Visual Basic işleçine benzer bir işleve sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7ab65-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in C# or the `GetType` operator in Microsoft Visual Basic.</span></span>

<span data-ttu-id="7ab65-115">`x:Type`Biçimlendirme uzantısı, türü alan özellikler için dizeden bir dönüştürme davranışı sağlar <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="7ab65-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="7ab65-116">Giriş bir XAML türüdür.</span><span class="sxs-lookup"><span data-stu-id="7ab65-116">The input is a XAML type.</span></span> <span data-ttu-id="7ab65-117">Giriş XAML türü ve çıkış CLR arasındaki ilişki, <xref:System.Type> <xref:System.Type> <xref:System.Xaml.XamlType.UnderlyingType%2A> <xref:System.Xaml.XamlType> <xref:System.Xaml.XamlType> xaml şema bağlamına ve <xref:System.Windows.Markup.IXamlTypeResolver> bağlamın sağladığı hizmete bağlı olarak gerekli olan, çıktının girişin bulunduğu bir giriştir.</span><span class="sxs-lookup"><span data-stu-id="7ab65-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="7ab65-118">.NET XAML hizmetlerinde, bu biçimlendirme uzantısının işlenmesi sınıfı tarafından tanımlanır <xref:System.Windows.Markup.TypeExtension> .</span><span class="sxs-lookup"><span data-stu-id="7ab65-118">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>

<span data-ttu-id="7ab65-119">Belirli çerçeve uygulamalarında, değer olarak alan bazı özellikler <xref:System.Type> doğrudan türün adını kabul edebilir (türün dize değeri `Name` ).</span><span class="sxs-lookup"><span data-stu-id="7ab65-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="7ab65-120">Ancak, bu davranışı uygulamak karmaşık bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="7ab65-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="7ab65-121">Örnekler için aşağıdaki "WPF kullanım notları" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7ab65-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>

<span data-ttu-id="7ab65-122">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="7ab65-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="7ab65-123">Tanımlayıcı dizeden sonra belirtilen dize belirteci, `x:Type` <xref:System.Windows.Markup.TypeExtension.TypeName%2A> temel uzantı sınıfının değeri olarak atanır <xref:System.Windows.Markup.TypeExtension> .</span><span class="sxs-lookup"><span data-stu-id="7ab65-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="7ab65-124">CLR türlerini temel alan .NET XAML Hizmetleri için varsayılan XAML şeması bağlamı altında, bu özniteliğin değeri <xref:System.Reflection.MemberInfo.Name%2A> istenen türden ya da <xref:System.Reflection.MemberInfo.Name%2A> varsayılan olmayan xaml ad alanı eşlemesi için ön ek tarafından önceden bir ön eki tarafından bulunur.</span><span class="sxs-lookup"><span data-stu-id="7ab65-124">Under the default XAML schema context for .NET XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>

<span data-ttu-id="7ab65-125">`x:Type`Biçimlendirme uzantısı nesne öğesi sözdiziminde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ab65-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="7ab65-126">Bu durumda, <xref:System.Windows.Markup.TypeExtension.TypeName%2A> uzantıyı doğru şekilde başlatmak için özelliğinin değerini belirtmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ab65-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>

<span data-ttu-id="7ab65-127">`x:Type`Biçimlendirme uzantısı da verbose özniteliği olarak kullanılabilir; ancak bu kullanım tipik değildir:`<object property="{x:Type TypeName=typeNameValue}" .../>`</span><span class="sxs-lookup"><span data-stu-id="7ab65-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<object property="{x:Type TypeName=typeNameValue}" .../>`</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="7ab65-128">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="7ab65-128">WPF Usage Notes</span></span>

### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="7ab65-129">Varsayılan XAML ad alanı ve tür eşleme</span><span class="sxs-lookup"><span data-stu-id="7ab65-129">Default XAML Namespace and Type Mapping</span></span>

<span data-ttu-id="7ab65-130">WPF programlama için varsayılan XAML ad alanı, tipik XAML senaryoları için ihtiyacınız olan XAML türlerinin çoğunu içerir; Bu nedenle, XAML türü değerlerine başvuru yaparken genellikle öneklerden kaçınabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ab65-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="7ab65-131">Özel bir derlemeden veya bir WPF derlemesinde bulunan ancak varsayılan XAML ad alanıyla eşlenmeyen bir CLR ad alanı olan türler için bir türe başvuruyordıysanız bir ön eki eşlemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7ab65-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="7ab65-132">Ön ekler, XAML ad alanları ve eşleme CLR ad alanları hakkında daha fazla bilgi için bkz. [WPF XAML Için xaml ad alanları ve ad alanı eşlemesi](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).</span><span class="sxs-lookup"><span data-stu-id="7ab65-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).</span></span>

### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="7ab65-133">Dize olarak TypeName 'ı destekleyen tür özellikleri</span><span class="sxs-lookup"><span data-stu-id="7ab65-133">Type Properties That Support Typename-as-String</span></span>

<span data-ttu-id="7ab65-134">WPF, <xref:System.Type> biçimlendirme uzantısı kullanımı gerekmeden türdeki bazı özelliklerin değerini belirtmeyi etkinleştiren teknikleri destekler `x:Type` .</span><span class="sxs-lookup"><span data-stu-id="7ab65-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="7ab65-135">Bunun yerine, değeri türü adı belirleyen bir dize olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ab65-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="7ab65-136">Bunun örnekleri <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> ve <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7ab65-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7ab65-137">Bu davranış için destek, tür dönüştürücüler veya biçimlendirme uzantıları aracılığıyla sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="7ab65-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="7ab65-138">Bunun yerine, bu, ile uygulanan bir erteleme davranışıdır <xref:System.Windows.FrameworkElementFactory> .</span><span class="sxs-lookup"><span data-stu-id="7ab65-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>

<span data-ttu-id="7ab65-139">Silverlight benzer bir kuralı destekler.</span><span class="sxs-lookup"><span data-stu-id="7ab65-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="7ab65-140">Aslında, Silverlight şu anda `{x:Type}` xaml dil desteğiyle desteklemez ve `{x:Type}` WPF-Silverlight xaml geçişini desteklemek için tasarlanan birkaç koşulda kullanımları kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="7ab65-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="7ab65-141">Bu nedenle, dize olarak TypeName davranışı, bir değeri olduğu yerde tüm Silverlight yerel özellik değerlendirmesinde yerleşik olarak bulunur <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="7ab65-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>

## <a name="xaml-2009"></a><span data-ttu-id="7ab65-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="7ab65-142">XAML 2009</span></span>

<span data-ttu-id="7ab65-143">XAML 2009, genel türler için ek destek sağlar ve `x:TypeArguments` `x:Type` Bu desteği sağlamak için ve özelliklerinin davranışını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="7ab65-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>

- <span data-ttu-id="7ab65-144">`x:TypeArguments` ve genel nesne örneklemesi için ilişkili nesne öğesi kök dışında bir öğe üzerinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ab65-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="7ab65-145">Daha fazla bilgi için, [X:TypeArguments yönergesinin](xtypearguments-directive.md)"xaml 2009" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7ab65-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](xtypearguments-directive.md).</span></span>

- <span data-ttu-id="7ab65-146">XAML 2009, biçimlendirme içinde genel bir türün kısıtlamasını belirtmek için bir sözdizimi destekler.</span><span class="sxs-lookup"><span data-stu-id="7ab65-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="7ab65-147">Bu, ya da ile `x:TypeArguments` `x:Type` birlikte iki özellik tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ab65-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>

- <span data-ttu-id="7ab65-148">Yükleme için XAML 2009 ' i işlerken WPF XAML uygulamasında bu özellik, türü kullanan belirli Framework özellikleri için örtük tür dönüştürme davranışına de eklenir <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="7ab65-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>

<span data-ttu-id="7ab65-149">WPF 'de XAML 2009 özelliklerini, ancak yalnızca gevşek XAML (biçimlendirme ile derlenen XAML) için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ab65-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="7ab65-150">WPF için biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 anahtar sözcüklerini ve özelliklerini desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="7ab65-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ab65-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ab65-151">See also</span></span>

- <xref:System.Windows.Style>
- [<span data-ttu-id="7ab65-152">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7ab65-152">Styling and Templating</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="7ab65-153">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="7ab65-153">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="7ab65-154">Biçimlendirme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="7ab65-154">Markup Extensions and WPF XAML</span></span>](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
