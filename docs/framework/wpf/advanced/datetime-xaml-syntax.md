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
ms.openlocfilehash: 57b73d3b80f0392b99aacfbfac4d8709f72d52e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186326"
---
# <a name="datetime-xaml-syntax"></a>DateTime XAML Sözdizimi
Bazı denetimler <xref:System.Windows.Controls.Calendar> gibi <xref:System.Windows.Controls.DatePicker>ve, <xref:System.DateTime> türü kullanan özelliklere sahip. Bu denetimlerin başlangıç tarihini veya saatini genellikle çalışma zamanında kod arkasında belirtseniz de, XAML'de bir başlangıç tarihi veya saati belirtebilirsiniz. WPF XAML parser yerleşik xaml metin sözdizimi kullanarak <xref:System.DateTime> değerlerin ayrıştırma işler. Bu konu, XAML <xref:System.DateTime> metin sözdiziminin özelliklerini açıklar.  

<a name="where_datetime_xaml_syntax_is_used"></a>
## <a name="when-to-use-datetime-xaml-syntax"></a>DateTime XAML Sözdizimi Ne Zaman Kullanılır  
 XAML'de tarih ayarlama her zaman gerekli değildir ve hatta istenmeyebilir. Örneğin, bir tarihi <xref:System.DateTime.Now%2A?displayProperty=nameWithType> çalışma zamanında başlatmak için özelliği kullanabilirsiniz veya kullanıcı girişine dayalı olarak kodun arkasında bir takvim için tüm tarih ayarlamalarınızı yapabilirsiniz. Ancak, tarihleri bir <xref:System.Windows.Controls.Calendar> ve denetim <xref:System.Windows.Controls.DatePicker> şablonuna sabit kodlamak isteyebileceğiniz senaryolar vardır. Bu <xref:System.DateTime> senaryolar için XAML sözdizimi kullanılmalıdır.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>DateTime XAML Sözdizimi Yerel Bir Davranıştır  
 <xref:System.DateTime>CLR'nin taban sınıf kitaplıklarında tanımlanan bir sınıftır. Taban sınıf kitaplıklarının CLR'nin geri kalanıyla olan ilişkisi <xref:System.ComponentModel.TypeConverterAttribute> nden dolayı, sınıfa başvurmak ve XAML'den dizeleri <xref:System.DateTime> işlemek ve bunları çalışma süresi nesnesi modeline dönüştürmek için bir tür dönüştürücü kullanmak mümkün değildir. Dönüşüm davranışını sağlayan bir sınıf yoktur; `DateTimeConverter` Bu konuda açıklanan dönüşüm davranışı WPF XAML parser'a özgüdür.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>
## <a name="format-strings-for-datetime-xaml-syntax"></a>DateTime XAML Sözdizimi için Biçim Dizeleri  
 Biçim dizesi ile <xref:System.DateTime> a biçimini belirtebilirsiniz. Biçim dizeleri, değer oluşturmak için kullanılabilecek metin sözdizimini resmileştirir. <xref:System.DateTime>varolan WPF denetimleri için değerler genellikle <xref:System.DateTime> yalnızca tarih bileşenlerini kullanır ve zaman bileşenlerini kullanmaz.  
  
 XAML'de bir sözcük <xref:System.DateTime> belirtirken, biçim dizelerinden herhangi birini birbirinin yerine kullanabilirsiniz.  
  
 Ayrıca, bu konuda özel olarak gösterilmeyen biçimleri ve biçim dizeleri de kullanabilirsiniz. Teknik olarak, Belirtilen ve <xref:System.DateTime> daha sonra WPF XAML parser tarafından ayrıştırılan herhangi <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>bir değer için XAML <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> için bir iç çağrı kullanır , bu nedenle XAML girişi için kabul edilen herhangi bir dize kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> DateTime XAML sözdizimi `en-us` her <xref:System.Globalization.CultureInfo> zaman yerel dönüştürme olarak kullanır. XAML öznitelik `xml:lang` düzeyi türü dönüştürme bu bağlam olmadan hareket ettiği için, bu XAML değeri veya değeri etkilenmez. <xref:System.Windows.FrameworkElement.Language%2A> Gün ve ayın görüntülenme sırası gibi kültürel varyasyonlar nedeniyle burada gösterilen biçim dizelerini enterpolasyona etmeye çalışmayın. Burada gösterilen biçim dizeleri, diğer kültür ayarlarına bakılmaksızın XAML'yi ayrıştirırken kullanılan tam biçim dizeleridir.  
  
 Aşağıdaki bölümlerde bazı ortak <xref:System.DateTime> biçim dizeleri açıklayınız.  
  
### <a name="short-date-pattern-d"></a>Kısa Tarih Deseni ("d")  
 Aşağıdaki XAML bir <xref:System.DateTime> için kısa tarih biçimini gösterir:  
  
 `M/d/YYYY`  
  
 Bu, WPF denetimleri tarafından tipik kullanımlar için gerekli tüm bilgileri belirten en basit formdur ve bir saat bileşenine karşı yanlışlıkla saat dilimi uzaklıklarından etkilenemez ve bu nedenle diğer biçimler üzerinde önerilir.  
  
 Örneğin, 1 Haziran 2010 tarihini belirtmek için aşağıdaki dizeyi kullanın:  
  
 `3/1/2010`  
  
 Daha fazla bilgi için bkz. <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Sıralanabilir DateTime Deseni ("ler")  
 Aşağıdaki XAML'de sıralanabilir <xref:System.DateTime> deseni gösterir:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Örneğin, 1 Haziran 2010 tarihini belirtmek için aşağıdaki dizeyi kullanın (zaman bileşenlerinin tümü 0 olarak girilir):  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>RFC1123 Desen ("r")  
 RFC1123 deseni, kültür değişmez nedenleriyle RFC1123 deseni kullanan diğer tarih jeneratörlerinden gelen bir dize girişi olabileceğinden yararlıdır. Aşağıdaki XAML'de RFC1123 <xref:System.DateTime> deseni gösterilmektedir:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Örneğin, 1 Haziran 2010 tarihini belirtmek için aşağıdaki dizeyi kullanın (zaman bileşenlerinin tümü 0 olarak girilir):  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Diğer Biçimler ve Desenler  
 Daha önce belirtildiği <xref:System.DateTime> gibi, XAML bir giriş olarak kabul edilebilir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>herhangi bir dize olarak belirtilebilir. Bu, diğer biçimlendirilmiş biçimleri <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>(örneğin) ve belirli <xref:System.Globalization.DateTimeFormatInfo> bir form olarak biçimlendirilmemiş biçimleri içerir. Örneğin, form `YYYY/mm/dd` için <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>giriş olarak kabul edilebilir. Bu konu, çalışan tüm olası biçimleri açıklamaya çalışmaz ve bunun yerine kısa tarih deseni standart bir uygulama olarak önerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
