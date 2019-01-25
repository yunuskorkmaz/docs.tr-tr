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
ms.openlocfilehash: e94928f17a31cdadae11f69c37a4f148452b5d2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699746"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="8bdef-102">x:Array İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="8bdef-102">x:Array Markup Extension</span></span>
<span data-ttu-id="8bdef-103">XAML işaretleme uzantısı aracılığıyla nesne dizileri için genel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bdef-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="8bdef-104">Bu karşılık gelir `x:ArrayExtension` XAML [MS-XAML] yazın.</span><span class="sxs-lookup"><span data-stu-id="8bdef-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="8bdef-105">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="8bdef-105">XAML Object Element Usage</span></span>  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="8bdef-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="8bdef-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`typeName`|<span data-ttu-id="8bdef-107">Tür adı, kendi `x:Array` içerir.</span><span class="sxs-lookup"><span data-stu-id="8bdef-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="8bdef-108">`typeName` olabilir (ve genellikle) önekli bir XAML için XAML içeren ad türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8bdef-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|  
|`arrayContents`|<span data-ttu-id="8bdef-109">İç atanan öğeleri içerikler `ArrayExtension.Items` özelliği.</span><span class="sxs-lookup"><span data-stu-id="8bdef-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="8bdef-110">Genellikle, bu öğeler bulunan bir veya daha fazla nesne öğeleri olarak belirtilen `x:Array` açılış ve kapanış etiketlerinin.</span><span class="sxs-lookup"><span data-stu-id="8bdef-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="8bdef-111">Nesneleri belirtilen burada bekleniyor belirtilen XAML türüne atanabilir olmasını `typeName`.</span><span class="sxs-lookup"><span data-stu-id="8bdef-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bdef-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bdef-112">Remarks</span></span>  
 <span data-ttu-id="8bdef-113">`Type` Tüm gerekli bir özniteliği olan `x:Array` nesne öğeleri.</span><span class="sxs-lookup"><span data-stu-id="8bdef-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="8bdef-114">A `Type` parametre değeri kullanın gerekmez bir `x:Type` işaretleme uzantısı; kısa türün adını dize olarak belirtilen bir XAML türü olan.</span><span class="sxs-lookup"><span data-stu-id="8bdef-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>  
  
 <span data-ttu-id="8bdef-115">.NET Framework XAML hizmetlerinde uygulama, giriş XAML türü ve ' % s'çıkış CLR arasındaki ilişkiyi <xref:System.Type> biçimlendirme uzantıları için hizmet bağlamı tarafından oluşturulan bir dizi etkilenir.</span><span class="sxs-lookup"><span data-stu-id="8bdef-115">In the .NET Framework XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="8bdef-116">Çıkış <xref:System.Type> olduğu <xref:System.Xaml.XamlType.UnderlyingType%2A> türünün gerekli bakan sonra giriş XAML <xref:System.Xaml.XamlType> XAML şema bağlama göre ve <xref:System.Windows.Markup.IXamlTypeResolver> Hizmet bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bdef-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="8bdef-117">Dizi içerikleri atanmış olan işlendiğinde `ArrayExtension.Items` iç özellik.</span><span class="sxs-lookup"><span data-stu-id="8bdef-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="8bdef-118">İçinde <xref:System.Windows.Markup.ArrayExtension> uygulaması, bu tarafından temsil edilen <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8bdef-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="8bdef-119">.NET Framework XAML hizmetlerinde uygulamasında, bu işaretleme uzantısının işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.ArrayExtension> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8bdef-119">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="8bdef-120"><xref:System.Windows.Markup.ArrayExtension> korumalı değil ve bir özel bir dizi türü için işaretleme uzantısı uygulaması için temel olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8bdef-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>  
  
 <span data-ttu-id="8bdef-121">`x:Array` Daha fazla genel XAML dil genişletilebilirlikteki hedeflenen olur.</span><span class="sxs-lookup"><span data-stu-id="8bdef-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="8bdef-122">Ancak `x:Array` XAML desteklenen koleksiyonları, yapılandırılmış özelliği içerik olarak ele belirli özelliklerin XAML değerleri belirtmek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8bdef-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="8bdef-123">Örneğin, içeriği belirtebilirsiniz bir <xref:System.Collections.IEnumerable> özelliğiyle bir `x:Array` kullanım.</span><span class="sxs-lookup"><span data-stu-id="8bdef-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>  
  
 <span data-ttu-id="8bdef-124">`x:Array` bir işaretleme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="8bdef-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="8bdef-125">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8bdef-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="8bdef-126">`x:Array` kısmen bu kural için bir özel çünkü alternatif özniteliği değeri işleme sağlamak yerine `x:Array` iç metin içeriği alternatif işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bdef-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="8bdef-127">Bu davranış, bir dizi içine gruplanır ve adlandırılmış dizi erişerek daha sonra arka plan kod içinde başvurulan, mevcut bir içerik modeli tarafından desteklenmeyebilir türleri sağlar; çağırabilirsiniz <xref:System.Array> dizi öğeleri almak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="8bdef-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>  
  
 <span data-ttu-id="8bdef-128">XAML içindeki tüm biçimlendirme uzantıları parantezler kullanın ({,} `)` kendi öznitelik sözdizimi içinde olduğu kuralı tarafından bir XAML işlemcisinin bir işaretleme uzantısı öznitelik değeri işlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8bdef-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="8bdef-129">Genel olarak işaretleme uzantıları hakkında daha fazla bilgi için bkz. [tür dönüştürücüleri ve İşaretleme uzantıları için XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="8bdef-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span></span>  
  
 <span data-ttu-id="8bdef-130">XAML 2009 `x:Array` bir işaretleme uzantısı yerine basit dili olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8bdef-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="8bdef-131">Daha fazla bilgi için [XAML dili ortak temelleri için yerleşik türler](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="8bdef-131">For more information, see [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="8bdef-132">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="8bdef-132">WPF Usage Notes</span></span>  
 <span data-ttu-id="8bdef-133">Genellikle, doldurmak nesne öğeleri bir `x:Array` mevcut öğesi olmayan [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML ad alanı ve bir varsayılan olmayan bir XAML ad alanı ön eki eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8bdef-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>  
  
 <span data-ttu-id="8bdef-134">Örneğin, iki dizenin basit bir dizi ile verilmiştir `sys` ön eki (ve ayrıca `x`) dizinin düzeyinde tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="8bdef-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>  
  
 <span data-ttu-id="8bdef-135">[xaml]</span><span class="sxs-lookup"><span data-stu-id="8bdef-135">[xaml]</span></span>  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 <span data-ttu-id="8bdef-136">Dizi öğeleri kullanılan özel türleri sınıf ayrıca XAML içinde nesne öğeleri olarak oluşturulmasını gereksinimleri desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8bdef-136">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="8bdef-137">Daha fazla bilgi için [XAML ve özel sınıflar için WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="8bdef-137">For more information, see [XAML and Custom Classes for WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bdef-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bdef-138">See also</span></span>
- [<span data-ttu-id="8bdef-139">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="8bdef-139">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="8bdef-140">WPF'den System.Xaml'e Geçirilen Türler</span><span class="sxs-lookup"><span data-stu-id="8bdef-140">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
