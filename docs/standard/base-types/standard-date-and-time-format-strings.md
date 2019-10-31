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
ms.openlocfilehash: b67b00fdb4a5c484c112cc2f3321ce2268d4dad7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121716"
---
# <a name="standard-date-and-time-format-strings"></a>Standart Tarih ve Saat Biçim Dizeleri

Standart tarih ve saat biçimi dizesi tek biçim belirleyici bir tarih ve saat değerinin metin gösterimini tanımlamak için kullanır. Boşluk da dahil olmak üzere birden fazla karakter içeren herhangi bir tarih ve saat biçim dizesi, özel bir tarih ve saat biçimi dizesi olarak yorumlanır; daha fazla bilgi için bkz. [özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md). Standart veya özel bir biçim dizesi iki şekilde kullanılabilir:

- Bir biçimlendirme işleminin sonucunda ortaya çıkan dizeyi tanımlamak için.

- Bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> değerine dönüştürülebilen bir ayrıştırma işlemi tarafından bir tarih ve saat değerinin metin temsilini tanımlamak için.

> [!TIP]
> Sayısal veya tarih ve saat değerlerine biçim dizeleri uygulamanızı sağlayan ve sonuç dizesini görüntüleyen bir .NET Core Windows Forms uygulaması olan **biçimlendirme yardımcı programını**indirebilirsiniz. Kaynak kodu, ve [C#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)için kullanılabilir.

Standart Tarih ve saat biçim dizeleri, hem <xref:System.DateTime> hem de <xref:System.DateTimeOffset> değerleriyle birlikte kullanılabilir.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)]

<a name="table"></a>Aşağıdaki tabloda standart tarih ve saat biçimi belirticileri açıklanmaktadır. Aksi belirtilmedikçe, belirli bir standart tarih ve saat biçimi belirticisi bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> değeriyle kullanılıp kullanılmadığına bakılmaksızın özdeş bir dize temsili üretir. Standart Tarih ve saat biçimi dizelerini kullanma hakkında ek bilgi için [Notlar](#Notes) bölümüne bakın.

|Biçim belirteci|Açıklama|Örnekler|
|----------------------|-----------------|--------------|
|"d"|Kısa Tarih Modeli<br /><br /> Daha fazla bilgi:[kısa tarih ("d") Biçim belirleyicisi](#ShortDate).|2009-06-15T13:45:30-> 6/15/2009 (en-US)<br /><br /> 2009-06-15T13:45:30-> 15/06/2009 (fr-FR)<br /><br /> 2009-06-15T13:45:30-> 2009/06/15 (ja-JP)|
|"D"|Uzun tarih deseni.<br /><br /> Daha fazla bilgi:[uzun tarih ("D") Biçim belirleyicisi](#LongDate).|2009-06-15T13:45:30-> Pazartesi, 15 Haziran 2009 (en-US)<br /><br /> 2009-06-15T13:45:30-> 15 июня 2009 г. (ru-RU)<br /><br /> 2009-06-15T13:45:30-> Montag, 15. Juni 2009 (de-DE)|
|"f"|Tam tarih veya saat deseni (süre).<br /><br /> Daha fazla bilgi: [tam tarih kısa saat ("f") Biçim belirleyicisi](#FullDateShortTime).|2009-06-15T13:45:30-> Pazartesi, 15 Haziran 2009 1:45 PM (en-US)<br /><br /> 2009-06-15T13:45:30-> den 15 junı 2009 13:45 (ZF-o)<br /><br /> 2009-06-15T13:45:30-> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)|
|"F"|Tam tarih veya saat deseni (uzun süre).<br /><br /> Daha fazla bilgi: [tam tarih uzun saat ("F") Biçim belirleyicisi](#FullDateLongTime).|2009-06-15T13:45:30-> Pazartesi, 15 Haziran 2009 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30-> den 15 junı 2009 13:45:30 (ZF-o)<br /><br /> 2009-06-15T13:45:30-> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)|
|"g"|Genel tarih veya saat deseni (süre).<br /><br /> Daha fazla bilgi: [Genel Tarih kısa saat ("g") Biçim belirleyicisi](#GeneralDateShortTime).|2009-06-15T13:45:30-> 6/15/2009 1:45 PM (en-US)<br /><br /> 2009-06-15T13:45:30-> 15/06/2009 13:45 (ES-ES)<br /><br /> 2009-06-15T13:45:30-> 2009/6/15 13:45 (zh-CN)|
|"G"|Genel tarih veya saat deseni (uzun süre).<br /><br /> Daha fazla bilgi: [Genel Tarih uzun saat ("G") Biçim belirleyicisi](#GeneralDateLongTime).|2009-06-15T13:45:30-> 6/15/2009 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30-> 15/06/2009 13:45:30 (ES-ES)<br /><br /> 2009-06-15T13:45:30-> 2009/6/15 13:45:30 (zh-CN)|
|"M", "m"|Ay/gün deseni.<br /><br /> Daha fazla bilgi: [ay ("ı", "d") Biçim belirleyicisi](#MonthDay).|2009-06-15T13:45:30-> 15 Haziran (en-US)<br /><br /> 2009-06-15T13:45:30-> 15. junı (da-DK)<br /><br /> 2009-06-15T13:45:30-> 15 Junı (kimlik KIMLIĞI)|
|"O", "o"|Gidiş tarihi/saati desen.<br /><br /> Daha fazla bilgi: [gidiş dönüş ("o", "o") Biçim belirleyicisi](#Roundtrip).|<xref:System.DateTime> değerleri:<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. Local)--> 2009-06-15T13:45:30.0000000-07:00<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. UTC)--> 2009-06-15T13:45:30.0000000 Z<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. Unspecified)--> 2009-06-15T13:45:30.0000000<br /><br /> <xref:System.DateTimeOffset> değerleri:<br /><br /> 2009-06-15T13:45:30-07:00--> 2009-06-15T13:45:30.0000000-07:00|
|"R", "r"|Desen: RFC1123<br /><br /> Daha fazla bilgi: [RFC1123 ("r", "r") Biçim belirleyicisi](#RFC1123).|2009-06-15T13:45:30-> Mon, 15 Haz 2009 20:45:30 GMT|
|"s"|Sıralanabilir tarih veya saat deseni.<br /><br /> Daha fazla bilgi: [sıralanabilir ("s") Biçim belirleyicisi](#Sortable).|2009-06-15T13:45:30 (DateTimeKind. Local)-> 2009-06-15T13:45:30<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. UTC)-> 2009-06-15T13:45:30|
|"t"|Kısa bir süre deseni.<br /><br /> Daha fazla bilgi: [kısa saat ("t") Biçim belirleyicisi](#ShortTime).|2009-06-15T13:45:30-> 1:45 PM (en-US)<br /><br /> 2009-06-15T13:45:30-> 13:45 (HR-HR)<br /><br /> 2009-06-15T13:45:30-> 01:45 م (ar-EG)|
|"T"|Uzun süre deseni.<br /><br /> Daha fazla bilgi: [uzun saat ("T") Biçim belirleyicisi](#LongTime).|2009-06-15T13:45:30-> 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30-> 13:45:30 (HR-HR)<br /><br /> 2009-06-15T13:45:30-> 01:45:30 م (ar-EG)|
|"u"|Evrensel sıralanabilir tarih/saat deseni.<br /><br /> Daha fazla bilgi: [evrensel sıralanabilir ("u") Biçim belirleyicisi](#UniversalSortable).|<xref:System.DateTime> değeriyle: 2009-06-15T13:45:30-> 2009-06-15 13:45:30Z<br /><br /> <xref:System.DateTimeOffset> değeriyle: 2009-06-15T13:45:30-> 2009-06-15 20:45:30Z|
|"U"|Evrensel tam tarih/saat deseni.<br /><br /> Daha fazla bilgi: [Evrensel tam ("U") Biçim belirleyicisi](#UniversalFull).|2009-06-15T13:45:30-> Pazartesi, 15 Haziran 2009 8:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30-> den 15 junı 2009 20:45:30 (ZF-o)<br /><br /> 2009-06-15T13:45:30-> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)|
|"Y", "y"|Yıl ay deseni.<br /><br /> Daha fazla bilgi: [yıl ay ("Y") Biçim belirleyicisi](#YearMonth).|2009-06-15T13:45:30-> Haziran 2009 (en-US)<br /><br /> 2009-06-15T13:45:30-> junı 2009 (da-DK)<br /><br /> 2009-06-15T13:45:30-> Junı 2009 (kimlik KIMLIĞI)|
|Başka bir tek karakter|Bilinmeyen tanımlayıcı.|Bir çalışma zamanı <xref:System.FormatException>oluşturur.|

## <a name="how-standard-format-strings-work"></a>Standart Biçim Dizeleri Nasıl Çalışır

Bir biçimlendirme işleminde, standart biçim dizesi aslında bir özel biçim dizesi için diğer addır. Bir özel biçim dizesine başvururken diğer ad kullanmanın yararı, diğer ad değişmez iken özel biçim dizesinin kendisinin değişebilmesidir. Bu, tarih ve saat değerleri genellikle kültüre göre değiştiği için önemlidir. Örneğin, "d" standart biçim dizesi bir tarih ve saat değerinin kısa tarih deseni kullanılarak görüntüleneceğini belirtir. Sabit kültür için bu desen "MM/dd/yyyy" şeklindedir. fr-FR kültürü için "dd/MM/yyyy" şeklindedir. ja-JP kültürü için "yyyy/MM/dd" şeklindedir.

Eğer bir biçimlendirme işleminde standart format dizesi belirli bir kültürün özel biçim dizesiyle eşleniyorsa, uygulamanız özel biçim dizeleri aşağıdaki şekillerden birinde kullanılan belirli kültürü tanımlayabilir:

- Varsayılan (veya geçerli( kültürü kullanabilirsiniz. Aşağıdaki örnek geçerli kültürün kısa tarih biçimini kullanarak bir tarih görüntüler. Bu durumda geçerli kültür en-US değeridir.

  [!code-csharp-interactive[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#1)]
  [!code-vb[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#1)]

- Biçimlendirmesi, bir <xref:System.IFormatProvider> parametresine sahip bir yöntemde kullanılacak olan kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesnesi geçirebilirsiniz. Aşağıdaki örnek pt-BR kültürünün kısa tarih biçimini kullanarak bir tarih görüntüler.

  [!code-csharp[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#2)]
  [!code-vb[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#2)]

- Bir <xref:System.IFormatProvider> parametresine sahip bir yönteme biçimlendirme bilgileri sağlayan bir <xref:System.Globalization.DateTimeFormatInfo> nesnesini geçirebilirsiniz. Aşağıdaki örnek, HR-HR kültürü için <xref:System.Globalization.DateTimeFormatInfo> nesnesinden kısa tarih biçimini kullanarak bir tarih görüntüler.

  [!code-csharp[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#3)]
  [!code-vb[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#3)]

> [!NOTE]
> Tarih ve saat değerlerinde kullanılan desenleri veya dizeleri özelleştirme hakkında daha fazla bilgi için <xref:System.Globalization.NumberFormatInfo> sınıfı konusuna bakın.

Bazı durumlarda, standart biçim dizesi sabit olan daha uzun bir özel biçim dizesi için uygun bir kısaltma görevi görür. Dört standart biçim dizesi bu kategoriye girer: "O" (veya "o"), "R" (veya "r"), "s" ve "u". Bu dizeler sabit kültür tarafından tanımlanan özel biçim dizelerine karşılık gelir. Kültürler arası aynı olan tarih ve saat değerlerinin dize temsillerini oluştururlar. Aşağıdaki tablo bu dört standart tarih ve saat biçim dizesi hakkında bilgi verir.

|Standart biçim dizeleri|DateTimeFormatInfo.InvariantInfo özelliği tarafından tanımı|Özel biçim dizesi|
|----------------------------|----------------------------------------------------------|--------------------------|
|"O" veya "o"|Yok.|yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz|
|"R" ya da "r"|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|ddd, dd MMM yyyy HH':'mm':'ss 'GMT'|
|"s"|<xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A>|yyyy'-'MM'-'dd'T'HH':'mm':'ss|
|"u"|<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>|yyyy'-'MM'-'dd HH':'mm':'ss'Z'|

Standart biçim dizeleri Ayrıca, ayrıştırma işleminin başarılı olması için bir giriş dizesinin belirli bir modele tam olarak uyması gereken <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> yöntemleriyle ayrıştırma işlemlerinde kullanılabilir. Birçok standart biçim dizesi birden çok özel biçim dizesine eşlenir, yani bir tarih ve saat değeri çeşitli biçimlerde temsil edilebilir ve ayrıştırma işlemi yine de başarılı olur. <xref:System.Globalization.DateTimeFormatInfo.GetAllDateTimePatterns%28System.Char%29?displayProperty=nameWithType> yöntemini çağırarak standart biçim dizesine karşılık gelen özel biçim dizesini veya dizeleri belirleyebilirsiniz. Aşağıdaki örnek "d" (kısa tarih deseni) standart biçim dizesiyle eşlenen özel biçim dizelerini görüntüler.

[!code-csharp[Formatting.DateAndTime.Standard#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/stdandparsing1.cs#17)]
[!code-vb[Formatting.DateAndTime.Standard#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/stdandparsing1.vb#17)]

Aşağıdaki bölümlerde <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri için standart biçim belirticileri açıklanır.

<a name="ShortDate"></a>

## <a name="the-short-date-d-format-specifier"></a>Kısa Tarih ("d") Biçim Tanımlayıcısı

"D" standart biçim Belirleyicisi, belirli bir kültürün <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder. Örneğin, sabit kültürün <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A> özelliği tarafından döndürülen özel biçim dizesi "aa/gg/yyyy" şeklindedir.

Aşağıdaki tabloda döndürülen dizenin biçimlendirmesini denetleyen <xref:System.Globalization.DateTimeFormatInfo> nesne özellikleri listelenmektedir.

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

"D" standart biçim belirticisi geçerli <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder. Örneğin, sabit kültür için özel biçim dizesi "dddd, dd MMMM yyyy" değeridir.

Aşağıdaki tabloda döndürülen dizenin biçimlendirmesini denetleyen <xref:System.Globalization.DateTimeFormatInfo> nesnesinin özellikleri listelenmektedir.

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

Sonuç dizesi, belirli bir <xref:System.Globalization.DateTimeFormatInfo> nesnesinin biçimlendirme bilgileri tarafından etkilenir. Aşağıdaki tabloda döndürülen dizenin biçimlendirilmesini denetleyelebilecek <xref:System.Globalization.DateTimeFormatInfo> nesne özellikleri listelenmektedir. Bazı kültürlerin <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> ve <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> özellikleri tarafından döndürülen özel biçim belirticisi tüm özellikleri kullanamaz.

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

"F" standart biçim belirticisi geçerli <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder. Örneğin, sabit kültür için özel biçim dizesi "dddd, dd MMMM yyyy HH:mm:ss" değeridir.

Aşağıdaki tabloda döndürülen dizenin biçimlendirilmesini denetleyelebilecek <xref:System.Globalization.DateTimeFormatInfo> nesne özellikleri listelenmektedir. Bazı kültürlerin <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> özelliği tarafından döndürülen özel biçim belirticisi tüm özellikleri kullanmayabilir.

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

Sonuç dizesi, belirli bir <xref:System.Globalization.DateTimeFormatInfo> nesnesinin biçimlendirme bilgileri tarafından etkilenir. Aşağıdaki tabloda döndürülen dizenin biçimlendirilmesini denetleyelebilecek <xref:System.Globalization.DateTimeFormatInfo> nesne özellikleri listelenmektedir. Bazı kültürlerin <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> ve <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> özellikleri tarafından döndürülen özel biçim belirticisi tüm özellikleri kullanamaz.

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

Sonuç dizesi, belirli bir <xref:System.Globalization.DateTimeFormatInfo> nesnesinin biçimlendirme bilgileri tarafından etkilenir. Aşağıdaki tabloda döndürülen dizenin biçimlendirilmesini denetleyelebilecek <xref:System.Globalization.DateTimeFormatInfo> nesne özellikleri listelenmektedir. Bazı kültürlerin <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> ve <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> özellikleri tarafından döndürülen özel biçim belirticisi tüm özellikleri kullanamaz.

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

"D" veya "d" standart biçim belirticisi geçerli <xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder. Örneğin, sabit kültür için özel biçim dizesi "MMMM dd" değeridir.

Aşağıdaki tabloda döndürülen dizenin biçimlendirmesini denetleyen <xref:System.Globalization.DateTimeFormatInfo> nesne özellikleri listelenmektedir.

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

"O" veya "o" standart biçim Belirleyicisi, saat dilimi bilgilerini koruyan ve ISO 8601 ile uyumlu bir sonuç dizesi veren bir model kullanarak özel bir tarih ve saat biçim dizesini temsil eder. <xref:System.DateTime> değerler için, bu Biçim belirleyicisi metin içindeki <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği ile birlikte tarih ve saat değerlerini korumak için tasarlanmıştır. `styles` parametresi <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>olarak ayarlandıysa, biçimlendirilen dize, <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> veya <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> yöntemi kullanılarak geri ayrıştırılabilir.

"O" veya "o" standart biçim Belirleyicisi, "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' öğesine karşılık gelir. Gönderildiğinde fffffffK biçiminde "<xref:System.DateTime> değerleri için özel biçim dizesi ve" yyyy'-': '-Idd't'hh ': ' mm ': ' ss '. ' fffffffzzz, <xref:System.DateTimeOffset> değerleri için özel biçim dizesi. Bu dizede; kısa çizgiler, iki nokta üst üste ve "T" harfi gibi tek karakterleri sınırlayan tek soru işareti çiftleri, tek karakterin değiştirilemeyen bir değişmez değer olduğunu belirtir. Kesme işaretleri çıktı dizesinde görünmez.

"O" veya "o" standart biçim Belirleyicisi (ve "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' Gönderildiğinde fffffffK biçiminde "özel biçim dizesi), ISO 8601 ' nin <xref:System.DateTime> değerlerinin <xref:System.DateTime.Kind%2A> özelliğini korumak için zaman dilimi bilgilerini temsil eden üç yol avantajlarından yararlanır:

- Tarih ve saat değerlerinin <xref:System.DateTimeKind.Local?displayProperty=nameWithType> saat dilimi bileşeni UTC 'den bir kaydırmadır (örneğin, + 01:00,-07:00). Tüm <xref:System.DateTimeOffset> değerleri de bu biçimde temsil edilir.

- Tarih ve saat değerlerinin saat dilimi <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> bileşeni UTC 'yi göstermek için "Z" (sıfır sapmasını temsil eder) kullanır.

- <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> tarih ve saat değerlerinde saat dilimi bilgisi yok.

"O" veya "o" standart biçim belirticisi uluslararası bir standarda uygun olduğundan, belirtici kullanan biçimlendirme veya ayrıştırma işlemi her zaman sabit kültür ve Gregoryen takvimi kullanır.

<xref:System.DateTime> ve <xref:System.DateTimeOffset> `Parse`, `TryParse`, `ParseExact`ve `TryParseExact` yöntemlerine aktarılan dizeler, bu biçimlerden birinde yer alıyorsa "O" veya "o" biçim belirticisi kullanılarak ayrıştırılabilir. <xref:System.DateTime> nesneler söz konusu olduğunda, çağırdığınız ayrıştırma aşırı yüklemesi de <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>değeri olan bir `styles` parametresi içermelidir. "O" veya "o" biçim belirticisine karşılık gelen özel biçim dizesiyle bir ayrıştırma yöntemi çağırırsanız, "O" veya "o" ile aynı sonuçları almazsınız. Bunun nedeni, özel biçim dizesi kullanan ayrıştırma yöntemlerinin, saat dilimi bileşeni olmayan tarih ve saat değerlerinin dize temsilini ayrıştıramaması veya UTC 'yi göstermek için "Z" kullanmasına yol göstermektir.

Aşağıdaki örnek ABD Pasifik saati dilimindeki bir sistem üzerinde bir dizi <xref:System.DateTime> değerini ve <xref:System.DateTimeOffset> değerini göstermek için "o" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/o1.cs#8)]
[!code-vb[Formatting.DateAndTime.Standard#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/o1.vb#8)]

Aşağıdaki örnek, biçimli bir dize oluşturmak için "o" biçim belirticisini kullanır ve sonra tarih ve saat `Parse` yöntemini çağırarak özgün tarih ve saat değerini geri yükler.

[!code-csharp[Formatting.DateandTime.Standard#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Roundtrip1.cs#16)]
[!code-vb[Formatting.DateandTime.Standard#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/RoundTrip1.vb#16)]

[Tabloya dön](#table)

<a name="RFC1123"></a>

## <a name="the-rfc1123-r-r-format-specifier"></a>RFC1123 ("R", "r") Biçim Tanımlayıcısı

"R" veya "r" Standart Biçim belirleyicisi <xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder. Desen tanımlı bir standardı yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "ddd, dd MMM yyyy HH':'mm':'ss 'GMT'" değeridir. Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.

Sonuç dizesi, sabit kültürü temsil eden <xref:System.Globalization.DateTimeFormatInfo.InvariantInfo%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Globalization.DateTimeFormatInfo> nesnesinin aşağıdaki özelliklerinden etkilenir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|Sonuç dizesinin biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>|Sonuç dizesinde görünebilen kısaltılmış gün adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A>|Sonuç dizesinde görünebilen kısaltılmış ay adlarını tanımlar.|

RFC 1123 standardı bir saati Eşgüdümlü Evrensel Saat (UTC) olarak ifade etse de biçimlendirme işlemi biçimlendirilmekte olan <xref:System.DateTime> nesnesinin değerini değiştirmez. Bu nedenle, biçimlendirme işlemini gerçekleştirmeden önce <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> metodunu çağırarak <xref:System.DateTime> değerini UTC 'ye dönüştürmeniz gerekir. Buna karşılık, <xref:System.DateTimeOffset> değerler bu dönüştürmeyi otomatik olarak gerçekleştirir; biçimlendirme işleminden önce <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> yöntemini çağırmanız gerekmez.

Aşağıdaki örnek ABD Pasifik saati dilimindeki bir sistemde <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerini göstermek için "r" biçim tanımlayıcısını kullanır.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#9)]
[!code-vb[Formatting.DateAndTime.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#9)]

[Tabloya dön](#table)

<a name="Sortable"></a>

## <a name="the-sortable-s-format-specifier"></a>Sıralanabilir ("s") Biçim Tanımlayıcısı

"S" Standart Biçim belirleyicisi <xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder. Desen tanımlı bir standardı (ISO 8601) yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "yyyy'-'MM'-'dd'T'HH':'mm':'ss" değeridir.

"S" Biçim belirticisinin amacı, tarih ve saat değerlerine göre düzenli olarak artan veya azalan düzende sıralayan sonuç dizelerini üretmeniz sağlamaktır. Sonuç olarak, "s" Standart Biçim belirleyicisi bir tarih ve saat değerini tutarlı biçimde temsil ediyorsa, biçimlendirme işlemi <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliğini veya <xref:System.DateTimeOffset.Offset%2A?displayProperty=nameWithType> yansıtacak şekilde biçimlendirilmekte olan tarih ve saat nesnesinin değerini değiştirmez deeri. Örneğin, 2014-11-15T18:32:17 + 00:00 ve 2014-11-15T18:32:17 + 08:00 gibi tarih ve saat değerlerini biçimlendirirken oluşturulan sonuç dizeleri aynıdır.

Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.

Aşağıdaki örnek ABD Pasifik saati dilimindeki bir sistemde <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerini göstermek için "s" biçim tanımlayıcısını kullanır.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#10)]
[!code-vb[Formatting.DateAndTime.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#10)]

[Tabloya dön](#table)

<a name="ShortTime"></a>

## <a name="the-short-time-t-format-specifier"></a>Kısa Saat ("t") Biçim Tanımlayıcısı

"T" standart biçim belirticisi geçerli <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder. Örneğin, sabit kültür için özel biçim dizesi "HH:mm" değeridir.

Sonuç dizesi, belirli bir <xref:System.Globalization.DateTimeFormatInfo> nesnesinin biçimlendirme bilgileri tarafından etkilenir. Aşağıdaki tabloda döndürülen dizenin biçimlendirilmesini denetleyelebilecek <xref:System.Globalization.DateTimeFormatInfo> nesne özellikleri listelenmektedir. Bazı kültürlerin <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> özelliği tarafından döndürülen özel biçim belirticisi tüm özellikleri kullanmayabilir.

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

"T" standart biçim Belirleyicisi, belirli bir kültürün <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder. Örneğin, sabit kültür için özel biçim dizesi "HH:mm:ss" değeridir.

Aşağıdaki tabloda döndürülen dizenin biçimlendirilmesini denetleyelebilecek <xref:System.Globalization.DateTimeFormatInfo> nesne özellikleri listelenmektedir. Bazı kültürlerin <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> özelliği tarafından döndürülen özel biçim belirticisi tüm özellikleri kullanmayabilir.

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

"U" standart biçim Belirleyicisi, <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder. Desen tanımlı bir standardı yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "yyyy'-'MM'-'dd HH':'mm':'ss'Z'" değeridir. Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.

Sonuç dizesi bir saati Eşgüdümlü Evrensel Saat (UTC) olarak ifade etmelidir, ancak biçimlendirme işlemi sırasında özgün <xref:System.DateTime> değeri dönüştürmesi yapılmaz. Bu nedenle, biçimlendirmeden önce <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> yöntemini çağırarak bir <xref:System.DateTime> değerini UTC 'ye dönüştürmeniz gerekir.  Buna karşılık, <xref:System.DateTimeOffset> değerler bu dönüştürmeyi otomatik olarak gerçekleştirir; biçimlendirme işleminden önce <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> yöntemini çağırmanız gerekmez.

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "u" biçim tanımlayıcısını kullanır.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#13)]
[!code-vb[Formatting.DateAndTime.Standard#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#13)]

[Tabloya dön](#table)

<a name="UniversalFull"></a>

## <a name="the-universal-full-u-format-specifier"></a>Evrensel Tam ("U") Biçim Tanımlayıcısı

"U" standart biçim Belirleyicisi, belirtilen bir kültürün <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder. Desen "F" deseni ile aynıdır. Ancak, <xref:System.DateTime> değeri, biçimlendirilmeden önce otomatik olarak UTC 'ye dönüştürülür.

Aşağıdaki tabloda döndürülen dizenin biçimlendirilmesini denetleyelebilecek <xref:System.Globalization.DateTimeFormatInfo> nesne özellikleri listelenmektedir. Bazı kültürlerin <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> özelliği tarafından döndürülen özel biçim belirticisi tüm özellikleri kullanmayabilir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş gün adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|

"U" Biçim belirleyicisi <xref:System.DateTimeOffset> türü tarafından desteklenmez ve bir <xref:System.DateTimeOffset> değeri biçimlendirmek için kullanılırsa bir <xref:System.FormatException> oluşturur.

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "U" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#14)]
[!code-vb[Formatting.DateAndTime.Standard#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#14)]

[Tabloya dön](#table)

<a name="YearMonth"></a>

## <a name="the-year-month-y-y-format-specifier"></a>Yıl Ay ("Y", "y") Biçim Tanımlayıcısı

"Y" veya "y" standart biçim Belirleyicisi, belirtilen bir kültürün <xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder. Örneğin, sabit kültür için özel biçim dizesi "yyyy MMMM" değeridir.

Aşağıdaki tabloda döndürülen dizenin biçimlendirmesini denetleyen <xref:System.Globalization.DateTimeFormatInfo> nesne özellikleri listelenmektedir.

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

Denetim Masası 'ndaki **bölge ve dil seçenekleri** öğesindeki ayarlar, bir biçimlendirme işlemi tarafından üretilen sonuç dizesini etkiler. Bu ayarlar, biçimlendirmeyi yönetmek için kullanılan değerleri sağlayan geçerli iş parçacığı kültürüyle ilişkili <xref:System.Globalization.DateTimeFormatInfo> nesnesini başlatmak için kullanılır. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.

Ayrıca, geçerli sistem kültürüyle aynı kültürü temsil eden yeni bir <xref:System.Globalization.CultureInfo> nesnesini başlatmak için <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> oluşturucusunu kullanırsanız, Denetim Masası 'ndaki **bölge ve dil seçenekleri** öğesi tarafından belirlenen tüm özelleştirmeler şu şekilde olur Yeni <xref:System.Globalization.CultureInfo> nesnesine uygulandı. Bir sistemin özelleştirmelerini yansıtmayan bir <xref:System.Globalization.CultureInfo> nesnesi oluşturmak için <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> oluşturucusunu kullanabilirsiniz.

### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo Özellikleri

Biçimlendirme, geçerli iş parçacığı kültürü tarafından örtük olarak sağlanmış olan veya biçimlendirmeyi çağıran metodun <xref:System.IFormatProvider> parametresi tarafından açıkça sunulan geçerli <xref:System.Globalization.DateTimeFormatInfo> nesnesinin özelliklerinden etkilenir. <xref:System.IFormatProvider> parametresi için, uygulamanız bir kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesnesi veya belirli bir kültürün tarih ve saat biçimlendirme kurallarını temsil eden bir <xref:System.Globalization.DateTimeFormatInfo> nesnesi belirtmelidir. Standart Tarih ve saat biçimi belirticileri çoğu, geçerli <xref:System.Globalization.DateTimeFormatInfo> nesnesinin özellikleri tarafından tanımlanan biçimlendirme desenleri için diğer adlardır. Uygulamanız, karşılık gelen <xref:System.Globalization.DateTimeFormatInfo> özelliğinin karşılık gelen Tarih ve saat biçimi düzenlerini değiştirerek bazı standart tarih ve saat biçimi belirticileri tarafından oluşturulan sonucu değiştirebilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.DateTimeOffset?displayProperty=nameWithType>
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Örnek: .NET Core WinForms biçimlendirme yardımcı programıC#()](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Örnek: .NET Core WinForms biçimlendirme yardımcı programı (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
