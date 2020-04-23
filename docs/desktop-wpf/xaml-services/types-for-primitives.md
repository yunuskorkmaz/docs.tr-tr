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
ms.openlocfilehash: 3bd486ee66c5f9a32621416638bb7575025f7dee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071838"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Ortak XAML dil ilkelleri için yerleşik türleri

XAML 2009, ortak dil çalışma zamanında (CLR) ve diğer programlama dillerinde sık kullanılan çeşitli veri türleri için XAML dil düzeyinde destek sunar. XAML 2009 bu ilkel için `x:Object` `x:Boolean`destek `x:Char` `x:String`ekler: `x:Single` `x:Double`, `x:Int16` `x:Int32` `x:Int64` `x:TimeSpan` `x:Uri` `x:Decimal`, , `x:Byte`, , , , , ,`x:Array`

## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>XAML Biçimlendirmede Dil İlkelleri Için Önceki Teknikler

 Önceki WPF sürümleri için XAML'de, .NET Framework için CLR ilkel tanım sınıfı içeren derleme ve ad alanını eşleyerek CLR dil ilkellerine başvuruda bulunabilirsiniz. Bunların çoğu mscorlib montaj ve <xref:System> ad alanı bulunmaktadır. Örneğin, kullanmak <xref:System.Int32>için, aşağıdaki eşleme (bundan sonra gösterilen bir örnek kullanımı ile) bildirebilirsiniz:

```xaml
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Application.Resources>
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>
  </Application.Resources>
</Application>
```

## <a name="xaml-2009-language-primitives"></a>XAML 2009 Dil İlkel

Kural olarak, XAML ve diğer tüm XAML dil öğeleri için `x:` dil ilkel, önek de dahil olmak üzere gösterilir. XAML dil öğeleri genellikle gerçek dünya biçimlendirmesinde bu şekilde kullanılır. Bu sözleşme, WPF'deki XAML kavramsal dokümantasyonlarında ve ayrıca XAML belirtiminde takip edilir.

### <a name="xobject"></a>x:Nesne

CLR desteği `x:Object` için, <xref:System.Object>ilkel karşılık gelir.

Bu ilkel genellikle uygulama biçimlendirmesinde kullanılmaz, ancak XAML türü sistemde atabilmeyi denetleme gibi bazı senaryolar için yararlı olabilir.

### <a name="xboolean"></a>x:Boolean

CLR desteği `x:Boolean` için, <xref:System.Boolean>ilkel karşılık gelir.

XAML, değerleri `x:Boolean` karşıkonuolmayan durum olarak ayrıştırır. `x:Bool` Kabul edilen bir alternatif olmadığını unutmayın. XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.17 ve 5.4.11'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

### <a name="xchar"></a>x:Char

CLR desteği `x:Char` için, <xref:System.Char>ilkel karşılık gelir.

Dize ve char türleri, XML düzeyinde dosyanın genel kodlaması ile etkileşime sahiptir. XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölüm 5.2.7 ve 5.4.1'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

### <a name="xstring"></a>x:Dize

CLR desteği `x:String` için, <xref:System.String>ilkel karşılık gelir.

Dize ve char türleri, XML düzeyinde dosyanın genel kodlaması ile etkileşime sahiptir. XAML dil belirtimi tanımı için [ \[MS-XAML\] Bölümleri 5.2.6'ya](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

### <a name="xdecimal"></a>x:Ondalık

CLR desteği `x:Decimal` için, <xref:System.Decimal>ilkel karşılık gelir.

XAML ayrıştırma doğal `en-US` olarak kültür altında yapılır. Kültür `en-US` altında, ondalık bileşenler için doğru ayırıcı her`.`zaman bir dönemdir ( ) geliştirme ortamının kültür ayarları ne olursa olsun, ya da XAML çalışma zamanında yüklenir nihai istemci hedefi.

XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.14 ve 5.4.8'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

### <a name="xsingle"></a>x:Tek

CLR desteği `x:Single` için, <xref:System.Single>ilkel karşılık gelir.

Sayısal değerlere ek olarak, metin `x:Single` sözdizimi de belirteçleri `Infinity`, ve `-Infinity` `NaN`. Bu belirteçler duruma duyarlı olarak kabul edilir.

`x:Single`metin sözdiziminde ilk karakter `e` veya `E`.

XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölüm 5.2.8 ve 5.4.2'ye](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

### <a name="xdouble"></a>x:Çift

CLR desteği `x:Double` için, <xref:System.Double>ilkel karşılık gelir.

`x:Double` Sayısal değerlere ek olarak, belirteçlere `Infinity`izin vermek için `-Infinity`metin `NaN`sözdizimi , ve . Bu belirteçler duruma duyarlı olarak kabul edilir.

`x:Double`değerleri bilimsel gösterim biçiminde destekleyebilir. Karakteri `e` kullanın `E` veya üs kısmını tanıtmak için.

XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.9 ve 5.4.3'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

### <a name="xint16"></a>x:Int16

CLR desteği için, `x:Int16` <xref:System.Int16> ilkel karşılık `x:Int16` gelir ve imzalı olarak kabul edilir. XAML'de, metin sözdiziminde artı ( )`+`işaretinin olmaması pozitif imzalı değer olarak ima edilir.

XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.11 ve 5.4.5'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

### <a name="xint32"></a>x:Int32

CLR desteği `x:Int32` için, <xref:System.Int32>ilkel karşılık gelir. `x:Int32`imzalı olarak kabul edilir. XAML'de, metin sözdiziminde artı ( )`+`işaretinin olmaması pozitif imzalı değer olarak ima edilir.

XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.12 ve 5.4.6'ya](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

### <a name="xint64"></a>x:Int64

CLR desteği `x:Int64` için, <xref:System.Int64>ilkel karşılık gelir. `x:Int64`imzalı olarak kabul edilir. XAML'de, metin sözdiziminde artı ( )`+`işaretinin olmaması pozitif imzalı değer olarak ima edilir.

XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.13 ve 5.4.7'ye](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

### <a name="xtimespan"></a>x:TimeSpan

CLR desteği `x:TimeSpan` için, <xref:System.TimeSpan>ilkel karşılık gelir.

XAML zaman-tarih biçimi için ayrıştırma `en-US` doğal olarak kültür altında yapılır.

XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.16 ve 5.4.10'a](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

### <a name="xuri"></a>x:Uri

CLR desteği `x:Uri` için, <xref:System.Uri>ilkel karşılık gelir.

Protokolleri denetlemek `x:Uri`XAML tanımının bir parçası değildir.

XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.15 ve 5.4.9'a](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

### <a name="xbyte"></a>x:Bayt

CLR desteği `x:Byte` için, <xref:System.Byte>ilkel karşılık gelir. <xref:System.Byte>  /  A `x:Byte` imzasız olarak kabul edilir.

XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.10 ve 5.4.4'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

### <a name="xarray"></a>x:Dizi

CLR desteği `x:Array` için, <xref:System.Array>ilkel karşılık gelir.

XAML 2006'da bir dizi biçimlendirme uzantısı sözdizimini kullanarak tanımlayabilirsiniz; ancak, XAML 2009 sözdizimi bir biçimlendirme uzantısı erişim gerektirmeyen bir dil tanımlı ilkel. XAML 2006 desteği hakkında daha fazla bilgi için [bkz: x:Array Markup Extension](xarray-markup-extension.md).

XAML dil belirtimi tanımı için [ \[MS-XAML\] Bölümleri 5.2.18'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

## <a name="wpf-support"></a>WPF Desteği

WPF'de XAML 2009 özelliklerini ancak yalnızca biçimlendirmeyle derlenen XAML için kullanabilirsiniz. WPF için biçimlendirmeyle derlenen XAML ve XAML'nin BAML formu şu anda XAML 2009 anahtar kelimelerini ve özelliklerini desteklemez.

XAML 2009 özelliklerini WPF ile birlikte kullanabileceğiniz bir senaryo, gevşek XAML yazarsanız ve bu XAML'yi <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>WPF çalışma süresi ve nesne grafiğine yükleyin. WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> ve <xref:System.Windows.Markup.XamlReader.Load%2A> onun XAML 2009 dil anahtar kelimeleri ve özellikleri geçerli bir nesne grafik gösterimi içine işleyebilir.
