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
# <a name="xarray-markup-extension"></a>x:Array İşaretleme Uzantısı
Nesnelerin XAML biçimlendirme uzantısı aracılığıyla diziler için genel destek sağlar. Bu karşılık `x:ArrayExtension` [MS-XAML] XAML yazın.  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`typeName`|Türünün adı, sizin `x:Array` içerecektir. `typeName` olabilir (ve genellikle) XAML için önek XAML içeren ad alanını yazın tanımlar.|  
|`arrayContents`|İç için atanan öğeleri içerikler `ArrayExtension.Items` özelliği. Genellikle, bu öğeler içinde bulunan bir veya daha fazla nesne öğeleri olarak belirtilen `x:Array` açma ve kapatma etiketleri. Nesneleri belirtilen burada bekleniyor belirtilen XAML türüne atanabilir olması `typeName`.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Type` gerekli bir öznitelik tümüdür `x:Array` nesne öğeleri. A `Type` parametre değeri kullanmak gerekmez bir `x:Type` biçimlendirme uzantısı; kısa türünün adı olan bir dize olarak belirtilen bir XAML türü.  
  
 .NET Framework XAML Hizmetleri uygulaması, giriş XAML türü ve CLR çıkış arasındaki ilişkiyi <xref:System.Type> oluşturulmuş bir dizi hizmet bağlam için işaretleme uzantıları tarafından etkilenir. Çıktı <xref:System.Type> olan <xref:System.Xaml.XamlType.UnderlyingType%2A> gerekli bakan sonra giriş XAML türü <xref:System.Xaml.XamlType> XAML şema bağlamına dayalı ve <xref:System.Windows.Markup.IXamlTypeResolver> Hizmet bağlamı sağlar.  
  
 Dizi içeriği atanmış olan işlendiğinde, `ArrayExtension.Items` iç özelliği. İçinde <xref:System.Windows.Markup.ArrayExtension> uygulaması, bu belirtildiği <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.  
  
 .NET Framework XAML hizmetlerinde uygulamasında bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.ArrayExtension> sınıfı. <xref:System.Windows.Markup.ArrayExtension> korumalı değil ve bir özel dizi türü için bir biçimlendirme uzantısı uygulama için temel olarak kullanılabilir.  
  
 `x:Array` Daha fazla bilgi için genel dil genişletilebilirlik XAML'de hedeflenen olur. Ancak `x:Array` XAML desteklenen koleksiyonları yapısal özellik içeriklerini ele belirli özelliklerin XAML değerleri belirlemek için yararlı olabilir. Örneğin, içeriği belirtebilirsiniz bir <xref:System.Collections.IEnumerable> özelliği ile bir `x:Array` kullanımı.  
  
 `x:Array` bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. `x:Array` kısmen bu kural için bir özel çünkü alternatif öznitelik değeri işleme sağlama yerine `x:Array` iç metin içeriğini alternatif işlenmesini sağlar. Bu davranış bir diziye gruplandırılmış ve adlandırılmış dizi erişerek daha sonra kod arkasında başvurulan için varolan bir içerik modeli tarafından desteklenmeyebilir türleri sağlar; çağırabilirsiniz <xref:System.Array> tek tek dizi öğeleri almak için yöntemleri.  
  
 XAML'de tüm biçimlendirme uzantıları küme ayraçları kullanın ({,} `)` kendi öznitelik sözdiziminde olduğu olarak XAML işlemci tanıdığı biçimlendirme uzantısı öznitelik değeri işlemelidir kuralı. Genel olarak işaretleme uzantıları hakkında daha fazla bilgi için bkz: [tür dönüştürücüleri ve İşaretleme uzantıları XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 XAML 2009 `x:Array` biçimlendirme uzantısı yerine basit bir dil olarak tanımlanır. Daha fazla bilgi için bkz: [XAML dili ortak temelleri için yerleşik türler](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 Genellikle, doldurmak nesne öğelerinin bir `x:Array` mevcut öğeleri olmayan [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML ad uzayı ve varsayılan olmayan XAML ad uzayı için önek eşleştirme gerektirir.  
  
 Örneğin, iki dizeyi basit bir dizi ile verilmiştir `sys` önek (ve ayrıca `x`) dizi düzeyinde tanımlanan.  
  
 [xaml]  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 Dizi öğeleri olarak kullanılan özel türler için sınıf ayrıca XAML'de nesne öğeleri oluşturulmasını gereksinimleri desteklemesi gerekir. Daha fazla bilgi için bkz: [XAML ve WPF için özel sınıfları](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşaretleme Uzantıları ve WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [WPF'den System.Xaml'e Geçirilen Türler](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
