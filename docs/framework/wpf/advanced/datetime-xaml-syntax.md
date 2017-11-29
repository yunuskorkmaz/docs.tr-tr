---
title: "DateTime XAML Sözdizimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DateTime XAML syntax [WPF], strings for
- DateTime XAML syntax [WPF], where used
- short date format [WPF], DateTime
- DateTime XAML syntax [WPF]
- DateTime XAML text [WPF]
- DateTime XAML syntax [WPF], format strings for
ms.assetid: 5901710a-609b-40c8-9d65-f0016cd9090b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55e261018e6c7b9fea9ad449c5e92a131df40807
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="datetime-xaml-syntax"></a>DateTime XAML Sözdizimi
Gibi bazı denetimleri <xref:System.Windows.Controls.Calendar> ve <xref:System.Windows.Controls.DatePicker>, kullanın özelliklere sahip <xref:System.DateTime> türü. Genellikle bir ilk tarih veya saat bu denetimleri için arka plan kodu çalışma zamanında belirttiğiniz karşın, bir başlangıç tarih veya saat XAML'de belirtebilirsiniz. WPF XAML ayrıştırıcısı ayrıştırılmasını işler <xref:System.DateTime> değerlerini yerleşik XAML metin sözdizimini kullanarak. Bu konuda, özelliklerini açıklanmaktadır <xref:System.DateTime> XAML metin sözdizimi.  
  
  
<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>DateTime XAML sözdiziminin kullanıldığı durumlar  
 XAML'de tarihleri ayarlamak her zaman gerekli değildir ve hatta tercih edilebilir değil. Örneğin, kullanabilirsiniz <xref:System.DateTime.Now%2A?displayProperty=nameWithType> çalıştırma veya bir tarihte başlatmak için özellik yapmak tüm tarih ayarlamaları Takvim kullanıcı girişini temel alarak arka plan kod içinde. Ancak, burada isteyebilirsiniz kod sabit tarihler senaryolar vardır bir <xref:System.Windows.Controls.Calendar> ve <xref:System.Windows.Controls.DatePicker> bir denetim şablonu içinde. <xref:System.DateTime> XAML sözdizimi bu senaryoları için kullanılmalıdır.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>DateTime XAML sözdizimi yerel bir davranıştır  
 <xref:System.DateTime>CLR temel sınıf kitaplıklarında tanımlı bir sınıftır. Taban sınıf kitaplıkları CLR geri kalanı için ne ilişkili nedeniyle, bu uygulamak mümkün değildir <xref:System.ComponentModel.TypeConverterAttribute> sınıfı ve kullanımına XAML dizelerden işlemek ve bunlara dönüştürmek için tür dönüştürücüsünü <xref:System.DateTime> çalışma zamanı nesne modeli. Yoktur hiçbir `DateTimeConverter` sınıfı dönüştürme davranış sağlar; bu konuda açıklanan dönüştürme WPF XAML ayrıştırıcısı yerel bir davranıştır.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>DateTime XAML için biçim dizeleri  
 Biçimi belirtebilirsiniz bir <xref:System.DateTime> ile bir biçim dizesi. Biçim dizeleri bir değer oluşturmak için kullanılan metin sözdizimini resmileştirin. <xref:System.DateTime>tarih bileşenlerini genellikle yalnızca varolan WPF denetimleri için değerleri <xref:System.DateTime> ve zaman bileşenlerini değil.  
  
 Belirtirken bir <xref:System.DateTime> XAML içinde herhangi bir biçim dizeleri birbirinin yerine kullanabilirsiniz.  
  
 Biçimleri ve bu konuda özellikle gösterilmeyen biçim dizeleri de kullanabilirsiniz. Teknik olarak, herhangi bir için XAML <xref:System.DateTime> belirtilen ve daha sonra WPF XAML tarafından ayrıştırılan değeri bir iç çağrısı kullanır <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>, bu nedenle kabul eden herhangi bir dize kullanabilirsiniz <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> XAML girişiniz için. Daha fazla bilgi için bkz. <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  DateTime XAML sözdizimi her zaman kullanır `en-us` olarak <xref:System.Globalization.CultureInfo> kendi yerel dönüşümü için. Bu tarafından etkilenir değil <xref:System.Windows.FrameworkElement.Language%2A> değeri veya `xml:lang` XAML öznitelik düzeyi tür dönüştürme bu bağlam olmaksızın davrandığından XAML'de değeri. Ay ve gün görünme sırasını gibi kültürel farklılıkları nedeniyle burada gösterilen biçim dizeleri kesinti denemeyin. Burada gösterilen biçim dizeleri diğer kültür ayarlarından bağımsız olarak XAML ayrıştırılırken kullanılan tam biçim dizelerdir.  
  
 Aşağıdaki bölümlerde bazı yaygın açıklanmaktadır <xref:System.DateTime> biçim dizeleri.  
  
### <a name="short-date-pattern-d"></a>Kısa tarih deseni ("d")  
 Aşağıdaki kısa tarih biçiminde gösteren bir <xref:System.DateTime> XAML'de:  
  
 `M/d/YYYY`  
  
 Bu, tipik kullanımlar için gerekli tüm bilgileri WPF denetimleri tarafından belirtir ve yanlışlıkla saat dilimi kaymasını ile saat bileşeni tarafından etkilenmez ve bu nedenle diğer biçimlere göre önerilen en basit biçimidir.  
  
 Örneğin, 1 Haziran 2010 tarihini belirtmek için aşağıdaki dizeyi kullanın:  
  
 `3/1/2010`  
  
 Daha fazla bilgi için bkz. <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Sıralanabilir DateTime modeli ("s")  
 Aşağıdaki sıralanabilir gösterir <xref:System.DateTime> XAML desende:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Örneğin, 1 Haziran 2010 tarihini belirtmek için aşağıdaki dizeyi (zamanı bileşenleri tüm 0 olarak girilir) kullanın:  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>RFC1123 modeli ("r")  
 Ayrıca kültür nedenleri için RFC1123 modeli kullanan diğer tarih oluşturucuları dize girişten olabileceğinden RFC1123 modeli yararlıdır. Aşağıdaki RFC1123 gösterir <xref:System.DateTime> XAML desende:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Örneğin, 1 Haziran 2010 tarihini belirtmek için aşağıdaki dizeyi (zamanı bileşenleri tüm 0 olarak girilir) kullanın:  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Diğer biçimler ve modeller  
 Önceden belirtildiği gibi bir <xref:System.DateTime> XAML'de kabul edilebilir olan herhangi bir dize belirtilmesi için giriş olarak <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. Bu, diğer şekillendirilmiş biçimleri içerir (örneğin <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>) ve belirli bir HTTP'dir değil biçimleri <xref:System.Globalization.DateTimeFormatInfo> formu. Örneğin, form `YYYY/mm/dd` kabul edilebilir için giriş olarak <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. Bu konu, çalışan ve bunun yerine standart bir yöntem olarak kısa tarih düzeni önerir tüm olası biçimleri açıklamaya denemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
