---
title: Özel tarih ve saat biçim dizeleri - .NET
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90e9dbbd43751412c25dd5ca4dae2d503139db69
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64634546"
---
# <a name="custom-date-and-time-format-strings"></a>Özel tarih ve saat biçim dizeleri

Bir tarih ve saat biçimi dizesi metin olarak bildirimini tanımlar. bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> bir biçimlendirme işleminden kaynaklanan değeri. Ayrıca, dizeyi tarih ve saate başarılı bir şekilde dönüştürmek için bir ayrıştırma işleminde gerekli olan tarih ve saat değerinin bildirimini tanımlayabilir. Özel biçim dizesi, bir veya daha fazla özel tarih ve saat biçimi belirleyicisinden oluşur. Herhangi bir dize değil bir [standart tarih ve saat biçim dizesi](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) özel tarih ve saat biçimi dizesi olarak yorumlanır.

> [!TIP]
> İndirebileceğiniz [biçimlendirme yardımcı programı](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), biçim sağlayan bir uygulama dizeleri için tarih ve saat veya sayısal değerleri ve sonuç dizeyi görüntülemenizi.

Özel tarih ve saat biçim dizeleri ile her ikisini de kullanılabilir <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)] 

<a name="table"></a> Biçimlendirme işlemlerinde, özel tarih ve saat biçim dizeleri olabilir ile birlikte kullanılan `ToString` yöntemiyle veya bileşik biçimlendirmeyi destekleyen bir yöntemle bir tarih ve saat örneğinin. Aşağıdaki örnek her iki kullanımı da gösterir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandformatting1.cs#17)]
[!code-vb[Formatting.DateAndTime.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandformatting1.vb#17)]

Ayrıştırma işlemlerinde, özel tarih ve saat biçimlendirme dizeleri kullanılabilir <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, ve <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> yöntemleri. Bu yöntemler, bir Giriş dizesinin tam olarak ayrıştırma işleminin başarılı olması için belirli bir desene uygun olduğunu gerektirir. Aşağıdaki örnek bir çağrıyı gösterir <xref:System.DateTimeOffset.ParseExact%28System.String%2CSystem.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> gün, ay ve iki basamaklı bir yıl içermelidir bir tarihi ayrıştırmak için yöntemi.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandparsing1.cs#18)]
[!code-vb[Formatting.DateAndTime.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandparsing1.vb#18)]

Aşağıdaki tabloda özel tarih ve saat biçimi belirteçleri açıklanır ve her biçim belirticisi tarafından üretilen bir sonuç dizesini görüntülenir. Varsayılan olarak, sonuç dizeleri en-US kültürünün, biçimlendirme kurallarını yansıtır. Belirli bir biçim belirticisi yerelleştirilmiş bir sonuç dizesi üretirse örnek aynı zamanda sonuç dizesinin uygulanacağı kültürü de not alır. Özel tarih ve saat biçim dizeleri kullanma hakkında daha fazla bilgi için bkz. [notları](#notes) bölümü.

| Biçim belirteci | Açıklama | Örnekler |
| ---------------------- | ----------------- | -------------- |
|"d"|1 İle 31 arasında ayın günü.<br /><br /> Daha fazla bilgi: ["D" özel Biçim belirleyicisi](#dSpecifier).|2009-06-01T13:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 15|
|"dd"|01 İle 31 arasında ayın günü.<br /><br /> Daha fazla bilgi: ["Dd" özel Biçim belirleyicisi](#ddSpecifier).|2009-06-01T13:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 15|
|"ddd"|Haftanın günü, kısaltılmış adı.<br /><br /> Daha fazla bilgi: ["Ddd" özel Biçim belirleyicisi](#dddSpecifier).|2009-06-15T13:45:30 -> Pzt (en-US)<br /><br /> 2009-06-15T13:45:30 -> Пн (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lun. (fr-FR)|
|"dddd"|Haftanın gününün tam adı.<br /><br /> Daha fazla bilgi: ["Dddd" özel Biçim belirleyicisi](#ddddSpecifier).|2009-06-15T13:45:30 -> Pazartesi (en-US)<br /><br /> 2009-06-15T13:45:30 понедельник (ru-RU) -><br /><br /> 2009-06-15T13:45:30 -> lundi (fr-FR)|
|"f"|Saniyenin onda biri bir tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["F" özel Biçim belirleyicisi](#fSpecifier).|2009-06-15T13:45:30.6170000 -> 6<br /><br /> 2009-06-15T13:45:30.05 -> 0|
|"ff"|Tarih ve saat değerindeki saniyenin yüzde biri.<br /><br /> Daha fazla bilgi: ["Ff" özel Biçim belirleyicisi](#ffSpecifier).|2009-06-15T13:45:30.6170000 -> 61<br /><br /> 2009-06-15T13:45:30.0050000 -> 00|
|"fff"|Tarih ve saat değerindeki milisaniye.<br /><br /> Daha fazla bilgi: ["Fff" özel Biçim belirleyicisi](#fffSpecifier).|6/15/2009 13:45:30.617 -> 617<br /><br /> 6/15/2009 13:45:30.0005 -> 000|
|"ffff"|Saniyenin on binde birindeki tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["Ffff" özel Biçim belirleyicisi](#ffffSpecifier).|2009-06-15T13:45:30.6175000 -> 6175<br /><br /> 2009-06-15T13:45:30.0000500  -> 0000|
|"fffff"|Tarih ve saat değerindeki saniyenin yüz binde biri.<br /><br /> Daha fazla bilgi: ["Fffff" özel Biçim belirleyicisi](#fffffSpecifier).|2009-06-15T13:45:30.6175400 -> 61754<br /><br /> 6/15/2009 13:45:30.000005 -> 00000|
|"ffffff"|Tarih ve saat değerindeki saniyenin milyonda biri.<br /><br /> Daha fazla bilgi: ["Ffffff" özel Biçim belirleyicisi](#ffffffSpecifier).|2009-06-15T13:45:30.6175420 -> 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> 000000|
|"fffffff"|Saniyenin on milyonda birindeki tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["Fffffff" özel Biçim belirleyicisi](#fffffffSpecifier).|2009-06-15T13:45:30.6175425 -> 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -> 0001150|
|"F"|Sıfır olmayan, saniyenin onda biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["F" özel Biçim belirleyicisi](#F_Specifier).|2009-06-15T13:45:30.6170000 -> 6<br /><br /> 2009-06-15T13:45:30.0500000 (çıktı) ->|
|"FF"|Sıfır olmayan, saniyenin yüzde biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FF" özel Biçim belirleyicisi](#FF_Specifier).|2009-06-15T13:45:30.6170000 -> 61<br /><br /> 2009-06-15T13:45:30.0050000 (çıktı) ->|
|"FFF"|Sıfır olmayan, milisaniye cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFF" özel Biçim belirleyicisi](#FFF_Specifier).|2009-06-15T13:45:30.6170000 -> 617<br /><br /> 2009-06-15T13:45:30.0005000 (çıktı) ->|
|"FFFF"|Sıfır olmayan, saniyenin on binde biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFFF" özel Biçim belirleyicisi](#FFFF_Specifier).|2009-06-15T13:45:30.5275000 -> 5275<br /><br /> 2009-06-15T13:45:30.0000500 (çıktı) ->|
|"FFFFF"|Sıfır olmayan, saniyenin yüz binde biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFFFF" özel Biçim belirleyicisi](#FFFFF_Specifier).|2009-06-15T13:45:30.6175400 -> 61754<br /><br /> 2009-06-15T13:45:30.0000050 (çıktı) ->|
|"FFFFFF"|Sıfır olmayan, saniyenin milyonda birinde cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFFFFF" özel Biçim belirleyicisi](#FFFFFF_Specifier).|2009-06-15T13:45:30.6175420 -> 617542<br /><br /> 2009-06-15T13:45:30.0000005 (çıktı) ->|
|"FFFFFFF"|Sıfır olmayan, saniyenin on milyonda biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFFFFFF" özel Biçim belirleyicisi](#FFFFFFF_Specifier).|2009-06-15T13:45:30.6175425 -> 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -> 000115|
|"g", "gg"|Süre veya dönem.<br /><br /> Daha fazla bilgi: ["G" veya "gg" özel Biçim belirleyicisi](#gSpecifier).|2009-06-15T13:45:30.6170000 -> A.D.|
|"h"|Saat, 12 saatlik biçimde, 1 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["H" özel biçim belirticisi](#hSpecifier).|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 1|
|"hh"|Saat, 12 saatlik biçimde, 01 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["Hh" özel Biçim belirleyicisi](#hhSpecifier).|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 01|
|"H"|24 saatlik düzende 0 ile 23 arasında saat.<br /><br /> Daha fazla bilgi: ["H" özel Biçim belirleyicisi](#H_Specifier).|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 13|
|"HH"|Saat, 24 saatlik biçimde, 00 ile 23 arasında.<br /><br /> Daha fazla bilgi: ["HH" özel Biçim belirleyicisi](#HH_Specifier).|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 13|
|"K"|Saat dilimi bilgileri.<br /><br /> Daha fazla bilgi: ["K" özel Biçim belirleyicisi](#KSpecifier).|İle <xref:System.DateTime> değerleri:<br /><br /> 2009-06-15T13:45:30, Kind belirtilmemiş -><br /><br /> 2009-06-15T13:45:30, çeşit Utc -> Z<br /><br /> 2009-06-15T13:45:30, Kind yerel->-07:00 (yerel bilgisayar ayarlarına bağlıdır)<br /><br /> İle <xref:System.DateTimeOffset> değerleri:<br /><br /> 2009-06-15T01:45:30-07:00 --> -07:00<br /><br /> 2009-06-15T08:45:30+00:00 --> +00:00|
|"m"|Dakika, 0 ile 59 arasında.<br /><br /> Daha fazla bilgi: ["M" özel Biçim belirleyicisi](#mSpecifier).|2009-06-15T01:09:30 9 -&GT;<br /><br /> 2009-06-15T13:29:30 -> 29|
|"mm"|Dakika, 00 ile 59 arasında.<br /><br /> Daha fazla bilgi: ["Mm" özel Biçim belirleyicisi](#mmSpecifier).|2009-06-15T01:09:30 -> 09<br /><br /> 2009-06-15T01:45:30 -> 45|
|"M"|Ay, 1 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["M" özel Biçim belirleyicisi](#M_Specifier).|2009-06-15T13:45:30 -> 6|
|"AA"|Ay, 01 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["MM" özel Biçim belirleyicisi](#MM_Specifier).|2009-06-15T13:45:30 -> 06|
|"AAA"|Ayın kısaltılmış adı.<br /><br /> Daha fazla bilgi: ["MMM" özel Biçim belirleyicisi](#MMM_Specifier).|2009-06-15T13:45:30 -> Haz (en-US)<br /><br /> 2009-06-15T13:45:30 -> juin (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> Haz (zu-ZA)|
|"AAAA"|Ayın tam adı.<br /><br /> Daha fazla bilgi: ["MMMM" özel Biçim belirleyicisi](#MMMM_Specifier).|2009-06-15T13:45:30 -> Haziran (en-US)<br /><br /> 2009-06-15T13:45:30 juni (v-DK) -><br /><br /> 2009-06-15T13:45:30 uJuni (zu-ZA) ->|
|"s"|Saniye, 0'dan 59'a kadardır.<br /><br /> Daha fazla bilgi: ["S" özel biçim belirticisi](#sSpecifier).|2009-06-15T13:45:09 -> 9|
|"ss"|Saniye, 00'dan 59'a kadardır.<br /><br /> Daha fazla bilgi: ["Ss" özel biçim belirticisi](#ssSpecifier).|2009-06-15T13:45:09 -> 09|
|"t"|AM/PM göstergesinin ilk karakteri.<br /><br /> Daha fazla bilgi: ["T" özel biçim belirticisi](#tSpecifier).|2009-06-15T13:45:30 -> P (en-US)<br /><br /> 2009-06-15T13:45:30 -> 午 (ja-JP)<br /><br /> 2009-06-15T13:45:30 ->  (fr-FR)|
|"tt"|AM/PM göstergesi.<br /><br /> Daha fazla bilgi: ["Tt" özel Biçim belirleyicisi](#ttSpecifier).|2009-06-15T13:45:30 PM (en-US) -><br /><br /> 2009-06-15T13:45:30 午後 (ja-JP) -><br /><br /> 2009-06-15T13:45:30 ->  (fr-FR)|
|"y"|0 dan 99 'a kadar yıl.<br /><br /> Daha fazla bilgi: ["Y" özel biçim belirticisi](#ySpecifier).|0001-01-01T00:00:00 -> 1<br /><br /> 0900-01-01T00:00:00 -> 0<br /><br /> 1900-01-01T00:00:00 -> 0<br /><br /> 2009-06-15T13:45:30 -> 9<br /><br /> 2019-06-15T13:45:30 -> 19|
|"yy"|00 dan 99 'a kadar yıl.<br /><br /> Daha fazla bilgi: ["Yy" özel Biçim belirleyicisi](#yySpecifier).|0001-01-01T00:00:00 -> 01<br /><br /> 0900-01-01T00:00:00 -> 00<br /><br /> 1900-01-01T00:00:00 -> 00<br /><br /> 2019-06-15T13:45:30 -> 19|
|"yyy"|En az üç basamaklı olarak yıl.<br /><br /> Daha fazla bilgi: ["Yyy" özel Biçim belirleyicisi](#yyySpecifier).|0001-01-01T00:00:00 -> 001<br /><br /> 0900-01-01T00:00:00 -> 900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -> 2009|
|"yyyy"|Dört basamaklı bir sayı olarak yıl.<br /><br /> Daha fazla bilgi: ["Yyyy" özel Biçim belirleyicisi](#yyyySpecifier).|0001-01-01T00:00:00 -> 0001<br /><br /> 0900-01-01T00:00:00 -> 0900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -> 2009|
|"yyyyy"|Beş basamaklı bir sayı olarak yıl.<br /><br /> Daha fazla bilgi: ["Yyyyy" özel Biçim belirleyicisi](#yyyyySpecifier).|0001-01-01T00:00:00 -> 00001<br /><br /> 2009-06-15T13:45:30 -> 02009|
|"z"|Önünde sıfır olmadan UTC biçiminden saat uzaklığı.<br /><br /> Daha fazla bilgi: ["Z" özel Biçim belirleyicisi](#zSpecifier).|2009-06-15T13:45:30-07:00 -> -7|
|"zz"|Önünde sıfır bulunan tek basamaklı değerden oluşan UTC biçiminden saat uzaklığı.<br /><br /> Daha fazla bilgi: ["Zz" özel Biçim belirleyicisi](#zzSpecifier).|2009-06-15T13:45:30-07:00 -> -07|
|"zzz"|UTC biçiminden saat ve dakika uzaklığı.<br /><br /> Daha fazla bilgi: ["Zzz" özel Biçim belirleyicisi](#zzzSpecifier).|2009-06-15T13:45:30-07:00 -> -07:00|
|":"|Zaman ayırıcı.<br /><br /> Daha fazla bilgi: [":" Özel biçim belirticisi](#timeSeparator).|2009-06-15T13:45:30 -> : (en-US)<br /><br /> 2009-06-15T13:45:30 -> . (it-IT)<br /><br /> 2009-06-15T13:45:30 ->: (ja-JP)|
|"/"|Tarih ayırıcı.<br /><br /> Daha fazla bilgi: ["/" Özel Biçim belirleyicisi](#dateSeparator).|2009-06-15T13:45:30 -> / (en-US)<br /><br /> 2009-06-15T13:45:30 -> - (ar-DZ)<br /><br /> 2009-06-15T13:45:30 -> . (tr-TR)|
|"*dize*"<br /><br /> '*dize*'|Değişmez dize sınırlayıcısı.<br /><br /> Daha fazla bilgi: [Karakter değişmez değerleri](#Literals).|2009-06-15T13:45:30 ("varış:" s t) -> varış: 1:45 P<br /><br /> 2009-06-15T13:45:30 ('arr:' s t) -> varış: 1:45 P|
|%|Aşağıdaki karakteri özel biçim belirticisi olarak tanımlar.<br /><br /> Daha fazla bilgi:[tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers).|2009-06-15T13:45:30 (%h) -> 1|
|&#92;|"\" çıkış karakteri.<br /><br /> Daha fazla bilgi: [Karakter değişmez değerleri](#Literals) ve [çıkış karakterini kullanma](#escape).|2009-06-15T13:45:30 (h \h) -> 1 saat|
|Başka bir karakter|Karakter, değişmeyen sonuç dizesine kopyalanır.<br /><br /> Daha fazla bilgi: [Karakter değişmez değerleri](#Literals).|2009-06-15T01:45:30 (varış ss: dd t) -> varış 01:45 a|

Aşağıdaki bölümlerde, her özel tarih ve saat biçim belirticisi hakkında ek bilgi sağlanır. Aksi belirtilmediği sürece her belirleyici kullanılmış bakılmaksızın aynı dize temsilini oluşturur. bir <xref:System.DateTime> değeri veya <xref:System.DateTimeOffset> değeri.

## <a name="dSpecifier"></a> "D" özel biçim Belirleyicisi

"d" özel biçim belirticisi, 1 ile 31 arasında bir sayı olarak ayın gününü temsil eder. Tek basamaklı gün önünde sıfır olmadan biçimlendirilir.

"D" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında "d" standart tarih ve saat biçimi Belirleyicisi olarak yorumlanır. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

Aşağıdaki örnek birçok biçim dizesinde "d" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#1)]
[!code-vb[Formatting.DateAndTime.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#1)]

[Tabloya dön](#table)

## <a name="ddSpecifier"></a> "Dd" özel biçim Belirleyicisi

"dd" özel biçim dizesi, 01 ile 31 arasında bir sayı olarak ayın gününü temsil eder. Tek basamaklı gün önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "dd" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Tabloya dön](#table)

## <a name="dddSpecifier"></a> "Ddd" özel biçim Belirleyicisi

"ddd" özel biçim belirticisi haftanın gününün kısaltılmış adını temsil eder. Haftanın gününün yerelleştirilmiş kısaltılmış adı alınır <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültürün özelliği.

Aşağıdaki örnek bir özel biçim dizesinde "ddd" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Tabloya dön](#table)

## <a name="ddddSpecifier"></a> "Dddd" özel biçim Belirleyicisi

"dddd" özel biçim belirticisi (artı herhangi bir sayıda ek "d" tanımlayıcısı) haftanın gününün tam adını temsil eder. Haftanın gününün yerelleştirilmiş adı alınır <xref:System.Globalization.DateTimeFormatInfo.DayNames%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültürün özelliği.

Aşağıdaki örnek bir özel biçim dizesinde "dddd" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Tabloya dön](#table)

## <a name="fSpecifier"></a> "F" özel biçim Belirleyicisi

"f" özel biçim belirticisi saniye bölümünün en önemli basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin onda birini temsil eder.

"F" biçim belirticisi diğer biçim belirticileri olmadan kullanıldığında "f" standart tarih ve saat biçimi Belirleyicisi olarak yorumlanır. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

Kullandığınızda, "f" biçim belirleyicilerinin sağlanan bir biçim dizesinin parçası olarak <xref:System.DateTime.ParseExact%2A>, <xref:System.DateTime.TryParseExact%2A>, <xref:System.DateTimeOffset.ParseExact%2A>, veya <xref:System.DateTimeOffset.TryParseExact%2A> yöntemi, "f" biçim belirleyicilerinin sayısı, saniye bölümünün en önemli basamaklarının sayısını belirtir Bu dizeyi başarıyla ayrıştırmak için mevcut olması gerekir.

Aşağıdaki örnek bir özel biçim dizesinde "f" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya dön](#table)

## <a name="ffSpecifier"></a> "Ff" özel biçim Belirleyicisi

"ff" özel biçim belirticisi saniye bölümünün en önemli iki basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüzde birini temsil eder.

Aşağıdaki örnek, özel biçim dizesindeki "ff" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya dön](#table)

## <a name="fffSpecifier"></a> "Fff" özel biçim Belirleyicisi

"fff" özel biçim belirticisi saniye bölümünün en önemli üç basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin binde birini temsil eder.

Aşağıdaki örnek bir özel biçim dizesinde "fff" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya dön](#table)

## <a name="ffffSpecifier"></a> "Ffff" özel biçim Belirleyicisi

"ffff" özel biçim belirticisi saniye bölümünün en önemli dört basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on binde birini temsil eder.

Bir zaman değerine ait saniye bileşenini on binde duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 sürümünde (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

## <a name="fffffSpecifier"></a> "Fffff" özel biçim Belirleyicisi

"fffff" özel biçim belirticisi saniye bölümünün en önemli beş basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüz binde birini temsil eder.

Yüz binde bir zaman değerine ait saniye bileşenini duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

## <a name="ffffffSpecifier"></a> "Ffffff" özel biçim Belirleyicisi

"ffffff" özel biçim belirticisi saniye bölümünün en önemli altı basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin milyonda birini temsil eder.

Bir zaman değerine ait saniye bileşenini milyonda duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

## <a name="fffffffSpecifier"></a> "Fffffff" özel biçim Belirleyicisi

"fffffff" özel biçim belirticisi saniye bölümünün en önemli yedi basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on milyonda birini temsil eder.

Bir zaman değerine ait saniye bileşenini on milyonda duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

## <a name="F_Specifier"></a> "F" özel biçim Belirleyicisi

"F" özel biçim belirticisi saniye bölümünün en önemli basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin onda birini temsil eder. Basamak sıfırsa hiçbir şey görüntülenmez.

"F" biçim belirticisi diğer biçim belirticileri olmadan kullanıldığında "F" standart tarih ve saat biçimi Belirleyicisi olarak yorumlanır. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

İle birlikte kullanılan "F" biçim belirleyicilerinin sayısı <xref:System.DateTime.ParseExact%2A>, <xref:System.DateTime.TryParseExact%2A>, <xref:System.DateTimeOffset.ParseExact%2A>, veya <xref:System.DateTimeOffset.TryParseExact%2A> yöntemi dizeyi başarıyla ayrıştırmak için saniye bölümünün en önemli basamaklarının maksimum sayısını belirtir.

Aşağıdaki örnek bir özel biçim dizesinde "F" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya dön](#table)

## <a name="FF_Specifier"></a> "FF" özel biçim Belirleyicisi

"FF" özel biçim belirticisi saniye bölümünün en önemli iki basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüzde birini temsil eder. Ancak öndeki sıfırlar veya iki sıfır basamak görüntülenmez.

Aşağıdaki örnek bir özel biçim dizesinde "FF" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya dön](#table)

## <a name="FFF_Specifier"></a> "FFF" özel biçim Belirleyicisi

"FFF" özel biçim belirticisi saniye bölümünün en önemli üç basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin binde birini temsil eder. Ancak öndeki sıfırlar veya üç sıfır basamak görüntülenmez.

Aşağıdaki örnek bir özel biçim dizesinde "FFF" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya dön](#table)

## <a name="FFFF_Specifier"></a> "FFFF" özel biçim Belirleyicisi

"FFFF" özel biçim belirticisi saniye bölümünün en önemli dört basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on binde birini temsil eder. Ancak öndeki sıfırlar veya dört sıfır basamak görüntülenmez.

Bir zaman değerine ait saniye bileşenini on binde duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

## <a name="FFFFF_Specifier"></a> "FFFFF" özel biçim Belirleyicisi

"FFFFF" özel biçim belirticisi saniye bölümünün en önemli beş basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüz binde birini temsil eder. Ancak öndeki sıfırlar veya beş sıfır basamak görüntülenmez.

Yüz binde bir zaman değerine ait saniye bileşenini duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

## <a name="FFFFFF_Specifier"></a> "FFFFFF" özel biçim Belirleyicisi

"FFFFFF" özel biçim belirticisi saniye bölümünün en önemli altı basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin milyonda birini temsil eder. Ancak öndeki sıfırlar veya altı sıfır basamak görüntülenmez.

Bir zaman değerine ait saniye bileşenini milyonda duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

## <a name="FFFFFFF_Specifier"></a> "FFFFFFF" özel biçim Belirleyicisi

"FFFFFFF" özel biçim belirticisi saniye bölümünün en önemli yedi basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on milyonda birini temsil eder. Ancak öndeki sıfırlar veya yedi sıfır basamak görüntülenmez.

Bir zaman değerine ait saniye bileşenini on milyonda duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

## <a name="gSpecifier"></a> "G" veya "gg" özel biçim Belirleyicisi

"g" veya "gg" özel biçim belirticileri (artı herhangi bir sayıda ek "g" belirticisi) M.S. gibi bir dönem veya çağı temsil eder Biçimlendirilecek tarih ilişkili bir dönem veya Çağ dizesine sahip değilse, biçimlendirme işlemi bu belirticiyi yok sayar.

"G" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında "g" standart tarih ve saat biçimi Belirleyicisi olarak yorumlanır. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

Aşağıdaki örnek bir özel biçim dizesinde "g" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#6)]
[!code-vb[Formatting.DateAndTime.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#6)]

[Tabloya dön](#table)

## <a name="hSpecifier"></a> "H" özel biçim Belirleyicisi

"h" özel biçim belirticisi 1 ile 12 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, saatleri gece yarısından veya öğleden itibaren tam saatleri sayan 12 saatlik zaman biçimi ile temsil edilir. Gece yarısından sonraki bir saat, öğleden sonraki aynı saatle ayırt edilemez. Saat yuvarlanmaz ve önünde sıfır olmadan tek basamaklı bir saat biçimlendirilir. Örneğin, sabah veya öğleden sonra 5:43 saati verildiğinde bu özel biçim belirtici "5" görüntüler.

"H" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, standart tarih ve saat biçimi Belirleyicisi yorumlanır ve oluşturur bir <xref:System.FormatException>. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

Aşağıdaki örnek bir özel biçim dizesinde "h" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Tabloya dön](#table)

## <a name="hhSpecifier"></a> "Hh" özel biçim Belirleyicisi

"hh" özel biçim belirticisi (artı herhangi bir sayıda ek "h" belirticisi) 01 ile 12 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, tam saatleri gece yarısından veya öğleden itibaren sayan 12 saatlik zaman biçimi ile temsil edilir. Gece yarısından sonraki bir saat, öğleden sonraki aynı saatle ayırt edilemez. Saat yuvarlanmaz ve önünde sıfır ile birlikte tek basamaklı bir saat biçimlendirilir. Örneğin, sabah veya öğleden sonra 5:43 saati verildiğinde bu biçim belirtici "05" görüntüler.

Aşağıdaki örnek bir özel biçim dizesinde "hh" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Tabloya dön](#table)

## <a name="H_Specifier"></a> "H" özel biçim Belirleyicisi

"H" özel biçim belirticisi 0 ile 23 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, saatleri gece yarısından itibaren sayan sıfır tabanlı bir 24 saatlik zaman biçimi ile temsil edilir. Tek basamaklı saat önünde sıfır olmadan biçimlendirilir.

"H" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, standart tarih ve saat biçimi Belirleyicisi yorumlanır ve oluşturur bir <xref:System.FormatException>. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

Aşağıdaki örnek bir özel biçim dizesinde "H" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#9)]
[!code-vb[Formatting.DateAndTime.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#9)]

[Tabloya dön](#table)

## <a name="HH_Specifier"></a> "HH" özel biçim Belirleyicisi

"HH" özel biçim belirticisi (artı herhangi bir sayıda ek "H" belirticisi) 00 ile 23 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, saatleri gece yarısından itibaren sayan sıfır tabanlı bir 24 saatlik zaman biçimi ile temsil edilir. Tek basamaklı saat önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "HH" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#10)]
[!code-vb[Formatting.DateAndTime.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#10)]

[Tabloya dön](#table)

## <a name="KSpecifier"></a> "K" özel biçim Belirleyicisi

"K" özel biçim belirticisi bir tarih ve saat değerinin saat dilimi bilgisini temsil eder. Bu biçim tanımlayıcısı kullanıldığında <xref:System.DateTime> değerleri, sonuç dizesi değeri tarafından tanımlanan <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği:

- Yerel saat dilimi için (bir <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği değerinin <xref:System.DateTimeKind.Local?displayProperty=nameWithType>), bu belirtici "zzz" belirticisi ile aynıdır ve yerel Eşgüdümlü Evrensel Saat (UTC); içeren bir sonuç dizesi oluşturur Örneğin, "-07:00".

- UTC saati için (bir <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği değerinin <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), sonuç dizesi UTC tarihini belirtmek üzere "Z" karakterini içerir.

- Belirtilmeyen bir saat diliminde bir süre boyunca (bir saat olan <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliğini eşittir <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>), sonuç <xref:System.String.Empty?displayProperty=nameWithType>.

İçin <xref:System.DateTimeOffset> değerleri "K" biçim belirtici "zzz" biçim belirtici ile aynıdır ve içeren bir sonuç dizesi oluşturur <xref:System.DateTimeOffset> değerinin UTC ile olan uzaklığını.

"K" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, standart tarih ve saat biçimi Belirleyicisi yorumlanır ve oluşturur bir <xref:System.FormatException>. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

Aşağıdaki örnek, "K" özel Biçim belirleyicisi çeşitli ile kullanılması sonucu elde edilen dizeyi gösterir <xref:System.DateTime> ve <xref:System.DateTimeOffset> ABD'deki bir sistemde değerleri Pasifik Saat dilimi.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#12)]
[!code-vb[Formatting.DateAndTime.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#12)]

[Tabloya dön](#table)

## <a name="mSpecifier"></a> "M" özel biçim Belirleyicisi

"m" özel biçim belirticisi, 0 ile 59 arasında bir sayı olarak dakikayı temsil eder. Dakika, son saatten beri geçen tam dakikaları temsil eder. Tek basamaklı dakika önünde sıfır olmadan biçimlendirilir.

"M" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında "m" standart tarih ve saat biçimi Belirleyicisi olarak yorumlanır. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

Aşağıdaki örnek bir özel biçim dizesinde "m" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Tabloya dön](#table)

## <a name="mmSpecifier"></a> "Mm" özel biçim belirticisi

"m" özel biçim belirticisi (artı herhangi bir sayıda ek "m" belirticisi) 00 ile 59 arasında bir sayı olarak dakikayı temsil eder. Dakika, son saatten beri geçen tam dakikaları temsil eder. Tek basamaklı dakika önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "mm" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Tabloya dön](#table)

## <a name="M_Specifier"></a> "M" özel biçim Belirleyicisi

"M" özel biçim belirticisi, 1 ile 12 arasında (veya 13 ay içeren takvimler için 1 ile 13 arasında) bir sayı olarak ayı temsil eder. Tek basamaklı ay önünde sıfır olmadan biçimlendirilir.

"M" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında "M" standart tarih ve saat biçimi Belirleyicisi olarak yorumlanır. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

Aşağıdaki örnek bir özel biçim dizesinde "M" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#11)]
[!code-vb[Formatting.DateAndTime.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#11)]

[Tabloya dön](#table) 

## <a name="MM_Specifier"></a> "MM" özel biçim Belirleyicisi

"MM" özel biçim belirticisi, 01 ile 12 arasında (veya 13 ay içeren takvimler için 1 ile 13 arasında) bir sayı olarak ayı temsil eder. Tek basamaklı ay önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "MM" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Tabloya dön](#table)

## <a name="MMM_Specifier"></a> "MMM" özel biçim Belirleyicisi

"MMM" özel biçim belirticisi ayın gününün kısaltılmış adını temsil eder. Ayın yerelleştirilmiş kısaltılmış adı alınır <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültürün özelliği.

Aşağıdaki örnek bir özel biçim dizesinde "MMM" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Tabloya dön](#table)

## <a name="MMMM_Specifier"></a> "MMMM" özel biçim Belirleyicisi

"MMMM" özel biçim belirticisi ayın gününün tam adını temsil eder. Ayın yerelleştirilmiş adı alınır <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültürün özelliği.

Aşağıdaki örnek bir özel biçim dizesinde "MMMM" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Tabloya dön](#table)

## <a name="sSpecifier"></a> "S" özel biçim Belirleyicisi

"s" özel biçim belirticisi, 0 ile 59 arasında bir sayı olarak saniyeyi temsil eder. Sonuç, son dakikadan beri geçen tam saniyeleri temsil eder. Tek basamaklı saniye önünde sıfır olmadan biçimlendirilir.

"S" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında "s" standart tarih ve saat biçimi Belirleyicisi olarak yorumlanır. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

Aşağıdaki örnek bir özel biçim dizesinde "s" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Tabloya dön](#table)

## <a name="ssSpecifier"></a> "Ss" özel biçim Belirleyicisi

"ss" özel biçim belirticisi (artı herhangi bir sayıda ek "s" belirticisi) 00 ile 59 arasında bir sayı olarak saniyeyi temsil eder. Sonuç, son dakikadan beri geçen tam saniyeleri temsil eder. Tek basamaklı saniye önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "ss" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Tabloya dön](#table)

## <a name="tSpecifier"></a> "T" özel biçim Belirleyicisi

"t" özel biçim belirticisi AM/PM göstergelerinin ilk karakterini temsil eder. Yerelleştirilmiş uygun gösterge alınır <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> veya <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> özelliği geçerli ya da belirli bir kültürün. AM göstergesi, 0:00:00 (gece yarısı) ile 11:59:59.999 arasındaki tüm zamanlar için kullanılır. PM göstergesi, 12:00:00 (öğlen) ile 23:59:59.999 arasındaki tüm zamanlar için kullanılır.

"T" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında "t" standart tarih ve saat biçimi Belirleyicisi olarak yorumlanır. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

Aşağıdaki örnek bir özel biçim dizesinde "t" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Tabloya dön](#table)

## <a name="ttSpecifier"></a> "Tt" özel biçim Belirleyicisi

"tt" özel biçim belirticisi (artı herhangi bir sayıda ek "t" belirticisi) tüm AM/PM göstergelerini temsil eder. Yerelleştirilmiş uygun gösterge alınır <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> veya <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> özelliği geçerli ya da belirli bir kültürün. AM göstergesi, 0:00:00 (gece yarısı) ile 11:59:59.999 arasındaki tüm zamanlar için kullanılır. PM göstergesi, 12:00:00 (öğlen) ile 23:59:59.999 arasındaki tüm zamanlar için kullanılır.

Diller, AM ve PM arasında ayrım korumak için gerekli olduğu için "tt" belirticisini kullandığınızdan emin olun. Japonca buna bir örnektir; AM ve PM göstergeleri birinci karakter yerine ikinci karakterde farklılık gösterir.

Aşağıdaki örnek bir özel biçim dizesinde "tt" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Tabloya dön](#table)

## <a name="ySpecifier"></a> "Y" özel biçim Belirleyicisi

"y" özel biçim belirticisi tek basamaklı veya iki basamaklı bir sayı olarak yılı temsil eder. Yılda ikiden fazla basamak varsa, yalnızca son kısımdaki iki basamak sonuçta görünür. İki basamaklı yılın ilk basamağı sıfır ise (örneğin, 2008), sayı önünde sıfır olmadan biçimlendirilir.

"Y" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında "y" standart tarih ve saat biçimi Belirleyicisi olarak yorumlanır. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

Aşağıdaki örnek bir özel biçim dizesinde "y" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya dön](#table)

## <a name="yySpecifier"></a> "Yy" özel biçim Belirleyicisi

"yy" özel biçim belirticisi iki basamaklı bir sayı olarak yılı temsil eder. Yılda ikiden fazla basamak varsa, yalnızca son kısımdaki iki basamak sonuçta görünür. İki basamaklı yılda ikiden az belirtici basamak varsa, iki basamak oluşturulabilmesi için sayının önüne sıfır eklenir.

Bir ayrıştırma işleminde "yy" özel biçim belirticisi kullanılarak Ayrıştırılan iki basamaklı bir yıl göre yorumlanır <xref:System.Globalization.Calendar.TwoDigitYearMax%2A?displayProperty=nameWithType> biçim sağlayıcısının geçerli takvimindeki özelliği. Aşağıdaki örnek, bu durumda en-US kültürü olan geçerli kültürün varsayılan Gregoryen takvimini kullanarak iki basamaklı yıl içeren bir tarih dize gösterimini ayrıştırır. Ardından geçerli kültürün değişiklikleri <xref:System.Globalization.CultureInfo> kullanılacak nesne bir <xref:System.Globalization.GregorianCalendar> nesnesi <xref:System.Globalization.GregorianCalendar.TwoDigitYearMax%2A> özelliği değiştirilmiş.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/parseexact2digityear1.cs#19)]
[!code-vb[Formatting.DateAndTime.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/parseexact2digityear1.vb#19)]

Aşağıdaki örnek bir özel biçim dizesinde "yy" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya dön](#table)

## <a name="yyySpecifier"></a> "Yyy" özel biçim Belirleyicisi

"yyy" özel biçim belirticisi en az üç basamakla yılı temsil eder. Yılda üçten fazla belirtici basamak varsa, bunlar sonuç dizesine eklenir. Yıl üçten az basamaktan oluşuyorsa, üç basamak oluşturulabilmesi için sayının önüne sıfır eklenir.

> [!NOTE]
> Beş basamaklı yıllar içeren Thai Budist takvimi için bu biçim belirtici tüm basamakları görüntüler.

Aşağıdaki örnek bir özel biçim dizesinde "yyy" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya dön](#table)

## <a name="yyyySpecifier"></a> "Yyyy" özel biçim Belirleyicisi

"yyyy" özel biçim belirticisi en az dört basamakla yılı temsil eder. Yılda dörtten fazla belirtici basamak varsa, bunlar sonuç dizesine eklenir. Yıl dörtten az basamaktan oluşuyorsa, dört basamak oluşturulabilmesi için sayının önüne sıfır eklenir.

> [!NOTE]
> Beş basamaklı yıllar içeren Thai Budist takvimi için bu biçim belirtici en az dört basamak görüntüler.

Aşağıdaki örnek bir özel biçim dizesinde "yyyy" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya dön](#table)

## <a name="yyyyySpecifier"></a> "Yyyyy" özel biçim Belirleyicisi

"yyyyy" özel biçim belirticisi (artı herhangi bir sayıda ek "y" belirticisi) en az beş basamakla yılı temsil eder. Yılda beşten fazla belirtici basamak varsa, bunlar sonuç dizesine eklenir. Yıl beşten az basamaktan oluşuyorsa, beş basamak oluşturulabilmesi için sayının önüne sıfır eklenir.

Ek "y" belirticileri varsa sayının önüne "y" belirticileriyle aynı sayıda olacak kadar sıfır eklenir.

Aşağıdaki örnek bir özel biçim dizesinde "yyyyy" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya dön](#table)

## <a name="zSpecifier"></a> "Z" özel biçim Belirleyicisi

İle <xref:System.DateTime> değerleri, "z" özel biçim belirticisi temsil eden imzalı uzaklığı yerel işletim sisteminin saat dilimi ile eşgüdümlü evrensel saat (saat cinsinden UTC). Bir örneğin değerini yansıtılmıyor <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği. Bu nedenle "z" biçim belirticisi ile kullanım için önerilmez <xref:System.DateTime> değerleri.

İle <xref:System.DateTimeOffset> değerleriyle Bu biçim belirtici temsil eder <xref:System.DateTimeOffset> değerinin UTC ile olan uzaklığını saat.

Uzaklık her zaman önünde bir işaretle görüntülenir. Artı işareti (+) UTC'den önceki saatleri belirtir, eksi işareti (-) UTC'den sonraki saatleri belirtir. Tek basamaklı sapma önünde sıfır olmadan biçimlendirilir.

"Z" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, standart tarih ve saat biçimi Belirleyicisi yorumlanır ve oluşturur bir <xref:System.FormatException>. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

Aşağıdaki örnek bir özel biçim dizesinde "z" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Tabloya dön](#table)

## <a name="zzSpecifier"></a> "Zz" özel biçim Belirleyicisi

İle <xref:System.DateTime> değerleriyle "zz" özel biçim belirticisi temsil eder yerel işletim sisteminin saat dilimi imzalı uzaklığı saat cinsinden UTC. Bir örneğin değerini yansıtılmıyor <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği. Bu nedenle "zz" biçim belirticisi ile kullanım için önerilmez <xref:System.DateTime> değerleri.

İle <xref:System.DateTimeOffset> değerleriyle Bu biçim belirtici temsil eder <xref:System.DateTimeOffset> değerinin UTC ile olan uzaklığını saat.

Uzaklık her zaman önünde bir işaretle görüntülenir. Artı işareti (+) UTC'den önceki saatleri belirtir, eksi işareti (-) UTC'den sonraki saatleri belirtir. Tek basamaklı sapma önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "zz" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Tabloya dön](#table)

## <a name="zzzSpecifier"></a> "Zzz" özel biçim Belirleyicisi

İle <xref:System.DateTime> değerleriyle "zzz" özel biçim belirticisi temsil eder yerel işletim sisteminin saat dilimi imzalı uzaklığı saat ve dakika cinsinden UTC. Bir örneğin değerini yansıtılmıyor <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği. Bu nedenle "zzz" biçim belirticisi ile kullanım için önerilmez <xref:System.DateTime> değerleri.

İle <xref:System.DateTimeOffset> değerleriyle Bu biçim belirtici temsil eder <xref:System.DateTimeOffset> değerinin UTC ile olan uzaklığını, saat ve dakika olarak.

Uzaklık her zaman önünde bir işaretle görüntülenir. Artı işareti (+) UTC'den önceki saatleri belirtir, eksi işareti (-) UTC'den sonraki saatleri belirtir. Tek basamaklı sapma önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "zzz" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Tabloya dön](#table)

## <a name="timeSeparator"></a> ":" Özel biçim Belirleyicisi
":" özel biçim belirticisi, saat, dakika ve saniyeyi ayırt etmek için kullanılan zaman ayırıcıyı temsil eder. Yerelleştirilmiş uygun zaman ayırıcı alınır <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültürün özelliği.

> [!NOTE]
> Belirli bir tarih ve saat dizesi için zaman ayırıcı değiştirmek için ayırıcı karakter değişmez dize sınırlayıcısı içinde belirtin. Örneğin, özel biçim dizesi `hh'_'dd'_'ss` üreten bir sonuç dizesinde "\_" (alt çizgi) her zaman zaman ayırıcı olarak kullanılır. Bir kültür için tüm tarihleri zaman ayırıcı değiştirmek için ya da değerini değiştirmek <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> özelliği geçerli kültür ya da örneği bir <xref:System.Globalization.DateTimeFormatInfo> nesne, karakter atama kendi <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A> özelliği ve bir aşırı yüklemesini çağırın biçimlendirme içeren yöntemi bir <xref:System.IFormatProvider> parametresi.

":" Biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, standart tarih ve saat biçimi Belirleyicisi yorumlanır ve oluşturur bir <xref:System.FormatException>. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

[Tabloya dön](#table)

## <a name="dateSeparator"></a> "/" Özel biçim Belirleyicisi

"/" özel biçim belirticisi, yıl, ay ve günü ayırt etmek için kullanılan tarih ayırıcıyı temsil eder. Yerelleştirilmiş uygun tarih ayırıcı alınır <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültürün özelliği.

> [!NOTE]
> Tarih Ayırıcı, belirli bir tarih ve saat dizesi için değiştirmek için ayırıcı karakter değişmez dize sınırlayıcısı içinde belirtin. Örneğin, özel biçim dizesi `mm'/'dd'/'yyyy` üreten bir sonuç dizesinde "/" her zaman tarih ayırıcı olarak kullanılır. Tüm tarihler bir kültür için tarih ayırıcı değiştirmek için ya da değerini değiştirmek <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> özelliği geçerli kültür ya da örneği bir <xref:System.Globalization.DateTimeFormatInfo> nesne, karakter atama kendi <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A> özelliği ve bir aşırı yüklemesini çağırın biçimlendirme içeren yöntemi bir <xref:System.IFormatProvider> parametresi.

"/" Biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, standart tarih ve saat biçimi Belirleyicisi yorumlanır ve oluşturur bir <xref:System.FormatException>. Bir tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz. [tek özel biçim Belirleyicilerini kullanma](#UsingSingleSpecifiers) bu makalenin ilerleyen bölümlerinde.

[Tabloya dön](#table)

## <a name="Literals"></a> Karakter değişmez değerleri

Aşağıdaki karakteri özel bir tarih ve saat biçim dizesi ayrılmıştır ve her zaman yorumlanır gibi biçimlendirme karakterleri veya durumunda, ", ', /, ve \\, özel karakterler olarak.

||||||
|-|-|-|-|-|
|F|H|K|M|d|
|F|G|h|m|s|
|t|y|z|%|:|
|/|"|'|&#92;||

Diğer tüm karakterler, her zaman karakter değişmez değer olarak yorumlanır ve bir biçimlendirme işleminde değiştirilmeden sonuç dizesine eklenir.  Bir ayrıştırma işleminde Bunlar giriş dizesindeki bir karakter tam olarak eşleşmelidir; Karşılaştırma büyük/küçük harf duyarlıdır.

Aşağıdaki örnek, bir biçim dizesindeki yerel saat dilimini temsil etmek için "PST" (Pasifik Standart Saati için) ve (Pasifik Yaz Saati için) "Pasifik Yaz SAATİ'ne" sabit karakterleriyle içerir. Dize sonuç dizesine eklenir ve yerel saat dilimi dizesini içeren bir dizeyi de başarıyla ayrıştırır olduğunu unutmayın.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx1.cs#20)]
[!code-vb[Formatting.DateAndTime.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx1.vb#20)]

Sonuç dizesinde veya bir giriş dizesinde başarıyla ayrıştırıldı ayrılmış karakterler olarak değil de değişmez karakter olarak yorumlanması için karakter olduğunu belirtmek için iki yolu vardır:

- Her ayrılmış bir karakter kaçış tarafından. Daha fazla bilgi için [çıkış karakterini kullanma](#escape).

Aşağıdaki örnek "pst" sabit karakterleriyle biçim dizesindeki yerel saat dilimini temsil etmek için (Pasifik Standart Saati) içerir. Hem "s" ve "t" özel biçim dizeleri olduğundan, her iki karakterleri karakter değişmez değerleri yorumlanması için kaçış karakterleri eklenmelidir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx2.cs#21)]
[!code-vb[Formatting.DateAndTime.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx2.vb#21)]

- Tüm sabit dizesini tırnak işareti veya kesme kapsayan tarafından. Aşağıdaki örnek Öncekine, "pst" tüm ayrılmış dizesini karakter değişmez değerleri yorumlanması gerektiğini belirtmek için tırnak işaretleri içine dışında aynıdır.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx3.cs#22)]
[!code-vb[Formatting.DateAndTime.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx3.vb#22)]

## <a name="notes"></a>Notlar

### <a name="UsingSingleSpecifiers"></a> Tek özel biçim belirticileri kullanma

Özel tarih ve saat biçimi dizesi iki veya daha fazla karakterden oluşur. Tarih ve saat biçimlendirme yöntemleri, herhangi tek karakterli dizeyi standart tarih ve saat biçim dizesi olarak yorumlar. Geçerli bir biçim belirtici bunlar karakter tanımıyorsanız, oluştururlar bir <xref:System.FormatException>. Örneğin, yalnızca belirleyici "h" içeren bir biçim dizesi standart tarih ve saat biçimi dizesi olarak yorumlanır. Ancak, bu durumda herhangi bir "h" standart tarih ve timeformat belirticisi olmadığından bir özel durum oluşturulur.

Bir biçim dizesinde tek belirleyici olarak özel tarih ve saat biçimi belirleyicilerinden birini kullanmak için ("d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" veya "/" özel biçim belirleyicisinin kendisi), belirleyiciden önce veya sonra bir boşluk bırakın veya tek özel tarih ve saat belirleyicisinden önce yüzde ("%") biçim belirleyicisi ekleyin.

Örneğin, "`%h"` özel tarih ve saatin geçerli tarih ve saat değeriyle temsil edildiği saat biçimi dizesi olarak yorumlanır. Sonuç dizesinde saatin yanında bir boşluk içerse de " h" veya "h " biçimlendirme dizisini de kullanabilirsiniz. Aşağıdaki örnek bu üç biçim dizesini gösterir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/literal1.cs#16)]
[!code-vb[Formatting.DateAndTime.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/literal1.vb#16)]

### <a name="escape"></a> Çıkış karakterini kullanma

Bir biçim dizesindeki "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" veya "/" karakterleri, değişmez karakterler olarak değil özel biçim belirticileri olarak yorumlanır. Bir karakterin Biçim belirleyicisi olarak yorumlanmasını önlemek için bu ters eğik çizgi koyabilirsiniz (\\), kaçış karakteri olan. Çıkış karakteri, aşağıdaki karakterin değiştirilmeden sonuç dizesini dahil edilmesi gereken bir karakter sabiti olduğunu belirtir.

Sonuç dizesine ters eğik çizgi dahil etmek için bunu başka bir ters eğik çizgiyle kaçışını yapmanız gerekir (`\\`).

> [!NOTE]
> C++ ve C# derleyicileri gibi bazı derleyiciler, tek bir ters eğik çizgiyi çıkış karakteri olarak yorumlayabilir. Bir dizenin yalnızca düzgün biçimlendirildiğinde yorumlanmasını sağlamak için C# içinde dizeden önce değişmez değer karakterini (@ karakteri) kullanabilirsiniz veya C# ve C++ içinde her ters eğik çizgiden önce bir ters eğik çizgi daha ekleyebilirsiniz. Aşağıdaki C# örneği her iki yaklaşımı da gösterir.

Aşağıdaki örnek, biçimlendirme işleminin "h" ve "m" karakterlerini biçim belirticileri olarak yorumlamasını önlemek için çıkış karakteri kullanır.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/escape1.cs#15)]
[!code-vb[Formatting.DateAndTime.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/escape1.vb#15)]

### <a name="control-panel-settings"></a>Denetim Masası Ayarları

**Bölge ve Dil Seçenekleri** Denetim Masası'ndaki ayarları birçok özel tarih ve saat biçimi belirticisi içeren bir biçimlendirme işlemiyle oluşturulan Sonuç dizesini etkiler. Bu ayarları başlatmak için kullanılan <xref:System.Globalization.DateTimeFormatInfo> biçimlendirmeyi yönetmek için değerler sunar geçerli iş parçacığı kültürüyle ilgili nesne. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.

Ayrıca kullandığınız, <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> yeni bir örneğini oluşturmak için oluşturucu <xref:System.Globalization.CultureInfo> yapılan her özelleştirme mevcut sistem kültürüyle aynı kültürü temsil eden nesne **bölge ve Dil Seçenekleri** Denetim Masası'ndaki öğesi uygulanacak yeni <xref:System.Globalization.CultureInfo> nesne. Kullanabileceğiniz <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> oluşturmak için bir <xref:System.Globalization.CultureInfo> bir sistem özelleştirmelerini değil bir nesne.

### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo properties

Biçimlendirme geçerli bir özellik tarafından etkilenir <xref:System.Globalization.DateTimeFormatInfo> tarafından açık olarak veya geçerli iş parçacığı kültürü tarafından örtük olarak sağlanan nesne <xref:System.IFormatProvider> biçimlendirmeyi çağıran yöntemin parametre. İçin <xref:System.IFormatProvider> parametresini belirtmeniz gerekir bir <xref:System.Globalization.CultureInfo> bir kültürü temsil eden bir nesne veya <xref:System.Globalization.DateTimeFormatInfo> nesne.

Birçok özel tarih ve saat biçimi belirticisi tarafından üretilen sonuç dizesi ayrıca geçerli özelliklerine de bağlıdır <xref:System.Globalization.DateTimeFormatInfo> nesne. Uygulamanız karşılık gelen değiştirerek bazı özel tarih ve saat biçimi belirticisi tarafından üretilen sonuç değiştirebilirsiniz <xref:System.Globalization.DateTimeFormatInfo> özelliği. Örneğin, "ddd" biçim belirticisi bulunan kısaltılmış gün adını ekler <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A> sonuç dizesine dize dizisi. Benzer şekilde "MMMM" biçim belirticisi bulunan tam ay adını ekler <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A> sonuç dizesine dize dizisi.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Örnek: .NET Framework 4 biçimlendirme yardımcı](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
