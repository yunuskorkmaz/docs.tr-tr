---
title: Standart Tarih ve Saat Biçim Dizeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- custom DateTime format string
- format specifiers, custom date and time
- format strings
- custom date and time format strings
- formatting [.NET Framework], time
- date and time strings
ms.assetid: bb79761a-ca08-44ee-b142-b06b3e2fc22b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4c6d10fad075a70d80bf6e5aa32edf0f89c42dc
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151297"
---
# <a name="standard-date-and-time-format-strings"></a>Standart Tarih ve Saat Biçim Dizeleri
Standart tarih ve saat biçimi dizesi tek biçim belirleyici bir tarih ve saat değerinin metin gösterimini tanımlamak için kullanır. Beyaz boşluk da dahil olmak üzere birden fazla karakter içeren bir tarih ve saat biçim dizesi, özel bir tarih ve saat biçimi dizesi yorumlanır; Daha fazla bilgi için [özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md). Standart veya özel bir biçim dizesi iki şekilde kullanılabilir:  
  
-   Bir biçimlendirme işleminin sonucunda ortaya çıkan dizeyi tanımlamak için.  
  
-   Dönüştürülebilir bir tarih ve saat değeri metin temsilini tanımlamak için bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> ayrıştırma işlemiyle değeri.  

> [!TIP]
>  İndirebileceğiniz [biçimlendirme yardımcı programı](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), biçim sağlayan bir uygulama dizeleri sayısal veya tarih ve saat değerleri ve sonuç dizeyi görüntülemenizi.  

Standart tarih ve saat biçim dizeleri ile her ikisini de kullanılabilir <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.  
  
[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)] 

<a name="table"></a> Aşağıdaki tabloda standart tarih ve saat biçim tanımlayıcılarının açıklanmaktadır. Aksi belirtilmediği sürece, belirli bir standart tarih ve saat biçimi belirticisi ile mi kullanılacağını bakılmaksızın aynı dize temsilini oluşturur bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> değeri. Bkz: [notları](#Notes) standart tarih ve saat biçim dizeleri kullanma hakkında ek bilgi bölümü.  
  
|Biçim belirteci|Açıklama|Örnekler|  
|----------------------|-----------------|--------------|  
|"d"|Kısa Tarih Modeli<br /><br /> Daha fazla bilgi:[kısa tarih ("d") Biçim belirleyicisi](#ShortDate).|2009-06-15T13:45:30 -> 6/15/2009 (en-US)<br /><br /> 2009-06-15T13:45:30 15/06/2009 (fr-FR) -><br /><br /> 2009-06-15T13:45:30 2009/06/15 (ja-JP) ->|  
|"D"|Uzun tarih deseni.<br /><br /> Daha fazla bilgi:[uzun tarih ("D") Biçim belirleyicisi](#LongDate).|2009-06-15T13:45:30 15 Haziran 2009, Pazartesi (en-US) -><br /><br /> 2009-06-15T13:45:30 15 июня 2009 г ->. (ru-RU)<br /><br /> 2009-06-15T13:45:30 Montag, 15 ->. Juni 2009 (de-DE)|  
|"f"|Tam tarih veya saat deseni (süre).<br /><br /> Daha fazla bilgi: [Tam tarih kısa saat ("f") biçim tanımlayıcısı](#FullDateShortTime).|2009-06-15T13:45:30 ->, 15 Haziran 2009, Pazartesi 1:45 PM (en-US)<br /><br /> 2009-06-15T13:45:30 bey 15 juni 2009 -> 13:45 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)|  
|"F"|Tam tarih veya saat deseni (uzun süre).<br /><br /> Daha fazla bilgi: [Tam tarih uzun saat ("F") biçim tanımlayıcısı](#FullDateLongTime).|2009-06-15T13:45:30 ->, 15 Haziran 2009, Pazartesi 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 bey 15 juni 2009 -> 13:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)|  
|"g"|Genel tarih veya saat deseni (süre).<br /><br /> Daha fazla bilgi: [Genel Tarih kısa saat ("g") Biçim belirleyicisi](#GeneralDateShortTime).|2009-06-15T13:45:30 -> 6/15/2009 1:45 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> 06/15/2009 13:45 (es-ES)<br /><br /> 2009-06-15T13:45:30 2009/6/15 13:45 (zh-CN) ->|  
|"G"|Genel tarih veya saat deseni (uzun süre).<br /><br /> Daha fazla bilgi: [Genel Tarih uzun saat ("G") Biçim belirleyicisi](#GeneralDateLongTime).|2009-06-15T13:45:30 -> 6/15/2009 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 06/15/2009-> 13:45:30 (es-ES)<br /><br /> 2009-06-15T13:45:30 2009/6/15 13:45:30 (zh-CN) ->|  
|"M", "m"|Ay/gün deseni.<br /><br /> Daha fazla bilgi: [Ay ("M", "m") biçim tanımlayıcısı](#MonthDay).|2009-06-15T13:45:30 -> 15 Haziran (en-US)<br /><br /> 2009-06-15T13:45:30 15 -&GT;. juni (v-k.)<br /><br /> 2009-06-15T13:45:30 15 Juni (ID) ->|  
|"O", "o"|Gidiş tarihi/saati desen.<br /><br /> Daha fazla bilgi: [Gidiş dönüş ("O", "o") biçim belirteci](#Roundtrip).|<xref:System.DateTime> Değerler:<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Local)--> 2009-06-15T13:45:30.0000000-07:00<br /><br /> 2009-06-15T13:45:30 (değeri DateTimeKind.Utc)--> 2009-06-15T13:45:30.0000000Z<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Unspecified)--> 2009-06-15T13:45:30.0000000<br /><br /> <xref:System.DateTimeOffset> Değerler:<br /><br /> 2009-06-15T13:45:30-07:00, 2009 '--&GT;-06-15T13:45:30.0000000-07:00|  
|"R", "r"|Desen: RFC1123<br /><br /> Daha fazla bilgi: [RFC1123 ("R", "r") Biçim belirleyicisi](#RFC1123).|2009-06-15T13:45:30 -> Pzt, 15 Haz 2009 20:45:30 GMT|  
|"s"|Sıralanabilir tarih veya saat deseni.<br /><br /> Daha fazla bilgi: [Sıralanabilir ("s") biçim belirteci](#Sortable).|2009-06-15T13:45:30 (DateTimeKind.Local) -> 2009-06-15T13:45:30<br /><br /> 2009-06-15T13:45:30 (değeri DateTimeKind.Utc) -> 2009-06-15T13:45:30|  
|"t"|Kısa bir süre deseni.<br /><br /> Daha fazla bilgi: [Kısa saat ("t") Biçim belirleyicisi](#ShortTime).|2009-06-15T13:45:30 1:45 PM (en-US) -><br /><br /> 2009-06-15T13:45:30 13:45 (hr-HR) -><br /><br /> 2009-06-15T13:45:30 -> 01:45 م (ar-ÖR)|  
|"T"|Uzun süre deseni.<br /><br /> Daha fazla bilgi: [Uzun saat ("T") biçim tanımlayıcısı](#LongTime).|2009-06-15T13:45:30 1:45:30 PM (en-US) -><br /><br /> 2009-06-15T13:45:30 13:45:30 (hr-HR) -><br /><br /> 2009-06-15T13:45:30 01:45:30 -> م (ar-ÖR)|  
|"u"|Evrensel sıralanabilir tarih/saat deseni.<br /><br /> Daha fazla bilgi: [Evrensel sıralanabilir ("u") biçim belirteci](#UniversalSortable).|İle bir <xref:System.DateTime> değeri: 2009-06-15T13:45:30 2009-06-15-&GT; 13:45:30Z<br /><br /> İle bir <xref:System.DateTimeOffset> değeri: 2009-06-15T13:45:30 2009-06-15-&GT; 20:45:30Z|  
|"U"|Evrensel tam tarih/saat deseni.<br /><br /> Daha fazla bilgi: [Evrensel tam ("U") Biçim belirleyicisi](#UniversalFull).|2009-06-15T13:45:30 15 Haziran 2009, Pazartesi -> 8:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> bey 15 juni 2009 20:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)|  
|"Y", "y"|Yıl ay deseni.<br /><br /> Daha fazla bilgi: [Yıl ay ("Y") biçim tanımlayıcısı](#YearMonth).|2009-06-15T13:45:30 -> Haziran, 2009 (en-US)<br /><br /> 2009-06-15T13:45:30 juni 2009 (DK da) -><br /><br /> 2009-06-15T13:45:30 Juni 2009 (ID) ->|  
|Başka bir tek karakter|Bilinmeyen tanımlayıcı.|Çalışma zamanı oluşturur <xref:System.FormatException>.|  
  
## <a name="how-standard-format-strings-work"></a>Standart Biçim Dizeleri Nasıl Çalışır  
 Bir biçimlendirme işleminde, standart biçim dizesi aslında bir özel biçim dizesi için diğer addır. Bir özel biçim dizesine başvururken diğer ad kullanmanın yararı, diğer ad değişmez iken özel biçim dizesinin kendisinin değişebilmesidir. Bu, tarih ve saat değerleri genellikle kültüre göre değiştiği için önemlidir. Örneğin, "d" standart biçim dizesi bir tarih ve saat değerinin kısa tarih deseni kullanılarak görüntüleneceğini belirtir. Sabit kültür için bu desen "MM/dd/yyyy" şeklindedir. fr-FR kültürü için "dd/MM/yyyy" şeklindedir. ja-JP kültürü için "yyyy/MM/dd" şeklindedir.  
  
 Eğer bir biçimlendirme işleminde standart format dizesi belirli bir kültürün özel biçim dizesiyle eşleniyorsa, uygulamanız özel biçim dizeleri aşağıdaki şekillerden birinde kullanılan belirli kültürü tanımlayabilir:  
  
-   Varsayılan (veya geçerli( kültürü kullanabilirsiniz. Aşağıdaki örnek geçerli kültürün kısa tarih biçimini kullanarak bir tarih görüntüler. Bu durumda geçerli kültür en-US değeridir.  
  
     [!code-csharp-interactive[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#1)]
     [!code-vb[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#1)]  
  
-   Geçirebilirsiniz bir <xref:System.Globalization.CultureInfo> biçimlendirmesi olan bir yöntem kullanılacak kültürü temsil eden bir nesne bir <xref:System.IFormatProvider> parametresi. Aşağıdaki örnek pt-BR kültürünün kısa tarih biçimini kullanarak bir tarih görüntüler.  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#2)]
     [!code-vb[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#2)]  
  
-   Geçirebilirsiniz bir <xref:System.Globalization.DateTimeFormatInfo> olan bir yönteme biçimlendirme bilgisini sağlayan nesnenin bir <xref:System.IFormatProvider> parametresi. Aşağıdaki örnek, kısa tarih biçimini kullanarak bir tarih görüntüler. bir <xref:System.Globalization.DateTimeFormatInfo> hr-HR kültürü için nesne.  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#3)]
     [!code-vb[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#3)]  
  
> [!NOTE]
>  Desenleri veya dizeleri tarih ve saat değerlerini biçimlendirmede kullanılan özelleştirme hakkında daha fazla bilgi için bkz: <xref:System.Globalization.NumberFormatInfo> sınıf konusuna.  
  
 Bazı durumlarda, standart biçim dizesi sabit olan daha uzun bir özel biçim dizesi için uygun bir kısaltma görevi görür. Dört standart biçim dizesi bu kategoriye ayrılır: "O" ("o"), "R" (veya "r"), "s" ve "u". Bu dizeler sabit kültür tarafından tanımlanan özel biçim dizelerine karşılık gelir. Kültürler arası aynı olan tarih ve saat değerlerinin dize temsillerini oluştururlar. Aşağıdaki tablo bu dört standart tarih ve saat biçim dizesi hakkında bilgi verir.  
  
|Standart biçim dizeleri|DateTimeFormatInfo.InvariantInfo özelliği tarafından tanımı|Özel biçim dizesi|  
|----------------------------|----------------------------------------------------------|--------------------------|  
|"O" veya "o"|Hiçbiri|yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz|  
|"R" ya da "r"|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|ddd, dd MMM yyyy HH':'mm':'ss 'GMT'|  
|"s"|<xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A>|yyyy'-'MM'-'dd'T'HH':'mm':'ss|  
|"u"|<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>|yyyy'-'MM'-'dd HH':'mm':'ss'Z'|  
  
 Standart biçim dizeleri de kullanılabilir ayrıştırma işlemlerinde <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> ayrıştırma işleminin başarılı olması belirli bir desene tam olarak uymak için bir Giriş dizesinin gerektiren yöntemleri. Birçok standart biçim dizesi birden çok özel biçim dizesine eşlenir, yani bir tarih ve saat değeri çeşitli biçimlerde temsil edilebilir ve ayrıştırma işlemi yine de başarılı olur. Özel biçim dizesi ya da çağırarak bir standart biçim dizesine karşılık gelen dizeleri belirleyebilirsiniz <xref:System.Globalization.DateTimeFormatInfo.GetAllDateTimePatterns%28System.Char%29?displayProperty=nameWithType> yöntemi. Aşağıdaki örnek "d" (kısa tarih deseni) standart biçim dizesiyle eşlenen özel biçim dizelerini görüntüler.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/stdandparsing1.cs#17)]
 [!code-vb[Formatting.DateAndTime.Standard#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/stdandparsing1.vb#17)]  
  
 Standart biçim tanımlayıcıları aşağıdaki bölümlerde <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.  
  
<a name="ShortDate"></a>   
## <a name="the-short-date-d-format-specifier"></a>Kısa Tarih ("d") Biçim Tanımlayıcısı  
 "D" standart biçim tanımlayıcısı bir özel tarih ve saat biçim dizesini bir belirli kültürün tarafından tanımlanan temsil <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> özelliği. Örneğin, tarafından döndürülen özel biçim dizesi <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A> "MM/dd/yyyy" sabit kültür özelliğidir.  
  
 Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizenin biçimlendirilmesini denetleyen özellikler.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Bir tarihin yıl, ay ve gün bileşenlerini ayıran dizeyi tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "d" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#1)]
 [!code-vb[Formatting.DateAndTime.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#1)]  
  
 [Tabloya dön](#table)  
  
<a name="LongDate"></a>   
## <a name="the-long-date-d-format-specifier"></a>Uzun Tarih ("D") Biçim Tanımlayıcısı  
 "D" standart biçim tanımlayıcısı bir özel tarih ve saat biçim dizesini geçerli tarafından tanımlanan temsil <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> özelliği. Örneğin, sabit kültür için özel biçim dizesi "dddd, dd MMMM yyyy" değeridir.  
  
 Aşağıdaki tabloda özelliklerini listeler <xref:System.Globalization.DateTimeFormatInfo> döndürülen dizenin biçimlendirilmesini denetleyen nesne.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş gün adlarını tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "D" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#2)]  
  
 [Tabloya dön](#table)  
  
<a name="FullDateShortTime"></a>   
## <a name="the-full-date-short-time-f-format-specifier"></a>Tam Tarih Kısa Saat ("f") Biçim Tanımlayıcısı  
 "f" standart biçim tanımlayıcısı uzun tarih ("D") ve kısa saat ("t") desenlerinin bir boşlukla ayrılarak birleştirilmiş şeklini temsil eder.  
  
 Sonuç dizesi belirli bir biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.DateTimeFormatInfo> nesne. Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizenin biçimlendirilmesini denetleyebilen özellikleri. Tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> ve <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> bazı kültürlerin özelliklerinden tüm özellikleri kullanmayabilir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Sonuç dizesinin tarih bileşeninin biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Sonuç dizesinin saat bileşeninin biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş gün adlarını tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "f" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#3)]
 [!code-vb[Formatting.DateAndTime.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#3)]  
  
 [Tabloya dön](#table)  
  
<a name="FullDateLongTime"></a>   
## <a name="the-full-date-long-time-f-format-specifier"></a>Tam Tarih Uzun Saat ("F") Biçim Tanımlayıcısı  
 "F" standart biçim tanımlayıcısı bir özel tarih ve saat biçim dizesini geçerli tarafından tanımlanan temsil <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> özelliği. Örneğin, sabit kültür için özel biçim dizesi "dddd, dd MMMM yyyy HH:mm:ss" değeridir.  
  
 Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizenin biçimlendirilmesini denetleyebilen özellikleri. Tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> bazı kültürlerin özelliği değil duruma tüm özellikleri kullanmayabilir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş gün adlarını tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "F" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#4)]
 [!code-vb[Formatting.DateAndTime.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#4)]  
  
 [Tabloya dön](#table)  
  
<a name="GeneralDateShortTime"></a>   
## <a name="the-general-date-short-time-g-format-specifier"></a>Genel Tarih Kısa Saat ("g") Biçim Tanımlayıcısı  
 "g" standart biçim tanımlayıcısı kısa tarih ("d") ve kısa saat ("t") desenlerinin bir boşlukla ayrılarak birleştirilmiş şeklini temsil eder.  
  
 Sonuç dizesi belirli bir biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.DateTimeFormatInfo> nesne. Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizenin biçimlendirilmesini denetleyebilen özellikleri. Tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> ve <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> bazı kültürlerin özelliklerinden tüm özellikleri kullanmayabilir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Sonuç dizesinin tarih bileşeninin biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Sonuç dizesinin saat bileşeninin biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Bir tarihin yıl, ay ve gün bileşenlerini ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "g" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#5)]  
  
 [Tabloya dön](#table)  
  
<a name="GeneralDateLongTime"></a>   
## <a name="the-general-date-long-time-g-format-specifier"></a>Genel Tarih Uzun Saat ("G") Biçim Tanımlayıcısı  
 "G" standart biçim tanımlayıcısı kısa tarih ("d") ve uzun saat ("T") desenlerinin bir boşlukla ayrılarak birleştirilmiş şeklini temsil eder.  
  
 Sonuç dizesi belirli bir biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.DateTimeFormatInfo> nesne. Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizenin biçimlendirilmesini denetleyebilen özellikleri. Tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> ve <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> bazı kültürlerin özelliklerinden tüm özellikleri kullanmayabilir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Sonuç dizesinin tarih bileşeninin biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Sonuç dizesinin saat bileşeninin biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Bir tarihin yıl, ay ve gün bileşenlerini ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "G" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#6)]
 [!code-vb[Formatting.DateAndTime.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#6)]  
  
 [Tabloya dön](#table)  
  
<a name="MonthDay"></a>   
## <a name="the-month-m-m-format-specifier"></a>Ay ("M", "m") Biçim Tanımlayıcısı  
 "M" veya "m" standart biçim tanımlayıcısı bir özel tarih ve saat biçim dizesini geçerli tarafından tanımlanan temsil <xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A?displayProperty=nameWithType> özelliği. Örneğin, sabit kültür için özel biçim dizesi "MMMM dd" değeridir.  
  
 Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizenin biçimlendirilmesini denetleyen özellikler.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "m" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#7)]  
  
 [Tabloya dön](#table)  
  
<a name="Roundtrip"></a>   
## <a name="the-round-trip-o-o-format-specifier"></a>Gidiş Dönüş ("O", "o") Biçim Tanımlayıcısı  
 "O" veya "o" standart biçim tanımlayıcısı bir özel tarih ve saat biçim dizesini saat dilimi bilgilerini korur ve ISO 8601 ile uyumlu bir sonuç dizesi yayan bir deseni kullanılarak temsil eder. İçin <xref:System.DateTime> değerleriyle Bu biçim tanımlayıcısı tarih ve saat değerleri ile birlikte korumak için tasarlanan <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> metin özelliği. Geri kullanarak biçimlendirilmiş dize ayrıştırılabilir <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> veya <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> yöntemi varsa `styles` parametrenin ayarlanmış <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>.  
  
 'O"veya"o"standart biçim tanımlayıcısı karşılık gelen" yyyy '-' MM'-'dd'T' HH': 'mm':'ss '.' fffffffK"özel biçim dizesi için <xref:System.DateTime> değerleri ve" yyyy '-' MM'-'dd'T' HH': 'mm':'ss '.' fffffffzzz"özel biçim dizesi için <xref:System.DateTimeOffset> değerleri. Bu dizede; kısa çizgiler, iki nokta üst üste ve "T" harfi gibi tek karakterleri sınırlayan tek soru işareti çiftleri, tek karakterin değiştirilemeyen bir değişmez değer olduğunu belirtir. Kesme işaretleri çıktı dizesinde görünmez.  
  
 'O"veya"o"standart biçim tanımlayıcısı (ve" yyyy '-' MM'-'dd'T' HH': 'mm':'ss '.' fffffffK"özel biçim dizesi), ISO 8601 temsil eden saat dilimi bilgilerini korumak için üç yol avantajlarından yararlanır <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTime> değerleri:  
  
-   Saat dilimi bileşeninin <xref:System.DateTimeKind.Local?displayProperty=nameWithType> bir uzaklık UTC tarih ve saat değerleri olan (örneğin, +01: 00, -07:00). Tüm <xref:System.DateTimeOffset> değerleri de bu biçimde temsil edilir.  
  
-   Saat dilimi bileşeninin <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> tarih ve saat değerleri UTC temsil etmek üzere "Z" (hangi temsil eden sıfır uzaklık) kullanır.  
  
-   <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> Tarih ve saat değerlerini hiçbir saat dilimi bilgisi var.  
  
 "O" veya "o" standart biçim tanımlayıcısı bir Uluslararası standardına uygun olduğundan, biçimlendirme ve ayrıştırma işlemi her zaman belirticisi kullanan sabit kültürü ve Miladi takvimi kullanır.  
  
 Geçirilen dizeler `Parse`, `TryParse`, `ParseExact`, ve `TryParseExact` yöntemlerinin <xref:System.DateTime> ve <xref:System.DateTimeOffset> şu biçimlerden birinde olmaları durumunda, "O" veya "o" biçim belirticisi kullanılarak Ayrıştırılan. Durumunda, <xref:System.DateTime> nesneler, ayrıştırma aşırı yükleme çağırmanızı de içermelidir bir `styles` parametre değerini <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>. Karşılık gelen "O" özel biçim dizesi ile ayrıştırma bir yöntem çağırmanızı veya "o" biçim belirticisi, "O" veya "o" olarak aynı sonucu vermeyecektir unutmayın. Bir saat dilimi bileşeni eksik ya da "Z" UTC belirtin kullanacağınız tarih ve saat değerlerinin dize gösterimini kullanan bir özel biçim dizesinde yöntemleri ayrıştırma ayrıştıramadığından budur.  
  
 Aşağıdaki örnek, bir dizi görüntülemek için "o" biçim tanımlayıcısını kullanır. <xref:System.DateTime> değerleri ve <xref:System.DateTimeOffset> ABD'deki bir sistemde değeri Pasifik Saat dilimi.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/o1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Standard#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/o1.vb#8)]  
  
 Aşağıdaki örnek biçimlendirilmiş bir dize oluşturmak için "o" biçim tanımlayıcısını kullanır ve ardından bir tarih ve saat çağırarak orijinal tarih ve saat değerini geri yükler `Parse` yöntemi.  
  
 [!code-csharp[Formatting.DateandTime.Standard#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Roundtrip1.cs#16)]
 [!code-vb[Formatting.DateandTime.Standard#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/RoundTrip1.vb#16)]  
  
 [Tabloya dön](#table)  
  
<a name="RFC1123"></a>   
## <a name="the-rfc1123-r-r-format-specifier"></a>RFC1123 ("R", "r") Biçim Tanımlayıcısı  
 "R" veya "r" standart biçim tanımlayıcısı bir özel tarih ve saat biçim dizesini tarafından tanımlanan temsil <xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A?displayProperty=nameWithType> özelliği. Desen tanımlı bir standardı yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "ddd, dd MMM yyyy HH':'mm':'ss 'GMT'" değeridir. Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.  
  
 Sonuç dizesi aşağıdaki özelliklerinden etkilenir <xref:System.Globalization.DateTimeFormatInfo> tarafından döndürülen nesne <xref:System.Globalization.DateTimeFormatInfo.InvariantInfo%2A?displayProperty=nameWithType> sabit kültürü temsil eden özellik.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|Sonuç dizesinin biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>|Sonuç dizesinde görünebilen kısaltılmış gün adlarını tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A>|Sonuç dizesinde görünebilen kısaltılmış ay adlarını tanımlar.|  
  
 RFC 1123 standardı saati Eşgüdümlü Evrensel Saat (UTC) olarak ifade etse de, biçimlendirme işlemi değerini değiştirmez <xref:System.DateTime> Biçimlendirilmekte olan nesne. Bu nedenle, dönüştürmelisiniz <xref:System.DateTime> çağırarak değerini UTC'ye <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> yöntemi biçimlendirme işlemini gerçekleştirmeden önce. Buna karşılık, <xref:System.DateTimeOffset> değerleri bu dönüştürmeyi otomatik olarak gerçekleştirir; çağırmaya gerek yoktur <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> yöntemi biçimlendirme işleminden önce.  
  
 Aşağıdaki örnek, görüntülemek için "r" biçim tanımlayıcısını kullanır. bir <xref:System.DateTime> ve <xref:System.DateTimeOffset> ABD'deki bir sistemde değeri Pasifik Saat dilimi.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#9)]
 [!code-vb[Formatting.DateAndTime.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#9)]  
  
 [Tabloya dön](#table)  
  
<a name="Sortable"></a>   
## <a name="the-sortable-s-format-specifier"></a>Sıralanabilir ("s") Biçim Tanımlayıcısı  
 "S" standart biçim tanımlayıcısı bir özel tarih ve saat biçim dizesini tarafından tanımlanan temsil <xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A?displayProperty=nameWithType> özelliği. Desen tanımlı bir standardı (ISO 8601) yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "yyyy'-'MM'-'dd'T'HH':'mm':'ss" değeridir.  
  
 "S" biçim belirticisi amacı, tutarlı bir şekilde tarih ve saat değerlerine göre azalan veya artan düzende sıralamak sonuç dizeleri üretir sağlamaktır. "S" standart biçim tanımlayıcısı tutarlı bir biçimde bir tarih ve saat değerini temsil eder, ancak sonuç olarak, biçimlendirme işlemi yansıtacak şekilde biçimlendirilmiş tarih ve saat nesnenin değerini değiştirmez, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik ya da kendi <xref:System.DateTimeOffset.Offset%2A?displayProperty=nameWithType> değeri. Örneğin, sonuç dizeleri üretilen tarih ve saat değerlerini 2014 biçimlendirme-11-15T18:32:17 + 00:00 ve 2014-11-15T18:32:17 + 08:00 aynıdır.  
  
 Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.  
  
 Aşağıdaki örnek, görüntülemek için "s" biçim tanımlayıcısını kullanır. bir <xref:System.DateTime> ve <xref:System.DateTimeOffset> ABD'deki bir sistemde değeri Pasifik Saat dilimi.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#10)]
 [!code-vb[Formatting.DateAndTime.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#10)]  
  
 [Tabloya dön](#table)  
  
<a name="ShortTime"></a>   
## <a name="the-short-time-t-format-specifier"></a>Kısa Saat ("t") Biçim Tanımlayıcısı  
 "T" standart biçim tanımlayıcısı bir özel tarih ve saat biçim dizesini geçerli tarafından tanımlanan temsil <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> özelliği. Örneğin, sabit kültür için özel biçim dizesi "HH:mm" değeridir.  
  
 Sonuç dizesi belirli bir biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.DateTimeFormatInfo> nesne. Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizenin biçimlendirilmesini denetleyebilen özellikleri. Tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> bazı kültürlerin özelliği değil duruma tüm özellikleri kullanmayabilir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Sonuç dizesinin saat bileşeninin biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "t" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#11)]
 [!code-vb[Formatting.DateAndTime.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#11)]  
  
 [Tabloya dön](#table)  
  
<a name="LongTime"></a>   
## <a name="the-long-time-t-format-specifier"></a>Uzun Saat ("T") Biçim Tanımlayıcısı  
 "T" standart biçim tanımlayıcısı bir özel tarih ve saat biçim dizesini bir belirli kültürün tarafından tanımlanan temsil <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> özelliği. Örneğin, sabit kültür için özel biçim dizesi "HH:mm:ss" değeridir.  
  
 Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizenin biçimlendirilmesini denetleyebilen özellikleri. Tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> bazı kültürlerin özelliği değil duruma tüm özellikleri kullanmayabilir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Sonuç dizesinin saat bileşeninin biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "T" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#12)]
 [!code-vb[Formatting.DateAndTime.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#12)]  
  
 [Tabloya dön](#table)  
  
<a name="UniversalSortable"></a>   
## <a name="the-universal-sortable-u-format-specifier"></a>Evrensel Sıralanabilir ("u") Biçim Tanımlayıcısı  
 "U" standart biçim tanımlayıcısı bir özel tarih ve saat biçim dizesini tarafından tanımlanan temsil <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A?displayProperty=nameWithType> özelliği. Desen tanımlı bir standardı yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "yyyy'-'MM'-'dd HH':'mm':'ss'Z'" değeridir. Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.  
  
 Sonuç dizesini bir saati Eşgüdümlü Evrensel Saat (UTC) olarak, özgün dönüştürme ifade etmesi gerekse de <xref:System.DateTime> değeri biçimlendirme işlemi sırasında gerçekleştirilir. Bu nedenle, dönüştürmelisiniz bir <xref:System.DateTime> çağırarak değerini UTC'ye <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> biçimlendirmeyi önce yöntemi.  Buna karşılık, <xref:System.DateTimeOffset> değerleri bu dönüştürmeyi otomatik olarak gerçekleştirir; çağırmaya gerek yoktur <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> yöntemi biçimlendirme işleminden önce.  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "u" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Standard#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#13)]  
  
 [Tabloya dön](#table)  
  
<a name="UniversalFull"></a>   
## <a name="the-universal-full-u-format-specifier"></a>Evrensel Tam ("U") Biçim Tanımlayıcısı  
 "U" standart biçim tanımlayıcısı bir özel tarih ve saat biçim dizesini bir belirtilen kültürün tarafından tanımlanan temsil <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> özelliği. Desen "F" deseni ile aynıdır. Ancak, <xref:System.DateTime> biçimlendirilmeden önce değerini UTC'ye otomatik olarak dönüştürülür.  
  
 Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizenin biçimlendirilmesini denetleyebilen özellikleri. Tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> bazı kültürlerin özelliği değil duruma tüm özellikleri kullanmayabilir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş gün adlarını tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|  
  
 "U" biçim belirticisi tarafından desteklenmeyen <xref:System.DateTimeOffset> türü ve oluşturur bir <xref:System.FormatException> biçimlendirme için kullanılıyorsa bir <xref:System.DateTimeOffset> değeri.  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "U" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Standard#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#14)]  
  
 [Tabloya dön](#table)  
  
<a name="YearMonth"></a>   
## <a name="the-year-month-y-y-format-specifier"></a>Yıl Ay ("Y", "y") Biçim Tanımlayıcısı  
 "Y" veya "y" standart biçim tanımlayıcısı bir özel tarih ve saat biçim dizesini tarafından tanımlanan temsil <xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A?displayProperty=nameWithType> belirtilen bir kültürün özelliği. Örneğin, sabit kültür için özel biçim dizesi "yyyy MMMM" değeridir.  
  
 Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizenin biçimlendirilmesini denetleyen özellikler.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "y" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#15)]
 [!code-vb[Formatting.DateAndTime.Standard#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#15)]  
  
 [Tabloya dön](#table)  
  
<a name="Notes"></a>   
## <a name="notes"></a>Notlar  
  
### <a name="control-panel-settings"></a>Denetim Masası Ayarları  
 Ayarlarında **bölge ve Dil Seçenekleri** öğesinde bir biçimlendirme işlemiyle oluşturulan Sonuç dizesini Denetim Masası etkiler. Bu ayarları başlatmak için kullanılan <xref:System.Globalization.DateTimeFormatInfo> biçimlendirmeyi yönetmek için değerler sunar geçerli iş parçacığı kültürüyle ilgili nesne. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.  
  
 Ayrıca kullandığınız, <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> yeni bir örneğini oluşturmak için oluşturucu <xref:System.Globalization.CultureInfo> yapılan her özelleştirme mevcut sistem kültürüyle aynı kültürü temsil eden nesne **bölge ve Dil Seçenekleri** Denetim Masası'ndaki öğesi uygulanacak yeni <xref:System.Globalization.CultureInfo> nesne. Kullanabileceğiniz <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> oluşturmak için bir <xref:System.Globalization.CultureInfo> sistem özelleştirmelerini içermeyen bir nesne.  
  
### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo Özellikleri  
 Biçimlendirme geçerli bir özellik tarafından etkilenir <xref:System.Globalization.DateTimeFormatInfo> tarafından açık olarak veya geçerli iş parçacığı kültürü tarafından örtük olarak sağlanan nesne <xref:System.IFormatProvider> biçimlendirmeyi çağıran yöntemin parametre. İçin <xref:System.IFormatProvider> parametresi, uygulamanızın belirtmelidir bir <xref:System.Globalization.CultureInfo> bir kültürü temsil eden bir nesne veya <xref:System.Globalization.DateTimeFormatInfo> belirli bir kültürün tarih ve saat biçimlendirme kurallarını temsil eden nesne. Standart tarih ve saat biçim tanımlayıcılarının çoğu geçerli özellikleri tarafından tanımlanan biçimlendirme desenleri için diğer adlar: <xref:System.Globalization.DateTimeFormatInfo> nesne. Uygulamanız bazı standart tarih sonucu değiştirebilirsiniz ve saat biçim tanımlayıcılarının değiştirerek karşılık gelen tarih ve saat biçim desenleri karşılık gelen <xref:System.Globalization.DateTimeFormatInfo> özelliği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.DateTime?displayProperty=nameWithType>  
- <xref:System.DateTimeOffset?displayProperty=nameWithType>  
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)  
- [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
- [Örnek: .NET Framework 4 biçimlendirme yardımcı](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
