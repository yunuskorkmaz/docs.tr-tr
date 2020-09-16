---
title: XAML Dili Ortak Temelleri İçin Yerleşik Türler
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: ec0e2a29a191d5057ce66a5f3272d00e92b01bd7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540035"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Ortak XAML dil temelleri için yerleşik türler

XAML 2009, ortak dil çalışma zamanında (CLR) ve diğer programlama dillerinde sık kullanılan temel elemanlar olan çeşitli veri türleri için XAML dil düzeyinde destek sunar. XAML 2009, bu temel öğeler için destek ekler: `x:Object` , `x:Boolean` ,, `x:Char` `x:String` , `x:Decimal` , `x:Single` , `x:Double` , `x:Int16` , `x:Int32` , `x:Int64` , `x:TimeSpan` , `x:Uri` , `x:Byte` ve `x:Array`

## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>XAML biçimlendirmesinde dil temelleri için önceki teknikler

 Önceki WPF sürümleri için XAML 'de, .NET Framework için bir CLR ilkel tanım sınıfı içeren derlemeyi ve ad alanını eşleyerek CLR dil temel temellerine başvurabilirsiniz. Bunların çoğu mscorlib derlemesinde ve <xref:System> ad alanında bulunur. Örneğin, kullanmak için <xref:System.Int32> aşağıdaki eşlemeyi bildirebilirsiniz (bundan sonra bir örnek kullanım ile gösterilir):

```xaml
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Application.Resources>
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>
  </Application.Resources>
</Application>
```

## <a name="xaml-2009-language-primitives"></a>XAML 2009 dil temelleri

Kurala göre, XAML için dil temelleri ve diğer XAML dil öğeleri, `x:` ön ek dahil gösterilir. XAML dil öğeleri genellikle gerçek zamanlı biçimlendirmede kullanılır. Bu kural, WPF 'de XAML için kavramsal belgelerde ve ayrıca XAML belirtiminde izlenir.

### <a name="xobject"></a>x:Object

CLR yedeklemesi için, `x:Object` ilkel öğesine karşılık gelir <xref:System.Object> .

Bu ilkel genellikle uygulama biçimlendirmesinde kullanılmaz, ancak bir XAML tür sisteminde atananlıya bilirlik gibi bazı senaryolarda yararlı olabilir.

### <a name="xboolean"></a>x:Boolean

CLR yedeklemesi için, `x:Boolean` ilkel öğesine karşılık gelir <xref:System.Boolean> .

XAML, `x:Boolean` büyük/küçük harfe duyarsız değerleri ayrıştırır. `x:Bool`Kabul edilen bir alternatif değildir. XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.17 ve 5.4.11](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xchar"></a>x:Char

CLR yedeklemesi için, `x:Char` ilkel öğesine karşılık gelir <xref:System.Char> .

Dize ve karakter türlerinin, XML düzeyinde dosyanın genel kodlamasıyla etkileşimi vardır. XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.7 ve 5.4.1](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xstring"></a>x:String

CLR yedeklemesi için, `x:String` ilkel öğesine karşılık gelir <xref:System.String> .

Dize ve karakter türlerinin, XML düzeyinde dosyanın genel kodlamasıyla etkileşimi vardır. XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xdecimal"></a>x:Decimal

CLR yedeklemesi için, `x:Decimal` ilkel öğesine karşılık gelir <xref:System.Decimal> .

XAML ayrıştırma, kültür altında kendiliğinden yapılır `en-US` . `en-US`Kültür altında, bir Decimal bileşenleri için doğru ayırıcı, `.` geliştirme ortamının kültür ayarlarından ya da xaml 'nin çalışma zamanında yüklendiği son istemci hedefinde bağımsız olarak her zaman bir nokta () olur.

XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.14 ve 5.4.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xsingle"></a>x:Single

CLR yedeklemesi için, `x:Single` ilkel öğesine karşılık gelir <xref:System.Single> .

Sayısal değerlere ek olarak, için de metin sözdizimi, `x:Single` ve belirteçlerine izin `Infinity` verir `-Infinity` `NaN` . Bu belirteçler büyük/küçük harfe duyarlı olarak değerlendirilir.

`x:Single` metin sözdiziminde ilk karakter veya ise, bilimsel gösterim biçimindeki değerleri destekleyebilir `e` `E` .

XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.8 ve 5.4.2](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xdouble"></a>x:Double

CLR yedeklemesi için, `x:Double` ilkel öğesine karşılık gelir <xref:System.Double> .

Sayısal değerlere ek olarak, için metin sözdizimi, `x:Double` ve belirteçlerine izin `Infinity` verir `-Infinity` `NaN` . Bu belirteçler büyük/küçük harfe duyarlı olarak değerlendirilir.

`x:Double` , bilimsel gösterim biçimindeki değerleri destekleyebilir. `e` `E` Üs kısmını tanıtmak için veya karakterini kullanın.

XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.9 ve 5.4.3](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint16"></a>x:Int16

CLR yedeklemesi için, `x:Int16` ilkel öğesine karşılık gelir <xref:System.Int16> ve `x:Int16` imzalı olarak kabul edilir. XAML 'de, artı ( `+` ) işareti metin sözdiziminde devamsızlık pozitif bir işaretli değer olarak kapsanır.

XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.11 ve 5.4.5](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint32"></a>x:Int32

CLR yedeklemesi için, `x:Int32` ilkel öğesine karşılık gelir <xref:System.Int32> . `x:Int32` imzalı olarak kabul edilir. XAML 'de, artı ( `+` ) işareti metin sözdiziminde devamsızlık pozitif bir işaretli değer olarak kapsanır.

XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.12 ve 5.4.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint64"></a>x:Int64

CLR yedeklemesi için, `x:Int64` ilkel öğesine karşılık gelir <xref:System.Int64> . `x:Int64` imzalı olarak kabul edilir. XAML 'de, artı ( `+` ) işareti metin sözdiziminde devamsızlık pozitif bir işaretli değer olarak kapsanır.

XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.13 ve 5.4.7](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xtimespan"></a>x:TimeSpan

CLR yedeklemesi için, `x:TimeSpan` ilkel öğesine karşılık gelir <xref:System.TimeSpan> .

Zaman tarih biçimi için XAML ayrıştırma, kültür altında kendiliğinden yapılır `en-US` .

XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.16 ve 5.4.10](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xuri"></a>x:Uri

CLR yedeklemesi için, `x:Uri` ilkel öğesine karşılık gelir <xref:System.Uri> .

Protokollerin denetlenmesi için XAML tanımının bir parçası değildir `x:Uri` .

XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.15 ve 5.4.9](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xbyte"></a>x:Byte

CLR yedeklemesi için, `x:Byte` ilkel öğesine karşılık gelir <xref:System.Byte> . <xref:System.Byte>  /  `x:Byte` , İmzasız olarak kabul edilir.

XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.10 ve 5.4.4](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xarray"></a>x:Array

CLR yedeklemesi için, `x:Array` ilkel öğesine karşılık gelir <xref:System.Array> .

Bir diziyi, biçimlendirme uzantısı söz dizimini kullanarak XAML 2006 ' de tanımlayabilirsiniz; Ancak XAML 2009 sözdizimi, biçimlendirme uzantısına erişmeyi gerektirmeyen dil tanımlı bir temel dildir. XAML 2006 desteği hakkında daha fazla bilgi için bkz. [X:Array Işaretleme uzantısı](xarray-markup-extension.md).

XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.18](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="wpf-support"></a>WPF desteği

WPF 'de XAML 2009 özelliklerini, ancak yalnızca işaretleme ile derlenen XAML için kullanabilirsiniz. WPF için biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 anahtar sözcüklerini ve özelliklerini desteklememektedir.

XAML 2009 özelliklerini WPF ile birlikte kullanabileceğiniz bir senaryo, gevşek XAML yazarsa ve bu XAML 'yi ile bir WPF çalışma zamanına ve nesne grafiğine yüklerseniz <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> . WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> ve, <xref:System.Windows.Markup.XamlReader.Load%2A> XAML 2009 dil anahtar sözcüklerini ve özelliklerini geçerli bir nesne grafiği temsiline işleyebilir.
