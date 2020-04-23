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
# <a name="xarray-markup-extension"></a>x:Array İşaretleme Uzantısı

Biçimlendirme uzantısı aracılığıyla XAML'deki nesne dizileri için genel destek sağlar. Bu , [MS-XAML] xaml `x:ArrayExtension` türüne karşılık gelir.

## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`typeName`|İçereceğiniz `x:Array` türün adı. `typeName`XAML türü tanımlarını içeren bir XAML ad alanı için önceden belirlenmiş olabilir (ve genellikle de vardır).|
|`arrayContents`|İçsel `ArrayExtension.Items` özelliğe atanan öğeler içeriği. Genellikle, bu öğeler açılış ve kapanış etiketleri `x:Array` içinde bulunan bir veya daha fazla nesne öğeleri olarak belirtilir. Burada belirtilen nesnelerin `typeName`XAML türüne atayabilmeleri beklenir.|

## <a name="remarks"></a>Açıklamalar

`Type`tüm `x:Array` nesne öğeleri için gerekli bir özniteliktir. Bir `Type` parametre değerinin `x:Type` biçimlendirme uzantısı kullanması gerekmez; türün kısa adı, dize olarak belirtilebilen bir XAML türüdür.

.NET XAML Hizmetleri uygulamasında, giriş XAML türü ile oluşturulan <xref:System.Type> dizinin çıktı CLR'si arasındaki ilişki, biçimlendirme uzantıları için hizmet bağlamından etkilenir. Çıktı, <xref:System.Type> XAML şeması bağlamına ve bağlamın <xref:System.Xaml.XamlType> sağladığı hizmete göre gerekli olana <xref:System.Windows.Markup.IXamlTypeResolver> baktıktan sonra, giriş XAML tipinin çıktısi. <xref:System.Xaml.XamlType.UnderlyingType%2A>

İşlendiğinde, dizi içeriği içsel `ArrayExtension.Items` özelliğe atanır. <xref:System.Windows.Markup.ArrayExtension> Uygulamada, <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>bu.

.NET XAML Hizmetleri uygulamasında, bu biçimlendirme uzantısı için <xref:System.Windows.Markup.ArrayExtension> işleme sınıf tarafından tanımlanır. <xref:System.Windows.Markup.ArrayExtension>mühürlü değildir ve özel bir dizi türü için biçimlendirme uzantısı uygulaması için temel olarak kullanılabilir.

`x:Array`daha çok XAML'de genel dil genişletilebilirliği için tasarlanmıştır. Ancak, `x:Array` XAML destekli koleksiyonları yapılandırılmış özellik içeriği olarak alan belirli özelliklerin XAML değerlerini belirtmek için de yararlı olabilir. Örneğin, `x:Array` bir kullanım ile bir <xref:System.Collections.IEnumerable> özelliğin içeriğini belirtebilirsiniz.

`x:Array`biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. `x:Array`alternatif öznitelik değer işleme sağlamak yerine, `x:Array` kendi iç metin içeriğinin alternatif işleme sağlar, çünkü kısmen bu kuralın bir istisnadır. Bu davranış, varolan bir içerik modeli tarafından desteklenmeyen türlerin bir dizi halinde gruplandırılmasını ve daha sonra adlandırılmış diziye erişerek kod arkasında başvurulmasını sağlar; tek tek <xref:System.Array> dizi öğeleri almak için yöntemleri arayabilirsiniz.

XAML'deki tüm biçimlendirme uzantıları ayraçları kullanır (bir{,} `)` XAML işlemcisinin bir biçimlendirme uzantısıöz değeri işlemesi gerektiğini kabul ettiği kuraldır) öznitelik sözdiziminde. Genel olarak biçimlendirme uzantıları hakkında daha fazla bilgi için [XAML için Tür Dönüştürücüler ve Biçimlendirme Uzantıları'na](type-converters-and-markup-extensions.md)bakın.

XAML 2009 `x:Array` yılında, bir biçimlendirme uzantısı yerine ilkel bir dil olarak tanımlanır. Daha fazla bilgi [için, Ortak XAML Dil İlkelleri için Yerleşik Türleri'ne](types-for-primitives.md)bakın.

## <a name="wpf-usage-notes"></a>WPF Kullanım Notları

Genellikle, bir `x:Array` doldurma nesne öğeleri [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML ad alanında var olan öğeler değildir ve varsayılan olmayan bir XAML ad alanı için bir önek eşlemesi gerektirir.

Örneğin, aşağıdaki iki dize basit bir dizi, `sys` önek (ve aynı zamanda) `x`dizi düzeyinde tanımlanır.

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

Dizi öğeleri olarak kullanılan özel türler için, sınıfın XAML'de nesne öğesi olarak anlık olarak kullanıma alınması gereksinimlerini de desteklemesi gerekir. Daha fazla bilgi için [WPF için XAML ve Özel Sınıflar'a](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme Uzantıları ve WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [WPF'den System.Xaml'e Geçirilen Türler](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
