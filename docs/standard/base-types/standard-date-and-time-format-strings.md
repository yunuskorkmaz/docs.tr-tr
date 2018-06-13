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
ms.openlocfilehash: cfa44187d846c72f0dfd4fb131cacbe41648dd32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579814"
---
# <a name="standard-date-and-time-format-strings"></a>Standart Tarih ve Saat Biçim Dizeleri
Standart tarih ve saat biçimi dizesi tek biçim belirleyici bir tarih ve saat değerinin metin gösterimini tanımlamak için kullanır. Beyaz alan dahil, birden fazla karakteri içeren tüm tarih ve saat biçim dizesi, özel bir tarih ve saat biçim dizesi yorumlanır; Daha fazla bilgi için bkz: [özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md). Standart veya özel bir biçim dizesi iki şekilde kullanılabilir:  
  
-   Bir biçimlendirme işleminin sonucunda ortaya çıkan dizeyi tanımlamak için.  
  
-   Dönüştürülebilir bir tarih ve saat değeri metin gösterimini tanımlamak için bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> ayrıştırma işlemi tarafından değeri.  
  
 Standart tarih ve saat biçim dizeleri ikisi ile kullanılabilecek <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.  
  
> [!TIP]
>  İndirebilirsiniz [biçimlendirme yardımcı programı](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), biçimi uygulamanıza olanak sağlayan bir uygulama dizeleri sayısal veya tarih ve saat değerleri ve sonuç dizesini görüntüler.  
  
<a name="table"></a> Aşağıdaki tabloda standart tarih ve saat biçim belirticileri açıklanmaktadır. Aksi belirtilmediği sürece, belirli bir standart tarih ve saat biçimi belirleyici ile mi kullanılacağını bakılmaksızın bir aynı dize gösterimini üreten bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> değeri. Bkz: [notları](#Notes) standart tarih ve saat biçim dizeleri kullanma hakkında ek bilgi bölümü.  
  
|Biçim belirteci|Açıklama|Örnekler|  
|----------------------|-----------------|--------------|  
|"d"|Kısa Tarih Modeli<br /><br /> Daha fazla bilgi:[kısa tarih ("d") biçim belirticisi](#ShortDate).|2009-06-15T13:45:30 -> 6/15/2009 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> 2009/06/15 (ja-JP)|  
|"D"|Uzun tarih deseni.<br /><br /> Daha fazla bilgi:[uzun tarih ("D") biçim belirticisi](#LongDate).|2009-06-15T13:45:30 -> 15 Haziran 2009, Pazartesi (en-US)<br /><br /> 2009-06-15T13:45:30 15 июня 2009 г ->. (ru-RU)<br /><br /> 2009-06-15T13:45:30 Montag, 15 ->. Juni 2009 (de-DE)|  
|"f"|Tam tarih veya saat deseni (süre).<br /><br /> Daha fazla bilgi: [tam kısa tarih ("f") biçim belirticisi](#FullDateShortTime).|2009-06-15T13:45:30 15 Haziran 2009, Pazartesi -> 13: 45'te (en-US)<br /><br /> 2009-06-15T13:45:30 -> bey 15 juni 2009 13:45 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)|  
|"F"|Tam tarih veya saat deseni (uzun süre).<br /><br /> Daha fazla bilgi: [tam tarih uzun süre ("F") biçim belirticisi](#FullDateLongTime).|2009-06-15T13:45:30 15 Haziran 2009, Pazartesi -> 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> bey 15 juni 2009 13:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)|  
|"g"|Genel tarih veya saat deseni (süre).<br /><br /> Daha fazla bilgi: [genel kısa tarih ("g") biçim belirticisi](#GeneralDateShortTime).|2009-06-15T13:45:30 15/6/2009-> 13: 45'te (en-US)<br /><br /> 2009-06-15T13:45:30 -> 06/15/2009 13:45 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45 (zh-CN)|  
|"G"|Genel tarih veya saat deseni (uzun süre).<br /><br /> Daha fazla bilgi: [genel uzun tarih ("G") biçim belirticisi](#GeneralDateLongTime).|2009-06-15T13:45:30 15/6/2009-> 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 06/15/2009-> 13:45:30 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45:30 (zh-CN)|  
|"M", "m"|Ay/gün deseni.<br /><br /> Daha fazla bilgi: [("M", "m") ayın biçimi belirleyici](#MonthDay).|2009-06-15T13:45:30 -> 15 Haziran (en-US)<br /><br /> 2009-06-15T13:45:30 15 -&GT;. juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> 15 Juni (ID)|  
|"O", "o"|Gidiş tarihi/saati desen.<br /><br /> Daha fazla bilgi: [gidiş ("O", "o") biçim belirticisi](#Roundtrip).|<xref:System.DateTime> Değerler:<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Local)--> 2009-06-15T13:45:30.0000000-07:00<br /><br /> 2009-06-15T13:45:30 (değeri DateTimeKind.Utc)--> 2009-06-15T13:45:30.0000000Z<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Unspecified)--> 2009-06-15T13:45:30.0000000<br /><br /> <xref:System.DateTimeOffset> Değerler:<br /><br /> 2009-06-15T13:45:30-07:00--&GT; 2009-06-15T13:45:30.0000000-07:00|  
|"R", "r"|Desen: RFC1123<br /><br /> Daha fazla bilgi: [RFC1123 ("R", "r") biçim belirticisi](#RFC1123).|2009-06-15T13:45:30 -> Mon, 15 Haz 2009 20:45:30 GMT|  
|"s"|Sıralanabilir tarih veya saat deseni.<br /><br /> Daha fazla bilgi: [sıralanabilir ("s") biçim belirticisi](#Sortable).|2009-06-15T13:45:30 (DateTimeKind.Local) -> 2009-06-15T13:45:30<br /><br /> 2009-06-15T13:45:30 (değeri DateTimeKind.Utc) -> 2009-06-15T13:45:30|  
|"t"|Kısa bir süre deseni.<br /><br /> Daha fazla bilgi: [kısa bir süre ("t") biçim belirticisi](#ShortTime).|2009-06-15T13:45:30 -> 13: 45'te (en-US)<br /><br /> 2009-06-15T13:45:30 -> 13:45 (hr-HR)<br /><br /> 2009-06-15T13:45:30 -> 01:45 م (ar-ÖR)|  
|"T"|Uzun süre deseni.<br /><br /> Daha fazla bilgi: [uzun süre ("T") biçim belirticisi](#LongTime).|2009-06-15T13:45:30 -> 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> 13:45:30 (hr-HR)<br /><br /> 2009-06-15T13:45:30 01:45:30 -> م (ar-ÖR)|  
|"u"|Evrensel sıralanabilir tarih/saat deseni.<br /><br /> Daha fazla bilgi: [Evrensel sıralanabilir ("u") biçim belirticisi](#UniversalSortable).|İle bir <xref:System.DateTime> değeri: 2009-06-15T13:45:30 2009-06-15-> 13:45:30Z<br /><br /> İle bir <xref:System.DateTimeOffset> değeri: 2009-06-15T13:45:30 2009-06-15-> 20:45:30Z|  
|"U"|Evrensel tam tarih/saat deseni.<br /><br /> Daha fazla bilgi: [evrensel tam ("U") biçim belirticisi](#UniversalFull).|2009-06-15T13:45:30 -> 15 Haziran 2009, Pazartesi 8:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> bey 15 juni 2009 20:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)|  
|"Y", "y"|Yıl ay deseni.<br /><br /> Daha fazla bilgi: [yıl ay ("Y") biçim belirticisi](#YearMonth).|2009-06-15T13:45:30 -> Haziran 2009 (en-US)<br /><br /> 2009-06-15T13:45:30 -> juni 2009 (da-DK)<br /><br /> 2009-06-15T13:45:30 -> Juni 2009 (ID)|  
|Başka bir tek karakter|Bilinmeyen tanımlayıcı.|Çalışma zamanında oluşturur <xref:System.FormatException>.|  
  
## <a name="how-standard-format-strings-work"></a>Standart Biçim Dizeleri Nasıl Çalışır  
 Bir biçimlendirme işleminde, standart biçim dizesi aslında bir özel biçim dizesi için diğer addır. Bir özel biçim dizesine başvururken diğer ad kullanmanın yararı, diğer ad değişmez iken özel biçim dizesinin kendisinin değişebilmesidir. Bu, tarih ve saat değerleri genellikle kültüre göre değiştiği için önemlidir. Örneğin, "d" standart biçim dizesi bir tarih ve saat değerinin kısa tarih deseni kullanılarak görüntüleneceğini belirtir. Sabit kültür için bu desen "MM/dd/yyyy" şeklindedir. fr-FR kültürü için "dd/MM/yyyy" şeklindedir. ja-JP kültürü için "yyyy/MM/dd" şeklindedir.  
  
 Eğer bir biçimlendirme işleminde standart format dizesi belirli bir kültürün özel biçim dizesiyle eşleniyorsa, uygulamanız özel biçim dizeleri aşağıdaki şekillerden birinde kullanılan belirli kültürü tanımlayabilir:  
  
-   Varsayılan (veya geçerli( kültürü kullanabilirsiniz. Aşağıdaki örnek geçerli kültürün kısa tarih biçimini kullanarak bir tarih görüntüler. Bu durumda geçerli kültür en-US değeridir.  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#1)]
     [!code-vb[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#1)]  
  
-   Geçirebilirsiniz bir <xref:System.Globalization.CultureInfo> biçimlendirmesini olduğu sahip bir yöntemi için kullanılacak kültürü temsil eden nesne bir <xref:System.IFormatProvider> parametresi. Aşağıdaki örnek pt-BR kültürünün kısa tarih biçimini kullanarak bir tarih görüntüler.  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#2)]
     [!code-vb[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#2)]  
  
-   Geçirebilirsiniz bir <xref:System.Globalization.DateTimeFormatInfo> biçimlendirme bilgilerini içeren bir yöntem sağlayan nesne bir <xref:System.IFormatProvider> parametresi. Aşağıdaki örnek kısa tarih biçimi kullanarak bir tarihi görüntüler. bir <xref:System.Globalization.DateTimeFormatInfo> ik HR kültür için nesne.  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#3)]
     [!code-vb[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#3)]  
  
> [!NOTE]
>  Desenler veya tarih ve saat değerleri biçimlendirmede kullanılan dizelerin özelleştirme hakkında daha fazla bilgi için bkz: <xref:System.Globalization.NumberFormatInfo> sınıfı konu.  
  
 Bazı durumlarda, standart biçim dizesi sabit olan daha uzun bir özel biçim dizesi için uygun bir kısaltma görevi görür. Dört standart biçim dizesi bu kategoriye girer: "O" (veya "o"), "R" (veya "r"), "s" ve "u". Bu dizeler sabit kültür tarafından tanımlanan özel biçim dizelerine karşılık gelir. Kültürler arası aynı olan tarih ve saat değerlerinin dize temsillerini oluştururlar. Aşağıdaki tablo bu dört standart tarih ve saat biçim dizesi hakkında bilgi verir.  
  
|Standart biçim dizeleri|DateTimeFormatInfo.InvariantInfo özelliği tarafından tanımı|Özel biçim dizesi|  
|----------------------------|----------------------------------------------------------|--------------------------|  
|"O" veya "o"|Yok.|yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz|  
|"R" ya da "r"|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|ddd, dd MMM yyyy HH':'mm':'ss 'GMT'|  
|"s"|<xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A>|yyyy'-'MM'-'dd'T'HH':'mm':'ss|  
|"u"|<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>|yyyy'-'MM'-'dd HH':'mm':'ss'Z'|  
  
 Standart biçim dizeleri de kullanılabilir işlemleriyle ayrıştırma <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> tam olarak belirli bir desene başarılı olması ayrıştırma işlemi için uygun olması için bir giriş dizesi gerektiren yöntemleri. Birçok standart biçim dizesi birden çok özel biçim dizesine eşlenir, yani bir tarih ve saat değeri çeşitli biçimlerde temsil edilebilir ve ayrıştırma işlemi yine de başarılı olur. Özel biçim dizesi veya çağırarak bir standart biçim dizesine karşılık dizeleri belirleyebilirsiniz <xref:System.Globalization.DateTimeFormatInfo.GetAllDateTimePatterns%28System.Char%29?displayProperty=nameWithType> yöntemi. Aşağıdaki örnek "d" (kısa tarih deseni) standart biçim dizesiyle eşlenen özel biçim dizelerini görüntüler.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/stdandparsing1.cs#17)]
 [!code-vb[Formatting.DateAndTime.Standard#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/stdandparsing1.vb#17)]  
  
 Standart biçim tanımlayıcıları aşağıdaki bölümlerde <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.  
  
<a name="ShortDate"></a>   
## <a name="the-short-date-d-format-specifier"></a>Kısa Tarih ("d") Biçim Tanımlayıcısı  
 Özel tarih ve bir özel kültürün tarafından tanımlanan saat biçim dizesi "d" standart biçim belirticisi temsil eden <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> özelliği. Örneğin, tarafından döndürülen özel biçim dizesi <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A> "Aa/gg/yyyy" sabit kültür özelliğidir.  
  
 Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizesinin biçimlendirmesinde denetleyen özellikler.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Bir tarihin yıl, ay ve gün bileşenlerini ayıran dizeyi tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "d" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#1)]
 [!code-vb[Formatting.DateAndTime.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#1)]  
  
 [Tablo dön](#table)  
  
<a name="LongDate"></a>   
## <a name="the-long-date-d-format-specifier"></a>Uzun Tarih ("D") Biçim Tanımlayıcısı  
 Özel tarih ve geçerli tarafından tanımlanan saat biçim dizesi "D" standart biçim belirticisi temsil eden <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> özelliği. Örneğin, sabit kültür için özel biçim dizesi "dddd, dd MMMM yyyy" değeridir.  
  
 Aşağıdaki tabloda özelliklerini <xref:System.Globalization.DateTimeFormatInfo> döndürülen dizesinin biçimlendirmesinde denetim nesnesi.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş gün adlarını tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "D" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#2)]  
  
 [Tablo dön](#table)  
  
<a name="FullDateShortTime"></a>   
## <a name="the-full-date-short-time-f-format-specifier"></a>Tam Tarih Kısa Saat ("f") Biçim Tanımlayıcısı  
 "f" standart biçim tanımlayıcısı uzun tarih ("D") ve kısa saat ("t") desenlerinin bir boşlukla ayrılarak birleştirilmiş şeklini temsil eder.  
  
 Sonuç dizesini belirli bir biçimlendirme bilgilerini tarafından etkilenen <xref:System.Globalization.DateTimeFormatInfo> nesnesi. Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizesinin biçimlendirmesinde denetleyen özellikler. Tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> ve <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> bazı kültürler özelliklerini hale tüm özelliklerini kullanın.  
  
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
  
 [Tablo dön](#table)  
  
<a name="FullDateLongTime"></a>   
## <a name="the-full-date-long-time-f-format-specifier"></a>Tam Tarih Uzun Saat ("F") Biçim Tanımlayıcısı  
 Özel tarih ve geçerli tarafından tanımlanan saat biçim dizesi "F" standart biçim belirticisi temsil eden <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> özelliği. Örneğin, sabit kültür için özel biçim dizesi "dddd, dd MMMM yyyy HH:mm:ss" değeridir.  
  
 Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizesinin biçimlendirmesinde denetleyen özellikler. Tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> bazı kültürler özelliğinin hale tüm özelliklerini kullanın.  
  
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
  
 [Tablo dön](#table)  
  
<a name="GeneralDateShortTime"></a>   
## <a name="the-general-date-short-time-g-format-specifier"></a>Genel Tarih Kısa Saat ("g") Biçim Tanımlayıcısı  
 "g" standart biçim tanımlayıcısı kısa tarih ("d") ve kısa saat ("t") desenlerinin bir boşlukla ayrılarak birleştirilmiş şeklini temsil eder.  
  
 Sonuç dizesini belirli bir biçimlendirme bilgilerini tarafından etkilenen <xref:System.Globalization.DateTimeFormatInfo> nesnesi. Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizesinin biçimlendirmesinde denetleyen özellikler. Tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> ve <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> bazı kültürler özelliklerini hale tüm özelliklerini kullanın.  
  
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
  
 [Tablo dön](#table)  
  
<a name="GeneralDateLongTime"></a>   
## <a name="the-general-date-long-time-g-format-specifier"></a>Genel Tarih Uzun Saat ("G") Biçim Tanımlayıcısı  
 "G" standart biçim tanımlayıcısı kısa tarih ("d") ve uzun saat ("T") desenlerinin bir boşlukla ayrılarak birleştirilmiş şeklini temsil eder.  
  
 Sonuç dizesini belirli bir biçimlendirme bilgilerini tarafından etkilenen <xref:System.Globalization.DateTimeFormatInfo> nesnesi. Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizesinin biçimlendirmesinde denetleyen özellikler. Tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> ve <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> bazı kültürler özelliklerini hale tüm özelliklerini kullanın.  
  
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
  
 [Tablo dön](#table)  
  
<a name="MonthDay"></a>   
## <a name="the-month-m-m-format-specifier"></a>Ay ("M", "m") Biçim Tanımlayıcısı  
 Özel tarih ve geçerli tarafından tanımlanan saat biçim dizesi "M" veya "m" standart biçim belirticisi temsil eden <xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A?displayProperty=nameWithType> özelliği. Örneğin, sabit kültür için özel biçim dizesi "MMMM dd" değeridir.  
  
 Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizesinin biçimlendirmesinde denetleyen özellikler.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "m" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#7)]  
  
 [Tablo dön](#table)  
  
<a name="Roundtrip"></a>   
## <a name="the-round-trip-o-o-format-specifier"></a>Gidiş Dönüş ("O", "o") Biçim Tanımlayıcısı  
 Özel tarih ve saat dilimi bilgilerini korur ve ISO 8601 ile uyumlu bir sonuç dizesini yayar bir desen saat biçim dizesi "O" veya "o" standart biçim belirticisi temsil eder. İçin <xref:System.DateTime> değerleri, bu biçim belirticisi tarih ve saat değerleri ile birlikte korumak için tasarlanmıştır <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik metin. Biçimlendirilmiş dize geri kullanarak ayrıştırılabilir <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> veya <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> yöntemi varsa `styles` parametrenin ayarlanmış <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>.  
  
 'O"veya"o"standart biçim belirticisi karşılık gelen" yyyy '-' MM'-'dd'T' HH': 'mm':'ss '.' fffffffK"özel biçim dizesi <xref:System.DateTime> değerleri ve" yyyy '-' MM'-'dd'T' HH': 'mm':'ss '.' fffffffzzz"özel biçim dizesi <xref:System.DateTimeOffset> değerleri. Bu dizede; kısa çizgiler, iki nokta üst üste ve "T" harfi gibi tek karakterleri sınırlayan tek soru işareti çiftleri, tek karakterin değiştirilemeyen bir değişmez değer olduğunu belirtir. Kesme işaretleri çıktı dizesinde görünmez.  
  
 'O"veya"o"standart biçim belirticisi (ve" yyyy '-' MM'-'dd'T' HH': 'mm':'ss '.' fffffffK"özel biçim dizesi), ISO 8601 temsil eden saat dilimi bilgilerini korumak için üç yol avantajlarından yararlanır <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTime> değerler:  
  
-   Saat dilimi bileşenini <xref:System.DateTimeKind.Local?displayProperty=nameWithType> tarih ve saat değerleri olan UTC uzaklık (örneğin, +01: 00,-07: 00). Tüm <xref:System.DateTimeOffset> değerleri de bu biçimde temsil.  
  
-   Saat dilimi bileşenini <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> tarih ve saat değerleri UTC temsil etmek için "(uzaklığı sıfır hangi anlamına gelir) Z" kullanır.  
  
-   <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> Tarih ve saat değerleri, saat dilimi bilgisi yok vardır.  
  
 Çünkü O "veya"o"standart biçim belirticisi uyan bir uluslararası standardı, biçimlendirme veya belirleyici her zaman kullanır işlemi ayrıştırma sabit kültür ve Gregoryen takvim kullanır.  
  
 Geçirilen dizeleri `Parse`, `TryParse`, `ParseExact`, ve `TryParseExact` yöntemlerinin <xref:System.DateTime> ve <xref:System.DateTimeOffset> şu biçimlerden birinde olmaları durumunda "O" veya "o" biçim belirteci kullanarak ayrıştırılır. Durumunda <xref:System.DateTime> nesneleri çağırmanız ayrıştırma aşırı de içermelidir bir `styles` parametre değeriyle <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>. "O" karşılık gelen özel biçim dizesi ile ayrıştırma bir yöntem çağrısı veya "o" belirticisi biçim, "O" veya "o" olarak aynı sonucu vermeyecektir unutmayın. Özel bir biçim dizesi kullanan yöntemleri ayrıştırma bir saat dilimi bileşeni eksik veya UTC belirtmek için "Z" kullanan tarih ve saat değerleri dize gösterimini ayrıştırılamıyor olmasıdır.  
  
 Aşağıdaki örnek, bir dizi görüntülemek için "o" biçim belirticisi kullanır <xref:System.DateTime> değerleri ve bir <xref:System.DateTimeOffset> ABD sisteminde değeri Pasifik Saat dilimi.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/o1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Standard#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/o1.vb#8)]  
  
 Aşağıdaki örnek biçimlendirilmiş bir dize oluşturmak için "o" biçim belirteci kullanır ve ardından bir tarih ve saat çağırarak özgün tarih ve saat değerini yükler `Parse` yöntemi.  
  
 [!code-csharp[Formatting.DateandTime.Standard#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Roundtrip1.cs#16)]
 [!code-vb[Formatting.DateandTime.Standard#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/RoundTrip1.vb#16)]  
  
 [Tablo dön](#table)  
  
<a name="RFC1123"></a>   
## <a name="the-rfc1123-r-r-format-specifier"></a>RFC1123 ("R", "r") Biçim Tanımlayıcısı  
 Özel tarih ve tarafından tanımlanan saat biçim dizesi "R" veya "r" standart biçim belirticisi temsil eden <xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A?displayProperty=nameWithType> özelliği. Desen tanımlı bir standardı yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "ddd, dd MMM yyyy HH':'mm':'ss 'GMT'" değeridir. Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.  
  
 Sonuç dizesini aşağıdaki özellikleri tarafından etkilenen <xref:System.Globalization.DateTimeFormatInfo> tarafından döndürülen nesne <xref:System.Globalization.DateTimeFormatInfo.InvariantInfo%2A?displayProperty=nameWithType> sabit kültür temsil eden özellik.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|Sonuç dizesinin biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>|Sonuç dizesinde görünebilen kısaltılmış gün adlarını tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A>|Sonuç dizesinde görünebilen kısaltılmış ay adlarını tanımlar.|  
  
 RFC 1123 standart saat olarak Eşgüdümlü Evrensel Saat (UTC) ifade eder ancak biçimlendirme işlemi değerini değiştirmez <xref:System.DateTime> biçimlendirilen nesnesi. Bu nedenle, dönüştürmelidir <xref:System.DateTime> çağırarak UTC değerine <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> biçimlendirme işlemi gerçekleştirmeden önce yöntemi. Buna karşılık, <xref:System.DateTimeOffset> değerleri bu dönüştürme otomatik olarak gerçekleştirmek; çağırmak için gerek yoktur <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> biçimlendirme işleminden önce yöntemi.  
  
 Aşağıdaki örnek, görüntülemek için "r" biçim belirticisi kullanır. bir <xref:System.DateTime> ve <xref:System.DateTimeOffset> ABD sisteminde değeri Pasifik Saat dilimi.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#9)]
 [!code-vb[Formatting.DateAndTime.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#9)]  
  
 [Tablo dön](#table)  
  
<a name="Sortable"></a>   
## <a name="the-sortable-s-format-specifier"></a>Sıralanabilir ("s") Biçim Tanımlayıcısı  
 Özel tarih ve tarafından tanımlanan saat biçim dizesi "s" standart biçim belirticisi temsil eden <xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A?displayProperty=nameWithType> özelliği. Desen tanımlı bir standardı (ISO 8601) yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "yyyy'-'MM'-'dd'T'HH':'mm':'ss" değeridir.  
  
 Tarih ve saat değerlerine göre azalan veya artan düzende tutarlı bir şekilde sıralamak sonuç dizeleri üretmek için "s" biçim belirticisi amacı budur. "S" standart biçim belirleyici bir tarih ve saat değeri tutarlı biçimde temsil eder, ancak sonuç olarak, biçimlendirme işlemi yansıtacak şekilde biçimlendirilmiş tarih ve saat nesnenin değeri değiştirmez kendi <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği veya kendi <xref:System.DateTimeOffset.Offset%2A?displayProperty=nameWithType> değeri. Örneğin, sonuç dizeleri üretilen biçimlendirme tarih ve saat değerleri 2014 tarafından-11-15T18:32:17 + 00:00 ve 2014-11-15T18:32:17 + 08:00 aynıdır.  
  
 Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.  
  
 Aşağıdaki örnek, görüntülemek için "s" biçim belirticisi kullanır. bir <xref:System.DateTime> ve <xref:System.DateTimeOffset> ABD sisteminde değeri Pasifik Saat dilimi.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#10)]
 [!code-vb[Formatting.DateAndTime.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#10)]  
  
 [Tablo dön](#table)  
  
<a name="ShortTime"></a>   
## <a name="the-short-time-t-format-specifier"></a>Kısa Saat ("t") Biçim Tanımlayıcısı  
 Özel tarih ve geçerli tarafından tanımlanan saat biçim dizesi "t" standart biçim belirticisi temsil eden <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> özelliği. Örneğin, sabit kültür için özel biçim dizesi "HH:mm" değeridir.  
  
 Sonuç dizesini belirli bir biçimlendirme bilgilerini tarafından etkilenen <xref:System.Globalization.DateTimeFormatInfo> nesnesi. Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizesinin biçimlendirmesinde denetleyen özellikler. Tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> bazı kültürler özelliğinin hale tüm özelliklerini kullanın.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Sonuç dizesinin saat bileşeninin biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "t" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#11)]
 [!code-vb[Formatting.DateAndTime.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#11)]  
  
 [Tablo dön](#table)  
  
<a name="LongTime"></a>   
## <a name="the-long-time-t-format-specifier"></a>Uzun Saat ("T") Biçim Tanımlayıcısı  
 Özel tarih ve bir özel kültürün tarafından tanımlanan saat biçim dizesi "T" standart biçim belirticisi temsil eden <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> özelliği. Örneğin, sabit kültür için özel biçim dizesi "HH:mm:ss" değeridir.  
  
 Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizesinin biçimlendirmesinde denetleyen özellikler. Tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> bazı kültürler özelliğinin hale tüm özelliklerini kullanın.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Sonuç dizesinin saat bileşeninin biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "T" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#12)]
 [!code-vb[Formatting.DateAndTime.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#12)]  
  
 [Tablo dön](#table)  
  
<a name="UniversalSortable"></a>   
## <a name="the-universal-sortable-u-format-specifier"></a>Evrensel Sıralanabilir ("u") Biçim Tanımlayıcısı  
 Özel tarih ve tarafından tanımlanan saat biçim dizesi "u" standart biçim belirticisi temsil eden <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A?displayProperty=nameWithType> özelliği. Desen tanımlı bir standardı yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "yyyy'-'MM'-'dd HH':'mm':'ss'Z'" değeridir. Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.  
  
 Sonuç dizesini bir saat olarak Eşgüdümlü Evrensel Saat (UTC), özgün bir dönüştürme yok express ancak <xref:System.DateTime> değeri biçimlendirme işlemi sırasında gerçekleştirilir. Bu nedenle, dönüştürmelidir bir <xref:System.DateTime> çağırarak UTC değerine <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> biçimlendirmeyi önce yöntemi.  Buna karşılık, <xref:System.DateTimeOffset> değerleri bu dönüştürme otomatik olarak gerçekleştirmek; çağırmak için gerek yoktur <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> biçimlendirme işleminden önce yöntemi.  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "u" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Standard#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#13)]  
  
 [Tablo dön](#table)  
  
<a name="UniversalFull"></a>   
## <a name="the-universal-full-u-format-specifier"></a>Evrensel Tam ("U") Biçim Tanımlayıcısı  
 Özel tarih ve bir belirtilen kültürün tarafından tanımlanan saat biçim dizesi "U" standart biçim belirticisi temsil eden <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> özelliği. Desen "F" deseni ile aynıdır. Ancak, <xref:System.DateTime> biçimlendirildikten önce değer UTC'ye otomatik olarak dönüştürülür.  
  
 Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizesinin biçimlendirmesinde denetleyen özellikler. Tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> bazı kültürler özelliğinin hale tüm özelliklerini kullanın.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş gün adlarını tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|  
  
 "U" biçim belirticisi tarafından desteklenmeyen <xref:System.DateTimeOffset> türü ve atar bir <xref:System.FormatException> biçimlendirmek için kullanılan bir <xref:System.DateTimeOffset> değeri.  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "U" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Standard#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#14)]  
  
 [Tablo dön](#table)  
  
<a name="YearMonth"></a>   
## <a name="the-year-month-y-y-format-specifier"></a>Yıl Ay ("Y", "y") Biçim Tanımlayıcısı  
 Özel tarih ve tarafından tanımlanan saat biçim dizesi "Y" veya "y" standart biçim belirticisi temsil eden <xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A?displayProperty=nameWithType> belirtilen kültür özelliği. Örneğin, sabit kültür için özel biçim dizesi "yyyy MMMM" değeridir.  
  
 Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürülen dizesinin biçimlendirmesinde denetleyen özellikler.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|  
  
 Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "y" biçim tanımlayıcısını kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#15)]
 [!code-vb[Formatting.DateAndTime.Standard#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#15)]  
  
 [Tablo dön](#table)  
  
<a name="Notes"></a>   
## <a name="notes"></a>Notlar  
  
### <a name="control-panel-settings"></a>Denetim Masası Ayarları  
 Ayarlarında **bölge ve Dil Seçenekleri** Sonuç dizesini biçimlendirme bir işlem tarafından üretilen Denetim Masası etkisi öğesinde. Bu ayarları başlatmak için kullanılan <xref:System.Globalization.DateTimeFormatInfo> biçimlendirme yönetmek için kullanılan değerleri sağlayan geçerli iş parçacığı kültürünü ile ilişkili nesne. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.  
  
 Kullanırsanız, ayrıca, <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> yeni bir örneğini oluşturmak için Oluşturucusu <xref:System.Globalization.CultureInfo> aynı kültür geçerli sistem kültürü tarafından oluşturulan tüm özelleştirmeler olarak temsil eden nesnesi **bölge ve Dil Seçenekleri** Denetim Masası uygulanacak yeni <xref:System.Globalization.CultureInfo> nesnesi. Kullanabileceğiniz <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Oluşturucusu oluşturmak için bir <xref:System.Globalization.CultureInfo> sistemin özelleştirmeleri yansıtmaz nesnesi.  
  
### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo Özellikleri  
 Biçimlendirme geçerli özellikleri tarafından Etkileyenler <xref:System.Globalization.DateTimeFormatInfo> örtük olarak geçerli iş parçacığı kültürünü veya açıkça tarafından sağlanan nesne <xref:System.IFormatProvider> biçimlendirme çağıran yönteminin parametresi. İçin <xref:System.IFormatProvider> parametresi, uygulamanızın belirtmelidir bir <xref:System.Globalization.CultureInfo> bir kültür temsil eder, nesne veya <xref:System.Globalization.DateTimeFormatInfo> belirli kültürün tarih ve saat kuralları biçimlendirme temsil eden nesne. Standart tarih ve saat biçim belirticileri çoğu geçerli özellikleri tarafından tanımlanan desenleri biçimlendirme için diğer adlardır <xref:System.Globalization.DateTimeFormatInfo> nesnesi. Uygulamanızı bazı standart tarih tarafından üretilen sonuç değiştirebilirsiniz ve saat biçim belirticileri değiştirerek ilgili tarih ve saat biçim ilgili desenleri <xref:System.Globalization.DateTimeFormatInfo> özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.DateTime?displayProperty=nameWithType>  
 <xref:System.DateTimeOffset?displayProperty=nameWithType>  
 [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)  
 [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [Örnek: .NET Framework 4 yardımcı biçimlendirme](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
