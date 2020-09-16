---
title: x:Array İşaretleme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: b812939cbaa74576361de534c0d39ba45536cbcf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555178"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="37885-102">x:Array İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="37885-102">x:Array Markup Extension</span></span>

<span data-ttu-id="37885-103">Bir işaretleme uzantısı aracılığıyla XAML içindeki nesne dizileri için genel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="37885-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="37885-104">Bu, `x:ArrayExtension` [ms-xaml] içindeki xaml türüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="37885-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="37885-105">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="37885-105">XAML Object Element Usage</span></span>

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a><span data-ttu-id="37885-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="37885-106">XAML Values</span></span>

|||
|-|-|
|`typeName`|<span data-ttu-id="37885-107">`x:Array`Sahip olacağı türün adı.</span><span class="sxs-lookup"><span data-stu-id="37885-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="37885-108">`typeName` XAML türü tanımlarını içeren bir XAML ad alanı için ön eki olan (ve genellikle) olabilir.</span><span class="sxs-lookup"><span data-stu-id="37885-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|
|`arrayContents`|<span data-ttu-id="37885-109">İç özelliğe atanan öğe içeriği `ArrayExtension.Items` .</span><span class="sxs-lookup"><span data-stu-id="37885-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="37885-110">Genellikle, bu öğeler `x:Array` açılış ve kapanış etiketlerinin içinde bulunan bir veya daha fazla nesne öğesi olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="37885-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="37885-111">Burada belirtilen nesnelerin içinde belirtilen XAML türüne atanabilir olması beklenir `typeName` .</span><span class="sxs-lookup"><span data-stu-id="37885-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|

## <a name="remarks"></a><span data-ttu-id="37885-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37885-112">Remarks</span></span>

<span data-ttu-id="37885-113">`Type` Tüm nesne öğeleri için gerekli bir özniteliktir `x:Array` .</span><span class="sxs-lookup"><span data-stu-id="37885-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="37885-114">Bir `Type` parametre değerinin `x:Type` Biçimlendirme Uzantısı kullanması gerekmez; türün kısa adı bir dize olarak BELIRTIBILEN bir xaml türüdür.</span><span class="sxs-lookup"><span data-stu-id="37885-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>

<span data-ttu-id="37885-115">.NET XAML Hizmetleri uygulamasında, giriş XAML türü ve oluşturulan dizinin çıkış CLR arasındaki ilişki, <xref:System.Type> Biçimlendirme uzantıları için hizmet bağlamına göre etkilenir.</span><span class="sxs-lookup"><span data-stu-id="37885-115">In .NET XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="37885-116">Çıktı, <xref:System.Type> <xref:System.Xaml.XamlType.UnderlyingType%2A> <xref:System.Xaml.XamlType> xaml şema bağlamına ve bağlamın sağladığı hizmete bağlı olarak gerekli olan arama sonrasında giriş xaml türünden oluşur <xref:System.Windows.Markup.IXamlTypeResolver> .</span><span class="sxs-lookup"><span data-stu-id="37885-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="37885-117">İşlendiğinde, dizi içeriği `ArrayExtension.Items` iç özelliğe atanır.</span><span class="sxs-lookup"><span data-stu-id="37885-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="37885-118"><xref:System.Windows.Markup.ArrayExtension>Uygulamada, bu tarafından temsil edilir <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="37885-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="37885-119">.NET XAML Hizmetleri uygulamasında, bu biçimlendirme uzantısının işlenmesi sınıfı tarafından tanımlanır <xref:System.Windows.Markup.ArrayExtension> .</span><span class="sxs-lookup"><span data-stu-id="37885-119">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="37885-120"><xref:System.Windows.Markup.ArrayExtension> Sealed değildir ve özel bir dizi türü için biçimlendirme uzantısı uygulamasının temeli olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="37885-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>

<span data-ttu-id="37885-121">`x:Array` , XAML 'de Genel dil genişletilebilirliği için daha yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="37885-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="37885-122">Ancak `x:Array` XAML tarafından desteklenen koleksiyonları yapılandırılmış Özellik içerikleri olarak alan belirli ÖZELLIKLERIN xaml değerlerini belirtmek için de kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="37885-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="37885-123">Örneğin, bir <xref:System.Collections.IEnumerable> özelliğin içeriğini kullanım ile belirtebilirsiniz `x:Array` .</span><span class="sxs-lookup"><span data-stu-id="37885-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>

<span data-ttu-id="37885-124">`x:Array` bir biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="37885-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="37885-125">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="37885-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="37885-126">`x:Array` , alternatif öznitelik değeri işleme sağlamak yerine, `x:Array` iç metin içeriğinin alternatif işlemesini sağlayan bu kural için kısmen bir özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="37885-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="37885-127">Bu davranış, varolan bir içerik modeli tarafından bir dizide gruplanmak ve daha sonra adlandırılmış diziye erişerek kod arkasında başvurulmak üzere desteklenmeyen türleri sağlar; <xref:System.Array> tek tek dizi öğelerini almak için yöntemler çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37885-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>

<span data-ttu-id="37885-128">XAML 'deki tüm biçimlendirme uzantıları, bir {,} `)` XAML işlemcisinin bir biçimlendirme uzantısının öznitelik değerini işlemesi gerektiğini tanıdığı kural olan küme ayraçlarını (öznitelik sözdiziminde) kullanır.</span><span class="sxs-lookup"><span data-stu-id="37885-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="37885-129">Genel olarak biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [xaml Için tür dönüştürücüleri ve biçimlendirme uzantıları](type-converters-and-markup-extensions.md).</span><span class="sxs-lookup"><span data-stu-id="37885-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).</span></span>

<span data-ttu-id="37885-130">XAML 2009 ' de, `x:Array` biçimlendirme uzantısı yerine bir dil temel olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="37885-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="37885-131">Daha fazla bilgi için bkz. [genel xaml dil temelleri Için yerleşik türler](types-for-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="37885-131">For more information, see [Built-in Types for Common XAML Language Primitives](types-for-primitives.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="37885-132">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="37885-132">WPF Usage Notes</span></span>

<span data-ttu-id="37885-133">Genellikle, öğesini dolduran nesne öğeleri `x:Array` xaml ad alanında var olan öğeler değildir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ve varsayılan olmayan xaml ad alanı için bir önek eşlemesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="37885-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>

<span data-ttu-id="37885-134">Örneğin, aşağıdaki `sys` önek (ve ayrıca `x` ) dizi düzeyinde tanımlanmış olan iki dizenin basit bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="37885-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

<span data-ttu-id="37885-135">Dizi öğeleri olarak kullanılan özel türler için, sınıfı XAML 'de nesne öğeleri olarak örneği oluşturulması gereken gereksinimleri de desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="37885-135">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="37885-136">Daha fazla bilgi için bkz. [WPF Için XAML ve özel sınıflar](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf).</span><span class="sxs-lookup"><span data-stu-id="37885-136">For more information, see [XAML and Custom Classes for WPF](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf).</span></span>

## <a name="see-also"></a><span data-ttu-id="37885-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37885-137">See also</span></span>

- [<span data-ttu-id="37885-138">Biçimlendirme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="37885-138">Markup Extensions and WPF XAML</span></span>](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
- [<span data-ttu-id="37885-139">WPF'den System.Xaml'e Geçirilen Türler</span><span class="sxs-lookup"><span data-stu-id="37885-139">Types Migrated from WPF to System.Xaml</span></span>](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
