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
ms.openlocfilehash: 36066d6b2405051a3d35befffe53af8895e26220
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964829"
---
# <a name="datetime-xaml-syntax"></a>DateTime XAML Sözdizimi
<xref:System.Windows.Controls.Calendar> <xref:System.DateTime> Ve gibibazıdenetimlerin,türükullananözelliklerivardır<xref:System.Windows.Controls.DatePicker>. Çalışma zamanında arka plan kodunda bu denetimler için bir başlangıç tarihi veya saati belirtseniz de, XAML 'de bir başlangıç tarihi veya saati belirtebilirsiniz. WPF XAML ayrıştırıcısı, yerleşik xaml metin <xref:System.DateTime> sözdizimi kullanarak değerlerin ayrıştırılmasını işler. Bu konuda <xref:System.DateTime> xaml metin sözdiziminin özellikleri açıklanmaktadır.  

<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>DateTime XAML sözdizimi ne zaman kullanılır?  
 XAML 'de tarihlerin ayarlanması her zaman gerekli değildir ve istenmeyebilir. Örneğin, çalışma zamanında bir tarih başlatmak <xref:System.DateTime.Now%2A?displayProperty=nameWithType> için özelliğini kullanabilir veya kullanıcı girdisine göre arka plan kod içindeki bir takvime ait tüm tarih ayarlamalarınızı yapabilirsiniz. Ancak, bir denetim şablonunda tarihleri bir <xref:System.Windows.Controls.Calendar> ve <xref:System.Windows.Controls.DatePicker> içinde sabit kodlarda bırakmak isteyebileceğiniz senaryolar vardır. <xref:System.DateTime> Xaml söz dizimi Bu senaryolar için kullanılmalıdır.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>DateTime XAML söz dizimi yerel bir davranıştır  
 <xref:System.DateTime>, CLR 'nin temel sınıf kitaplıklarında tanımlanan bir sınıftır. Temel sınıf kitaplıklarının clr 'nin geri kalanıyla ilişkilendirilmesi nedeniyle, sınıfa uygulanamaz <xref:System.ComponentModel.TypeConverterAttribute> ve xaml 'den dizeleri işlemek ve çalışma zamanı nesne modelinde dönüştürmek <xref:System.DateTime> üzere bir tür dönüştürücüsü kullanmak mümkün değildir. Dönüştürme davranışını sağlayan bir sınıfyoktur;bukonudaaçıklanandönüştürmedavranışıWPFXAMLayrıştırıcısındayereldir.`DateTimeConverter`  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>DateTime XAML sözdizimi için biçim dizeleri  
 Biçim dizesiyle bir <xref:System.DateTime> biçimini belirtebilirsiniz. Biçim dizeleri bir değer oluşturmak için kullanılabilen metin sözdizimini şekilleştir. <xref:System.DateTime>Mevcut WPF denetimlerinin değerleri genellikle, saat bileşenlerinden değil yalnızca öğesinin <xref:System.DateTime> Tarih bileşenlerini kullanır.  
  
 XAML içinde bir <xref:System.DateTime> belirtildiğinde, biçim dizelerinden herhangi birini birbirinin yerine kullanabilirsiniz.  
  
 Bu konuda özellikle gösterilen biçimleri ve biçim dizelerini de kullanabilirsiniz. Teknik olarak, belirtilen ve daha <xref:System.DateTime> sonra WPF XAML ayrıştırıcısı tarafından ayrıştırılmış bir değer için XAML, için <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>bir iç çağrı kullanır, bu nedenle XAML girişinde tarafından <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> kabul edilen herhangi bir dizeyi kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> DateTime xaml sözdizimi her zaman kendi `en-us` yerel dönüştürmesi <xref:System.Globalization.CultureInfo> için olarak kullanır. Xaml öznitelik düzeyi tür dönüştürmesi bu bağlam `xml:lang` olmadan davrandığı için XAML içindeki değerveyadeğerbundanetkilenmez.<xref:System.Windows.FrameworkElement.Language%2A> Burada gösterilen biçim dizelerini, gün ve ayın sırası gibi kültürel değişimler nedeniyle, burada gösterilen biçim dizelerini enterpolalemeye çalışmayın. Burada gösterilen biçim dizeleri, diğer kültür ayarlarından bağımsız olarak XAML ayrıştırılırken kullanılan tam biçim dizeleridir.  
  
 Aşağıdaki bölümlerde bazı ortak <xref:System.DateTime> biçim dizeleri açıklanır.  
  
### <a name="short-date-pattern-d"></a>Kısa tarih deseninin ("d")  
 Aşağıda bir <xref:System.DateTime> xaml içindeki için kısa tarih biçimi gösterilmektedir:  
  
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
 Daha önce belirtildiği gibi, <xref:System.DateTime> xaml içindeki bir, için <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>girdi olarak kabul edilebilir herhangi bir dize olarak belirtilebilir. Bu, diğer biçim biçimlerini (örneğin <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>,) ve belirli <xref:System.Globalization.DateTimeFormatInfo> bir form olarak biçimsiz olmayan biçimleri içerir. Örneğin, formu `YYYY/mm/dd` için <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>giriş olarak kabul edilebilir. Bu konu, çalışan tüm olası biçimleri açıklamaya çalışmaz ve bunun yerine kısa tarih deseninin standart bir uygulama olarak kullanılmasını önerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
