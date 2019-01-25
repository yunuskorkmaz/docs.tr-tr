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
# <a name="xarray-markup-extension"></a>x:Array İşaretleme Uzantısı
XAML işaretleme uzantısı aracılığıyla nesne dizileri için genel destek sağlar. Bu karşılık gelir `x:ArrayExtension` XAML [MS-XAML] yazın.  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`typeName`|Tür adı, kendi `x:Array` içerir. `typeName` olabilir (ve genellikle) önekli bir XAML için XAML içeren ad türü tanımlar.|  
|`arrayContents`|İç atanan öğeleri içerikler `ArrayExtension.Items` özelliği. Genellikle, bu öğeler bulunan bir veya daha fazla nesne öğeleri olarak belirtilen `x:Array` açılış ve kapanış etiketlerinin. Nesneleri belirtilen burada bekleniyor belirtilen XAML türüne atanabilir olmasını `typeName`.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Type` Tüm gerekli bir özniteliği olan `x:Array` nesne öğeleri. A `Type` parametre değeri kullanın gerekmez bir `x:Type` işaretleme uzantısı; kısa türün adını dize olarak belirtilen bir XAML türü olan.  
  
 .NET Framework XAML hizmetlerinde uygulama, giriş XAML türü ve ' % s'çıkış CLR arasındaki ilişkiyi <xref:System.Type> biçimlendirme uzantıları için hizmet bağlamı tarafından oluşturulan bir dizi etkilenir. Çıkış <xref:System.Type> olduğu <xref:System.Xaml.XamlType.UnderlyingType%2A> türünün gerekli bakan sonra giriş XAML <xref:System.Xaml.XamlType> XAML şema bağlama göre ve <xref:System.Windows.Markup.IXamlTypeResolver> Hizmet bağlamı sağlar.  
  
 Dizi içerikleri atanmış olan işlendiğinde `ArrayExtension.Items` iç özellik. İçinde <xref:System.Windows.Markup.ArrayExtension> uygulaması, bu tarafından temsil edilen <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.  
  
 .NET Framework XAML hizmetlerinde uygulamasında, bu işaretleme uzantısının işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.ArrayExtension> sınıfı. <xref:System.Windows.Markup.ArrayExtension> korumalı değil ve bir özel bir dizi türü için işaretleme uzantısı uygulaması için temel olarak kullanılabilir.  
  
 `x:Array` Daha fazla genel XAML dil genişletilebilirlikteki hedeflenen olur. Ancak `x:Array` XAML desteklenen koleksiyonları, yapılandırılmış özelliği içerik olarak ele belirli özelliklerin XAML değerleri belirtmek için yararlı olabilir. Örneğin, içeriği belirtebilirsiniz bir <xref:System.Collections.IEnumerable> özelliğiyle bir `x:Array` kullanım.  
  
 `x:Array` bir işaretleme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. `x:Array` kısmen bu kural için bir özel çünkü alternatif özniteliği değeri işleme sağlamak yerine `x:Array` iç metin içeriği alternatif işleme sağlar. Bu davranış, bir dizi içine gruplanır ve adlandırılmış dizi erişerek daha sonra arka plan kod içinde başvurulan, mevcut bir içerik modeli tarafından desteklenmeyebilir türleri sağlar; çağırabilirsiniz <xref:System.Array> dizi öğeleri almak için yöntemleri.  
  
 XAML içindeki tüm biçimlendirme uzantıları parantezler kullanın ({,} `)` kendi öznitelik sözdizimi içinde olduğu kuralı tarafından bir XAML işlemcisinin bir işaretleme uzantısı öznitelik değeri işlemesi gerekir. Genel olarak işaretleme uzantıları hakkında daha fazla bilgi için bkz. [tür dönüştürücüleri ve İşaretleme uzantıları için XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 XAML 2009 `x:Array` bir işaretleme uzantısı yerine basit dili olarak tanımlanır. Daha fazla bilgi için [XAML dili ortak temelleri için yerleşik türler](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 Genellikle, doldurmak nesne öğeleri bir `x:Array` mevcut öğesi olmayan [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML ad alanı ve bir varsayılan olmayan bir XAML ad alanı ön eki eşleşmesi gerekir.  
  
 Örneğin, iki dizenin basit bir dizi ile verilmiştir `sys` ön eki (ve ayrıca `x`) dizinin düzeyinde tanımlanan.  
  
 [xaml]  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 Dizi öğeleri kullanılan özel türleri sınıf ayrıca XAML içinde nesne öğeleri olarak oluşturulmasını gereksinimleri desteklemesi gerekir. Daha fazla bilgi için [XAML ve özel sınıflar için WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İşaretleme Uzantıları ve WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [WPF'den System.Xaml'e Geçirilen Türler](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
