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
# <a name="xarray-markup-extension"></a>x:Array İşaretleme Uzantısı

Bir işaretleme uzantısı aracılığıyla XAML içindeki nesne dizileri için genel destek sağlar. Bu, `x:ArrayExtension` [ms-xaml] içindeki xaml türüne karşılık gelir.

## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`typeName`|`x:Array`Sahip olacağı türün adı. `typeName` XAML türü tanımlarını içeren bir XAML ad alanı için ön eki olan (ve genellikle) olabilir.|
|`arrayContents`|İç özelliğe atanan öğe içeriği `ArrayExtension.Items` . Genellikle, bu öğeler `x:Array` açılış ve kapanış etiketlerinin içinde bulunan bir veya daha fazla nesne öğesi olarak belirtilir. Burada belirtilen nesnelerin içinde belirtilen XAML türüne atanabilir olması beklenir `typeName` .|

## <a name="remarks"></a>Açıklamalar

`Type` Tüm nesne öğeleri için gerekli bir özniteliktir `x:Array` . Bir `Type` parametre değerinin `x:Type` Biçimlendirme Uzantısı kullanması gerekmez; türün kısa adı bir dize olarak BELIRTIBILEN bir xaml türüdür.

.NET XAML Hizmetleri uygulamasında, giriş XAML türü ve oluşturulan dizinin çıkış CLR arasındaki ilişki, <xref:System.Type> Biçimlendirme uzantıları için hizmet bağlamına göre etkilenir. Çıktı, <xref:System.Type> <xref:System.Xaml.XamlType.UnderlyingType%2A> <xref:System.Xaml.XamlType> xaml şema bağlamına ve bağlamın sağladığı hizmete bağlı olarak gerekli olan arama sonrasında giriş xaml türünden oluşur <xref:System.Windows.Markup.IXamlTypeResolver> .

İşlendiğinde, dizi içeriği `ArrayExtension.Items` iç özelliğe atanır. <xref:System.Windows.Markup.ArrayExtension>Uygulamada, bu tarafından temsil edilir <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType> .

.NET XAML Hizmetleri uygulamasında, bu biçimlendirme uzantısının işlenmesi sınıfı tarafından tanımlanır <xref:System.Windows.Markup.ArrayExtension> . <xref:System.Windows.Markup.ArrayExtension> Sealed değildir ve özel bir dizi türü için biçimlendirme uzantısı uygulamasının temeli olarak kullanılabilir.

`x:Array` , XAML 'de Genel dil genişletilebilirliği için daha yöneliktir. Ancak `x:Array` XAML tarafından desteklenen koleksiyonları yapılandırılmış Özellik içerikleri olarak alan belirli ÖZELLIKLERIN xaml değerlerini belirtmek için de kullanışlı olabilir. Örneğin, bir <xref:System.Collections.IEnumerable> özelliğin içeriğini kullanım ile belirtebilirsiniz `x:Array` .

`x:Array` bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. `x:Array` , alternatif öznitelik değeri işleme sağlamak yerine, `x:Array` iç metin içeriğinin alternatif işlemesini sağlayan bu kural için kısmen bir özel durumdur. Bu davranış, varolan bir içerik modeli tarafından bir dizide gruplanmak ve daha sonra adlandırılmış diziye erişerek kod arkasında başvurulmak üzere desteklenmeyen türleri sağlar; <xref:System.Array> tek tek dizi öğelerini almak için yöntemler çağırabilirsiniz.

XAML 'deki tüm biçimlendirme uzantıları, bir {,} `)` XAML işlemcisinin bir biçimlendirme uzantısının öznitelik değerini işlemesi gerektiğini tanıdığı kural olan küme ayraçlarını (öznitelik sözdiziminde) kullanır. Genel olarak biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [xaml Için tür dönüştürücüleri ve biçimlendirme uzantıları](type-converters-and-markup-extensions.md).

XAML 2009 ' de, `x:Array` biçimlendirme uzantısı yerine bir dil temel olarak tanımlanmıştır. Daha fazla bilgi için bkz. [genel xaml dil temelleri Için yerleşik türler](types-for-primitives.md).

## <a name="wpf-usage-notes"></a>WPF kullanım notları

Genellikle, öğesini dolduran nesne öğeleri `x:Array` xaml ad alanında var olan öğeler değildir [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ve varsayılan olmayan xaml ad alanı için bir önek eşlemesi gerektirir.

Örneğin, aşağıdaki `sys` önek (ve ayrıca `x` ) dizi düzeyinde tanımlanmış olan iki dizenin basit bir dizisidir.

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

Dizi öğeleri olarak kullanılan özel türler için, sınıfı XAML 'de nesne öğeleri olarak örneği oluşturulması gereken gereksinimleri de desteklemelidir. Daha fazla bilgi için bkz. [WPF Için XAML ve özel sınıflar](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf).

## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme Uzantıları ve WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
- [WPF'den System.Xaml'e Geçirilen Türler](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
