---
title: x:TypeArguments Yönergesi
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 69da9329f140121b66c71d4cf2e99e9d14a1b207
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071355"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments Yönergesi

Genel bir jenerik türü bağımsız değişkenlerini genel türün oluşturucuya kısıtlayıcı tür bağımsız değişkenlerini geçer.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`object`|CLR genel türü tarafından desteklenen XAML türünün nesne öğesi bildirimi. Varsayılan `object` XAML ad alanından olmayan bir XAML türüne başvuruyorsa, `object` `object` var olan XAML ad alanını belirtmek için bir önek gerekir.|
|`typeString`|CLR genel türü için tür bağımsız değişkenleri sağlayan bir veya daha fazla XAML türü adlarını dizeleri olarak bildiren bir dize. Ek sözdizimi notları için Açıklamalar'a bakın.|

## <a name="remarks"></a>Açıklamalar

Çoğu durumda, bir `typeString` dize de bilgi öğesi olarak kullanılan XAML türleri önceden sabitlenir. Tipik CLR genel kısıtlama türleri (örneğin <xref:System.String>ve) <xref:System.Int32> CLR taban sınıf kitaplıklarından gelir. Bu kitaplıklar, tipik çerçeveye özgü varsayılan XAML ad alanlarına eşlenmez ve bu nedenle XAML kullanımı için bir önek eşleme gerektirir.

Virgül delimiter kullanarak birden fazla XAML türü adı belirtebilirsiniz.

Genel kısıtlamaların kendileri genel türleri kullanıyorsa, iç içe geçmiş kısıtlama türü bağımsız değişkenleri parantez () tarafından bulunabilir.

Bu tanımın `x:TypeArguments` .NET XAML Hizmetlerine özgü olduğunu ve CLR desteğini kullandığını unutmayın. [ \[MS-XAML\] Bölüm 5.3.11'de](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))dil düzeyi tanımı bulunabilir.

## <a name="usage-examples"></a>Kullanım Örnekleri

Bu örnekler için, aşağıdaki XAML ad alanı tanımlarının beyan edildiğine varyalım:

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a>Liste\<Dize>

`<scg:List x:TypeArguments="sys:String" ...>`bir tür bağımsız <xref:System.Collections.Generic.List%601> değişkeni <xref:System.String> ile yeni bir instantiates.

### <a name="dictionarystringstring"></a>Sözlük\<Dize, String>

`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`iki <xref:System.String> tür bağımsız <xref:System.Collections.Generic.Dictionary%602> değişkenlerle yeni bir instantiates.

### <a name="queuekeyvaluepairstringstring"></a>Sıra<KeyValuePair\<String, String>>

`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`iç kısıtlama türü <xref:System.Collections.Generic.Queue%601> bağımsız <xref:System.Collections.Generic.KeyValuePair%602> değişkenleri <xref:System.String> ile bir kısıtlama olan <xref:System.String>yeni bir instantiates ve .

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 ve WPF Genel XAML Kullanımları

XAML 2006 kullanımı ve WPF uygulamaları için kullanılan XAML için `x:TypeArguments` genel olarak XAML'den genel tür kullanımları için aşağıdaki kısıtlamalar vardır:

- Yalnızca bir XAML dosyasının kök öğesi, genel bir türe başvuran genel bir XAML kullanımını destekleyebilir.

- Kök öğe, en az bir tür bağımsız değişkeni olan genel bir türle eşlenmelidir. <xref:System.Windows.Navigation.PageFunction%601> bunun bir örneğidir. Sayfa işlevleri WPF'de XAML genel kullanım desteği için birincil senaryodur.

- Genel için kök öğesi XAML nesne öğesi de `x:Class`kullanarak kısmi bir sınıf beyan etmelidir. Bu, bir WPF oluşturma eylemi tanımlansa bile geçerlidir.

- `x:TypeArguments`iç içe geçmiş genel kısıtlamalara başvurulamıyor.

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>WPF 3.0 veya WPF 3.5 Bağımlılık olmadan XAML 2009 veya XAML 2006

XAML 2006 veya XAML 2009 için .NET XAML Hizmetlerinde, genel XAML kullanımına ilişkin WPF ile ilgili kısıtlamalar gevşetilir. Genel bir nesne öğe öğesini, destek türü sistemi ve nesne modelinin destekedebileceği XAML biçimlendirmesinde herhangi bir konumda anında atabilirsiniz.

Ortak dil ilkelleri için XAML türleri elde etmek için CLR taban türlerini eşlemek yerine XAML 2009 kullanıyorsanız, [Ortak XAML Dil İlkelleri için Yerleşik Türleri](types-for-primitives.md) bir `typeString`.'de bilgi öğesi olarak kullanabilirsiniz. Örneğin, aşağıdakileri bildirebilirsiniz (önek eşlemeleri gösterilmez, ancak x XAML 2009 için XAML dilixaml ad alanıdır):

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

WPF'de ve .NET Framework 4 veya .NET Core 3.0 (veya daha sonra) hedeflenirken, XAML 2009 özelliklerini ancak yalnızca gevşek XAML (biçimlendirme-derlenmemiş XAML) ile `x:TypeArguments` birlikte kullanabilirsiniz. WPF için biçimlendirmeyle derlenen XAML ve XAML'nin BAML formu şu anda XAML 2009 anahtar kelimelerini ve özelliklerini desteklemez. XAML'yi işaretlemeniz gerekiyorsa, [XAML 2006 ve WPF Generic XAML Kullanımları](#xaml-2006-and-wpf-generic-xaml-usages) bölümünde belirtilen kısıtlamalar altında çalışmanız gerekir. BAML yalnızca .NET Framework'de desteklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](xclass-directive.md)
- [x:Type İşaretleme Uzantısı](xtype-markup-extension.md)
- [XAML Dili Ortak Temelleri İçin Yerleşik Türler](types-for-primitives.md)
- [XAML'deki Genel Türler](generics.md)
