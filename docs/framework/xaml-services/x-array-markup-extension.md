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
ms.openlocfilehash: 7c728b63c16d8f24c4ad68d07e6d174f510204ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565019"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="31b20-102">x:Array İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="31b20-102">x:Array Markup Extension</span></span>
<span data-ttu-id="31b20-103">Nesnelerin XAML biçimlendirme uzantısı aracılığıyla diziler için genel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="31b20-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="31b20-104">Bu karşılık `x:ArrayExtension` [MS-XAML] XAML yazın.</span><span class="sxs-lookup"><span data-stu-id="31b20-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="31b20-105">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="31b20-105">XAML Object Element Usage</span></span>  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="31b20-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="31b20-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`typeName`|<span data-ttu-id="31b20-107">Türünün adı, sizin `x:Array` içerecektir.</span><span class="sxs-lookup"><span data-stu-id="31b20-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="31b20-108">`typeName` olabilir (ve genellikle) XAML için önek XAML içeren ad alanını yazın tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31b20-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|  
|`arrayContents`|<span data-ttu-id="31b20-109">İç için atanan öğeleri içerikler `ArrayExtension.Items` özelliği.</span><span class="sxs-lookup"><span data-stu-id="31b20-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="31b20-110">Genellikle, bu öğeler içinde bulunan bir veya daha fazla nesne öğeleri olarak belirtilen `x:Array` açma ve kapatma etiketleri.</span><span class="sxs-lookup"><span data-stu-id="31b20-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="31b20-111">Nesneleri belirtilen burada bekleniyor belirtilen XAML türüne atanabilir olması `typeName`.</span><span class="sxs-lookup"><span data-stu-id="31b20-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31b20-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31b20-112">Remarks</span></span>  
 <span data-ttu-id="31b20-113">`Type` gerekli bir öznitelik tümüdür `x:Array` nesne öğeleri.</span><span class="sxs-lookup"><span data-stu-id="31b20-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="31b20-114">A `Type` parametre değeri kullanmak gerekmez bir `x:Type` biçimlendirme uzantısı; kısa türünün adı olan bir dize olarak belirtilen bir XAML türü.</span><span class="sxs-lookup"><span data-stu-id="31b20-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>  
  
 <span data-ttu-id="31b20-115">.NET Framework XAML Hizmetleri uygulaması, giriş XAML türü ve CLR çıkış arasındaki ilişkiyi <xref:System.Type> oluşturulmuş bir dizi hizmet bağlam için işaretleme uzantıları tarafından etkilenir.</span><span class="sxs-lookup"><span data-stu-id="31b20-115">In the .NET Framework XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="31b20-116">Çıktı <xref:System.Type> olan <xref:System.Xaml.XamlType.UnderlyingType%2A> gerekli bakan sonra giriş XAML türü <xref:System.Xaml.XamlType> XAML şema bağlamına dayalı ve <xref:System.Windows.Markup.IXamlTypeResolver> Hizmet bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="31b20-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="31b20-117">Dizi içeriği atanmış olan işlendiğinde, `ArrayExtension.Items` iç özelliği.</span><span class="sxs-lookup"><span data-stu-id="31b20-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="31b20-118">İçinde <xref:System.Windows.Markup.ArrayExtension> uygulaması, bu belirtildiği <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="31b20-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="31b20-119">.NET Framework XAML hizmetlerinde uygulamasında bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.ArrayExtension> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="31b20-119">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="31b20-120"><xref:System.Windows.Markup.ArrayExtension> korumalı değil ve bir özel dizi türü için bir biçimlendirme uzantısı uygulama için temel olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31b20-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>  
  
 <span data-ttu-id="31b20-121">`x:Array` Daha fazla bilgi için genel dil genişletilebilirlik XAML'de hedeflenen olur.</span><span class="sxs-lookup"><span data-stu-id="31b20-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="31b20-122">Ancak `x:Array` XAML desteklenen koleksiyonları yapısal özellik içeriklerini ele belirli özelliklerin XAML değerleri belirlemek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="31b20-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="31b20-123">Örneğin, içeriği belirtebilirsiniz bir <xref:System.Collections.IEnumerable> özelliği ile bir `x:Array` kullanımı.</span><span class="sxs-lookup"><span data-stu-id="31b20-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>  
  
 <span data-ttu-id="31b20-124">`x:Array` bir biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="31b20-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="31b20-125">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="31b20-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="31b20-126">`x:Array` kısmen bu kural için bir özel çünkü alternatif öznitelik değeri işleme sağlama yerine `x:Array` iç metin içeriğini alternatif işlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="31b20-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="31b20-127">Bu davranış bir diziye gruplandırılmış ve adlandırılmış dizi erişerek daha sonra kod arkasında başvurulan için varolan bir içerik modeli tarafından desteklenmeyebilir türleri sağlar; çağırabilirsiniz <xref:System.Array> tek tek dizi öğeleri almak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="31b20-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>  
  
 <span data-ttu-id="31b20-128">XAML'de tüm biçimlendirme uzantıları küme ayraçları kullanın ({,} `)` kendi öznitelik sözdiziminde olduğu olarak XAML işlemci tanıdığı biçimlendirme uzantısı öznitelik değeri işlemelidir kuralı.</span><span class="sxs-lookup"><span data-stu-id="31b20-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="31b20-129">Genel olarak işaretleme uzantıları hakkında daha fazla bilgi için bkz: [tür dönüştürücüleri ve İşaretleme uzantıları XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="31b20-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span></span>  
  
 <span data-ttu-id="31b20-130">XAML 2009 `x:Array` biçimlendirme uzantısı yerine basit bir dil olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="31b20-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="31b20-131">Daha fazla bilgi için bkz: [XAML dili ortak temelleri için yerleşik türler](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="31b20-131">For more information, see [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="31b20-132">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="31b20-132">WPF Usage Notes</span></span>  
 <span data-ttu-id="31b20-133">Genellikle, doldurmak nesne öğelerinin bir `x:Array` mevcut öğeleri olmayan [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML ad uzayı ve varsayılan olmayan XAML ad uzayı için önek eşleştirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="31b20-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>  
  
 <span data-ttu-id="31b20-134">Örneğin, iki dizeyi basit bir dizi ile verilmiştir `sys` önek (ve ayrıca `x`) dizi düzeyinde tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="31b20-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>  
  
 <span data-ttu-id="31b20-135">[xaml]</span><span class="sxs-lookup"><span data-stu-id="31b20-135">[xaml]</span></span>  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 <span data-ttu-id="31b20-136">Dizi öğeleri olarak kullanılan özel türler için sınıf ayrıca XAML'de nesne öğeleri oluşturulmasını gereksinimleri desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="31b20-136">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="31b20-137">Daha fazla bilgi için bkz: [XAML ve WPF için özel sınıfları](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="31b20-137">For more information, see [XAML and Custom Classes for WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b20-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31b20-138">See Also</span></span>  
 [<span data-ttu-id="31b20-139">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="31b20-139">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="31b20-140">WPF'den System.Xaml'e Geçirilen Türler</span><span class="sxs-lookup"><span data-stu-id="31b20-140">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
