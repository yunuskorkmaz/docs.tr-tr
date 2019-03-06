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
ms.openlocfilehash: 8180064d1a500ea17568f6790e13398524eb5f36
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365691"
---
# <a name="datetime-xaml-syntax"></a>DateTime XAML Sözdizimi
Gibi bazı denetimleri <xref:System.Windows.Controls.Calendar> ve <xref:System.Windows.Controls.DatePicker>, kullandığınız özelliklere sahip <xref:System.DateTime> türü. Genellikle bir ilk tarih veya saat bu denetimleri için arka plan kod çalışma zamanında belirttiğiniz olsa da, XAML içinde bir başlangıç tarihi veya saati belirtebilirsiniz. WPF XAML ayrıştırıcı ayrıştırılmasını işler <xref:System.DateTime> yerleşik bir XAML metni söz dizimini kullanarak değerleri. Bu konunun ayrıntılarını açıklar <xref:System.DateTime> XAML metni söz dizimi.  
  
  
<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>DateTime XAML söz dizimini kullanacak şekilde ne zaman  
 XAML içinde tarihlerinin ayarlanması, her zaman gerekli değildir ve hatta istenmeyebilir. Örneğin, kullanabileceğinizi <xref:System.DateTime.Now%2A?displayProperty=nameWithType> çalıştırma veya bir tarihte başlatmak için özellik yapmak tüm tarih ayarlamaları Takvim kullanıcı girişini temel alarak gerideki kod içinde. Bununla birlikte, burada isteyebilirsiniz kod sabit tarihler senaryo vardır bir <xref:System.Windows.Controls.Calendar> ve <xref:System.Windows.Controls.DatePicker> bir denetim şablonu içinde. <xref:System.DateTime> Bu senaryolar için XAML söz dizimi kullanılmalıdır.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>DateTime XAML söz dizimi yerel bir davranıştır  
 <xref:System.DateTime> CLR temel sınıf kitaplıklarında tanımlanan bir sınıftır. Temel sınıf kitaplıklarının CLR geri kalanı için nasıl ilişkilendirilmesi nedeniyle, bunu uygulamak mümkün değildir <xref:System.ComponentModel.TypeConverterAttribute> sınıfı ve XAML dizeleri işlemek ve dönüştürmek için bir tür dönüştürücüsü kullanımına <xref:System.DateTime> çalışma süresi nesne modeli. Yok hiçbir `DateTimeConverter` sınıf dönüştürme davranışını sağlar; bu konuda açıklanan dönüştürme için WPF XAML ayrıştırıcı yerel bir davranıştır.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>DateTime XAML sözdizimi için biçim dizeleri  
 Biçimini belirtebileceğiniz bir <xref:System.DateTime> bir biçim dizesi ile. Biçim dizeleri bir değer oluşturmak için kullanılan metin sözdizimi resmileştirin. <xref:System.DateTime> varolan WPF genellikle yalnızca kullanım tarihi bileşenlerini denetimleri için değerleri <xref:System.DateTime> ve saat bileşenlerini değil.  
  
 Belirtirken bir <xref:System.DateTime> XAML içinde herhangi bir biçim dizesi birbirinin yerine kullanabilirsiniz.  
  
 Biçimleri ve bu konuda özellikle gösterilmeyen biçim dizeleri de kullanabilirsiniz. Teknik olarak, XAML herhangi <xref:System.DateTime> değeri belirtilen ve sonra da WPF XAML tarafından ayrıştırılan kullanan bir iç çağrı <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>, bu nedenle kabul eden herhangi bir dize kullanabileceğinizi <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> , XAML için giriş. Daha fazla bilgi için bkz. <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  DateTime XAML söz dizimi her zaman kullanan `en-us` olarak <xref:System.Globalization.CultureInfo> kendi yerel dönüşümü için. Bu tarafından etkilenir değil <xref:System.Windows.FrameworkElement.Language%2A> değeri veya `xml:lang` XAML özniteliği düzeyinde tür dönüştürme bu bağlamı karıncaların XAML içinde değer. Kültürel farklılıkları, gün ve ay görünme sırasını gibi nedeniyle burada gösterilen biçim dizeleri enterpolasyon çalışmayın. Burada gösterilen biçim dizeleri, diğer kültür ayarlarına bakılmaksızın XAML ayrıştırma kullanılması tam biçim dizelerdir.  
  
 Aşağıdaki bölümlerde bazı yaygın açıklanmaktadır <xref:System.DateTime> biçim dizeleri.  
  
### <a name="short-date-pattern-d"></a>Kısa tarih deseni ("d")  
 Aşağıdaki kısa tarih biçimini gösterir bir <xref:System.DateTime> XAML içinde:  
  
 `M/d/YYYY`  
  
 Bu tipik kullanımları için gerekli tüm bilgileri WPF denetimleri tarafından belirtir ve yanlışlıkla saat dilimi farkları saat bileşeni ile tarafından etkilenmez ve diğer biçimlere göre bu nedenle önerilir en basit biçimidir.  
  
 Örneğin, 1 Haziran 2010 tarihini belirtmek için şu dizeyi kullanın:  
  
 `3/1/2010`  
  
 Daha fazla bilgi için bkz. <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Sıralanabilir tarih/saat deseni ("s")  
 Aşağıdaki sıralanabilir gösterir <xref:System.DateTime> XAML Desen:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Örneğin, 1 Haziran 2010 tarihini belirtmek için (bileşenleri tüm 0 girilen saati) aşağıdaki dizeyi kullanın:  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>Desen: RFC1123 ("r")  
 Desen: RFC1123 yararlıdır, çünkü Desen: RFC1123 kültür nedenleri için de diğer tarih oluşturucuları gelen bir dize girişi olabilir. Aşağıdaki RFC1123 gösterir <xref:System.DateTime> XAML Desen:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Örneğin, 1 Haziran 2010 tarihini belirtmek için (bileşenleri tüm 0 girilen saati) aşağıdaki dizeyi kullanın:  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Diğer biçimler ve modeller  
 Daha önce belirtildiği gibi bir <xref:System.DateTime> XAML içinde kabul edilebilir bir dize belirtilmesi için giriş olarak <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. Bu, resmileştirilmiş diğer biçimlere içerir (örneğin <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>) ve belirli bir HTTP'dir değil biçimleri <xref:System.Globalization.DateTimeFormatInfo> formu. Örneğin, form `YYYY/mm/dd` kabul edilebilir için giriş olarak <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. Bu konu, çalışan ve bunun yerine standart bir yöntem olarak kısa tarih deseni önerir tüm olası biçimleri açıklamak denemez.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
