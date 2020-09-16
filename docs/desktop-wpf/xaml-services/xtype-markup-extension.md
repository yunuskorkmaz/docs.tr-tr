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
ms.openlocfilehash: 00e6684f6ad1eb8d96f72f49bd5e0d211c8166c3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559076"
---
# <a name="xtype-markup-extension"></a>x:Type İşaretleme Uzantısı

<xref:System.Type>BELIRTILEN xaml türü için temeldeki tür olan CLR nesnesini sağlar.

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
|`typeNameValue`|Gereklidir. Geçerli varsayılan XAML ad alanına çözümlenebilen bir tür adı; veya belirtilmişse belirtilen eşlenmiş ön ek `prefix` .|

## <a name="remarks"></a>Açıklamalar

`x:Type`Biçimlendirme uzantısı, `typeof()` C# ' deki Işlece veya `GetType` Microsoft Visual Basic işleçine benzer bir işleve sahiptir.

`x:Type`Biçimlendirme uzantısı, türü alan özellikler için dizeden bir dönüştürme davranışı sağlar <xref:System.Type> . Giriş bir XAML türüdür. Giriş XAML türü ve çıkış CLR arasındaki ilişki, <xref:System.Type> <xref:System.Type> <xref:System.Xaml.XamlType.UnderlyingType%2A> <xref:System.Xaml.XamlType> <xref:System.Xaml.XamlType> xaml şema bağlamına ve <xref:System.Windows.Markup.IXamlTypeResolver> bağlamın sağladığı hizmete bağlı olarak gerekli olan, çıktının girişin bulunduğu bir giriştir.

.NET XAML hizmetlerinde, bu biçimlendirme uzantısının işlenmesi sınıfı tarafından tanımlanır <xref:System.Windows.Markup.TypeExtension> .

Belirli çerçeve uygulamalarında, değer olarak alan bazı özellikler <xref:System.Type> doğrudan türün adını kabul edebilir (türün dize değeri `Name` ). Ancak, bu davranışı uygulamak karmaşık bir senaryodur. Örnekler için aşağıdaki "WPF kullanım notları" bölümüne bakın.

Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Tanımlayıcı dizeden sonra belirtilen dize belirteci, `x:Type` <xref:System.Windows.Markup.TypeExtension.TypeName%2A> temel uzantı sınıfının değeri olarak atanır <xref:System.Windows.Markup.TypeExtension> . CLR türlerini temel alan .NET XAML Hizmetleri için varsayılan XAML şeması bağlamı altında, bu özniteliğin değeri <xref:System.Reflection.MemberInfo.Name%2A> istenen türden ya da <xref:System.Reflection.MemberInfo.Name%2A> varsayılan olmayan xaml ad alanı eşlemesi için ön ek tarafından önceden bir ön eki tarafından bulunur.

`x:Type`Biçimlendirme uzantısı nesne öğesi sözdiziminde kullanılabilir. Bu durumda, <xref:System.Windows.Markup.TypeExtension.TypeName%2A> uzantıyı doğru şekilde başlatmak için özelliğinin değerini belirtmek gerekir.

`x:Type`Biçimlendirme uzantısı da verbose özniteliği olarak kullanılabilir; ancak bu kullanım tipik değildir:`<object property="{x:Type TypeName=typeNameValue}" .../>`

## <a name="wpf-usage-notes"></a>WPF kullanım notları

### <a name="default-xaml-namespace-and-type-mapping"></a>Varsayılan XAML ad alanı ve tür eşleme

WPF programlama için varsayılan XAML ad alanı, tipik XAML senaryoları için ihtiyacınız olan XAML türlerinin çoğunu içerir; Bu nedenle, XAML türü değerlerine başvuru yaparken genellikle öneklerden kaçınabilirsiniz. Özel bir derlemeden veya bir WPF derlemesinde bulunan ancak varsayılan XAML ad alanıyla eşlenmeyen bir CLR ad alanı olan türler için bir türe başvuruyordıysanız bir ön eki eşlemeniz gerekebilir. Ön ekler, XAML ad alanları ve eşleme CLR ad alanları hakkında daha fazla bilgi için bkz. [WPF XAML Için xaml ad alanları ve ad alanı eşlemesi](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).

### <a name="type-properties-that-support-typename-as-string"></a>Dize olarak TypeName 'ı destekleyen tür özellikleri

WPF, <xref:System.Type> biçimlendirme uzantısı kullanımı gerekmeden türdeki bazı özelliklerin değerini belirtmeyi etkinleştiren teknikleri destekler `x:Type` . Bunun yerine, değeri türü adı belirleyen bir dize olarak belirtebilirsiniz. Bunun örnekleri <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> ve <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType> . Bu davranış için destek, tür dönüştürücüler veya biçimlendirme uzantıları aracılığıyla sağlanmaz. Bunun yerine, bu, ile uygulanan bir erteleme davranışıdır <xref:System.Windows.FrameworkElementFactory> .

Silverlight benzer bir kuralı destekler. Aslında, Silverlight şu anda `{x:Type}` xaml dil desteğiyle desteklemez ve `{x:Type}` WPF-Silverlight xaml geçişini desteklemek için tasarlanan birkaç koşulda kullanımları kabul etmez. Bu nedenle, dize olarak TypeName davranışı, bir değeri olduğu yerde tüm Silverlight yerel özellik değerlendirmesinde yerleşik olarak bulunur <xref:System.Type> .

## <a name="xaml-2009"></a>XAML 2009

XAML 2009, genel türler için ek destek sağlar ve `x:TypeArguments` `x:Type` Bu desteği sağlamak için ve özelliklerinin davranışını değiştirir.

- `x:TypeArguments` ve genel nesne örneklemesi için ilişkili nesne öğesi kök dışında bir öğe üzerinde olabilir. Daha fazla bilgi için, [X:TypeArguments yönergesinin](xtypearguments-directive.md)"xaml 2009" bölümüne bakın.

- XAML 2009, biçimlendirme içinde genel bir türün kısıtlamasını belirtmek için bir sözdizimi destekler. Bu, ya da ile `x:TypeArguments` `x:Type` birlikte iki özellik tarafından kullanılabilir.

- Yükleme için XAML 2009 ' i işlerken WPF XAML uygulamasında bu özellik, türü kullanan belirli Framework özellikleri için örtük tür dönüştürme davranışına de eklenir <xref:System.Type> .

WPF 'de XAML 2009 özelliklerini, ancak yalnızca gevşek XAML (biçimlendirme ile derlenen XAML) için kullanabilirsiniz. WPF için biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 anahtar sözcüklerini ve özelliklerini desteklememektedir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Style>
- [Stil ve Şablon Oluşturma](../fundamentals/styles-templates-overview.md)
- [XAML'ye Genel Bakış (WPF)](../fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
