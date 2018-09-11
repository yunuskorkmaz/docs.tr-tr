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
ms.openlocfilehash: f6225dfcc02b90da58ccafd5c70726b6f80f29d4
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361173"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>XAML Dili Ortak Temelleri İçin Yerleşik Türler
XAML 2009, ortak dil çalışma zamanı (CLR) ve diğer programlama dillerinde sık kullanılan temel eleman olan birkaç veri türü için XAML dili düzeyinde destek sunar. XAML 2009 şu temelleri için destek ekler: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, ve `x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>XAML biçimlendirmede dil temelleri için önceki teknikler  
 WPF önceki sürümleri için XAML içinde .NET Framework için CLR temel tanım sınıfı içeren ad alanı ve derleme eşleyerek CLR dil temellerine başvurabilirsiniz. Bunların çoğu mscorlib derlemede ve <xref:System> ad alanı. Örneğin, kullanılacak <xref:System.Int32>, aşağıdaki eşlemeyi (Bundan sonra gösterilen örnek kullanım ile) bildirebilirsiniz:  
  
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
 Kural gereği, XAML ve diğer tüm XAML dil öğeleri dil temelleri birlikte gösterilir `x:` önek. Bu nasıl XAML dil öğeleri genellikle gerçek biçimlendirme içinde kullanılır. Bu kural, WPF ve ayrıca XAML belirtiminde XAML için kavramsal belgelerinde izlenir.  
  
### <a name="xobject"></a>x: nesne  
 CLR yedekleme `x:Object` karşılık gelen temel <xref:System.Object>.  
  
 Bu temel eleman uygulama biçimlendirme içinde genellikle kullanılmaz, ancak XAML türü sistemde atanabilirliği denetleme gibi bazı senaryolarda yararlı olabilir.  
  
### <a name="xboolean"></a>x: Boolean  
 CLR yedekleme `x:Boolean` karşılık gelen temel <xref:System.Boolean>.  
  
 XAML ayrıştırma değerlerini `x:Boolean` olarak büyük küçük harfe duyarlı. Unutmayın `x:Bool` kabul edilen bir alternatif değildir. XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.17 and 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xchar"></a>x: Char  
 CLR yedekleme `x:Char` karşılık gelen temel <xref:System.Char>.  
  
 Dize ve karakter türlerinin XML düzeyinde dosyanın genel kodlama ile etkileşimi vardır. XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.7 and 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xstring"></a>x: String  
 CLR yedekleme `x:String` karşılık gelen temel <xref:System.String>.  
  
 Dize ve karakter türlerinin XML düzeyinde dosyanın genel kodlama ile etkileşimi vardır. XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdecimal"></a>x: ondalık  
 CLR yedekleme `x:Decimal` karşılık gelen temel <xref:System.Decimal>.  
  
 XAML ayrıştırma altında kendiliğinden yapıldığına olduğunu unutmayın `en-US` kültür. Altında `en-US` kültür, ondalık sayı bileşenleri için doğru ayırıcı her zaman bir noktadır (`.`) geliştirme ortamının veya XAML çalışma zamanında yüklendiği nihai istemci hedef kültür ayarları ne olursa olsun.  
  
 XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.14 and 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xsingle"></a>x: Single  
 CLR yedekleme `x:Single` karşılık gelen temel <xref:System.Single>.  
  
 İçin metin sözdizimi sayısal değerlere ek olarak `x:Single` ayrıca belirteçleri verir `Infinity`, `-Infinity`, ve `NaN`. Bu belirteçleri olarak büyük küçük harfe duyarlı kabul edilir.  
  
 `x:Single` metin sözdiziminin ilk karakteri ise değerleri bilimsel gösterim biçiminde destekleyebilir `e` veya `E`.  
  
 XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.8 and 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdouble"></a>x: Double  
 CLR yedekleme `x:Double` karşılık gelen temel <xref:System.Double>.  
  
 İçin metin sözdizimi sayısal değerlere ek olarak `x:Double` belirteçlerine izin verir `Infinity`, `-Infinity`, ve `NaN`. Bu belirteçleri olarak büyük küçük harfe duyarlı kabul edilir.  
  
 `x:Double` değerleri bilimsel gösterim biçiminde destekleyebilir. Karakter kullanın `e` veya `E` üs bölümü tanıtmak için.  
  
 XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.9 and 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint16"></a>x: Int16  
 CLR yedekleme `x:Int16` karşılık gelen temel <xref:System.Int16> ve `x:Int16` imzalı olarak kabul edilir. XAML, artı olmaması, (`+`) içinde metin sözdiziminde oturum pozitif imzalı değer belirtilir.  
  
 XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.11 and 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint32"></a>x: Int32  
 CLR yedekleme `x:Int32` karşılık gelen temel <xref:System.Int32>. `x:Int32` işaretlenmiş olarak kabul edilir. XAML, artı olmaması, (`+`) içinde metin sözdiziminde oturum pozitif imzalı değer belirtilir.  
  
 XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.12 and 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint64"></a>x: Int64  
 CLR yedekleme `x:Int64` karşılık gelen temel <xref:System.Int64>. `x:Int64` işaretlenmiş olarak kabul edilir. XAML, artı olmaması, (`+`) içinde metin sözdiziminde oturum pozitif imzalı değer belirtilir.  
  
 XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.13 and 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xtimespan"></a>x: TimeSpan  
 CLR yedekleme `x:TimeSpan` karşılık gelen temel <xref:System.TimeSpan>.  
  
 Bu XAML ayrıştırma için saat ve tarih biçimi altında kendiliğinden yapıldığına dikkat edin `en-US` kültür.  
  
 XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.16 and 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xuri"></a>x: Uri  
 CLR yedekleme `x:Uri` karşılık gelen temel <xref:System.Uri>.  
  
 Protokollerin denetimi için XAML tanımının bir parçası değil `x:Uri`.  
  
 XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.15 and 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xbyte"></a>x: Byte  
 CLR yedekleme `x:Byte` karşılık gelen temel <xref:System.Byte>. A <xref:System.Byte>  /  `x:Byte` değerlendirilir işaretlenmemiş olarak.  
  
 XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.10 and 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xarray"></a>x: Array  
 CLR yedekleme `x:Array` karşılık gelen temel <xref:System.Array>.  
  
 Biçimlendirme uzantısı sözdizimi kullanarak XAML 2006'da dizi tanımlayabilirsiniz; Ancak, XAML 2009 biçimlendirme uzantısına erişmesi gerekmeyen dil tanımlı temel sözdizimidir. XAML 2006 desteği hakkında daha fazla bilgi için bkz. [x: Array işaretleme uzantısı](../../../docs/framework/xaml-services/x-array-markup-extension.md).  
  
 XAML dil belirtimi tanımı için bkz. [ \[MS-XAML\] Sections 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>WPF desteği  
 WPF içinde ancak yalnızca işaretleme yapılmayan XAML için XAML 2009 özelliklerini kullanabilirsiniz. WPF ve XAML, BAML formu için biçimlendirme derlenmiş XAML şu anda desteklemediğinden XAML 2009 anahtar sözcükleri ve özellikleri.  
  
 XAML 2009 özelliklerini WPF ile birlikte kullanabileceğiniz senaryo gevşek XAML yazar ve sonra içine bir WPF çalışma zamanı ve Nesne grafiği ile XAML yük olan <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>. WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> ve kendi <xref:System.Windows.Markup.XamlReader.Load%2A> XAML 2009 dil anahtar sözcükleri ve özellikleri bir geçerli nesne grafiği gösterimi halinde işler.
