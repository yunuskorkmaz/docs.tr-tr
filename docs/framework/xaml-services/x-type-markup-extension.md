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
ms.openlocfilehash: e4d56c5b5deda0bd1df8827020e0b76cc6276c1c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112367"
---
# <a name="xtype-markup-extension"></a>x:Type İşaretleme Uzantısı
CLR'nin sağladığı <xref:System.Type> belirtilen bir XAML türü için temel alınan türü bir nesne.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`prefix`|İsteğe bağlı. Eşleyen bir varsayılan olmayan XAML ad alanı öneki. Bir önek belirleyerek sık gerekli değildir. Açıklamalara bakın.|  
|`typeNameValue`|Gerekli. Geçerli varsayılan XAML ad alanına çözülebilir bir tür adı; veya belirtilen eşlenmiş önek, `prefix` sağlanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Type` İşaretleme uzantısı için benzer bir işlev olan `typeof()` C# dilinde işleç veya `GetType` Visual Basic'de işleç.  
  
 `x:Type` İşaretleme uzantısı türü alan özellikleri için gelen dize dönüştürme davranış sağlayan <xref:System.Type>. Giriş bir XAML türüdür. XAML türü giriş ve çıkış CLR arasındaki ilişkiyi <xref:System.Type> çıkış olan <xref:System.Type> olduğu <xref:System.Xaml.XamlType.UnderlyingType%2A> giriş <xref:System.Xaml.XamlType>, gerekli bakan sonra <xref:System.Xaml.XamlType> XAML şema içeriği ve göre<xref:System.Windows.Markup.IXamlTypeResolver>Hizmet bağlamı sağlar.  
  
 .NET Framework XAML hizmetlerinde bu işaretleme uzantısının işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.TypeExtension> sınıfı.  
  
 Bazı özellikler, belirli framework uygulamalarında ele <xref:System.Type> bir değer türünün adını doğrudan kabul (türünün dize değerini `Name`). Ancak, bu davranışı uygulayan karmaşık bir senaryo değildir. Örneğin, aşağıdaki "WPF kullanım notları" bölümüne bakın.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Sonra sağlanan dize belirteci `x:Type` tanımlayıcı dizesi olarak atandığı <xref:System.Windows.Markup.TypeExtension.TypeName%2A> temel değer <xref:System.Windows.Markup.TypeExtension> uzantısı sınıfı. Varsayılan XAML şema içeriği için CLR türlerine bağlı, .NET Framework XAML hizmetlerinde bu özniteliğin değeri ya da altındadır <xref:System.Reflection.MemberInfo.Name%2A> istenen türde veya içeren <xref:System.Reflection.MemberInfo.Name%2A> varsayılan olmayan XAML ad alanı için bir ön eke göre öncesinde eşleme.  
  
 `x:Type` Nesne öğesi sözdiziminde işaretleme uzantısı kullanılabilir. Bu durumda, değerini belirterek <xref:System.Windows.Markup.TypeExtension.TypeName%2A> özelliği uzantısı düzgün başlatmak için gereklidir.  
  
 `x:Type` İşaretleme uzantısı ayrıntılı bir özniteliği olarak da kullanılabilir; ancak bu kullanım tipik: `<object property="{x:Type TypeName=typeNameValue}" .../>`  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>Varsayılan XAML Namespace ve tür eşlemesi  
 Varsayılan XAML ad alanı WPF programlama için tipik XAML senaryoları için gereksinim duyduğunuz XAML türlerin çoğu içerir; Bu nedenle, genellikle önekleri XAML türü değerleri başvururken önleyebilirsiniz. Bir özel bütünleştirilmiş kod veya, bir WPF bütünleştirilmiş kodda mevcut ancak varsayılan XAML ad alanına eşlenmedi bir CLR ad alanındaki türleri için bir tür başvuru değilse bir önek harita gerekebilir. Ön ekleri, XAML ad alanları ve CLR ad alanlarını eşleme ile ilgili daha fazla bilgi için bkz. [XAML ad alanları ve WPF XAML için Namespace eşlemesi](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### <a name="type-properties-that-support-typename-as-string"></a>Bu destek Typename olarak-dizesini-özellikler yazın  
 WPF destekleyen bazı özelliklerin türünün değerini belirtmek teknikleri <xref:System.Type> gerektirmeden bir `x:Type` biçimlendirme uzantısı kullanımı. Bunun yerine, değer türü adları bir dize olarak belirtebilirsiniz. Örneğin <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> ve <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>. Bu davranış için destek, tür dönüştürücüleri veya biçimlendirme uzantıları sağlanmadı. Bunun yerine, bu aracılığıyla uygulanan bir erteleme, davranıştır <xref:System.Windows.FrameworkElementFactory>.  
  
 Silverlight benzer bir kuralı destekler. Aslında, Silverlight uygulamasının şu anda desteklemediği `{x:Type}` , XAML dil desteği ve kabul etmediği `{x:Type}` kullanımları Silverlight WPF XAML geçişi desteklemek için tasarlanan bazı durumlar dışında. Bu nedenle, dize olarak typename davranışı için tüm Silverlight yerel özellik değerlendirmesini yerleşik burada bir <xref:System.Type> değerdir.  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009, genel türleri ve özellik davranışını değiştiren için ek destek sağlar `x:TypeArguments` ve `x:Type` bu desteği sağlamak için.  
  
-   `x:TypeArguments` ve kök dışında öğelerde genel nesne örneklemesini için ilişkili nesne öğesi olabilir. Daha fazla bilgi için "XAML 2009" bölümüne bakın. [x: TypeArguments yönergesi](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
-   XAML 2009, genel bir türün kısıtlaması işaretlemede belirtmek için sözdizimi destekler. Bu, tarafından kullanılabilir `x:TypeArguments`tarafından `x:Type`, ya da iki özellik birlikte.  
  
-   Yükleme türünü kullanan bazı framework özellikleri örtük tür dönüştürme davranışını bu özellik ayrıca ekler için XAML 2009 işlerken WPF XAML uygulama <xref:System.Type>.  
  
 WPF içinde ancak yalnızca gevşek XAML için (biçimlendirme yapılmayan XAML) XAML 2009 özelliklerini kullanabilirsiniz. WPF ve XAML, BAML formu için biçimlendirme derlenmiş XAML şu anda desteklemediğinden XAML 2009 anahtar sözcükleri ve özellikleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Style>  
 [Stil ve Şablon Oluşturma](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [XAML'ye Genel Bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [İşaretleme Uzantıları ve WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
