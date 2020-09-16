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
ms.openlocfilehash: 430ab65af52282ccb1d429cd2523efe213f13609
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543557"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments Yönergesi

Bir genel öğesinin kısıtlayan tür bağımsız değişkenlerini genel türün oluşturucusuna geçirir.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`object`|Bir CLR genel türü tarafından desteklenen bir XAML türünün nesne öğesi bildirimi. `object`Varsayılan xaml ad alanından olmayan BIR xaml türüne başvuruyorsa, varsa `object` xaml ad alanını belirtmek için bir ön ek gerektirir `object` .|
|`typeString`|CLR genel türü için tür bağımsız değişkenlerini sağlayan dizeler olarak bir veya daha fazla XAML tür adı bildiren bir dize. Ek sözdizimi notları için bkz. açıklamalar.|

## <a name="remarks"></a>Açıklamalar

Çoğu durumda, bir dizedeki bilgi öğesi olarak kullanılan XAML türlerinin `typeString` ön eki alınır. CLR genel kısıtlamalarının tipik türleri (örneğin, <xref:System.Int32> ve <xref:System.String> ) clr temel sınıf kitaplıklarından gelir. Bu kitaplıklar, çerçeveye özgü tipik varsayılan XAML ad alanları ile eşlenmedi ve bu nedenle XAML kullanımı için bir ön ek eşlemesi gerektirir.

Bir virgül sınırlayıcısı kullanarak birden çok XAML türü adı belirtebilirsiniz.

Genel kısıtlamalar genel türler kullanıyorsa, iç içe geçmiş kısıtlama türü bağımsız değişkenleri parantez () ile yer alabilir.

Bu tanımın `x:TypeArguments` .net xaml hizmetlerine özgü olduğunu ve clr yedeklemesini kullandığını unutmayın. Bir dil düzeyi tanımı, [ \[ MS-xaml \] bölümünde 5.3.11](/previous-versions/msp-n-p/ff650760(v=pandp.10))bulunabilir.

## <a name="usage-examples"></a>Kullanım örnekleri

Bu örnekler için aşağıdaki XAML ad alanı tanımlarının bildirildiği varsayılır:

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a>Listele\<String>

`<scg:List x:TypeArguments="sys:String" ...>` bir <xref:System.Collections.Generic.List%601> <xref:System.String> tür bağımsız değişkeniyle yeni bir oluşturur.

### <a name="dictionarystringstring"></a>Sözlük\<String,String>

`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`<xref:System.Collections.Generic.Dictionary%602>iki tür bağımsız değişkeni ile yeni bir oluşturur <xref:System.String> .

### <a name="queuekeyvaluepairstringstring"></a><KeyValuePair kuyruğu\<String,String>>

`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`<xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Generic.KeyValuePair%602> iç kısıtlama türü bağımsız değişkenleri ve ile kısıtlaması olan yeni bir oluşturur <xref:System.String> <xref:System.String> .

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 ve WPF Genel XAML kullanımları

XAML 2006 kullanımı ve WPF uygulamaları için kullanılan XAML için aşağıdaki kısıtlamalar `x:TypeArguments` ve genel olarak xaml 'den genel tür kullanımları vardır:

- Yalnızca bir XAML dosyasının kök öğesi genel bir türe başvuran Genel XAML kullanımını destekleyebilir.

- Kök öğe, en az bir tür bağımsız değişkeni olan genel bir türe eşleşmelidir. <xref:System.Windows.Navigation.PageFunction%601> bunun bir örneğidir. Sayfa işlevleri, WPF 'de XAML genel kullanım desteğinin birincil senaryosudur.

- Genel için kök öğe XAML nesne öğesi, kullanarak kısmi bir sınıf de bildirmelidir `x:Class` . Bu, WPF oluşturma eylemi tanımlansa bile geçerlidir.

- `x:TypeArguments` iç içe geçmiş genel kısıtlamalara başvuramaz.

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>WPF 3,0 veya WPF 3,5 bağımlılığı olmayan XAML 2009 veya XAML 2006

XAML 2006 ya da XAML 2009 için .NET XAML hizmetlerinde, genel XAML kullanımı ile ilgili WPF ile ilgili kısıtlamalar gevşek olarak bulunur. XAML biçimlendirmesinde, yedekleme türü sisteminin ve nesne modelinin destekleyebileceği herhangi bir konumda genel nesne öğesi örneği oluşturabilirsiniz.

Ortak dil temel öğeleri için XAML türleri almak üzere CLR temel türlerini eşlemek yerine XAML 2009 kullanıyorsanız, [ortak xaml dil temelleri Için yerleşik türleri](types-for-primitives.md) bir içinde bilgi öğeleri olarak kullanabilirsiniz `typeString` . Örneğin, aşağıdaki bildirimi yapabilirsiniz (önek eşlemeleri gösterilmez, ancak x, XAML 2009 için XAML Language xaml ad alanıdır):

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

WPF 'de ve .NET Framework 4 veya .NET Core 3,0 (veya üzeri) hedeflenirken XAML 2009 özelliklerini `x:TypeArguments` yalnızca gevşek XAML (biçimlendirme derlenmiş olmayan XAML) ile birlikte kullanabilirsiniz. WPF için biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 anahtar sözcüklerini ve özelliklerini desteklememektedir. XAML 'yi derlemeyi işaretlemeyi gerekiyorsa, [xaml 2006 ve WPF genel xaml kullanımları](#xaml-2006-and-wpf-generic-xaml-usages) bölümünde belirtilen kısıtlamalar altında işlem yapmanız gerekir. BAML yalnızca .NET Framework desteklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](xclass-directive.md)
- [x:Type İşaretleme Uzantısı](xtype-markup-extension.md)
- [XAML Dili Ortak Temelleri İçin Yerleşik Türler](types-for-primitives.md)
- [XAML'deki Genel Türler](generics.md)
