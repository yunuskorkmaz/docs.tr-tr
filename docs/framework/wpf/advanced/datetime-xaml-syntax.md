---
title: DateTime XAML Sözdizimi
ms.date: 03/30/2017
helpviewer_keywords:
- DateTime XAML syntax [WPF], strings for
- DateTime XAML syntax [WPF], where used
- short date format [WPF], DateTime
- DateTime XAML syntax [WPF]
- DateTime XAML text [WPF]
- DateTime XAML syntax [WPF], format strings for
ms.assetid: 5901710a-609b-40c8-9d65-f0016cd9090b
ms.openlocfilehash: c9fb030e6f819b1ca463199a76acd32cb1865f33
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458944"
---
# <a name="datetime-xaml-syntax"></a>DateTime XAML Sözdizimi
<xref:System.Windows.Controls.Calendar> ve <xref:System.Windows.Controls.DatePicker>gibi bazı denetimlerin <xref:System.DateTime> türünü kullanan özellikleri vardır. Çalışma zamanında arka plan kodunda bu denetimler için bir başlangıç tarihi veya saati belirtseniz de, XAML 'de bir başlangıç tarihi veya saati belirtebilirsiniz. WPF XAML ayrıştırıcısı, yerleşik XAML metin sözdizimi kullanarak <xref:System.DateTime> değerlerinin ayrıştırılmasını yönetir. Bu konu, <xref:System.DateTime> XAML metin sözdiziminin özelliklerini açıklar.  

<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>DateTime XAML sözdizimi ne zaman kullanılır?  
 XAML 'de tarihlerin ayarlanması her zaman gerekli değildir ve istenmeyebilir. Örneğin, çalışma zamanında bir tarihi başlatmak için <xref:System.DateTime.Now%2A?displayProperty=nameWithType> özelliğini kullanabilir veya kullanıcı girdisine göre arka plan kod içindeki bir takvime ait tüm tarih ayarlamalarınızı yapabilirsiniz. Ancak, bir denetim şablonunda <xref:System.Windows.Controls.Calendar> ve <xref:System.Windows.Controls.DatePicker> için tarihleri sabit kodlarda bırakmak isteyebileceğiniz senaryolar vardır. <xref:System.DateTime> XAML söz dizimi Bu senaryolar için kullanılmalıdır.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>DateTime XAML söz dizimi yerel bir davranıştır  
 <xref:System.DateTime>, CLR 'nin temel sınıf kitaplıklarında tanımlanan bir sınıftır. Temel sınıf kitaplıklarının CLR 'nin geri kalanıyla ilişkilendirilmesi nedeniyle, sınıfa <xref:System.ComponentModel.TypeConverterAttribute> uygulamak ve XAML 'den dizeleri işlemek ve çalışma zamanı nesne modelinde <xref:System.DateTime> dönüştürmek için tür dönüştürücüsü kullanmak mümkün değildir. Dönüştürme davranışını sağlayan `DateTimeConverter` sınıfı yok; Bu konuda açıklanan dönüştürme davranışı WPF XAML ayrıştırıcısında yereldir.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>DateTime XAML sözdizimi için biçim dizeleri  
 Biçim dizesiyle bir <xref:System.DateTime> biçimini belirtebilirsiniz. Biçim dizeleri bir değer oluşturmak için kullanılabilen metin sözdizimini şekilleştir. Mevcut WPF denetimleri için <xref:System.DateTime> değerleri genellikle yalnızca <xref:System.DateTime> Tarih bileşenlerini kullanır, saat bileşenlerini değil.  
  
 XAML 'de bir <xref:System.DateTime> belirtirken, biçim dizelerinden herhangi birini birbirinin yerine kullanabilirsiniz.  
  
 Bu konuda özellikle gösterilen biçimleri ve biçim dizelerini de kullanabilirsiniz. Teknik olarak, belirtilen ve daha sonra WPF XAML ayrıştırıcısı tarafından ayrıştırılmış bir <xref:System.DateTime> değeri için XAML, <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>için bir iç çağrı kullanır, bu nedenle XAML girişinde <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> tarafından kabul edilen herhangi bir dizeyi kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> DateTime XAML sözdizimi her zaman `en-us` yerel dönüştürmesi için <xref:System.Globalization.CultureInfo> olarak kullanır. XAML öznitelik düzeyi tür dönüştürmesi bu bağlam olmadan davrandığı için XAML içindeki <xref:System.Windows.FrameworkElement.Language%2A> değer veya `xml:lang` değeri etkilenmez. Burada gösterilen biçim dizelerini, gün ve ayın sırası gibi kültürel değişimler nedeniyle, burada gösterilen biçim dizelerini enterpolalemeye çalışmayın. Burada gösterilen biçim dizeleri, diğer kültür ayarlarından bağımsız olarak XAML ayrıştırılırken kullanılan tam biçim dizeleridir.  
  
 Aşağıdaki bölümlerde bazı ortak <xref:System.DateTime> biçim dizeleri açıklanır.  
  
### <a name="short-date-pattern-d"></a>Kısa tarih deseninin ("d")  
 Aşağıda, XAML 'deki bir <xref:System.DateTime> için kısa tarih biçimi gösterilmektedir:  
  
 `M/d/YYYY`  
  
 Bu, WPF denetimleri tarafından tipik kullanımlar için gerekli tüm bilgileri belirten en basit biçimdir ve yanlışlıkla saat dilimi uzaklıkları bir zaman bileşeni ile etkilenmez ve bu nedenle diğer biçimler üzerinde önerilir.  
  
 Örneğin, 1 Haziran 2010 tarihini belirtmek için şu dizeyi kullanın:  
  
 `3/1/2010`  
  
 Daha fazla bilgi için bkz. <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Sıralanabilir DateTime kriteri ("s")  
 XAML 'de sıralanabilir <xref:System.DateTime> desenler aşağıda gösterilmiştir:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Örneğin, 1 Haziran 2010 tarihini belirtmek için aşağıdaki dizeyi kullanın (zaman bileşenleri 0 olarak girilir):  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>RFC1123 kalıbı ("r")  
 RFC1123 deseninin kullanılması faydalı olur çünkü kültür sabiti nedenleriyle RFC1123 modelini de kullanan diğer tarih oluşturucularından bir dize girişi olabilir. Aşağıda, XAML 'de RFC1123 <xref:System.DateTime> deseninin gösterildiği görülmektedir:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Örneğin, 1 Haziran 2010 tarihini belirtmek için aşağıdaki dizeyi kullanın (zaman bileşenleri 0 olarak girilir):  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Diğer biçimler ve desenler  
 Daha önce belirtildiği gibi, XAML içindeki bir <xref:System.DateTime>, <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>girdisi olarak kabul edilebilir herhangi bir dize olarak belirtilebilir. Bu, diğer şekillendirilmiş biçimleri (örneğin <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>) ve belirli bir <xref:System.Globalization.DateTimeFormatInfo> formu olarak şekillendirilmeyen biçimleri içerir. Örneğin, `YYYY/mm/dd` form <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>giriş olarak kabul edilebilir. Bu konu, çalışan tüm olası biçimleri açıklamaya çalışmaz ve bunun yerine kısa tarih deseninin standart bir uygulama olarak kullanılmasını önerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
