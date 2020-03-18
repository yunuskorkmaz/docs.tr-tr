---
title: Standart tarih ve saat biçimi dizeleri
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
ms.openlocfilehash: 883902142a91e275ab64ad5d12c197c665bd9b36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400339"
---
# <a name="standard-date-and-time-format-strings"></a>Standart tarih ve saat biçimi dizeleri

Standart tarih ve saat biçimi dizesi tek biçim belirleyici bir tarih ve saat değerinin metin gösterimini tanımlamak için kullanır. Beyaz boşluk da dahil olmak üzere birden fazla karakter içeren herhangi bir tarih ve saat biçimi dizesi, özel bir tarih ve saat biçimi dizesi olarak yorumlanır; daha fazla bilgi için [bkz: Özel tarih ve saat biçimi dizeleri.](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) Standart veya özel bir biçim dizesi iki şekilde kullanılabilir:

- Bir biçimlendirme işleminin sonucunda ortaya çıkan dizeyi tanımlamak için.

- Ayrışdırma işlemi yle bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> değere dönüştürülebilen bir tarih ve saat değerinin metin gösterimini tanımlamak için.

> [!TIP]
> **Biçimlendirme Yardımcı Programı'nı**indirebilirsiniz , bir .NET Core Windows Forms uygulamasını, biçim dizelerini sayısal veya tarih ve saat değerlerine uygulamanızı ve sonuç dizesini görüntülemenizi sağlar. Kaynak kodu [C#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) ve [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)için kullanılabilir.

Standart tarih ve saat biçimi dizeleri <xref:System.DateTime> <xref:System.DateTimeOffset> hem de değerlerle kullanılabilir.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)]

<a name="table"></a>Aşağıdaki tabloda standart tarih ve saat biçimi belirteciler açıklanmaktadır. Aksi belirtilmedikçe, belirli bir standart tarih ve saat biçimi belirtimi, bir <xref:System.DateTime> <xref:System.DateTimeOffset> değerle mi yoksa bir değerle mi kullanıldığına bakılmaksızın aynı dize gösterimi üretir. Standart tarih ve saat biçimi dizelerini kullanma hakkında ek bilgi için [Notlar](#Notes) bölümüne bakın.

|Biçim belirteci|Açıklama|Örnekler|
|----------------------|-----------------|--------------|
|"d"|Kısa Tarih Modeli<br /><br /> Daha fazla bilgi:[Kısa Tarih ("d") Biçim Belirtici](#ShortDate).|2009-06-15T13:45:30 -> 15.06.2009 (tr-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> 2009/06/15 (ja-JP)|
|"D"|Uzun tarih deseni.<br /><br /> Daha fazla bilgi:[Uzun Tarih ("D") Biçim Belirtici](#LongDate).|2009-06-15T13:45:30 -> Pazartesi, Haziran 15, 2009 (tr-ABD)<br /><br /> 2009-06-15T13:45:30 -> 15 ияня 2009 г. (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> Montaj, 15. Juni 2009 (de-DE)|
|"f"|Tam tarih veya saat deseni (süre).<br /><br /> Daha fazla bilgi: [Tam Tarih Kısa Saat ("f") Format Specifier](#FullDateShortTime).|2009-06-15T13:45:30 -> Pazartesi, Haziran 15, 2009 1:45 PM (tr-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 13:45 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)|
|"F"|Tam tarih veya saat deseni (uzun süre).<br /><br /> Daha fazla bilgi: [Tam Tarih Uzun Süre ("F") Format Belirtimi](#FullDateLongTime).|2009-06-15T13:45:30 -> 15 Haziran 2009 Pazartesi 13:45:30 (tr-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 13:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)|
|"g"|Genel tarih veya saat deseni (süre).<br /><br /> Daha fazla bilgi: [Genel Tarih Kısa Saat ("g") Biçim Belirtimi](#GeneralDateShortTime).|2009-06-15T13:45:30 -> 15.06.2009 13:45 (tr-US)<br /><br /> 2009-06-15T13:45:30 -> 15.06.2009 13:45 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45 (zh-CN)|
|"G"|Genel tarih veya saat deseni (uzun süre).<br /><br /> Daha fazla bilgi: [Genel Tarih Uzun Süre ("G") Biçim Belirtici](#GeneralDateLongTime).|2009-06-15T13:45:30 -> 15.06.2009 13:45:30 (tr-US)<br /><br /> 2009-06-15T13:45:30 -> 15.06.2009 13:45:30 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45:30 (zh-CN)|
|"M", "m"|Ay/gün deseni.<br /><br /> Daha fazla bilgi: [Ay ("M", "m") Biçim Belirtimi.](#MonthDay)|2009-06-15T13:45:30 -> 15 Haziran (tr-ABD)<br /><br /> 2009-06-15T13:45:30 -> 15. juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> 15 Juni (id-ID)|
|"O", "o"|Gidiş tarihi/saati desen.<br /><br /> Daha fazla bilgi: [Gidiş-Dönüş ("O", "o") Biçim Belirtimi.](#Roundtrip)|<xref:System.DateTime>Değer:<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Local) --> 2009-06-15T13:45:30.000000-07:00<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc) --> 2009-06-15T13:45:30.000000Z<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Belirtilmemiş) --> 2009-06-15T13:45:30.000000<br /><br /> <xref:System.DateTimeOffset>Değer:<br /><br /> 2009-06-15T13:45:30-07:00 --> 2009-06-15T13:45:30.000000-07:00|
|"R", "r"|Desen: RFC1123<br /><br /> Daha fazla bilgi: [RFC1123 ("R", "r") Biçim Belirtimi.](#RFC1123)|2009-06-15T13:45:30 -> Pzt, 15 Jun 2009 20:45:30 GMT|
|"s"|Sıralanabilir tarih veya saat deseni.<br /><br /> Daha fazla bilgi: [Sıralanabilir ("s") Biçim Belirtici](#Sortable).|2009-06-15T13:45:30 (DateTimeKind.Local) -> 2009-06-15T13:45:30<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc) -> 2009-06-15T13:45:30|
|"t"|Kısa bir süre deseni.<br /><br /> Daha fazla bilgi: [Kısa Süre ("t") Biçim Belirtici](#ShortTime).|2009-06-15T13:45:30 -> 13:45 (tr-ABD)<br /><br /> 2009-06-15T13:45:30 -> 13:45 (hr-HR)<br /><br /> 2009-06-15T13:45:30 -> 01:45 م (ar-EG)|
|"T"|Uzun süre deseni.<br /><br /> Daha fazla bilgi: [Uzun Süre ("T") Biçim Belirtici](#LongTime).|2009-06-15T13:45:30 -> 1:45:30 (tr-US)<br /><br /> 2009-06-15T13:45:30 -> 13:45:30 (hr-HR)<br /><br /> 2009-06-15T13:45:30 -> 01:45:30 م (ar-EG)|
|"u"|Evrensel sıralanabilir tarih/saat deseni.<br /><br /> Daha fazla bilgi: [Evrensel Sıralanabilir ("u") Biçim Belirtici](#UniversalSortable).|<xref:System.DateTime> Bir değer le: 2009-06-15T13:45:30 -> 2009-06-15 13:45:30Z<br /><br /> <xref:System.DateTimeOffset> Bir değer ile: 2009-06-15T13:45:30 -> 2009-06-15 20:45:30Z|
|"U"|Evrensel tam tarih/saat deseni.<br /><br /> Daha fazla bilgi: [Evrensel Tam ("U") Biçim Belirtimi.](#UniversalFull)|2009-06-15T13:45:30 -> 15 Haziran 2009 Pazartesi 20:45:30 (tr-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 20:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτρα, 15 Ιουνοου 2009 8:45:30 μμ (el-GR)|
|"Y", "y"|Yıl ay deseni.<br /><br /> Daha fazla bilgi: [Yıl Ay ("Y") Biçim Belirtimi](#YearMonth).|2009-06-15T13:45:30 -> Haziran, 2009 (tr-ABD)<br /><br /> 2009-06-15T13:45:30 -> juni 2009 (da-DK)<br /><br /> 2009-06-15T13:45:30 -> Juni 2009 (id-ID)|
|Başka bir tek karakter|Bilinmeyen tanımlayıcı.|Bir çalışma zamanı <xref:System.FormatException>atar.|

## <a name="how-standard-format-strings-work"></a>Standart Biçim Dizeleri Nasıl Çalışır

Bir biçimlendirme işleminde, standart biçim dizesi aslında bir özel biçim dizesi için diğer addır. Bir özel biçim dizesine başvururken diğer ad kullanmanın yararı, diğer ad değişmez iken özel biçim dizesinin kendisinin değişebilmesidir. Bu, tarih ve saat değerleri genellikle kültüre göre değiştiği için önemlidir. Örneğin, "d" standart biçim dizesi bir tarih ve saat değerinin kısa tarih deseni kullanılarak görüntüleneceğini belirtir. Sabit kültür için bu desen "MM/dd/yyyy" şeklindedir. fr-FR kültürü için "dd/MM/yyyy" şeklindedir. ja-JP kültürü için "yyyy/MM/dd" şeklindedir.

Eğer bir biçimlendirme işleminde standart format dizesi belirli bir kültürün özel biçim dizesiyle eşleniyorsa, uygulamanız özel biçim dizeleri aşağıdaki şekillerden birinde kullanılan belirli kültürü tanımlayabilir:

- Varsayılan (veya geçerli( kültürü kullanabilirsiniz. Aşağıdaki örnek geçerli kültürün kısa tarih biçimini kullanarak bir tarih görüntüler. Bu durumda geçerli kültür en-US değeridir.

  [!code-csharp-interactive[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#1)]
  [!code-vb[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#1)]

- Biçimlendirme si parametresi olan bir yöntemiçin kullanılacak olan kültürü <xref:System.IFormatProvider> temsil eden bir <xref:System.Globalization.CultureInfo> nesneyi geçirebilirsiniz. Aşağıdaki örnek pt-BR kültürünün kısa tarih biçimini kullanarak bir tarih görüntüler.

  [!code-csharp[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#2)]
  [!code-vb[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#2)]

- <xref:System.Globalization.DateTimeFormatInfo> Parametresi olan bir yönteme biçimlendirme bilgileri <xref:System.IFormatProvider> sağlayan bir nesneyi geçirebilirsiniz. Aşağıdaki örnek, Hr-HR kültürü için <xref:System.Globalization.DateTimeFormatInfo> bir nesnenin kısa tarih biçimini kullanarak bir tarih görüntüler.

  [!code-csharp[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#3)]
  [!code-vb[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#3)]

> [!NOTE]
> Tarih ve saat değerlerini biçimlendirmede kullanılan desenleri veya dizeleri <xref:System.Globalization.NumberFormatInfo> özelleştirme hakkında bilgi için sınıf konusuna bakın.

Bazı durumlarda, standart biçim dizesi sabit olan daha uzun bir özel biçim dizesi için uygun bir kısaltma görevi görür. Dört standart biçim dizesi bu kategoriye girer: "O" (veya "o"), "R" (veya "r"), "s" ve "u". Bu dizeler sabit kültür tarafından tanımlanan özel biçim dizelerine karşılık gelir. Kültürler arası aynı olan tarih ve saat değerlerinin dize temsillerini oluştururlar. Aşağıdaki tablo bu dört standart tarih ve saat biçim dizesi hakkında bilgi verir.

|Standart biçim dizeleri|DateTimeFormatInfo.InvariantInfo özelliği tarafından tanımı|Özel biçim dizesi|
|----------------------------|----------------------------------------------------------|--------------------------|
|"O" veya "o"|None|yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz|
|"R" ya da "r"|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|ddd, dd MMM yyyy HH':'mm':'ss 'GMT'|
|"s"|<xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A>|yyyy'-'MM'-'dd'T'HH':'mm':'ss|
|"u"|<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>|yyyy'-'MM'-'dd HH':'mm':'ss'Z'|

Standart biçim dizeleri, ayrışma işleminin <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> başarılı <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> olması için belirli bir desenin tam olarak uyumlu olmasını gerektiren giriş dizesi gerektiren işlemlerle ayrışma işlemlerinde de kullanılabilir. Birçok standart biçim dizesi birden çok özel biçim dizesine eşlenir, yani bir tarih ve saat değeri çeşitli biçimlerde temsil edilebilir ve ayrıştırma işlemi yine de başarılı olur. Yöntemi çağırarak, standart biçim dizesine karşılık gelen özel <xref:System.Globalization.DateTimeFormatInfo.GetAllDateTimePatterns%28System.Char%29?displayProperty=nameWithType> biçim dizesini veya dizeleri belirleyebilirsiniz. Aşağıdaki örnek "d" (kısa tarih deseni) standart biçim dizesiyle eşlenen özel biçim dizelerini görüntüler.

[!code-csharp[Formatting.DateAndTime.Standard#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/stdandparsing1.cs#17)]
[!code-vb[Formatting.DateAndTime.Standard#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/stdandparsing1.vb#17)]

Aşağıdaki bölümlerde standart biçim belirteciler <xref:System.DateTime> <xref:System.DateTimeOffset> ve değerler açıklayınız.

<a name="ShortDate"></a>

## <a name="the-short-date-d-format-specifier"></a>Kısa Tarih ("d") Biçim Tanımlayıcısı

"d" standart biçim belirtimi, belirli bir kültürün <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçimi dizesini temsil eder. Örneğin, değişmez kültürün <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A> özelliği tarafından döndürülen özel biçim dizesi "MM/dd/yyyy"dir.

Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dize biçimlendirmeyi denetleyen nesne özellikleri listelenmektedir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Bir tarihin yıl, ay ve gün bileşenlerini ayıran dizeyi tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "d" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#1)]
[!code-vb[Formatting.DateAndTime.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#1)]

[Tabloya geri dön](#table)

<a name="LongDate"></a>

## <a name="the-long-date-d-format-specifier"></a>Uzun Tarih ("D") Biçim Tanımlayıcısı

"D" standart biçim belirtimi, geçerli <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> özellik tarafından tanımlanan özel bir tarih ve saat biçimi dizesini temsil eder. Örneğin, sabit kültür için özel biçim dizesi "dddd, dd MMMM yyyy" değeridir.

Aşağıdaki tabloda, döndürülen <xref:System.Globalization.DateTimeFormatInfo> dize biçimlendirmeyi denetleyen nesnenin özellikleri listelenmektedir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş gün adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "D" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#2)]
[!code-vb[Formatting.DateAndTime.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#2)]

[Tabloya geri dön](#table)

<a name="FullDateShortTime"></a>

## <a name="the-full-date-short-time-f-format-specifier"></a>Tam Tarih Kısa Saat ("f") Biçim Tanımlayıcısı

"f" standart biçim tanımlayıcısı uzun tarih ("D") ve kısa saat ("t") desenlerinin bir boşlukla ayrılarak birleştirilmiş şeklini temsil eder.

Sonuç dizesi belirli bir <xref:System.Globalization.DateTimeFormatInfo> nesnenin biçimlendirme bilgietkilenir. Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dize biçimlendirmeyi denetleyebilecek nesne özellikleri listelenmektedir. Bazı kültürlerin <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> özellikleri ve <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> özellikleri tarafından döndürülen özel biçim belirtici tüm özellikleri kullanmayabilir.

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

[Tabloya geri dön](#table)

<a name="FullDateLongTime"></a>

## <a name="the-full-date-long-time-f-format-specifier"></a>Tam Tarih Uzun Saat ("F") Biçim Tanımlayıcısı

"F" standart biçim belirtimi, geçerli <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> özellik tarafından tanımlanan özel bir tarih ve saat biçimi dizesini temsil eder. Örneğin, sabit kültür için özel biçim dizesi "dddd, dd MMMM yyyy HH:mm:ss" değeridir.

Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dize biçimlendirmeyi denetleyebilecek nesne özellikleri listelenmektedir. Bazı kültürlerin <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> özelliği tarafından döndürülen özel biçim belirtimi tüm özellikleri kullanmayabilir.

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

[Tabloya geri dön](#table)

<a name="GeneralDateShortTime"></a>

## <a name="the-general-date-short-time-g-format-specifier"></a>Genel Tarih Kısa Saat ("g") Biçim Tanımlayıcısı

"g" standart biçim tanımlayıcısı kısa tarih ("d") ve kısa saat ("t") desenlerinin bir boşlukla ayrılarak birleştirilmiş şeklini temsil eder.

Sonuç dizesi belirli bir <xref:System.Globalization.DateTimeFormatInfo> nesnenin biçimlendirme bilgietkilenir. Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dize biçimlendirmeyi denetleyebilecek nesne özellikleri listelenmektedir. Bazı kültürlerin <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> özellikleri ve <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> özellikleri tarafından döndürülen özel biçim belirtimi tüm özellikleri kullanmayabilir.

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

[Tabloya geri dön](#table)

<a name="GeneralDateLongTime"></a>

## <a name="the-general-date-long-time-g-format-specifier"></a>Genel Tarih Uzun Saat ("G") Biçim Tanımlayıcısı

"G" standart biçim tanımlayıcısı kısa tarih ("d") ve uzun saat ("T") desenlerinin bir boşlukla ayrılarak birleştirilmiş şeklini temsil eder.

Sonuç dizesi belirli bir <xref:System.Globalization.DateTimeFormatInfo> nesnenin biçimlendirme bilgietkilenir. Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dize biçimlendirmeyi denetleyebilecek nesne özellikleri listelenmektedir. Bazı kültürlerin <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> özellikleri ve <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> özellikleri tarafından döndürülen özel biçim belirtimi tüm özellikleri kullanmayabilir.

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

[Tabloya geri dön](#table)

<a name="MonthDay"></a>

## <a name="the-month-m-m-format-specifier"></a>Ay ("M", "m") Biçim Tanımlayıcısı

"M" veya "m" standart biçim belirtimi, geçerli <xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A?displayProperty=nameWithType> özellik tarafından tanımlanan özel bir tarih ve saat biçimi dizesini temsil eder. Örneğin, sabit kültür için özel biçim dizesi "MMMM dd" değeridir.

Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dize biçimlendirmeyi denetleyen nesne özellikleri listelenmektedir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "m" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#7)]
[!code-vb[Formatting.DateAndTime.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#7)]

[Tabloya geri dön](#table)

<a name="Roundtrip"></a>

## <a name="the-round-trip-o-o-format-specifier"></a>Gidiş Dönüş ("O", "o") Biçim Tanımlayıcısı

"O" veya "o" standart biçim belirtimi, saat dilimi bilgilerini koruyan ve ISO 8601'e uygun bir sonuç dizesi yayar bir desen kullanarak özel bir tarih ve saat biçimi dizesini temsil eder. Değerler <xref:System.DateTime> için, bu biçim belirtimi metindeki <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik ile birlikte tarih ve saat değerlerini korumak için tasarlanmıştır. <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> Biçimlendirilmiş <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> `styles` dize, parametre <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>.

"O" veya "o" standart biçim belirtimi "yyyy'-'MM'-'dd'T'HH':'mm':'ss'' anlamına gelir. fffffffK" değerler için <xref:System.DateTime> özel biçim dizesi ve "yyyy'-'MM'-'dd'T'HH':'mm':'ss'. değerler için <xref:System.DateTimeOffset> fffffffzzz" özel biçim dizesi. Bu dizede; kısa çizgiler, iki nokta üst üste ve "T" harfi gibi tek karakterleri sınırlayan tek soru işareti çiftleri, tek karakterin değiştirilemeyen bir değişmez değer olduğunu belirtir. Kesme işaretleri çıktı dizesinde görünmez.

"O" veya "o" standart biçim belirtimi (ve "yyyy'-'MM'-'dd'T'HH':'mm':'ss'. fffffffK" özel biçim dizesi) ISO 8601 <xref:System.DateTime.Kind%2A> <xref:System.DateTime> değerlerin özelliğini korumak için saat dilimi bilgilerini temsil eden üç şekilde yararlanır:

- Tarih ve saat <xref:System.DateTimeKind.Local?displayProperty=nameWithType> değerlerinin saat dilimi bileşeni UTC'den bir mahsuptur (örneğin, +01:00, -07:00). Tüm <xref:System.DateTimeOffset> değerler de bu biçimde temsil edilir.

- Tarih ve saat <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> değerlerinin saat dilimi bileşeni UTC'yi temsil etmek için "Z" (sıfır ofset anlamına gelir) kullanır.

- <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>tarih ve saat değerlerinde saat dilimi bilgisi yoktur.

"O" veya "o" standart biçim belirtici uluslararası bir standarda uygun olduğundan, belirteci kullanan biçimlendirme veya ayrıştırma işlemi her zaman değişmez kültürü ve Gregoryen takvimini kullanır.

"O" veya "o" `ParseExact`biçimi `TryParseExact` kullanılarak <xref:System.DateTime> <xref:System.DateTimeOffset> ayrıştırılabilen `Parse` `TryParse`ve bu biçimlerden birinde olan dizeleri ayrıştırılabilir. Nesneler söz <xref:System.DateTime> konusu olduğunda, aradığınız ayrıştma aşırı yükü `styles` de <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>değeri olan bir parametre içermelidir. "O" veya "o" biçim belirticisine karşılık gelen özel biçim dizesiyle ayrıştırma yöntemi çağırırsanız, "O" veya "o" ile aynı sonuçları almazsınız. Bunun nedeni, özel biçim dizesi kullanan ayrıştırma yöntemlerinin saat dilimi bileşeni olmayan tarih ve saat değerlerinin dize temsilini ayrıştıramaması veya UTC'yi belirtmek için "Z" kullanmasıdır.

Aşağıdaki örnek, ABD Pasifik Saat dilimindeki bir sistemde <xref:System.DateTime> bir <xref:System.DateTimeOffset> dizi değer ve bir değer görüntülemek için "o" biçim belirtimini kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/o1.cs#8)]
[!code-vb[Formatting.DateAndTime.Standard#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/o1.vb#8)]

Aşağıdaki örnek, biçimlendirilmiş bir dize oluşturmak için "o" biçimbelirtirini kullanır ve ardından tarih `Parse` ve saat yöntemini çağırarak özgün tarih ve saat değerini geri yükler.

[!code-csharp[Formatting.DateandTime.Standard#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Roundtrip1.cs#16)]
[!code-vb[Formatting.DateandTime.Standard#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/RoundTrip1.vb#16)]

[Tabloya geri dön](#table)

<a name="RFC1123"></a>

## <a name="the-rfc1123-r-r-format-specifier"></a>RFC1123 ("R", "r") Biçim Tanımlayıcısı

"R" veya "r" standart biçim belirtimi özelliği tarafından <xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A?displayProperty=nameWithType> tanımlanan özel bir tarih ve saat biçimi dizesini temsil eder. Desen tanımlı bir standardı yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "ddd, dd MMM yyyy HH':'mm':'ss 'GMT'" değeridir. Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.

Sonuç dizesi değişmez kültürü temsil <xref:System.Globalization.DateTimeFormatInfo> eden <xref:System.Globalization.DateTimeFormatInfo.InvariantInfo%2A?displayProperty=nameWithType> özellik tarafından döndürülen nesnenin aşağıdaki özelliklerinden etkilenir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|Sonuç dizesinin biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>|Sonuç dizesinde görünebilen kısaltılmış gün adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A>|Sonuç dizesinde görünebilen kısaltılmış ay adlarını tanımlar.|

RFC 1123 standardı Eşgüdümlü Evrensel Zaman (UTC) olarak bir zamanı ifade etse de, biçimlendirme işlemi biçimlendirilmekte olan <xref:System.DateTime> nesnenin değerini değiştirmez. Bu nedenle, biçimlendirme işlemini <xref:System.DateTime> gerçekleştirmeden <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> önce yöntemi arayarak değeri UTC'ye dönüştürmeniz gerekir. Buna karşılık, <xref:System.DateTimeOffset> değerler bu dönüştürmeyi otomatik olarak gerçekleştirir; biçimlendirme işleminden <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> önce yöntemi aramaya gerek yoktur.

Aşağıdaki örnek, ABD Pasifik Saat dilimindeki bir <xref:System.DateTime> sistemde <xref:System.DateTimeOffset> bir ve bir değer görüntülemek için "r" biçim belirticisini kullanır.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#9)]
[!code-vb[Formatting.DateAndTime.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#9)]

[Tabloya geri dön](#table)

<a name="Sortable"></a>

## <a name="the-sortable-s-format-specifier"></a>Sıralanabilir ("s") Biçim Tanımlayıcısı

"s" standart biçim belirtimi özelliği tarafından <xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A?displayProperty=nameWithType> tanımlanan özel bir tarih ve saat biçimi dizesini temsil eder. Desen tanımlı bir standardı (ISO 8601) yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "yyyy'-'MM'-'dd'T'HH':'mm':'ss" değeridir.

"s" biçim belirticisinin amacı, tarih ve saat değerlerine göre artan veya azalan sırada tutarlı bir şekilde sıralanan sonuç dizeleri üretmektir. Sonuç olarak, "s" standart biçim belirtimi tutarlı bir biçimde bir tarih ve saat değerini temsil etse de, biçimlendirme <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> işlemi, özelliğini veya <xref:System.DateTimeOffset.Offset%2A?displayProperty=nameWithType> değerini yansıtacak şekilde biçimlendirilmekte olan tarih ve saat nesnesinin değerini değiştirmez. Örneğin, tarih ve saat değerleri 2014-11-15T18:32:17+00:00 ve 2014-11-15T18:32:17+08:00 biçimlendirme tarafından üretilen sonuç dizeleri aynıdır.

Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.

Aşağıdaki örnek, ABD Pasifik Saat dilimindeki bir <xref:System.DateTime> sistemde <xref:System.DateTimeOffset> bir ve bir değer görüntülemek için "s" biçim belirticisini kullanır.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#10)]
[!code-vb[Formatting.DateAndTime.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#10)]

[Tabloya geri dön](#table)

<a name="ShortTime"></a>

## <a name="the-short-time-t-format-specifier"></a>Kısa Saat ("t") Biçim Tanımlayıcısı

"t" standart biçim belirtimi, geçerli <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> özellik tarafından tanımlanan özel bir tarih ve saat biçimi dizesini temsil eder. Örneğin, sabit kültür için özel biçim dizesi "HH:mm" değeridir.

Sonuç dizesi belirli bir <xref:System.Globalization.DateTimeFormatInfo> nesnenin biçimlendirme bilgietkilenir. Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dize biçimlendirmeyi denetleyebilecek nesne özellikleri listelenmektedir. Bazı kültürlerin <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> özelliği tarafından döndürülen özel biçim belirtimi tüm özellikleri kullanmayabilir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Sonuç dizesinin saat bileşeninin biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "t" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#11)]
[!code-vb[Formatting.DateAndTime.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#11)]

[Tabloya geri dön](#table)

<a name="LongTime"></a>

## <a name="the-long-time-t-format-specifier"></a>Uzun Saat ("T") Biçim Tanımlayıcısı

"T" standart biçim belirtimi, belirli bir kültürün <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçimi dizesini temsil eder. Örneğin, sabit kültür için özel biçim dizesi "HH:mm:ss" değeridir.

Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dize biçimlendirmeyi denetleyebilecek nesne özellikleri listelenmektedir. Bazı kültürlerin <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> özelliği tarafından döndürülen özel biçim belirtimi tüm özellikleri kullanmayabilir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Sonuç dizesinin saat bileşeninin biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "T" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#12)]
[!code-vb[Formatting.DateAndTime.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#12)]

[Tabloya geri dön](#table)

<a name="UniversalSortable"></a>

## <a name="the-universal-sortable-u-format-specifier"></a>Evrensel Sıralanabilir ("u") Biçim Tanımlayıcısı

"u" standart biçim belirtici <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçimi dizesini temsil eder. Desen tanımlı bir standardı yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "yyyy'-'MM'-'dd HH':'mm':'ss'Z'" değeridir. Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.

Sonuç dizesi Eşgüdümlü Evrensel Zaman (UTC) olarak bir <xref:System.DateTime> süre ifade etmelidir, ancak biçimlendirme işlemi sırasında özgün değerin dönüşümü yapılmaz. Bu nedenle, bir <xref:System.DateTime> değeri biçimlendirmeden <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> önce yöntemi arayarak UTC'ye dönüştürmeniz gerekir.  Buna karşılık, <xref:System.DateTimeOffset> değerler bu dönüştürmeyi otomatik olarak gerçekleştirir; biçimlendirme işleminden <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> önce yöntemi aramaya gerek yoktur.

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "u" biçim tanımlayıcısını kullanır.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#13)]
[!code-vb[Formatting.DateAndTime.Standard#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#13)]

[Tabloya geri dön](#table)

<a name="UniversalFull"></a>

## <a name="the-universal-full-u-format-specifier"></a>Evrensel Tam ("U") Biçim Tanımlayıcısı

"U" standart biçim belirtimi, belirli bir kültürün <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçimi dizesini temsil eder. Desen "F" deseni ile aynıdır. Ancak, <xref:System.DateTime> değer biçimlendirilmeden önce otomatik olarak UTC'ye dönüştürülür.

Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dize biçimlendirmeyi denetleyebilecek nesne özellikleri listelenmektedir. Bazı kültürlerin <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> özelliği tarafından döndürülen özel biçim belirtimi tüm özellikleri kullanmayabilir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş gün adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|

"U" biçimi belirtimi <xref:System.DateTimeOffset> türü tarafından desteklenmez ve <xref:System.FormatException> bir <xref:System.DateTimeOffset> değeri biçimlendirmek için kullanılırsa a atar.

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "U" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#14)]
[!code-vb[Formatting.DateAndTime.Standard#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#14)]

[Tabloya geri dön](#table)

<a name="YearMonth"></a>

## <a name="the-year-month-y-y-format-specifier"></a>Yıl Ay ("Y", "y") Biçim Tanımlayıcısı

"Y" veya "y" standart biçim belirtimi, belirli bir kültürün <xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçimi dizesini temsil eder. Örneğin, sabit kültür için özel biçim dizesi "yyyy MMMM" değeridir.

Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dize biçimlendirmeyi denetleyen nesne özellikleri listelenmektedir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "y" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#15)]
[!code-vb[Formatting.DateAndTime.Standard#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#15)]

[Tabloya geri dön](#table)

<a name="Notes"></a>

## <a name="notes"></a>Notlar

### <a name="control-panel-settings"></a>Denetim Masası Ayarları

Denetim Masası'ndaki **Bölgesel ve Dil Seçenekleri** öğesindeki ayarlar, bir biçimlendirme işlemi yle üretilen sonuç dizesini etkiler. Bu ayarlar, biçimlendirmeyi <xref:System.Globalization.DateTimeFormatInfo> yönetmek için kullanılan değerleri sağlayan geçerli iş parçacığı kültürüyle ilişkili nesneyi başlatmaya kullanılır. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.

Ayrıca, <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> kurucuyu geçerli sistem kültürüyle aynı kültürü <xref:System.Globalization.CultureInfo> temsil eden yeni bir nesneyi anında kullanmak için kullanırsanız, Denetim Masası'ndaki Bölgesel ve Dil <xref:System.Globalization.CultureInfo> **Seçenekleri** öğesi tarafından oluşturulan özelleştirmeler yeni nesneye uygulanır. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Bir sistemin özelleştirmelerini yansıtmayan <xref:System.Globalization.CultureInfo> bir nesne oluşturmak için oluşturucuyu kullanabilirsiniz.

### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo Özellikleri

Biçimlendirme, geçerli iş parçacığı <xref:System.Globalization.DateTimeFormatInfo> kültürü tarafından dolaylı olarak sağlanan geçerli nesnenin özelliklerinden <xref:System.IFormatProvider> veya biçimlendirmeyi çağıran yöntemin parametresi tarafından açıkça etkilenir. Parametre için, uygulamanızın bir kültürü veya belirli bir <xref:System.Globalization.DateTimeFormatInfo> kültürün tarih ve saat biçimlendirme kurallarını temsil eden bir nesneyi belirtmesi gerekir. <xref:System.Globalization.CultureInfo> <xref:System.IFormatProvider> Standart tarih ve saat biçimi belirtecilerin çoğu, geçerli <xref:System.Globalization.DateTimeFormatInfo> nesnenin özellikleriyle tanımlanan desenleri biçimlendirmek için diğer adlardır. Uygulamanız, ilgili <xref:System.Globalization.DateTimeFormatInfo> özelliğin ilgili tarih ve saat biçimi desenlerini değiştirerek, bazı standart tarih ve saat biçimi belirteciler tarafından üretilen sonucu değiştirebilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.DateTimeOffset?displayProperty=nameWithType>
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Örnek: .NET Core WinForms Biçimlendirme Programı (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Örnek: .NET Core WinForms Biçimlendirme Programı (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
