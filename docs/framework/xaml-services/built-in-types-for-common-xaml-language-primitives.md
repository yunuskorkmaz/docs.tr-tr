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
ms.openlocfilehash: 15c359a9a7f9797fc03ce20c453905af01f925d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564358"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>XAML Dili Ortak Temelleri İçin Yerleşik Türler
XAML 2009 sık kullanılan temelleri ortak dil çalışma zamanı (CLR) ve diğer programlama dilleri olan çeşitli veri türleri için XAML dil düzeyi destek sunar. XAML 2009 bu temelleri için destek ekler: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, ve `x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>XAML biçimlendirme dil temelleri için önceki teknikleri  
 XAML'de önceki WPF sürümleri için derleme ve .NET Framework CLR ilkel tanımı sınıf bulunan ad alanını eşleyerek CLR dil temelleri başvurabilir. Bu çoğu mscorlib derlemede ve <xref:System> ad alanı. Örneğin, kullanılacak <xref:System.Int32>, aşağıdaki eşleme (Bundan sonra gösterilen kullanım örneği ile) bildirebilirsiniz:  
  
```  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a>XAML 2009 dil temelleri  
 Kurala göre XAML ve diğer tüm XAML dil öğeleri için dil temelleri dahil olmak üzere gösterilir `x:` öneki. XAML dil öğeleri genellikle kullanılan gerçek biçimlendirmede nasıl budur. Bu kural, XAML WPF hem de XAML belirtimi kavramsal belgelerindeki izlenir.  
  
### <a name="xobject"></a>x: nesne  
 CLR yedekleme için `x:Object` ilkel karşılık gelen <xref:System.Object>.  
  
 Bu temel genellikle uygulama biçimlendirmede kullanılmaz, ancak bir XAML türü sisteminde assignability denetimi gibi bazı senaryolar için yararlı olabilir.  
  
### <a name="xboolean"></a>x: Boolean  
 CLR yedekleme için `x:Boolean` ilkel karşılık gelen <xref:System.Boolean>.  
  
 XAML ayrıştırmak için değerleri `x:Boolean` olarak büyük küçük harfe duyarlı. Unutmayın `x:Bool` kabul edilen alternatif değildir. XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.17 ve 5.4.11 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xchar"></a>x: Char  
 CLR yedekleme için `x:Char` ilkel karşılık gelen <xref:System.Char>.  
  
 Dize ve karakter türleri XML düzeyinde dosya genel kodlama ile etkileşim sahip. XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.7'ye ve 5.4.1 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xstring"></a>x: String  
 CLR yedekleme için `x:String` ilkel karşılık gelen <xref:System.String>.  
  
 Dize ve karakter türleri XML düzeyinde dosya genel kodlama ile etkileşim sahip. XAML dil belirtimi, bkz. [ \[MS XAML\] bölümleri 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdecimal"></a>x: ondalık  
 CLR yedekleme için `x:Decimal` ilkel karşılık gelen <xref:System.Decimal>.  
  
 XAML ayrıştırma kendiliğinden altında yapıldığını unutmayın `en-US` kültür. Altında `en-US` , ondalık bileşenleri için doğru ayırıcı kültürdür her zaman bir süre (`.`) geliştirme ortamı veya çalışma zamanında XAML yüklendiği nihai istemci hedef kültür ayarları ne olursa olsun.  
  
 XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.14 ve 5.4.8 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xsingle"></a>x: Single  
 CLR yedekleme için `x:Single` ilkel karşılık gelen <xref:System.Single>.  
  
 Sayısal değerler için metin sözdizimi yanı sıra `x:Single` ayrıca belirteçleri verir `Infinity`, `-Infinity`, ve `NaN`. Bu belirteçler olarak büyük küçük harfe duyarlı kabul edilir.  
  
 `x:Single` ilk karakter, metin sözdizimi ise değerleri bilimsel gösterim biçiminde destekleyebilir `e` veya `E`.  
  
 XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.8 ve 5.4.2 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdouble"></a>x: Double  
 CLR yedekleme için `x:Double` ilkel karşılık gelen <xref:System.Double>.  
  
 Sayısal değerler için metin sözdizimi yanı sıra `x:Double` belirteçleri verir `Infinity`, `-Infinity`, ve `NaN`. Bu belirteçler olarak büyük küçük harfe duyarlı kabul edilir.  
  
 `x:Double` değerleri bilimsel gösterim biçiminde destekleyebilir. Karakter kullanın `e` veya `E` üs bölümü tanıtmak için.  
  
 XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.9 ve 5.4.3 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint16"></a>x: Int16  
 CLR yedekleme için `x:Int16` ilkel karşılık gelen <xref:System.Int16> ve `x:Int16` imzalanmış olarak kabul edilir. XAML'de artı yokluğu (`+`) metin sözdiziminde oturum olarak imzalanmış pozitif kapsanan.  
  
 XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.11 ve 5.4.5 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint32"></a>x: Int32  
 CLR yedekleme için `x:Int32` ilkel karşılık gelen <xref:System.Int32>. `x:Int32` imzalanmış olarak kabul edilir. XAML'de artı yokluğu (`+`) metin sözdiziminde oturum olarak imzalanmış pozitif kapsanan.  
  
 XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.12 ve 5.4.6 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint64"></a>x: Int64  
 CLR yedekleme için `x:Int64` ilkel karşılık gelen <xref:System.Int64>. `x:Int64` imzalanmış olarak kabul edilir. XAML'de artı yokluğu (`+`) metin sözdiziminde oturum olarak imzalanmış pozitif kapsanan.  
  
 XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.13 ve 5.4.7 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xtimespan"></a>x: TimeSpan  
 CLR yedekleme için `x:TimeSpan` ilkel karşılık gelen <xref:System.TimeSpan>.  
  
 Bu XAML ayrıştırma saat ve tarih biçimi kendiliğinden altında bitti için Not `en-US` kültür.  
  
 XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.16 ve 5.4.10 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xuri"></a>x: Uri  
 CLR yedekleme için `x:Uri` ilkel karşılık gelen <xref:System.Uri>.  
  
 Protokolleri denetimi için XAML tanımının bir parçası değil `x:Uri`.  
  
 XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.15 ve 5.4.9 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xbyte"></a>x: Byte  
 CLR yedekleme için `x:Byte` ilkel karşılık gelen <xref:System.Byte>. A <xref:System.Byte>  /  `x:Byte` davranılır olarak imzalanmamış.  
  
 XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.10 ve 5.4.4 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xarray"></a>x: Array  
 CLR yedekleme için `x:Array` ilkel karşılık gelen <xref:System.Array>.  
  
 Biçimlendirme uzantısı sözdizimi kullanarak, bir dizi XAML 2006'tanımlayabilirsiniz; Ancak, XAML 2009 söz dizimi biçimlendirme uzantısı erişme gerektirmez dili tarafından tanımlanan bir ilkel olur. XAML 2006 desteği hakkında daha fazla bilgi için bkz: [x: Array işaretleme uzantısı](../../../docs/framework/xaml-services/x-array-markup-extension.md).  
  
 XAML dil belirtimi, bkz. [ \[MS XAML\] bölümleri 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>WPF desteği  
 WPF'de, ancak yalnızca biçimlendirme-derlenmemiş XAML için XAML 2009 özellikleri kullanabilirsiniz. XAML biçimlendirme derlenmiş WPF ve XAML BAML form için şu anda desteklemediği XAML 2009 anahtar sözcükleri ve özellikler.  
  
 Burada kullanabileceğiniz XAML 2009 özellikleri WPF ile birlikte bir gevşek XAML yazar ve ardından bir WPF çalışma zamanı ve Nesne grafiği içine bu XAML yükleyin senaryodur <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>. WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> ve kendi <xref:System.Windows.Markup.XamlReader.Load%2A> XAML 2009 dil anahtar sözcükleri ve özellikleri geçerli nesne grafiği gösterimine işleyebilir.
