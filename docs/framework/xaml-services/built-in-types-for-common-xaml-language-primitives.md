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
ms.openlocfilehash: 85fd0c04a40b9de64979e4da1459dbf8953a93bf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053887"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>XAML Dili Ortak Temelleri İçin Yerleşik Türler
XAML 2009, ortak dil çalışma zamanında (CLR) ve diğer programlama dillerinde sık kullanılan temel elemanlar olan çeşitli veri türleri için XAML dil düzeyinde destek sunar. XAML 2009, bu temel öğeler için destek `x:Object`ekler `x:Boolean`: `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`,,, `x:TimeSpan`, `x:Uri`, ve`x:Byte``x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>XAML biçimlendirmesinde dil temelleri için önceki teknikler  
 Önceki WPF sürümleri için XAML 'de, .NET Framework için bir CLR ilkel tanım sınıfı içeren derlemeyi ve ad alanını eşleyerek CLR dil temel temellerine başvurabilirsiniz. Bunların çoğu mscorlib derlemesinde ve <xref:System> ad alanında bulunur. Örneğin, kullanmak <xref:System.Int32>için aşağıdaki eşlemeyi bildirebilirsiniz (bundan sonra bir örnek kullanım ile gösterilir):  
  
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
## <a name="xaml-2009-language-primitives"></a>XAML 2009 dil temelleri  
 Kurala göre, XAML için dil temelleri ve diğer xaml dil öğeleri, `x:` ön ek dahil gösterilir. XAML dil öğeleri genellikle gerçek zamanlı biçimlendirmede kullanılır. Bu kural, WPF 'de XAML için kavramsal belgelerde ve ayrıca XAML belirtiminde izlenir.  
  
### <a name="xobject"></a>x:Object  
 CLR yedeklemesi için, `x:Object` ilkel öğesine <xref:System.Object>karşılık gelir.  
  
 Bu ilkel genellikle uygulama biçimlendirmesinde kullanılmaz, ancak bir XAML tür sisteminde atananlıya bilirlik gibi bazı senaryolarda yararlı olabilir.  
  
### <a name="xboolean"></a>x:Boolean  
 CLR yedeklemesi için, `x:Boolean` ilkel öğesine <xref:System.Boolean>karşılık gelir.  
  
 XAML, büyük/ `x:Boolean` küçük harfe duyarsız değerleri ayrıştırır. `x:Bool` Kabul edilen bir alternatif değildir. XAML dil belirtimi tanımı için bkz [ \[. ms-xaml\] sections 5.2.17 ve 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xchar"></a>x:Char  
 CLR yedeklemesi için, `x:Char` ilkel öğesine <xref:System.Char>karşılık gelir.  
  
 Dize ve karakter türlerinin, XML düzeyinde dosyanın genel kodlamasıyla etkileşimi vardır. XAML dil belirtimi tanımı için bkz [ \[. ms-xaml\] sections 5.2.7 ve 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xstring"></a>x:String  
 CLR yedeklemesi için, `x:String` ilkel öğesine <xref:System.String>karşılık gelir.  
  
 Dize ve karakter türlerinin, XML düzeyinde dosyanın genel kodlamasıyla etkileşimi vardır. XAML dil belirtimi tanımı için bkz [ \[. MS-\] xaml sections 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdecimal"></a>x:Decimal  
 CLR yedeklemesi için, `x:Decimal` ilkel öğesine <xref:System.Decimal>karşılık gelir.  
  
 XAML ayrıştırma 'nın kültür altında `en-US` kendiliğinden yapıldığını unutmayın. Kültür `en-US` altında, bir Decimal bileşenleri için doğru ayırıcı, geliştirme ortamının kültür ayarlarından ya da xaml`.`'nin çalışma zamanında yüklendiği son istemci hedefinde bağımsız olarak her zaman bir nokta () olur.  
  
 XAML dil belirtimi tanımı için bkz [ \[. ms-xaml\] sections 5.2.14 ve 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xsingle"></a>x:Single  
 CLR yedeklemesi için, `x:Single` ilkel öğesine <xref:System.Single>karşılık gelir.  
  
 Sayısal değerlere ek `x:Single` olarak, için de metin sözdizimi, ve `Infinity` `-Infinity` `NaN`belirteçlerine izin verir. Bu belirteçler büyük/küçük harfe duyarlı olarak değerlendirilir.  
  
 `x:Single`metin sözdiziminde ilk karakter veya `e` `E`ise, bilimsel gösterim biçimindeki değerleri destekleyebilir.  
  
 XAML dil belirtimi tanımı için bkz [ \[. ms-xaml\] sections 5.2.8 ve 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdouble"></a>x:Double  
 CLR yedeklemesi için, `x:Double` ilkel öğesine <xref:System.Double>karşılık gelir.  
  
 Sayısal değerlere ek olarak, `x:Double` için metin sözdizimi, ve `Infinity` `-Infinity` `NaN`belirteçlerine izin verir. Bu belirteçler büyük/küçük harfe duyarlı olarak değerlendirilir.  
  
 `x:Double`, bilimsel gösterim biçimindeki değerleri destekleyebilir. Üs kısmını tanıtmak `e` için `E` veya karakterini kullanın.  
  
 XAML dil belirtimi tanımı için bkz [ \[. ms-xaml\] sections 5.2.9 ve 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint16"></a>x:Int16  
 CLR yedeklemesi için, `x:Int16` ilkel öğesine <xref:System.Int16> karşılık gelir ve `x:Int16` imzalı olarak kabul edilir. XAML 'de, artı (`+`) işareti metin sözdiziminde devamsızlık pozitif bir işaretli değer olarak kapsanır.  
  
 XAML dil belirtimi tanımı için bkz [ \[. ms-xaml\] sections 5.2.11 ve 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint32"></a>x:Int32  
 CLR yedeklemesi için, `x:Int32` ilkel öğesine <xref:System.Int32>karşılık gelir. `x:Int32`imzalı olarak kabul edilir. XAML 'de, artı (`+`) işareti metin sözdiziminde devamsızlık pozitif bir işaretli değer olarak kapsanır.  
  
 XAML dil belirtimi tanımı için bkz [ \[. ms-xaml\] sections 5.2.12 ve 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint64"></a>x:Int64  
 CLR yedeklemesi için, `x:Int64` ilkel öğesine <xref:System.Int64>karşılık gelir. `x:Int64`imzalı olarak kabul edilir. XAML 'de, artı (`+`) işareti metin sözdiziminde devamsızlık pozitif bir işaretli değer olarak kapsanır.  
  
 XAML dil belirtimi tanımı için bkz [ \[. ms-xaml\] sections 5.2.13 ve 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xtimespan"></a>x:TimeSpan  
 CLR yedeklemesi için, `x:TimeSpan` ilkel öğesine <xref:System.TimeSpan>karşılık gelir.  
  
 Zaman tarih biçimi için XAML ayrıştırma 'nın, kültür altında `en-US` kendiliğinden yapıldığını unutmayın.  
  
 XAML dil belirtimi tanımı için bkz [ \[. ms-xaml\] sections 5.2.16 ve 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xuri"></a>x:Uri  
 CLR yedeklemesi için, `x:Uri` ilkel öğesine <xref:System.Uri>karşılık gelir.  
  
 Protokollerin denetlenmesi için `x:Uri`xaml tanımının bir parçası değildir.  
  
 XAML dil belirtimi tanımı için bkz [ \[. ms-xaml\] sections 5.2.15 ve 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xbyte"></a>x:Byte  
 CLR yedeklemesi için, `x:Byte` ilkel öğesine <xref:System.Byte>karşılık gelir. ,İmzasızolarakkabul<xref:System.Byte>edilir.  /  `x:Byte`  
  
 XAML dil belirtimi tanımı için bkz [ \[. ms-xaml\] sections 5.2.10 ve 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xarray"></a>x:Array  
 CLR yedeklemesi için, `x:Array` ilkel öğesine <xref:System.Array>karşılık gelir.  
  
 Bir diziyi, biçimlendirme uzantısı söz dizimini kullanarak XAML 2006 ' de tanımlayabilirsiniz; Ancak XAML 2009 sözdizimi, biçimlendirme uzantısına erişmeyi gerektirmeyen dil tanımlı bir temel dildir. XAML 2006 desteği hakkında daha fazla bilgi için bkz. [X:Array Işaretleme uzantısı](x-array-markup-extension.md).  
  
 XAML dil belirtimi tanımı için bkz [ \[. MS-\] xaml sections 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>WPF desteği  
 WPF 'de XAML 2009 özelliklerini, ancak yalnızca işaretleme ile derlenen XAML için kullanabilirsiniz. WPF için biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 anahtar sözcüklerini ve özelliklerini desteklememektedir.  
  
 XAML 2009 özelliklerini WPF ile birlikte kullanabileceğiniz bir senaryo, gevşek XAML yazarsa ve bu XAML 'yi ile <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>bir WPF çalışma zamanına ve nesne grafiğine yüklerseniz. <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> WPF<xref:System.Windows.Markup.XamlReader.Load%2A> ve, XAML 2009 dil anahtar sözcüklerini ve özelliklerini geçerli bir nesne grafiği temsiline işleyebilir.
