---
title: Özel tarih ve saat biçimi dizeleri
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
ms.assetid: 98b374e3-0cc2-4c78-ab44-efb671d71984
ms.openlocfilehash: b33366922677b26f8fe99454206cacd5bb124f32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159279"
---
# <a name="custom-date-and-time-format-strings"></a>Özel tarih ve saat biçimi dizeleri

Tarih ve saat biçimi dizesi, <xref:System.DateTime> biçimlendirme işleminden kaynaklanan bir veya <xref:System.DateTimeOffset> değerin metin gösterimini tanımlar. Ayrıca, dizeyi tarih ve saate başarılı bir şekilde dönüştürmek için bir ayrıştırma işleminde gerekli olan tarih ve saat değerinin bildirimini tanımlayabilir. Özel biçim dizesi, bir veya daha fazla özel tarih ve saat biçimi belirleyicisinden oluşur. Standart tarih ve [saat biçimi dizesi](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) olmayan herhangi bir dize özel bir tarih ve saat biçimi dizesi olarak yorumlanır.

> [!TIP]
> **Biçimlendirme Yardımcı Programı'nı**indirebilirsiniz , bir .NET Core Windows Forms uygulamasını, biçim dizelerini sayısal veya tarih ve saat değerlerine uygulamanızı ve sonuç dizesini görüntülemenizi sağlar. Kaynak kodu [C#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) ve [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)için kullanılabilir.

Özel tarih ve saat biçimi dizeleri <xref:System.DateTime> <xref:System.DateTimeOffset> hem de değerlerle kullanılabilir.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)]

<a name="table"></a>Biçimlendirme işlemlerinde, özel tarih ve saat biçimi dizeleri, tarih ve saat örneğinin `ToString` yöntemiyle veya bileşik biçimlendirmeyi destekleyen bir yöntemle kullanılabilir. Aşağıdaki örnek her iki kullanımı da gösterir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandformatting1.cs#17)]
[!code-vb[Formatting.DateAndTime.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandformatting1.vb#17)]

Ayrıştma işlemlerinde, özel tarih ve saat biçimi <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>dizeleri , , <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, ve <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> yöntemleri ile kullanılabilir. Bu yöntemler, ayrışdırıcı işlemin başarılı olması için bir giriş dizesinin belirli bir desenin tam olarak uyumlu olmasını gerektirir. Aşağıdaki örnekte, bir gün, bir ay ve iki basamaklı bir yıl içermesi gereken bir tarihi ayrıştama <xref:System.DateTimeOffset.ParseExact%28System.String%2CSystem.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemine yapılan çağrı gösterilmelidir.

[!code-csharp[Formatting.DateAndTime.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandparsing1.cs#18)]
[!code-vb[Formatting.DateAndTime.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandparsing1.vb#18)]

Aşağıdaki tabloda özel tarih ve saat biçimi belirteçleri açıklanır ve her biçim belirticisi tarafından üretilen bir sonuç dizesini görüntülenir. Varsayılan olarak, sonuç dizeleri en-US kültürünün, biçimlendirme kurallarını yansıtır. Belirli bir biçim belirticisi yerelleştirilmiş bir sonuç dizesi üretirse örnek aynı zamanda sonuç dizesinin uygulanacağı kültürü de not alır. Özel tarih ve saat biçimi dizelerini kullanma hakkında daha fazla bilgi için [Notlar](#notes) bölümüne bakın.

| Biçim belirteci | Açıklama | Örnekler |
| ---------------------- | ----------------- | -------------- |
|"d"|1 İle 31 arasında ayın günü.<br /><br /> Daha fazla bilgi: ["d" Özel Biçim Belirtimi.](#dSpecifier)|2009-06-01T13:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 15|
|"dd"|01 İle 31 arasında ayın günü.<br /><br /> Daha fazla bilgi: ["dd" Özel Biçim Belirtimi.](#ddSpecifier)|2009-06-01T13:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 15|
|"ddd"|Haftanın günü, kısaltılmış adı.<br /><br /> Daha fazla bilgi: ["ddd" Özel Biçim Belirtimi.](#dddSpecifier)|2009-06-15T13:45:30 -> Pzt (tr-ABD)<br /><br /> 2009-06-15T13:45:30 -> Пн (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lun. (fr-FR)|
|"dddd"|Haftanın gününün tam adı.<br /><br /> Daha fazla bilgi: ["dddd" Özel Biçim Belirtimi.](#ddddSpecifier)|2009-06-15T13:45:30 -> Pazartesi (tr-ABD)<br /><br /> 2009-06-15T13:45:30 -> понедельник (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lundi (fr-FR)|
|"f"|Saniyenin onda biri bir tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["f" Özel Biçim Belirtimi.](#fSpecifier)|2009-06-15T13:45:30.6170000 -> 6<br /><br /> 2009-06-15T13:45:30.05 -> 0|
|"ff"|Tarih ve saat değerindeki saniyenin yüzde biri.<br /><br /> Daha fazla bilgi: ["ff" Özel Biçim Belirtimi](#ffSpecifier).|2009-06-15T13:45:30.6170000 -> 61<br /><br /> 2009-06-15T13:45:30.005000 -> 00|
|"fff"|Tarih ve saat değerindeki milisaniye.<br /><br /> Daha fazla bilgi: ["fff" Özel Biçim Belirtimi.](#fffSpecifier)|15.06.2009 13:45:30.617 -> 617<br /><br /> 15.06.2009 13:45:30.0005 -> 000|
|"ffff"|Saniyenin on binde birindeki tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["ffff" Özel Biçim Belirtimi.](#ffffSpecifier)|2009-06-15T13:45:30.6175000 -> 6175<br /><br /> 2009-06-15T13:45:30.0000500 -> 0000|
|"fffff"|Tarih ve saat değerindeki saniyenin yüz binde biri.<br /><br /> Daha fazla bilgi: ["fffff" Özel Biçim Belirtimi](#fffffSpecifier).|2009-06-15T13:45:30.6175400 -> 61754<br /><br /> 15.06.2009 13:45:30.000005 -> 00000|
|"ffffff"|Tarih ve saat değerindeki saniyenin milyonda biri.<br /><br /> Daha fazla bilgi: ["ffffff" Özel Biçim Belirtimi](#ffffffSpecifier).|2009-06-15T13:45:30.6175420 -> 617542<br /><br /> 2009-06-15T13:45:30.000005 -> 000000|
|"fffffff"|Saniyenin on milyonda birindeki tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["fffffff" Özel Format Belirtimi](#fffffffSpecifier).|2009-06-15T13:45:30.6175425 -> 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -> 0001150|
|"F"|Sıfır olmayan, saniyenin onda biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["F" Özel Biçim Belirtimi.](#F_Specifier)|2009-06-15T13:45:30.6170000 -> 6<br /><br /> 2009-06-15T13:45:30.0500000 -> (çıkış yok)|
|"FF"|Sıfır olmayan, saniyenin yüzde biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FF" Özel Biçim Belirtimi.](#FF_Specifier)|2009-06-15T13:45:30.6170000 -> 61<br /><br /> 2009-06-15T13:45:30.0050000 -> (çıkış yok)|
|"FFF"|Sıfır olmayan, milisaniye cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFF" Özel Biçim Belirtimi.](#FFF_Specifier)|2009-06-15T13:45:30.6170000 -> 617<br /><br /> 2009-06-15T13:45:30.0005000 -> (çıkış yok)|
|"FFFF"|Sıfır olmayan, saniyenin on binde biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFFF" Özel Biçim Belirtimi.](#FFFF_Specifier)|2009-06-15T13:45:30.5275000 -> 5275<br /><br /> 2009-06-15T13:45:30.0000500 -> (çıkış yok)|
|"FFFFF"|Sıfır olmayan, saniyenin yüz binde biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFFFF" Özel Biçim Belirtimi.](#FFFFF_Specifier)|2009-06-15T13:45:30.6175400 -> 61754<br /><br /> 2009-06-15T13:45:30.0000050 -> (çıkış yok)|
|"FFFFFF"|Sıfır olmayan, saniyenin milyonda birinde cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFFFFF" Özel Format Belirtimi](#FFFFFF_Specifier).|2009-06-15T13:45:30.6175420 -> 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> (çıkış yok)|
|"FFFFFFF"|Sıfır olmayan, saniyenin on milyonda biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFFFFFF" Özel Biçim Belirtimi.](#FFFFFFF_Specifier)|2009-06-15T13:45:30.6175425 -> 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -> 000115|
|"g", "gg"|Süre veya dönem.<br /><br /> Daha fazla bilgi: ["g" veya "gg" Özel Biçim Belirtimi.](#gSpecifier)|2009-06-15T13:45:30.6170000 -> A.D.|
|"h"|Saat, 12 saatlik biçimde, 1 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["h" Özel Biçim Belirtimi.](#hSpecifier)|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 1|
|"hh"|Saat, 12 saatlik biçimde, 01 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["hh" Özel Biçim Belirtimi](#hhSpecifier).|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 01|
|"H"|Saat, 0'dan 23'e kadar 24 saatlik bir saat kullanarak.<br /><br /> Daha fazla bilgi: ["H" Özel Biçim Belirtimi.](#H_Specifier)|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 13|
|"HH"|Saat, 24 saatlik biçimde, 00 ile 23 arasında.<br /><br /> Daha fazla bilgi: ["HH" Özel Biçim Belirtimi.](#HH_Specifier)|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 13|
|"K"|Saat dilimi bilgileri.<br /><br /> Daha fazla bilgi: ["K" Özel Biçim Belirtimi.](#KSpecifier)|Değerlerle: <xref:System.DateTime><br /><br /> 2009-06-15T13:45:30, Tür Belirtilmemiş -><br /><br /> 2009-06-15T13:45:30, Tür Utc -> Z<br /><br /> 2009-06-15T13:45:30, Kind Yerel -> -07:00 (yerel bilgisayar ayarlarına bağlıdır)<br /><br /> Değerlerle: <xref:System.DateTimeOffset><br /><br /> 2009-06-15T01:45:30-07:00 --> -07:00<br /><br /> 2009-06-15T08:45:30+00:00 --> +00:00|
|"m"|Dakika, 0 ile 59 arasında.<br /><br /> Daha fazla bilgi: ["m" Özel Biçim Belirtimi.](#mSpecifier)|2009-06-15T01:09:30 -> 9<br /><br /> 2009-06-15T13:29:30 -> 29|
|"mm"|Dakika, 00 ile 59 arasında.<br /><br /> Daha fazla bilgi: ["mm" Özel Biçim Belirtici](#mmSpecifier).|2009-06-15T01:09:30 -> 09<br /><br /> 2009-06-15T01:45:30 -> 45|
|"M"|Ay, 1 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["M" Özel Biçim Belirtimi.](#M_Specifier)|2009-06-15T13:45:30 -> 6|
|"AA"|Ay, 01 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["MM" Özel Biçim Belirtimi.](#MM_Specifier)|2009-06-15T13:45:30 -> 06|
|"AAA"|Ayın kısaltılmış adı.<br /><br /> Daha fazla bilgi: ["MMM" Özel Biçim Belirtimi.](#MMM_Specifier)|2009-06-15T13:45:30 -> Haz (tr-ABD)<br /><br /> 2009-06-15T13:45:30 -> juin (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> Haz (zu-ZA)|
|"AAAA"|Ayın tam adı.<br /><br /> Daha fazla bilgi: ["MMMM" Özel Biçim Belirtimi.](#MMMM_Specifier)|2009-06-15T13:45:30 -> Haziran (tr-ABD)<br /><br /> 2009-06-15T13:45:30 -> juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> uJuni (zu-ZA)|
|"s"|Saniye, 0'dan 59'a kadardır.<br /><br /> Daha fazla bilgi: ["s" Özel Biçim Belirtimi.](#sSpecifier)|2009-06-15T13:45:09 -> 9|
|"ss"|Saniye, 00'dan 59'a kadardır.<br /><br /> Daha fazla bilgi: ["ss" Özel Biçim Belirtimi.](#ssSpecifier)|2009-06-15T13:45:09 -> 09|
|"t"|AM/PM göstergesinin ilk karakteri.<br /><br /> Daha fazla bilgi: ["t" Özel Biçim Belirtimi.](#tSpecifier)|2009-06-15T13:45:30 -> P (tr-ABD)<br /><br /> 2009-06-15T13:45:30 -> (ja-JP)<br /><br /> 2009-06-15T13:45:30 -> (fr-FR)|
|"tt"|AM/PM göstergesi.<br /><br /> Daha fazla bilgi: ["tt" Özel Biçim Belirtimi.](#ttSpecifier)|2009-06-15T13:45:30 -> PM (tr-ABD)<br /><br /> 2009-06-15T13:45:30 -> (ja-JP)<br /><br /> 2009-06-15T13:45:30 -> (fr-FR)|
|"y"|0 dan 99 'a kadar yıl.<br /><br /> Daha fazla bilgi: ["y" Özel Biçim Belirtimi.](#ySpecifier)|0001-01-01T00:00:00 -> 1<br /><br /> 0900-01-01T00:00:00 -> 0<br /><br /> 1900-01-01T00:00:00 -> 0<br /><br /> 2009-06-15T13:45:30 -> 9<br /><br /> 2019-06-15T13:45:30 -> 19|
|"yy"|00 dan 99 'a kadar yıl.<br /><br /> Daha fazla bilgi: ["yy" Özel Biçim Belirtimi.](#yySpecifier)|0001-01-01T00:00:00 -> 01<br /><br /> 0900-01-01T00:00:00 -> 00<br /><br /> 1900-01-01T00:00:00 -> 00<br /><br /> 2019-06-15T13:45:30 -> 19|
|"yyy"|En az üç basamaklı olarak yıl.<br /><br /> Daha fazla bilgi: ["yyy" Özel Biçim Belirtimi](#yyySpecifier).|0001-01-01T00:00:00 -> 001<br /><br /> 0900-01-01T00:00:00 -> 900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -> 2009|
|"yyyy"|Dört basamaklı bir sayı olarak yıl.<br /><br /> Daha fazla bilgi: ["yyyy" Özel Biçim Belirtimi.](#yyyySpecifier)|0001-01-01T00:00:00 -> 0001<br /><br /> 0900-01-01T00:00:00 -> 0900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -> 2009|
|"yyyyy"|Beş basamaklı bir sayı olarak yıl.<br /><br /> Daha fazla bilgi: ["yyyyy" Özel Biçim Belirtimi](#yyyyySpecifier).|0001-01-01T00:00:00 -> 00001<br /><br /> 2009-06-15T13:45:30 -> 02009|
|"z"|Önünde sıfır olmadan UTC biçiminden saat uzaklığı.<br /><br /> Daha fazla bilgi: ["z" Özel Biçim Belirtimi.](#zSpecifier)|2009-06-15T13:45:30-07:00 -> -7|
|"zz"|Önünde sıfır bulunan tek basamaklı değerden oluşan UTC biçiminden saat uzaklığı.<br /><br /> Daha fazla bilgi: ["zz" Özel Biçim Belirtimi](#zzSpecifier).|2009-06-15T13:45:30-07:00 -> -07|
|"zzz"|UTC biçiminden saat ve dakika uzaklığı.<br /><br /> Daha fazla bilgi: ["zzz" Özel Biçim Belirtimi.](#zzzSpecifier)|2009-06-15T13:45:30-07:00 -> -07:00|
|":"|Zaman ayırıcı.<br /><br /> Daha fazla bilgi: [The ":" Özel Biçim Belirtici](#timeSeparator).|2009-06-15T13:45:30 -> : (tr-ABD)<br /><br /> 2009-06-15T13:45:30 -> . (it-IT)<br /><br /> 2009-06-15T13:45:30 -> : (ja-JP)|
|"/"|Tarih ayırıcı.<br /><br /> Daha fazla bilgi: ["/" Özel Biçim Belirtici](#dateSeparator).|2009-06-15T13:45:30 -> / (tr-ABD)<br /><br /> 2009-06-15T13:45:30 -> - (ar-DZ)<br /><br /> 2009-06-15T13:45:30 -> . (tr-TR)|
|"*dize*"<br /><br /> '*dize*'|Değişmez dize sınırlayıcısı.<br /><br /> Daha fazla bilgi: [Karakter literals](#Literals).|2009-06-15T13:45:30 ("arr:" h:m t) -> arr: 1:45 P<br /><br /> 2009-06-15T13:45:30 ('arr:' h:m t) -> arr: 1:45 P|
|%|Aşağıdaki karakteri özel biçim belirticisi olarak tanımlar.<br /><br /> Daha fazla bilgi:[Tek Özel Biçim Belirteci Kullanma.](#UsingSingleSpecifiers)|2009-06-15T13:45:30 (%h) -> 1|
|&#92;|"\" çıkış karakteri.<br /><br /> Daha fazla bilgi: [Karakter literals](#Literals) ve [Escape Karakter kullanma](#escape).|2009-06-15T13:45:30 (h \h) -> 1 saat|
|Başka bir karakter|Karakter, değişmeyen sonuç dizesine kopyalanır.<br /><br /> Daha fazla bilgi: [Karakter literals](#Literals).|2009-06-15T01:45:30 (arr hh:mm t) -> arr 01:45 A|

Aşağıdaki bölümlerde, her özel tarih ve saat biçim belirticisi hakkında ek bilgi sağlanır. Aksi belirtilmedikçe, her belirtici bir değer veya bir <xref:System.DateTime> <xref:System.DateTimeOffset> değer ile kullanılan olup olmadığına bakılmaksızın aynı dize gösterimi üretir.

## <a name="dSpecifier"></a>"d" özel biçim belirtimi

"d" özel biçim belirticisi, 1 ile 31 arasında bir sayı olarak ayın gününü temsil eder. Tek basamaklı gün önünde sıfır olmadan biçimlendirilir.

"D" biçimi belirtileyicisi diğer özel biçim belirteçleri olmadan kullanılırsa, "d" standart tarih ve saat biçimi belirtimi olarak yorumlanır. Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

Aşağıdaki örnek birçok biçim dizesinde "d" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#1)]
[!code-vb[Formatting.DateAndTime.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#1)]

[Tabloya geri dön](#table)

## <a name="ddSpecifier"></a>"dd" özel biçim belirtimi

"dd" özel biçim dizesi, 01 ile 31 arasında bir sayı olarak ayın gününü temsil eder. Tek basamaklı gün önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "dd" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Tabloya geri dön](#table)

## <a name="dddSpecifier"></a>"ddd" özel biçim belirtimi

"ddd" özel biçim belirticisi haftanın gününün kısaltılmış adını temsil eder. Haftanın yerelleştirilmiş kısaltılmış adı, geçerli veya belirtilen <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A?displayProperty=nameWithType> kültürün özelliğinden alınır.

Aşağıdaki örnek bir özel biçim dizesinde "ddd" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Tabloya geri dön](#table)

## <a name="ddddSpecifier"></a>"dddd" özel biçim belirtimi

"dddd" özel biçim belirticisi (artı herhangi bir sayıda ek "d" tanımlayıcısı) haftanın gününün tam adını temsil eder. Haftanın yerelleştirilmiş adı, geçerli veya belirtilen <xref:System.Globalization.DateTimeFormatInfo.DayNames%2A?displayProperty=nameWithType> kültürün özelliğinden alınır.

Aşağıdaki örnek bir özel biçim dizesinde "dddd" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Tabloya geri dön](#table)

## <a name="fSpecifier"></a>"f" özel biçim belirtimi

"f" özel biçim belirticisi saniye bölümünün en önemli basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin onda birini temsil eder.

"F" biçimi belirtileyicisi diğer biçim belirteçleri olmadan kullanılırsa, "f" standart tarih ve saat biçimi belirtileyicisi olarak yorumlanır. Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

"F" <xref:System.DateTime.ParseExact%2A>biçimi belirteçlerini, bir <xref:System.DateTime.TryParseExact%2A> <xref:System.DateTimeOffset.ParseExact%2A> <xref:System.DateTimeOffset.TryParseExact%2A> biçim dizesine verilen biçim dizesinin bir parçası olarak kullandığınızda, "f" biçimi belirtiçlerinin sayısı, dizeyi başarıyla ayrıştırmak için bulunması gereken saniye kesrisinin en önemli basamak sayısını gösterir.

Aşağıdaki örnek bir özel biçim dizesinde "f" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya geri dön](#table)

## <a name="ffSpecifier"></a>"ff" özel biçim belirtimi

"ff" özel biçim belirticisi saniye bölümünün en önemli iki basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüzde birini temsil eder.

Aşağıdaki örnek, özel biçim dizesindeki "ff" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya geri dön](#table)

## <a name="fffSpecifier"></a>"fff" özel biçim belirtimi

"fff" özel biçim belirticisi saniye bölümünün en önemli üç basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin binde birini temsil eder.

Aşağıdaki örnek bir özel biçim dizesinde "fff" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya geri dön](#table)

## <a name="ffffSpecifier"></a>"Ffff" özel biçim belirtimi

"ffff" özel biçim belirticisi saniye bölümünün en önemli dört basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on binde birini temsil eder.

Bir zaman değerinin ikinci bileşeninin on binde birini görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 sürümünde (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya geri dön](#table)

## <a name="fffffSpecifier"></a>"fffff" özel biçim belirtimi

"fffff" özel biçim belirticisi saniye bölümünün en önemli beş basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüz binde birini temsil eder.

Bir zaman değerinin ikinci bileşeninin yüz binde birini görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya geri dön](#table)

## <a name="ffffffSpecifier"></a>"ffffff" özel biçim belirtimi

"ffffff" özel biçim belirticisi saniye bölümünün en önemli altı basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin milyonda birini temsil eder.

Bir zaman değerinin ikinci bileşeninin milyonda birini görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya geri dön](#table)

## <a name="fffffffSpecifier"></a>"Fffffff" özel biçim belirtimi

"fffffff" özel biçim belirticisi saniye bölümünün en önemli yedi basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on milyonda birini temsil eder.

Bir zaman değerinin ikinci bileşeninin on milyonda birini görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya geri dön](#table)

## <a name="F_Specifier"></a>"F" özel biçim belirtimi

"F" özel biçim belirticisi saniye bölümünün en önemli basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin onda birini temsil eder. Basamak sıfırsa hiçbir şey görüntülenmez.

"F" biçimi belirtileyicisi diğer biçim belirteçleri olmadan kullanılırsa, "F" standart tarih ve saat biçimi belirtileyicisi olarak yorumlanır. Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

"F" biçimi belirteçlerinin <xref:System.DateTime.ParseExact%2A>sayısı, <xref:System.DateTime.TryParseExact%2A> <xref:System.DateTimeOffset.ParseExact%2A> <xref:System.DateTimeOffset.TryParseExact%2A> dizeyi başarıyla ayrıştırmak için mevcut olabilecek saniye kesrinin en önemli basamaklarının en büyük sayısını gösterir.

Aşağıdaki örnek bir özel biçim dizesinde "F" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya geri dön](#table)

## <a name="FF_Specifier"></a>"FF" özel biçim belirtimi

"FF" özel biçim belirticisi saniye bölümünün en önemli iki basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüzde birini temsil eder. Ancak, sondaki sıfırlar veya iki sıfır basamağı görüntülenmez.

Aşağıdaki örnek bir özel biçim dizesinde "FF" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya geri dön](#table)

## <a name="FFF_Specifier"></a>"FFF" özel biçim belirtimi

"FFF" özel biçim belirticisi saniye bölümünün en önemli üç basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin binde birini temsil eder. Ancak, sondaki sıfırlar veya üç sıfır basamağı görüntülenmez.

Aşağıdaki örnek bir özel biçim dizesinde "FFF" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya geri dön](#table)

## <a name="FFFF_Specifier"></a>"FFFF" özel biçim belirtimi

"FFFF" özel biçim belirticisi saniye bölümünün en önemli dört basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on binde birini temsil eder. Ancak, sondaki sıfırlar veya dört sıfır basamağı görüntülenmez.

Bir zaman değerinin ikinci bileşeninin on binde birini görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya geri dön](#table)

## <a name="FFFFF_Specifier"></a>"FFFFF" özel biçim belirtimi

"FFFFF" özel biçim belirticisi saniye bölümünün en önemli beş basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüz binde birini temsil eder. Ancak, sondaki sıfırlar veya beş sıfır basamağı görüntülenmez.

Bir zaman değerinin ikinci bileşeninin yüz binde birini görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya geri dön](#table)

## <a name="FFFFFF_Specifier"></a>"FFFFFF" özel biçim belirtimi

"FFFFFF" özel biçim belirticisi saniye bölümünün en önemli altı basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin milyonda birini temsil eder. Ancak, sondaki sıfırlar veya altı sıfır basamağı görüntülenmez.

Bir zaman değerinin ikinci bileşeninin milyonda birini görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya geri dön](#table)

## <a name="FFFFFFF_Specifier"></a>"FFFFFFF" özel biçim belirtimi

"FFFFFFF" özel biçim belirticisi saniye bölümünün en önemli yedi basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on milyonda birini temsil eder. Ancak, sondaki sıfırlar veya yedi sıfır basamağı görüntülenmez.

Bir zaman değerinin ikinci bileşeninin on milyonda birini görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya geri dön](#table)

## <a name="gSpecifier"></a>"g" veya "gg" özel biçim belirtimi

"g" veya "gg" özel biçim belirticileri (artı herhangi bir sayıda ek "g" belirticisi) M.S. gibi bir dönem veya çağı temsil eder Biçimlendirilecek tarih ilişkili bir dönem veya dönem dizesi yoksa biçimlendirme işlemi bu belirticiyi yok sayar.

"g" biçimi belirtileyicisi diğer özel biçim belirteçleri olmadan kullanılırsa, "g" standart tarih ve saat biçimi belirtimi olarak yorumlanır. Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

Aşağıdaki örnek bir özel biçim dizesinde "g" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#6)]
[!code-vb[Formatting.DateAndTime.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#6)]

[Tabloya geri dön](#table)

## <a name="hSpecifier"></a>"h" özel biçim belirtimi

"h" özel biçim belirticisi 1 ile 12 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, saatleri gece yarısından veya öğleden itibaren tam saatleri sayan 12 saatlik zaman biçimi ile temsil edilir. Gece yarısından sonraki bir saat, öğleden sonraki aynı saatle ayırt edilemez. Saat yuvarlanmaz ve önünde sıfır olmadan tek basamaklı bir saat biçimlendirilir. Örneğin, sabah veya öğleden sonra 5:43 saati verildiğinde bu özel biçim belirtici "5" görüntüler.

"H" biçimi belirtileyicisi diğer özel biçim belirteçleri olmadan kullanılırsa, standart bir tarih ve saat <xref:System.FormatException>biçimi belirtimi olarak yorumlanır ve bir . Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

Aşağıdaki örnek bir özel biçim dizesinde "h" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Tabloya geri dön](#table)

## <a name="hhSpecifier"></a>"hh" özel biçim belirtimi

"hh" özel biçim belirticisi (artı herhangi bir sayıda ek "h" belirticisi) 01 ile 12 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, tam saatleri gece yarısından veya öğleden itibaren sayan 12 saatlik zaman biçimi ile temsil edilir. Gece yarısından sonraki bir saat, öğleden sonraki aynı saatle ayırt edilemez. Saat yuvarlanmaz ve önünde sıfır ile birlikte tek basamaklı bir saat biçimlendirilir. Örneğin, sabah veya öğleden sonra 5:43 saati verildiğinde bu biçim belirtici "05" görüntüler.

Aşağıdaki örnek bir özel biçim dizesinde "hh" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Tabloya geri dön](#table)

## <a name="H_Specifier"></a>"H" özel biçim belirtimi

"H" özel biçim belirticisi 0 ile 23 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, saatleri gece yarısından itibaren sayan sıfır tabanlı bir 24 saatlik zaman biçimi ile temsil edilir. Tek basamaklı saat önünde sıfır olmadan biçimlendirilir.

"H" biçimi belirtileyicisi diğer özel biçim belirteçleri olmadan kullanılırsa, standart bir tarih ve saat <xref:System.FormatException>biçimi belirtimi olarak yorumlanır ve bir . Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

Aşağıdaki örnek bir özel biçim dizesinde "H" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#9)]
[!code-vb[Formatting.DateAndTime.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#9)]

[Tabloya geri dön](#table)

## <a name="HH_Specifier"></a>"HH" özel biçim belirtimi

"HH" özel biçim belirticisi (artı herhangi bir sayıda ek "H" belirticisi) 00 ile 23 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, saatleri gece yarısından itibaren sayan sıfır tabanlı bir 24 saatlik zaman biçimi ile temsil edilir. Tek basamaklı saat önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "HH" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#10)]
[!code-vb[Formatting.DateAndTime.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#10)]

[Tabloya geri dön](#table)

## <a name="KSpecifier"></a>"K" özel biçim belirtimi

"K" özel biçim belirticisi bir tarih ve saat değerinin saat dilimi bilgisini temsil eder. Bu biçim belirtici değerleri <xref:System.DateTime> ile kullanıldığında, sonuç dizesi <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliğin değeri ile tanımlanır:

- Yerel saat dilimi (bir <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> <xref:System.DateTimeKind.Local?displayProperty=nameWithType>özellik değeri) için, bu belirtitanımlayıcı "zzz" belirticieşdeğerdir ve Koordine Evrensel Zaman (UTC) yerel ofset içeren bir sonuç dizesi üretir; örneğin, "-07:00".

- UTC zamanı (özellik <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>değeri) için sonuç dizesi, UTC tarihini temsil edecek bir "Z" karakteri içerir.

- Belirtilmemiş bir saat diliminden (özelliği <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> eşit olan <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>bir zaman) <xref:System.String.Empty?displayProperty=nameWithType>bir süre için sonuç .

Değerler <xref:System.DateTimeOffset> için "K" biçim belirtici "zzz" biçim belirticisine eşdeğerdir ve UTC'den gelen değerin mahsupını <xref:System.DateTimeOffset> içeren bir sonuç dizesi üretir.

"K" biçimi belirtileyicisi diğer özel biçim belirteçleri olmadan kullanılırsa, standart bir tarih ve saat <xref:System.FormatException>biçimi belirtimi olarak yorumlanır ve bir . Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

Aşağıdaki örnek, "K" özel biçim belirticisini ABD Pasifik <xref:System.DateTime> Saat <xref:System.DateTimeOffset> dilimindeki bir sistemde çeşitli ve değerlerle birlikte kullanmanın sonucu olan dizeyi görüntüler.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#12)]
[!code-vb[Formatting.DateAndTime.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#12)]

[Tabloya geri dön](#table)

## <a name="mSpecifier"></a>"m" özel biçim belirtimi

"m" özel biçim belirticisi, 0 ile 59 arasında bir sayı olarak dakikayı temsil eder. Dakika, son saatten beri geçen tam dakikaları temsil eder. Tek basamaklı dakika önünde sıfır olmadan biçimlendirilir.

"m" biçimi belirtileyicisi diğer özel biçim belirteçleri olmadan kullanılırsa, "m" standart tarih ve saat biçimi belirtimi olarak yorumlanır. Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

Aşağıdaki örnek bir özel biçim dizesinde "m" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Tabloya geri dön](#table)

## <a name="mmSpecifier"></a>"mm" özel biçim belirtimi

"m" özel biçim belirticisi (artı herhangi bir sayıda ek "m" belirticisi) 00 ile 59 arasında bir sayı olarak dakikayı temsil eder. Dakika, son saatten beri geçen tam dakikaları temsil eder. Tek basamaklı dakika önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "mm" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Tabloya geri dön](#table)

## <a name="M_Specifier"></a>"M" özel biçim belirtimi

"M" özel biçim belirticisi, 1 ile 12 arasında (veya 13 ay içeren takvimler için 1 ile 13 arasında) bir sayı olarak ayı temsil eder. Tek basamaklı ay önünde sıfır olmadan biçimlendirilir.

"M" biçimi belirtileyicisi diğer özel biçim belirteçleri olmadan kullanılırsa, "M" standart tarih ve saat biçimi belirtimi olarak yorumlanır. Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

Aşağıdaki örnek bir özel biçim dizesinde "M" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#11)]
[!code-vb[Formatting.DateAndTime.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#11)]

[Tabloya geri dön](#table)

## <a name="MM_Specifier"></a>"MM" özel biçim belirtimi

"MM" özel biçim belirticisi, 01 ile 12 arasında (veya 13 ay içeren takvimler için 1 ile 13 arasında) bir sayı olarak ayı temsil eder. Tek basamaklı ay önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "MM" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Tabloya geri dön](#table)

## <a name="MMM_Specifier"></a>"MMM" özel biçim belirtimi

"MMM" özel biçim belirticisi ayın gününün kısaltılmış adını temsil eder. Ayın yerelleştirilmiş kısaltılmış adı, geçerli veya <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A?displayProperty=nameWithType> belirtilen kültürün özelliğinden alınır.

Aşağıdaki örnek bir özel biçim dizesinde "MMM" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Tabloya geri dön](#table)

## <a name="MMMM_Specifier"></a>"MMMM" özel biçim belirtimi

"MMMM" özel biçim belirticisi ayın gününün tam adını temsil eder. Ayın yerelleştirilmiş adı, geçerli veya <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> belirtilen kültürün özelliğinden alınır.

Aşağıdaki örnek bir özel biçim dizesinde "MMMM" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Tabloya geri dön](#table)

## <a name="sSpecifier"></a>"s" özel biçim belirtimi

"s" özel biçim belirticisi, 0 ile 59 arasında bir sayı olarak saniyeyi temsil eder. Sonuç, son dakikadan beri geçen tam saniyeleri temsil eder. Tek basamaklı saniye önünde sıfır olmadan biçimlendirilir.

"s" biçimi belirtileyicisi diğer özel biçim belirteçleri olmadan kullanılırsa, "s" standart tarih ve saat biçimi belirtimi olarak yorumlanır. Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

Aşağıdaki örnek bir özel biçim dizesinde "s" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Tabloya geri dön](#table)

## <a name="ssSpecifier"></a>"ss" özel biçim belirtimi

"ss" özel biçim belirticisi (artı herhangi bir sayıda ek "s" belirticisi) 00 ile 59 arasında bir sayı olarak saniyeyi temsil eder. Sonuç, son dakikadan beri geçen tam saniyeleri temsil eder. Tek basamaklı saniye önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "ss" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Tabloya geri dön](#table)

## <a name="tSpecifier"></a>"t" özel biçim belirtimi

"t" özel biçim belirticisi AM/PM göstergelerinin ilk karakterini temsil eder. Uygun yerelleştirilmiş atama, geçerli <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> veya belirli <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> kültürün özelliğinden veya özelliğinden alınır. AM göstergesi, 0:00:00 (gece yarısı) ile 11:59:59.999 arasındaki tüm zamanlar için kullanılır. PM göstergesi, 12:00:00 (öğlen) ile 23:59:59.999 arasındaki tüm zamanlar için kullanılır.

"t" biçimi belirtileyicisi diğer özel biçim belirteçleri olmadan kullanılırsa, "t" standart tarih ve saat biçimi belirtileyicisi olarak yorumlanır. Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

Aşağıdaki örnek bir özel biçim dizesinde "t" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Tabloya geri dön](#table)

## <a name="ttSpecifier"></a>"tt" özel biçim belirtimi

"tt" özel biçim belirticisi (artı herhangi bir sayıda ek "t" belirticisi) tüm AM/PM göstergelerini temsil eder. Uygun yerelleştirilmiş atama, geçerli <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> veya belirli <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> kültürün özelliğinden veya özelliğinden alınır. AM göstergesi, 0:00:00 (gece yarısı) ile 11:59:59.999 arasındaki tüm zamanlar için kullanılır. PM göstergesi, 12:00:00 (öğlen) ile 23:59:59.999 arasındaki tüm zamanlar için kullanılır.

ve PM arasındaki ayrımı korumak için gerekli olan diller için tt belirticisini kullandığınızdan emin olun. Japonca buna bir örnektir; AM ve PM göstergeleri birinci karakter yerine ikinci karakterde farklılık gösterir.

Aşağıdaki örnek bir özel biçim dizesinde "tt" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Tabloya geri dön](#table)

## <a name="ySpecifier"></a>"Y" özel biçim belirtimi

"y" özel biçim belirticisi tek basamaklı veya iki basamaklı bir sayı olarak yılı temsil eder. Yılda ikiden fazla basamak varsa, yalnızca son kısımdaki iki basamak sonuçta görünür. İki basamaklı yılın ilk basamağı sıfır ise (örneğin, 2008), sayı önünde sıfır olmadan biçimlendirilir.

"Y" biçimi belirtileyicisi diğer özel biçim belirteçleri olmadan kullanılırsa, "y" standart tarih ve saat biçimi belirtimi olarak yorumlanır. Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

Aşağıdaki örnek bir özel biçim dizesinde "y" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya geri dön](#table)

## <a name="yySpecifier"></a>"yy" özel biçim belirtimi

"yy" özel biçim belirticisi iki basamaklı bir sayı olarak yılı temsil eder. Yılda ikiden fazla basamak varsa, yalnızca son kısımdaki iki basamak sonuçta görünür. İki basamaklı yılda ikiden az belirtici basamak varsa, iki basamak oluşturulabilmesi için sayının önüne sıfır eklenir.

Ayrıştırma işleminde, "yy" özel biçim belirticisi kullanılarak ayrıştırılan iki basamaklı bir <xref:System.Globalization.Calendar.TwoDigitYearMax%2A?displayProperty=nameWithType> yıl, biçim sağlayıcısının geçerli takviminin özelliğine göre yorumlanır. Aşağıdaki örnek, bu durumda en-US kültürü olan geçerli kültürün varsayılan Gregoryen takvimini kullanarak iki basamaklı yıl içeren bir tarih dize gösterimini ayrıştırır. Daha sonra, <xref:System.Globalization.CultureInfo> <xref:System.Globalization.GregorianCalendar> <xref:System.Globalization.GregorianCalendar.TwoDigitYearMax%2A> özelliği değiştirilmiş bir nesneyi kullanmak için geçerli kültürün nesnesini değiştirir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/parseexact2digityear1.cs#19)]
[!code-vb[Formatting.DateAndTime.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/parseexact2digityear1.vb#19)]

Aşağıdaki örnek bir özel biçim dizesinde "yy" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya geri dön](#table)

## <a name="yyySpecifier"></a>"yyy" özel biçim belirtimi

"yyy" özel biçim belirticisi en az üç basamakla yılı temsil eder. Yılda üçten fazla belirtici basamak varsa, bunlar sonuç dizesine eklenir. Yıl üçten az basamaktan oluşuyorsa, üç basamak oluşturulabilmesi için sayının önüne sıfır eklenir.

> [!NOTE]
> Beş basamaklı yıllar içeren Thai Budist takvimi için bu biçim belirtici tüm basamakları görüntüler.

Aşağıdaki örnek bir özel biçim dizesinde "yyy" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya geri dön](#table)

## <a name="yyyySpecifier"></a>"Yyyy" özel biçim belirtimi

"yyyy" özel biçim belirticisi en az dört basamakla yılı temsil eder. Yılda dörtten fazla belirtici basamak varsa, bunlar sonuç dizesine eklenir. Yıl dörtten az basamaktan oluşuyorsa, dört basamak oluşturulabilmesi için sayının önüne sıfır eklenir.

> [!NOTE]
> Beş basamaklı yıllar içeren Thai Budist takvimi için bu biçim belirtici en az dört basamak görüntüler.

Aşağıdaki örnek bir özel biçim dizesinde "yyyy" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya geri dön](#table)

## <a name="yyyyySpecifier"></a>"Yyyy" özel biçim belirtimi

"yyyyy" özel biçim belirticisi (artı herhangi bir sayıda ek "y" belirticisi) en az beş basamakla yılı temsil eder. Yılda beşten fazla belirtici basamak varsa, bunlar sonuç dizesine eklenir. Yıl beşten az basamaktan oluşuyorsa, beş basamak oluşturulabilmesi için sayının önüne sıfır eklenir.

Ek "y" belirticileri varsa sayının önüne "y" belirticileriyle aynı sayıda olacak kadar sıfır eklenir.

Aşağıdaki örnek bir özel biçim dizesinde "yyyyy" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya geri dön](#table)

## <a name="zSpecifier"></a>"z" özel biçim belirtimi

Değerlerle <xref:System.DateTime> birlikte, "z" özel biçim belirtimi, yerel işletim sisteminin saat diliminin saat cinsinden ölçülen Eşgüdümlü Evrensel Zaman (UTC) tarafından imzalanmış mahsup undan temsil eder. Bir örneğin <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliğinin değerini yansıtmaz. Bu nedenle, "z" biçim belirticisi değerleri ile <xref:System.DateTime> kullanmak için tavsiye edilmez.

Değerlerle, <xref:System.DateTimeOffset> bu biçim belirtimi, değerin UTC'den saat içinde mahsup edilen <xref:System.DateTimeOffset> değeri temsil eder.

Uzaklık her zaman önünde bir işaretle görüntülenir. Artı işareti (+) UTC'den önceki saatleri belirtir, eksi işareti (-) UTC'den sonraki saatleri belirtir. Tek basamaklı sapma önünde sıfır olmadan biçimlendirilir.

"z" biçimi belirtileyicisi diğer özel biçim belirteçleri olmadan kullanılırsa, standart bir tarih ve saat <xref:System.FormatException>biçimi belirtimi olarak yorumlanır ve bir . Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

Aşağıdaki örnek bir özel biçim dizesinde "z" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Tabloya geri dön](#table)

## <a name="zzSpecifier"></a>"zz" özel biçim belirtimi

Değerlerle <xref:System.DateTime> birlikte, "zz" özel biçim belirtimi, yerel işletim sisteminin saat diliminin UTC'den saat cinsinden ölçülen imzalı mahsupını temsil eder. Bir örneğin <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliğinin değerini yansıtmaz. Bu nedenle, "zz" biçim belirticisi değerleri ile <xref:System.DateTime> kullanmak için tavsiye edilmez.

Değerlerle, <xref:System.DateTimeOffset> bu biçim belirtimi, değerin UTC'den saat içinde mahsup edilen <xref:System.DateTimeOffset> değeri temsil eder.

Uzaklık her zaman önünde bir işaretle görüntülenir. Artı işareti (+) UTC'den önceki saatleri belirtir, eksi işareti (-) UTC'den sonraki saatleri belirtir. Tek basamaklı sapma önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "zz" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Tabloya geri dön](#table)

## <a name="zzzSpecifier"></a>"zzz" özel biçim belirtimi

Değerlerle <xref:System.DateTime> birlikte, "zzz" özel biçim belirtimi, yerel işletim sisteminin saat diliminin UTC'den saat ve dakika cinsinden ölçülen imzalı mahsupını temsil eder. Bir örneğin <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliğinin değerini yansıtmaz. Bu nedenle, "zzz" biçim belirticisi değerleri ile <xref:System.DateTime> kullanmak için tavsiye edilmez.

Değerlerle, <xref:System.DateTimeOffset> bu biçim belirtimi, değerin <xref:System.DateTimeOffset> UTC'den saat ve dakika olarak mahsup edilen değeri temsil eder.

Uzaklık her zaman önünde bir işaretle görüntülenir. Artı işareti (+) UTC'den önceki saatleri belirtir, eksi işareti (-) UTC'den sonraki saatleri belirtir. Tek basamaklı sapma önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "zzz" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Tabloya geri dön](#table)

## <a name="timeSeparator"></a>":" özel biçim belirtimi
":" özel biçim belirticisi, saat, dakika ve saniyeyi ayırt etmek için kullanılan zaman ayırıcıyı temsil eder. Uygun yerelleştirilmiş zaman ayırıcısı, <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> geçerli veya belirtilen kültürün özelliğinden alınır.

> [!NOTE]
> Belirli bir tarih ve saat dizesinin zaman ayırıcısını değiştirmek için, ayırıcı karakteri gerçek bir dize sınırlayıcı içinde belirtin. Örneğin, özel biçim `hh'_'dd'_'ss` dizesi, "\_( alt skorun) her zaman zaman ayırıcısı olarak kullanıldığı bir sonuç dizesi üretir. Bir kültürün tüm tarihleri için zaman ayırıcısını değiştirmek için, geçerli <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> kültürün özelliğinin değerini değiştirin veya bir <xref:System.Globalization.DateTimeFormatInfo> nesneyi <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A> anında atayın, karakteri özelliğine atayın <xref:System.IFormatProvider> ve parametre içeren biçimlendirme yönteminin aşırı yüklenmesini çağırın.

":" format belirtileyicisi diğer özel biçim belirteçleri olmadan kullanılırsa, standart bir tarih ve saat <xref:System.FormatException>biçimi belirtimi olarak yorumlanır ve bir . Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

[Tabloya geri dön](#table)

## <a name="dateSeparator"></a>"/" özel biçim belirtimi

"/" özel biçim belirticisi, yıl, ay ve günü ayırt etmek için kullanılan tarih ayırıcıyı temsil eder. Uygun yerelleştirilmiş tarih ayırıcısı, <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> geçerli veya belirtilen kültürün özelliğinden alınır.

> [!NOTE]
> Belirli bir tarih ve saat dizesinin tarih ayırıcısını değiştirmek için, ayırıcı karakteri gerçek bir dize sınırlayıcı içinde belirtin. Örneğin, özel biçim `mm'/'dd'/'yyyy` dizesi, "/" her zaman tarih ayırıcısı olarak kullanılan bir sonuç dizesi üretir. Bir kültürün tüm tarihlerinin tarih ayırıcısını değiştirmek için, <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> geçerli kültürün özelliğinin değerini değiştirin <xref:System.Globalization.DateTimeFormatInfo> veya bir nesneyi <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A> anında atayın, karakteri özelliğine atayın ve <xref:System.IFormatProvider> parametre içeren biçimlendirme yönteminin aşırı yüklenmesini çağırın.

"/" biçim belirtileyicisi diğer özel biçim belirteçleri olmadan kullanılırsa, standart bir tarih ve saat <xref:System.FormatException>biçimi belirtimi olarak yorumlanır ve bir . Tek bir biçim belirtici kullanma hakkında daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Tek Özel Biçim Belirteçleri Kullanma'ya](#UsingSingleSpecifiers) bakın.

[Tabloya geri dön](#table)

## <a name="Literals"></a>Karakter literals

Özel tarih ve saat biçimi dizesinde aşağıdaki karakterler ayrılmıştır ve her zaman biçimlendirme karakterleri olarak veya ", ', /, ve \\, özel karakterler olarak" durumunda yorumlanır.

||||||
|-|-|-|-|-|
|F|H|K|M|d|
|f|g|h|m|s|
|t|y|z|%|:|
|/|"|'|&#92;||

Diğer tüm karakterler her zaman karakter gerçek olarak yorumlanır ve bir biçimlendirme işleminde, sonuç dizesinde değişmeden eklenir.  Ayrıştma işleminde, giriş dizesindeki karakterleri tam olarak eşleştirmeleri gerekir; karşılaştırma büyük/küçük harf duyarlıdır.

Aşağıdaki örnek, yerel saat dilimini biçimlendirme dizesinde temsil etmek üzere "PST" (Pasifik Standart Saati için) ve "PDT" (Pasifik Gün Işığı Saati için) karakterlerini içerir. Dize sonuç dizesi dahil olduğunu ve yerel saat dilimi dizesini içeren bir dize de başarıyla parses olduğunu unutmayın.

[!code-csharp[Formatting.DateAndTime.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx1.cs#20)]
[!code-vb[Formatting.DateAndTime.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx1.vb#20)]

Karakterlerin yedek karakter olarak değil, gerçek karakterler olarak yorumlanabileceğini göstermenin iki yolu vardır, böylece bir sonuç dizesi içinde dahil edilebilir ler veya bir giriş dizesi içinde başarılı bir şekilde ayrıştılar:

- Her ayrılmış karakter kaçarak. Daha fazla bilgi için [Escape Karakterini Kullanma'ya](#escape)bakın.

Aşağıdaki örnek, yerel saat dilimini biçimlendirme dizesinde temsil etmek için "pst" (Pasifik Standart saati için) gerçek karakterlerini içerir. Hem "s" hem de "t" özel biçim dizeleri olduğundan, karakter gerçek olarak yorumlanabilmesi için her iki karakterin de kaçabilmesi gerekir.

[!code-csharp[Formatting.DateAndTime.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx2.cs#21)]
[!code-vb[Formatting.DateAndTime.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx2.vb#21)]

- Tüm edebi dizeyi tırnak işaretlerine veya kesitlere ekleyerek. Aşağıdaki örnek, "pst"nin tüm sınırlı dize karakter literals olarak yorumlanması gerektiğini belirtmek için tırnak işaretleri eklenmiş olması dışında, bir önceki gibidir.

[!code-csharp[Formatting.DateAndTime.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx3.cs#22)]
[!code-vb[Formatting.DateAndTime.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx3.vb#22)]

## <a name="notes"></a>Notlar

### <a name="UsingSingleSpecifiers"></a>Tek özel biçim belirtecileri kullanma

Özel tarih ve saat biçimi dizesi iki veya daha fazla karakterden oluşur. Tarih ve saat biçimlendirme yöntemleri, herhangi tek karakterli dizeyi standart tarih ve saat biçim dizesi olarak yorumlar. Karakteri geçerli bir biçim belirtici olarak tanımıyorlarsa, bir <xref:System.FormatException>. Örneğin, yalnızca belirleyici "h" içeren bir biçim dizesi standart tarih ve saat biçimi dizesi olarak yorumlanır. Ancak, bu özel durumda, "h" standart tarih ve zaman biçimi belirtimi olmadığından bir özel durum atılır.

Bir biçim dizesinde tek belirleyici olarak özel tarih ve saat biçimi belirleyicilerinden birini kullanmak için ("d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" veya "/" özel biçim belirleyicisinin kendisi), belirleyiciden önce veya sonra bir boşluk bırakın veya tek özel tarih ve saat belirleyicisinden önce yüzde ("%") biçim belirleyicisi ekleyin.

Örneğin, "`%h"` geçerli tarih ve saat değeriyle temsil edilen saati görüntüleyen özel bir tarih ve saat biçimi dizesi olarak yorumlanır. Sonuç dizesinde saatin yanında bir boşluk içerse de " h" veya "h " biçimlendirme dizisini de kullanabilirsiniz. Aşağıdaki örnek bu üç biçim dizesini gösterir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/literal1.cs#16)]
[!code-vb[Formatting.DateAndTime.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/literal1.vb#16)]

### <a name="escape"></a>Kaçış Karakterini Kullanma

Bir biçim dizesindeki "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" veya "/" karakterleri, değişmez karakterler olarak değil özel biçim belirticileri olarak yorumlanır. Bir karakterin biçim belirtimi olarak yorumlanmasını önlemek için, bir ters çizgi\\( ), kaçış karakteri ile önce gelebilir. Çıkış karakteri, aşağıdaki karakterin değiştirilmeden sonuç dizesini dahil edilmesi gereken bir karakter sabiti olduğunu belirtir.

Bir sonuç dizesi bir backslash eklemek için, başka`\\`bir backslash ( ) ile kaçmak gerekir.

> [!NOTE]
> C++ ve C# derleyicileri gibi bazı derleyiciler, tek bir ters eğik çizgiyi çıkış karakteri olarak yorumlayabilir. Bir dizenin yalnızca düzgün biçimlendirildiğinde yorumlanmasını sağlamak için C# içinde dizeden önce değişmez değer karakterini (@ karakteri) kullanabilirsiniz veya C# ve C++ içinde her ters eğik çizgiden önce bir ters eğik çizgi daha ekleyebilirsiniz. Aşağıdaki C# örneği her iki yaklaşımı da gösterir.

Aşağıdaki örnek, biçimlendirme işleminin "h" ve "m" karakterlerini biçim belirticileri olarak yorumlamasını önlemek için çıkış karakteri kullanır.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/escape1.cs#15)]
[!code-vb[Formatting.DateAndTime.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/escape1.vb#15)]

### <a name="control-panel-settings"></a>Denetim Masası ayarları

Denetim Masası'ndaki **Bölgesel ve Dil Seçenekleri** ayarları, özel tarih ve saat biçimi belirticilerinin çoğunu içeren bir biçimlendirme işlemi tarafından üretilen sonuç dizesini etkiler. Bu ayarlar, biçimlendirmeyi <xref:System.Globalization.DateTimeFormatInfo> yönetmek için kullanılan değerleri sağlayan geçerli iş parçacığı kültürüyle ilişkili nesneyi başlatmaya kullanılır. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.

Ayrıca, <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> kurucuyu geçerli sistem kültürüyle aynı kültürü <xref:System.Globalization.CultureInfo> temsil eden yeni bir nesneyi anında kullanmak için kullanırsanız, Denetim Masası'ndaki Bölgesel ve Dil <xref:System.Globalization.CultureInfo> **Seçenekleri** öğesi tarafından oluşturulan özelleştirmeler yeni nesneye uygulanır. Oluşturucuyu, <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> sistemin özelleştirmelerini <xref:System.Globalization.CultureInfo> yansıtmayan bir nesne oluşturmak için kullanabilirsiniz.

### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo özellikleri

Biçimlendirme, geçerli iş parçacığı <xref:System.Globalization.DateTimeFormatInfo> kültürü tarafından dolaylı olarak sağlanan geçerli nesnenin özelliklerinden <xref:System.IFormatProvider> veya biçimlendirmeyi çağıran yöntemin parametresi tarafından açıkça etkilenir. <xref:System.IFormatProvider> Parametre için, bir kültürü <xref:System.Globalization.CultureInfo> veya nesneyi temsil eden <xref:System.Globalization.DateTimeFormatInfo> bir nesne belirtmeniz gerekir.

Özel tarih ve saat biçimi belirteçlerinin çoğu tarafından üretilen sonuç dizesi de geçerli <xref:System.Globalization.DateTimeFormatInfo> nesnenin özelliklerine bağlıdır. Uygulamanız, ilgili <xref:System.Globalization.DateTimeFormatInfo> özelliği değiştirerek bazı özel tarih ve saat biçimi belirteciler tarafından üretilen sonucu değiştirebilir. Örneğin, "ddd" biçim belirticisi, <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A> dize dizisinde bulunan kısaltılmış bir hafta içi adını sonuç dizesine ekler. Benzer şekilde, "MMMM" biçim belirtici sonuç dizesine <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A> dize dizisinde bulunan tam ay adı ekler.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Örnek: .NET Core WinForms Biçimlendirme Programı (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Örnek: .NET Core WinForms Biçimlendirme Programı (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
