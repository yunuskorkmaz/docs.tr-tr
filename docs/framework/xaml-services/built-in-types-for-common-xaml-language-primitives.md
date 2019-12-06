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
ms.openlocfilehash: c6af46fe2ea21d081e693ee83949651bd388a045
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837278"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>XAML Dili Ortak Temelleri İçin Yerleşik Türler
XAML 2009, ortak dil çalışma zamanında (CLR) ve diğer programlama dillerinde sık kullanılan temel elemanlar olan çeşitli veri türleri için XAML dil düzeyinde destek sunar. XAML 2009, bu temel öğeler için destek ekler: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`ve `x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>XAML Biçimlendirmede Dil Temelleri için Önceki Teknikler  
 WPF önceki sürümleri için XAML içinde .NET Framework için CLR temel tanım sınıfı içeren bir derlemeyi ve ad boşluğunu eşleyerek CLR dil temellerine başvurabilirsiniz. Bunların çoğu mscorlib derlemesi ve <xref:System> ad alanı içindedir. Örneğin, <xref:System.Int32> kullanmak için aşağıdaki eşlemeyi (bundan sonra örnek kullanım ile gösterilen) bildirebilirsiniz:  
  
```xaml  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a>XAML 2009 Dil Temelleri  
 Kural gereği, XAML dil temelleri ve diğer tüm XAML dil öğeleri `x:` öneki ile birlikte gösterilir. XAML dil öğeleri genellikle gerçek biçimlendirme içinde bu şekilde kullanılır. WPF'de XAML için kavramsal belgelerde ve ayrıca XAML belirtiminde bu kural izlenir.  
  
### <a name="xobject"></a>x:Nesne  
 CLR desteklemesi için `x:Object` temel öğesi <xref:System.Object> öğesine karşılık gelir.  
  
 Bu temel eleman uygulama biçimlendirme içinde genellikle kullanılmaz, ancak XAML türü bir sistemde atanabilirliği denetleme gibi bazı senaryolarda yararlı olabilir.  
  
### <a name="xboolean"></a>x:Boole  
 CLR desteklemesi için `x:Boolean` temel öğesi <xref:System.Boolean> öğesine karşılık gelir.  
  
 XAML, değerleri `x:Boolean` için ayrıştırır; büyük/küçük harf duyarlıdır. `x:Bool` kabul edilen bir alternatif olmadığına dikkat edin. XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.17 ve 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xchar"></a>x:Char  
 CLR desteklemesi için `x:Char` temel öğesi <xref:System.Char> öğesine karşılık gelir.  
  
 Dize ve karakter türlerinin, XML düzeyinde dosyanın genel kodlamasıyla etkileşimi vardır. XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.7 ve 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xstring"></a>x:Dize  
 CLR desteklemesi için `x:String` temel öğesi <xref:System.String> öğesine karşılık gelir.  
  
 Dize ve karakter türlerinin, XML düzeyinde dosyanın genel kodlamasıyla etkileşimi vardır. XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xdecimal"></a>x:Ondalık  
 CLR desteklemesi için `x:Decimal` temel öğesi <xref:System.Decimal> öğesine karşılık gelir.  
  
 XAML ayrıştırmanın `en-US` kültürü altında kendiliğinden yapıldığına dikkat edin. `en-US` kültürü altında, ondalık sayı bileşenleri için doğru ayırıcı her zaman, geliştirme ortamının veya XAML'nin çalışma zamanında yüklendiği asıl son istemcinin kültür ayarları göz ardı edilerek her zaman bir noktadır (`.`) .  
  
 XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.14 ve 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xsingle"></a>x:Tek  
 CLR desteklemesi için `x:Single` temel öğesi <xref:System.Single> öğesine karşılık gelir.  
  
 Sayısal değerlere ek olarak `x:Single` için metin sözdizimi `Infinity`, `-Infinity` ve `NaN` belirteçlerine izin verir. Bu belirteçlerin büyük/küçük harfe duyarlı olduğu kabul edilir.  
  
 `x:Single` metin sözdiziminin ilk karakteri `e` veya `E` ise değerleri bilimsel gösterim biçiminde destekleyebilir.  
  
 XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.8 ve 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xdouble"></a>x:Çift  
 CLR desteklemesi için `x:Double` temel öğesi <xref:System.Double> öğesine karşılık gelir.  
  
 Sayısal değerlere ek olarak `x:Double` için metin sözdizimi `Infinity`, `-Infinity` ve `NaN` belirteçlerine izin verir. Bu belirteçlerin büyük/küçük harfe duyarlı olduğu kabul edilir.  
  
 `x:Double` değerleri bilimsel gösterim biçiminde destekleyebilir. Üs bölümü tanıtmak için `e` veya `E` karakterini kullanın.  
  
 XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.9 ve 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xint16"></a>x:Int16  
 CLR yedekleme için `x:Int16` karşılık gelen temel <xref:System.Int16> ve `x:Int16` imzalı olarak kabul edilir. XAML içinde metin sözdiziminde artı (`+`) işaretinin olmaması pozitif imzalı değer olarak belirtilir.  
  
 XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.11 ve 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xint32"></a>x:Int32  
 CLR desteklemesi için `x:Int32` temel öğesi <xref:System.Int32> öğesine karşılık gelir. `x:Int32` işaretlenmiş olarak kabul edilir. XAML içinde metin sözdiziminde artı (`+`) işaretinin olmaması pozitif imzalı değer olarak belirtilir.  
  
 XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.12 ve 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xint64"></a>x:Int64  
 CLR desteklemesi için `x:Int64` temel öğesi <xref:System.Int64> öğesine karşılık gelir. `x:Int64` işaretlenmiş olarak kabul edilir. XAML içinde metin sözdiziminde artı (`+`) işaretinin olmaması pozitif imzalı değer olarak belirtilir.  
  
 XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.13 ve 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xtimespan"></a>x:TimeSpan  
 CLR desteklemesi için `x:TimeSpan` temel öğesi <xref:System.TimeSpan> öğesine karşılık gelir.  
  
 Saat tarih biçimi için XAML ayrıştırmanın `en-US` kültürü altında kendiliğinden yapıldığına dikkat edin.  
  
 XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.16 ve 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xuri"></a>x:Uri  
 CLR desteklemesi için `x:Uri` temel öğesi <xref:System.Uri> öğesine karşılık gelir.  
  
 Protokollerin denetimi, `x:Uri` için XAML tanımının bir parçası değildir.  
  
 XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.15 ve 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xbyte"></a>x:Byte  
 CLR desteklemesi için `x:Byte` temel öğesi <xref:System.Byte> öğesine karşılık gelir. <xref:System.Byte> / `x:Byte` imzasız olarak kabul edilir.  
  
 XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.10 ve 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xarray"></a>x:Dizi  
 CLR desteklemesi için `x:Array` temel öğesi <xref:System.Array> öğesine karşılık gelir.  
  
 Bir diziyi, biçimlendirme uzantısı söz dizimini kullanarak XAML 2006 ' de tanımlayabilirsiniz; Ancak XAML 2009 sözdizimi, biçimlendirme uzantısına erişmeyi gerektirmeyen dil tanımlı bir temel dildir. XAML 2006 desteği hakkında daha fazla bilgi için bkz. [X:Array Işaretleme uzantısı](x-array-markup-extension.md).  
  
 XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>WPF Desteği  
 WPF 'de XAML 2009 özelliklerini, ancak yalnızca işaretleme ile derlenen XAML için kullanabilirsiniz. WPF için biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 anahtar sözcüklerini ve özelliklerini desteklememektedir.  
  
 XAML 2009 özelliklerini WPF ile birlikte kullanabileceğiniz bir senaryo, gevşek XAML yazarsa ve bu XAML 'yi <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>bir WPF çalışma zamanına ve nesne grafiğine yüklerseniz. WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> ve <xref:System.Windows.Markup.XamlReader.Load%2A>, XAML 2009 dil anahtar sözcüklerini ve özelliklerini geçerli bir nesne grafiği temsiline işleyebilir.
