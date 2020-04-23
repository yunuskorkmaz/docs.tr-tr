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
ms.openlocfilehash: f75d4e30dc41bbce995e466466c96c1a2830949b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071362"
---
# <a name="xtype-markup-extension"></a>x:Type İşaretleme Uzantısı

Belirli bir <xref:System.Type> XAML türü için altta yatan türdeki CLR nesnesini sağlar.

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
|`prefix`|İsteğe bağlı. Varsayılan olmayan bir XAML ad alanını eşleyen bir önek. Önek belirtmek sık sık gerekli değildir. Bkz. Açıklamalar.|
|`typeNameValue`|Gereklidir. Geçerli varsayılan XAML ad alanına çözülebilen bir tür adı; veya sağlanırsa `prefix` belirtilen eşlenen önek.|

## <a name="remarks"></a>Açıklamalar

Biçimlendirme uzantısı, `x:Type` C#'daki `typeof()` işleçle veya `GetType` Microsoft Visual Basic'teki işleçle benzer bir işleve sahiptir.

`x:Type` Biçimlendirme uzantısı, türü <xref:System.Type>alan özellikler için dize dışından dönüştürme davranışı sağlar. Giriş bir XAML türüdür. Giriş XAML türü ve çıkış <xref:System.Type> CLR arasındaki ilişki, <xref:System.Type> çıkış <xref:System.Xaml.XamlType.UnderlyingType%2A> girişin <xref:System.Xaml.XamlType>, XAML <xref:System.Xaml.XamlType> şema bağlamı ve bağlam ın <xref:System.Windows.Markup.IXamlTypeResolver> sağladığı hizmete dayalı gerekli baktıktan sonra olmasıdır.

.NET XAML Hizmetleri'nde, bu biçimlendirme uzantısı <xref:System.Windows.Markup.TypeExtension> için işleme sınıf tarafından tanımlanır.

Belirli çerçeve uygulamalarında, değer <xref:System.Type> olarak kabul eden bazı özellikler doğrudan türün adını (türün `Name`dize değeri) kabul edebilir. Ancak, bu davranışı uygulamak karmaşık bir senaryodur. Örneğin, aşağıdaki "WPF Kullanım Notları" bölümüne bakın.

Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Tanımlayıcı dizesonra sağlanan `x:Type` dize belirteci alttaki <xref:System.Windows.Markup.TypeExtension.TypeName%2A> <xref:System.Windows.Markup.TypeExtension> uzantı sınıfının değeri olarak atanır. CLR türlerini temel alan .NET XAML Hizmetleri için varsayılan XAML şeması bağlamında, bu özniteliğin değeri istenen <xref:System.Reflection.MemberInfo.Name%2A> türdeki veya varsayılan olmayan xaml ad alanı eşlemi için bir önek önce gelen içerir. <xref:System.Reflection.MemberInfo.Name%2A>

`x:Type` Biçimlendirme uzantısı nesne öğesi sözdiziminde kullanılabilir. Bu durumda, uzantıyı düzgün <xref:System.Windows.Markup.TypeExtension.TypeName%2A> bir şekilde başlatmanın özelliğinin değerini belirtmeniz gerekir.

`x:Type` Biçimlendirme uzantısı ayrıntılı bir öznitelik olarak da kullanılabilir; ancak bu kullanım tipik değildir:`<object property="{x:Type TypeName=typeNameValue}" .../>`

## <a name="wpf-usage-notes"></a>WPF Kullanım Notları

### <a name="default-xaml-namespace-and-type-mapping"></a>Varsayılan XAML Ad Alanı ve Tür Eşleme

WPF programlama için varsayılan XAML ad alanı, tipik XAML senaryoları için gereken XAML türlerinin çoğunu içerir; bu nedenle, XAML türü değerlerine başvururken genellikle önekleri önleyebilirsiniz. Özel bir derlemeden veya WPF derlemesinde var olan ancak varsayılan XAML ad alanına eşlenmemiş bir CLR ad alanından gelen türler için bir türe başvuruyorsanız önek eşlemeniz gerekebilir. Önekler, XAML ad alanları ve CLR ad alanlarını eşleme hakkında daha fazla bilgi için [WPF XAML için XAML Ad Alanları ve Ad Alanı Eşleme'ye](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)bakın.

### <a name="type-properties-that-support-typename-as-string"></a>Dize Olarak Tür Adı Destekleyen Özellikler Yazın

WPF, `x:Type` biçimlendirme uzantısı kullanımı gerektirmeden bazı <xref:System.Type> tür özelliklerinin değerini belirtmeyi sağlayan teknikleri destekler. Bunun yerine, değeri türü adlayan bir dize olarak belirtebilirsiniz. Buna örnek <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> olarak <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>verilebilir ve . Bu davranış için destek tür dönüştürücüler veya biçimlendirme uzantıları aracılığıyla sağlanmaz. Bunun yerine, bu aracılığıyla <xref:System.Windows.FrameworkElementFactory>uygulanan bir erteleme davranışıdır.

Silverlight da benzer bir kongreyi destekliyor. Aslında, Silverlight şu anda XAML dil desteğini `{x:Type}` desteklemez `{x:Type}` ve WPF-Silverlight XAML geçişini desteklemek için tasarlanmış birkaç durum dışında kullanımları kabul etmez. Bu nedenle, dize olarak dize olarak dakti-as-davranış bir <xref:System.Type> değer olduğu tüm Silverlight yerel özellik değerlendirme yerleşiktir.

## <a name="xaml-2009"></a>XAML 2009

XAML 2009 genel türleri için ek destek sağlar `x:TypeArguments` ve `x:Type` özellik davranışını değiştirir ve bu desteği sağlar.

- `x:TypeArguments`ve genel bir nesne anlık için ilişkili nesne öğesi kök dışındaki öğeler üzerinde olabilir. Daha fazla bilgi için [x:TypeArguments](xtypearguments-directive.md)Yönergesi'nin "XAML 2009" bölümüne bakın.

- XAML 2009, biçimlendirmede genel bir tür kısıtlamasını belirtmek için bir sözdizimini destekler. Bu, iki `x:TypeArguments`özellik `x:Type`tarafından veya birlikte kullanılabilir.

- WPF XAML uygulaması yük için XAML 2009 işlenirken de türü <xref:System.Type>kullanan belirli çerçeve özellikleri için örtük tür dönüştürme davranışı bu yeteneği ekler.

WPF'de XAML 2009 özelliklerini ancak yalnızca gevşek XAML (biçimlendirme derlememiş XAML) için kullanabilirsiniz. WPF için biçimlendirmeyle derlenen XAML ve XAML'nin BAML formu şu anda XAML 2009 anahtar kelimelerini ve özelliklerini desteklemez.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Style>
- [Stil ve Şablon Oluşturma](../fundamentals/styles-templates-overview.md)
- [XAML'ye Genel Bakış (WPF)](../fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
