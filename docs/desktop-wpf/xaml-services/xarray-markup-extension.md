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
ms.openlocfilehash: b332c43d7f9ffe2117c9afe1ed625c3e3c869813
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072048"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="c6bee-102">x:Array İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="c6bee-102">x:Array Markup Extension</span></span>

<span data-ttu-id="c6bee-103">Biçimlendirme uzantısı aracılığıyla XAML'deki nesne dizileri için genel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6bee-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="c6bee-104">Bu , [MS-XAML] xaml `x:ArrayExtension` türüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="c6bee-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="c6bee-105">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="c6bee-105">XAML Object Element Usage</span></span>

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a><span data-ttu-id="c6bee-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="c6bee-106">XAML Values</span></span>

|||
|-|-|
|`typeName`|<span data-ttu-id="c6bee-107">İçereceğiniz `x:Array` türün adı.</span><span class="sxs-lookup"><span data-stu-id="c6bee-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="c6bee-108">`typeName`XAML türü tanımlarını içeren bir XAML ad alanı için önceden belirlenmiş olabilir (ve genellikle de vardır).</span><span class="sxs-lookup"><span data-stu-id="c6bee-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|
|`arrayContents`|<span data-ttu-id="c6bee-109">İçsel `ArrayExtension.Items` özelliğe atanan öğeler içeriği.</span><span class="sxs-lookup"><span data-stu-id="c6bee-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="c6bee-110">Genellikle, bu öğeler açılış ve kapanış etiketleri `x:Array` içinde bulunan bir veya daha fazla nesne öğeleri olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c6bee-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="c6bee-111">Burada belirtilen nesnelerin `typeName`XAML türüne atayabilmeleri beklenir.</span><span class="sxs-lookup"><span data-stu-id="c6bee-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c6bee-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6bee-112">Remarks</span></span>

<span data-ttu-id="c6bee-113">`Type`tüm `x:Array` nesne öğeleri için gerekli bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="c6bee-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="c6bee-114">Bir `Type` parametre değerinin `x:Type` biçimlendirme uzantısı kullanması gerekmez; türün kısa adı, dize olarak belirtilebilen bir XAML türüdür.</span><span class="sxs-lookup"><span data-stu-id="c6bee-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>

<span data-ttu-id="c6bee-115">.NET XAML Hizmetleri uygulamasında, giriş XAML türü ile oluşturulan <xref:System.Type> dizinin çıktı CLR'si arasındaki ilişki, biçimlendirme uzantıları için hizmet bağlamından etkilenir.</span><span class="sxs-lookup"><span data-stu-id="c6bee-115">In .NET XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="c6bee-116">Çıktı, <xref:System.Type> XAML şeması bağlamına ve bağlamın <xref:System.Xaml.XamlType> sağladığı hizmete göre gerekli olana <xref:System.Windows.Markup.IXamlTypeResolver> baktıktan sonra, giriş XAML tipinin çıktısi. <xref:System.Xaml.XamlType.UnderlyingType%2A></span><span class="sxs-lookup"><span data-stu-id="c6bee-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="c6bee-117">İşlendiğinde, dizi içeriği içsel `ArrayExtension.Items` özelliğe atanır.</span><span class="sxs-lookup"><span data-stu-id="c6bee-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="c6bee-118"><xref:System.Windows.Markup.ArrayExtension> Uygulamada, <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>bu.</span><span class="sxs-lookup"><span data-stu-id="c6bee-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c6bee-119">.NET XAML Hizmetleri uygulamasında, bu biçimlendirme uzantısı için <xref:System.Windows.Markup.ArrayExtension> işleme sınıf tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c6bee-119">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="c6bee-120"><xref:System.Windows.Markup.ArrayExtension>mühürlü değildir ve özel bir dizi türü için biçimlendirme uzantısı uygulaması için temel olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6bee-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>

<span data-ttu-id="c6bee-121">`x:Array`daha çok XAML'de genel dil genişletilebilirliği için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c6bee-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="c6bee-122">Ancak, `x:Array` XAML destekli koleksiyonları yapılandırılmış özellik içeriği olarak alan belirli özelliklerin XAML değerlerini belirtmek için de yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c6bee-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="c6bee-123">Örneğin, `x:Array` bir kullanım ile bir <xref:System.Collections.IEnumerable> özelliğin içeriğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6bee-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>

<span data-ttu-id="c6bee-124">`x:Array`biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="c6bee-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="c6bee-125">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c6bee-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="c6bee-126">`x:Array`alternatif öznitelik değer işleme sağlamak yerine, `x:Array` kendi iç metin içeriğinin alternatif işleme sağlar, çünkü kısmen bu kuralın bir istisnadır.</span><span class="sxs-lookup"><span data-stu-id="c6bee-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="c6bee-127">Bu davranış, varolan bir içerik modeli tarafından desteklenmeyen türlerin bir dizi halinde gruplandırılmasını ve daha sonra adlandırılmış diziye erişerek kod arkasında başvurulmasını sağlar; tek tek <xref:System.Array> dizi öğeleri almak için yöntemleri arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6bee-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>

<span data-ttu-id="c6bee-128">XAML'deki tüm biçimlendirme uzantıları ayraçları kullanır (bir{,} `)` XAML işlemcisinin bir biçimlendirme uzantısıöz değeri işlemesi gerektiğini kabul ettiği kuraldır) öznitelik sözdiziminde.</span><span class="sxs-lookup"><span data-stu-id="c6bee-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="c6bee-129">Genel olarak biçimlendirme uzantıları hakkında daha fazla bilgi için [XAML için Tür Dönüştürücüler ve Biçimlendirme Uzantıları'na](type-converters-and-markup-extensions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c6bee-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).</span></span>

<span data-ttu-id="c6bee-130">XAML 2009 `x:Array` yılında, bir biçimlendirme uzantısı yerine ilkel bir dil olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c6bee-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="c6bee-131">Daha fazla bilgi [için, Ortak XAML Dil İlkelleri için Yerleşik Türleri'ne](types-for-primitives.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c6bee-131">For more information, see [Built-in Types for Common XAML Language Primitives](types-for-primitives.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="c6bee-132">WPF Kullanım Notları</span><span class="sxs-lookup"><span data-stu-id="c6bee-132">WPF Usage Notes</span></span>

<span data-ttu-id="c6bee-133">Genellikle, bir `x:Array` doldurma nesne öğeleri [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML ad alanında var olan öğeler değildir ve varsayılan olmayan bir XAML ad alanı için bir önek eşlemesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c6bee-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>

<span data-ttu-id="c6bee-134">Örneğin, aşağıdaki iki dize basit bir dizi, `sys` önek (ve aynı zamanda) `x`dizi düzeyinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c6bee-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

<span data-ttu-id="c6bee-135">Dizi öğeleri olarak kullanılan özel türler için, sınıfın XAML'de nesne öğesi olarak anlık olarak kullanıma alınması gereksinimlerini de desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6bee-135">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="c6bee-136">Daha fazla bilgi için [WPF için XAML ve Özel Sınıflar'a](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c6bee-136">For more information, see [XAML and Custom Classes for WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6bee-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6bee-137">See also</span></span>

- [<span data-ttu-id="c6bee-138">Biçimlendirme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="c6bee-138">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="c6bee-139">WPF'den System.Xaml'e Geçirilen Türler</span><span class="sxs-lookup"><span data-stu-id="c6bee-139">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
