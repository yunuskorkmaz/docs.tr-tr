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
ms.openlocfilehash: df0b3fe53cb8f284fc6e2d79a9b2cea86318d701
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459917"
---
# <a name="xtype-markup-extension"></a>x:Type İşaretleme Uzantısı
Belirtilen XAML türü için temeldeki tür olan CLR <xref:System.Type> nesnesini sağlar.  
  
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
|`prefix`|İsteğe bağlı. Varsayılan olmayan XAML ad alanını eşleyen bir ön ek. Ön ek belirtmek genellikle gerekli değildir. Bkz. açıklamalar.|  
|`typeNameValue`|Gerekli. Geçerli varsayılan XAML ad alanına çözümlenebilen bir tür adı; veya `prefix` sağlanırsa belirtilen eşlenen ön eki.|  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Type` biçimlendirme uzantısının, içindeki C# `typeof()` işlecine benzer bir Işlevi veya Microsoft Visual Basic `GetType` işleci vardır.  
  
 `x:Type` biçimlendirme uzantısı, <xref:System.Type>türü alan özellikler için, dizeden bir dönüştürme davranışı sağlar. Giriş bir XAML türüdür. Giriş XAML türü ve çıkış CLR <xref:System.Type> arasındaki ilişki, XAML şema bağlamına ve içeriğin sağladığı <xref:System.Xaml.XamlType> hizmetine göre gerekli <xref:System.Windows.Markup.IXamlTypeResolver> aranırken, çıkış <xref:System.Type> giriş <xref:System.Xaml.XamlType><xref:System.Xaml.XamlType.UnderlyingType%2A>.  
  
 .NET Framework XAML hizmetlerinde, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.Markup.TypeExtension> sınıfı tarafından tanımlanır.  
  
 Belirli Framework uygulamalarında, değer olarak <xref:System.Type> alan bazı özellikler doğrudan türün adını kabul edebilir (`Name`türünün dize değeri). Ancak, bu davranışı uygulamak karmaşık bir senaryodur. Örnekler için aşağıdaki "WPF kullanım notları" bölümüne bakın.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. `x:Type` tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.Markup.TypeExtension> uzantı sınıfının <xref:System.Windows.Markup.TypeExtension.TypeName%2A> değeri olarak atanır. CLR türlerini temel alan .NET Framework XAML Hizmetleri için varsayılan XAML şeması bağlamı altında, bu özniteliğin değeri istenen türün <xref:System.Reflection.MemberInfo.Name%2A> veya bundan önce varsayılan olmayan XAML ad alanı eşlemesi için bir ön ek tarafından <xref:System.Reflection.MemberInfo.Name%2A> içerir.  
  
 `x:Type` biçimlendirme uzantısı nesne öğesi sözdiziminde kullanılabilir. Bu durumda, uzantıyı doğru şekilde başlatmak için <xref:System.Windows.Markup.TypeExtension.TypeName%2A> özelliğinin değerini belirtmek gerekir.  
  
 `x:Type` biçimlendirme uzantısı verbose özniteliği olarak da kullanılabilir; Ancak bu kullanım tipik değildir: `<object property="{x:Type TypeName=typeNameValue}" .../>`  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>Varsayılan XAML ad alanı ve tür eşleme  
 WPF programlama için varsayılan XAML ad alanı, tipik XAML senaryoları için ihtiyacınız olan XAML türlerinin çoğunu içerir; Bu nedenle, XAML türü değerlerine başvuru yaparken genellikle öneklerden kaçınabilirsiniz. Özel bir derlemeden veya bir WPF derlemesinde bulunan ancak varsayılan XAML ad alanıyla eşlenmeyen bir CLR ad alanı olan türler için bir türe başvuruyordıysanız bir ön eki eşlemeniz gerekebilir. Ön ekler, XAML ad alanları ve eşleme CLR ad alanları hakkında daha fazla bilgi için bkz. [WPF XAML Için xaml ad alanları ve ad alanı eşlemesi](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### <a name="type-properties-that-support-typename-as-string"></a>Dize olarak TypeName 'ı destekleyen tür özellikleri  
 WPF, `x:Type` biçimlendirme uzantısı kullanımı gerekmeden <xref:System.Type> türündeki bazı özelliklerin değerini belirtmeyi etkinleştiren teknikleri destekler. Bunun yerine, değeri türü adı belirleyen bir dize olarak belirtebilirsiniz. Bunun örnekleri <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> ve <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>. Bu davranış için destek, tür dönüştürücüler veya biçimlendirme uzantıları aracılığıyla sağlanmaz. Bunun yerine, <xref:System.Windows.FrameworkElementFactory>aracılığıyla uygulanan bir erteleme davranışıdır.  
  
 Silverlight benzer bir kuralı destekler. Aslında, Silverlight, XAML dil desteğiyle `{x:Type}` desteklememektedir ve WPF-Silverlight XAML geçişini desteklemeye yönelik birkaç durumda `{x:Type}` kullanımlarını kabul etmez. Bu nedenle, dize olarak TypeName davranışı, bir <xref:System.Type> değeri olduğu tüm Silverlight yerel özellik değerlendirmesinde yerleşik olarak bulunur.  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009, genel türler için ek destek sağlar ve bu desteği sağlamak üzere `x:TypeArguments` ve `x:Type` özellik davranışını değiştirir.  
  
- Genel nesne örneklemesi için `x:TypeArguments` ve ilişkili nesne öğesi kök dışında bir öğe üzerinde olabilir. Daha fazla bilgi için, [X:TypeArguments yönergesinin](x-typearguments-directive.md)"xaml 2009" bölümüne bakın.  
  
- XAML 2009, biçimlendirme içinde genel bir türün kısıtlamasını belirtmek için bir sözdizimi destekler. Bu, `x:TypeArguments`, `x:Type`veya iki özelliği ile birlikte kullanılabilir.  
  
- Yükleme için XAML 2009 ' i işlerken WPF XAML uygulamasında bu özellik, türü <xref:System.Type>kullanan belirli Framework özellikleri için örtük tür dönüştürme davranışına de eklenir.  
  
 WPF 'de XAML 2009 özelliklerini, ancak yalnızca gevşek XAML (biçimlendirme ile derlenen XAML) için kullanabilirsiniz. WPF için biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 anahtar sözcüklerini ve özelliklerini desteklememektedir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Style>
- [Stil ve Şablon Oluşturma](../wpf/controls/styling-and-templating.md)
- [XAML'ye Genel Bakış (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [İşaretleme Uzantıları ve WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
