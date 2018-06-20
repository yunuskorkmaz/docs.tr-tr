---
title: Özel Tarih ve Saat Biçim Dizeleri
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
ms.openlocfilehash: 5dbdb4aa70fcd14a914e1cb1b608260f1e51c1d0
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208531"
---
# <a name="custom-date-and-time-format-strings"></a>Özel Tarih ve Saat Biçim Dizeleri
Bir tarih ve saat biçim dizesi metin gösterimini tanımlayan bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> bir biçimlendirme işleminin sonuçları değeri. Ayrıca, dizeyi tarih ve saate başarılı bir şekilde dönüştürmek için bir ayrıştırma işleminde gerekli olan tarih ve saat değerinin bildirimini tanımlayabilir. Özel biçim dizesi, bir veya daha fazla özel tarih ve saat biçimi belirleyicisinden oluşur. Değil herhangi bir dize bir [standart tarih ve saat biçim dizesi](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) özel tarih ve saat biçim dizesi yorumlanır.  
  
 Özel tarih ve saat biçim dizeleri ikisi ile kullanılabilecek <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.  
  
> [!TIP]
>  İndirebilirsiniz [biçimlendirme yardımcı programı](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), biçimi uygulamanıza olanak sağlayan bir uygulama dizeleri için tarih ve saat veya sayısal değerleri ve sonuç dizesini görüntüler.  
  
<a name="table"></a> Özel tarih ve saat biçim dizeleri işlemleri biçimlendirmede olabilir ya da ile kullanılan `ToString` yöntemi tarih ve saat örneğinin veya bileşik biçimlendirme destekleyen bir yöntem. Aşağıdaki örnek her iki kullanımı da gösterir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandformatting1.cs#17)]
 [!code-vb[Formatting.DateAndTime.Custom#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandformatting1.vb#17)]  
  
 Ayrıştırma işlemleri özel tarih ve saat biçim dizeleri kullanılabilir <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, ve <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> yöntemleri. Bu yöntemlerin başarılı olması için bir giriş dizesinin bir ayrıştırma işlemi için belirli bir modele tam olarak uyması gerekir. Aşağıdaki örnek bir çağrı gösterilmektedir <xref:System.DateTimeOffset.ParseExact%28System.String%2CSystem.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemi, bir gün, ay ve iki rakamlı yıl içermesi gereken bir tarih ayrıştırılamadı.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#18](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandparsing1.cs#18)]
 [!code-vb[Formatting.DateAndTime.Custom#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandparsing1.vb#18)]  
  
 Aşağıdaki tabloda özel tarih ve saat biçimi belirteçleri açıklanır ve her biçim belirticisi tarafından üretilen bir sonuç dizesini görüntülenir. Varsayılan olarak, sonuç dizeleri en-US kültürünün, biçimlendirme kurallarını yansıtır. Belirli bir biçim belirticisi yerelleştirilmiş bir sonuç dizesi üretirse örnek aynı zamanda sonuç dizesinin uygulanacağı kültürü de not alır. Özel tarih ve saat biçimi dizelerini kullanma hakkında ek bilgi için Notlar bölümüne bakın.  
  
|Biçim belirteci|Açıklama|Örnekler|  
|----------------------|-----------------|--------------|  
|"d"|1 İle 31 arasında ayın günü.<br /><br /> Daha fazla bilgi: ["D" özel biçim belirticisi](#dSpecifier).|2009-06-01T13:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 15|  
|"dd"|01 İle 31 arasında ayın günü.<br /><br /> Daha fazla bilgi: ["Aa" özel biçim belirticisi](#ddSpecifier).|2009-06-01T13:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 15|  
|"ddd"|Haftanın günü, kısaltılmış adı.<br /><br /> Daha fazla bilgi: ["Ggg" özel biçim belirticisi](#dddSpecifier).|2009-06-15T13:45:30 -> Mon (en-US)<br /><br /> 2009-06-15T13:45:30 -> Пн (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lun. (fr-FR)|  
|"dddd"|Haftanın gününün tam adı.<br /><br /> Daha fazla bilgi: ["Dddd" özel biçim belirticisi](#ddddSpecifier).|2009-06-15T13:45:30 -> Pazartesi (en-US)<br /><br /> 2009-06-15T13:45:30 -> понедельник (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lundi (fr-FR)|  
|"f"|Saniyenin onda biri bir tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["F" özel biçim belirticisi](#fSpecifier).|2009-06-15T13:45:30.6170000 -> 6<br /><br /> 2009-06-15T13:45:30.05 -> 0|  
|"ff"|Tarih ve saat değerindeki saniyenin yüzde biri.<br /><br /> Daha fazla bilgi: ["Ff" özel biçim belirticisi](#ffSpecifier).|2009-06-15T13:45:30.6170000 -> 61<br /><br /> 2009-06-15T13:45:30.0050000 -> 00|  
|"fff"|Tarih ve saat değerindeki milisaniye.<br /><br /> Daha fazla bilgi: ["Fff" özel biçim belirticisi](#fffSpecifier).|6/15/2009 13:45:30.617 -> 617<br /><br /> 6/15/2009 13:45:30.0005 -> 000|  
|"ffff"|Saniyenin on binde birindeki tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["Ffff" özel biçim belirticisi](#ffffSpecifier).|2009-06-15T13:45:30.6175000 6175 -&GT;<br /><br /> 2009-06-15T13:45:30.0000500  -> 0000|  
|"fffff"|Tarih ve saat değerindeki saniyenin yüz binde biri.<br /><br /> Daha fazla bilgi: ["Fffff" özel biçim belirticisi](#fffffSpecifier).|2009-06-15T13:45:30.6175400 -> 61754<br /><br /> 6/15/2009 13:45:30.000005 -> 00000|  
|"ffffff"|Tarih ve saat değerindeki saniyenin milyonda biri.<br /><br /> Daha fazla bilgi: ["Ffffff" özel biçim belirticisi](#ffffffSpecifier).|2009-06-15T13:45:30.6175420 -> 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> 000000|  
|"fffffff"|Saniyenin on milyonda birindeki tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["Fffffff" özel biçim belirticisi](#fffffffSpecifier).|2009-06-15T13:45:30.6175425 -> 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -> 0001150|  
|"F"|Sıfır olmayan, saniyenin onda biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["F" özel biçim belirticisi](#F_Specifier).|2009-06-15T13:45:30.6170000 -> 6<br /><br /> 2009-06-15T13:45:30.0500000 -> (çıktı)|  
|"FF"|Sıfır olmayan, saniyenin yüzde biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FF" özel biçim belirticisi](#FF_Specifier).|2009-06-15T13:45:30.6170000 -> 61<br /><br /> 2009-06-15T13:45:30.0050000 -> (çıktı)|  
|"FFF"|Sıfır olmayan, milisaniye cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFF" özel biçim belirticisi](#FFF_Specifier).|2009-06-15T13:45:30.6170000 -> 617<br /><br /> 2009-06-15T13:45:30.0005000 -> (çıktı)|  
|"FFFF"|Sıfır olmayan, saniyenin on binde biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFFF" özel biçim belirticisi](#FFFF_Specifier).|2009-06-15T13:45:30.5275000 5275 -&GT;<br /><br /> 2009-06-15T13:45:30.0000500 -> (çıktı)|  
|"FFFFF"|Sıfır olmayan, saniyenin yüz binde biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFFFF" özel biçim belirticisi](#FFFFF_Specifier).|2009-06-15T13:45:30.6175400 -> 61754<br /><br /> 2009-06-15T13:45:30.0000050 -> (çıktı)|  
|"FFFFFF"|Sıfır olmayan, saniyenin milyonda birinde cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFFFFF" özel biçim belirticisi](#FFFFFF_Specifier).|2009-06-15T13:45:30.6175420 -> 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> (çıktı)|  
|"FFFFFFF"|Sıfır olmayan, saniyenin on milyonda biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFFFFFF" özel biçim belirticisi](#FFFFFFF_Specifier).|2009-06-15T13:45:30.6175425 -> 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -> 000115|  
|"g", "gg"|Süre veya dönem.<br /><br /> Daha fazla bilgi: ["g" veya "gg" özel biçim belirticisi](#gSpecifier).|2009-06-15T13:45:30.6170000 M.S. -&GT;|  
|"h"|Saat, 12 saatlik biçimde, 1 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["H" özel biçim belirticisi](#hSpecifier).|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 1|  
|"hh"|Saat, 12 saatlik biçimde, 01 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["Hh" özel biçim belirticisi](#hhSpecifier).|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 01|  
|"H"|Kullanarak bir 24 saatlik 0 ile 23 saat.<br /><br /> Daha fazla bilgi: ["H" özel biçim belirticisi](#H_Specifier).|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 13|  
|"HH"|Saat, 24 saatlik biçimde, 00 ile 23 arasında.<br /><br /> Daha fazla bilgi: ["HH" özel biçim belirticisi](#HH_Specifier).|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 13|  
|"K"|Saat dilimi bilgileri.<br /><br /> Daha fazla bilgi: ["K" özel biçim belirticisi](#KSpecifier).|İle <xref:System.DateTime> değerler:<br /><br /> 2009-06-15T13:45:30, belirtilmeyen türü -><br /><br /> 2009-06-15T13:45:30, tür Utc Z -><br /><br /> 2009-06-15T13:45:30, tür yerel ->-07: 00 (yerel bilgisayar ayarlarına bağlıdır)<br /><br /> İle <xref:System.DateTimeOffset> değerler:<br /><br /> 2009-06-15T01:45:30-07:00 --> -07:00<br /><br /> 2009-06-15T08:45:30+00:00 --> +00:00|  
|"m"|Dakika, 0 ile 59 arasında.<br /><br /> Daha fazla bilgi: ["M" özel biçim belirticisi](#mSpecifier).|2009-06-15T01:09:30 9 -&GT;<br /><br /> 2009-06-15T13:29:30 -> 29|  
|"mm"|Dakika, 00 ile 59 arasında.<br /><br /> Daha fazla bilgi: ["Aa" özel biçim belirticisi](#mmSpecifier).|2009-06-15T01:09:30 -> 09<br /><br /> 2009-06-15T01:45:30 -> 45|  
|"M"|Ay, 1 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["M" özel biçim belirticisi](#M_Specifier).|2009-06-15T13:45:30 -> 6|  
|"AA"|Ay, 01 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["Aa" özel biçim belirticisi](#MM_Specifier).|2009-06-15T13:45:30 -> 06|  
|"AAA"|Ayın kısaltılmış adı.<br /><br /> Daha fazla bilgi: ["Aaa" özel biçim belirticisi](#MMM_Specifier).|2009-06-15T13:45:30 -> Haz (en-US)<br /><br /> 2009-06-15T13:45:30 -> juin (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> Haz (zu-ZA)|  
|"AAAA"|Ayın tam adı.<br /><br /> Daha fazla bilgi: ["Aaaa" özel biçim belirticisi](#MMMM_Specifier).|2009-06-15T13:45:30 -> Haziran (en-US)<br /><br /> 2009-06-15T13:45:30 -> juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> uJuni (zu-ZA)|  
|"s"|Saniye, 0'dan 59'a kadardır.<br /><br /> Daha fazla bilgi: ["S" özel biçim belirticisi](#sSpecifier).|2009-06-15T13:45:09 9 -&GT;|  
|"ss"|Saniye, 00'dan 59'a kadardır.<br /><br /> Daha fazla bilgi: ["Ss" özel biçim belirticisi](#ssSpecifier).|2009-06-15T13:45:09 09 -&GT;|  
|"t"|AM/PM göstergesinin ilk karakteri.<br /><br /> Daha fazla bilgi: ["T" özel biçim belirticisi](#tSpecifier).|2009-06-15T13:45:30 -> P (en-US)<br /><br /> 2009-06-15T13:45:30 -> 午 (ja-JP)<br /><br /> 2009-06-15T13:45:30 -> (fr-FR)|  
|"tt"|AM/PM göstergesi.<br /><br /> Daha fazla bilgi: ["Tt" özel biçim belirticisi](#ttSpecifier).|2009-06-15T13:45:30 -> PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> 午後 (ja-JP)<br /><br /> 2009-06-15T13:45:30 -> (fr-FR)|  
|"y"|0 dan 99 'a kadar yıl.<br /><br /> Daha fazla bilgi: ["Y" özel biçim belirticisi](#ySpecifier).|0001-01-01T00:00:00 -> 1<br /><br /> 0900-01-01T00:00:00 -> 0<br /><br /> 1900-01-01T00:00:00 -> 0<br /><br /> 2009-06-15T13:45:30 -> 9<br /><br /> 2019-06-15T13:45:30 -> 19|  
|"yy"|00 dan 99 'a kadar yıl.<br /><br /> Daha fazla bilgi: ["Yy" özel biçim belirticisi](#yySpecifier).|0001-01-01T00:00:00 -> 01<br /><br /> 0900-01-01T00:00:00 -> 00<br /><br /> 1900-01-01T00:00:00 -> 00<br /><br /> 2019-06-15T13:45:30 -> 19|  
|"yyy"|En az üç basamaklı olarak yıl.<br /><br /> Daha fazla bilgi: ["Yyy" özel biçim belirticisi](#yyySpecifier).|0001-01-01T00:00:00 -> 001<br /><br /> 0900-01-01T00:00:00 -> 900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -> 2009|  
|"yyyy"|Dört basamaklı bir sayı olarak yıl.<br /><br /> Daha fazla bilgi: ["Yyyy" özel biçim belirticisi](#yyyySpecifier).|0001-01-01T00:00:00 -> 0001<br /><br /> 0900-01-01T00:00:00 -> 0900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -> 2009|  
|"yyyyy"|Beş basamaklı bir sayı olarak yıl.<br /><br /> Daha fazla bilgi: ["Yyyyy" özel biçim belirticisi](#yyyyySpecifier).|0001-01-01T00:00:00 -> 00001<br /><br /> 2009-06-15T13:45:30 -> 02009|  
|"z"|Önünde sıfır olmadan UTC biçiminden saat uzaklığı.<br /><br /> Daha fazla bilgi: ["Z" özel biçim belirticisi](#zSpecifier).|2009-06-15T13:45:30-07:00 -> -7|  
|"zz"|Önünde sıfır bulunan tek basamaklı değerden oluşan UTC biçiminden saat uzaklığı.<br /><br /> Daha fazla bilgi: ["Zz" özel biçim belirticisi](#zzSpecifier).|2009-06-15T13:45:30-07:00 -> -07|  
|"zzz"|UTC biçiminden saat ve dakika uzaklığı.<br /><br /> Daha fazla bilgi: ["Zzz" özel biçim belirticisi](#zzzSpecifier).|2009-06-15T13:45:30-07:00 -> -07:00|  
|":"|Zaman ayırıcı.<br /><br /> Daha fazla bilgi: [":" özel biçim belirticisi](#timeSeparator).|2009-06-15T13:45:30 ->: (en-US)<br /><br /> 2009-06-15T13:45:30 -&GT;. (it-IT)<br /><br /> 2009-06-15T13:45:30 ->: (ja-JP)|  
|"/"|Tarih ayırıcı.<br /><br /> Daha fazla bilgi: ["/" özel biçim belirticisi](#dateSeparator).|2009-06-15T13:45:30 -> / (en-US)<br /><br /> 2009-06-15T13:45:30 -> - (ar-DZ)<br /><br /> 2009-06-15T13:45:30 -&GT;. (tr-TR)|  
|"*dize*"<br /><br /> '*dize*'|Değişmez dize sınırlayıcısı.<br /><br /> Daha fazla bilgi: [karakter değişmez değerleri](#Literals).|2009-06-15T13:45:30 ("arr:" h:m t) arr ->: 1:45 P<br /><br /> 2009-06-15T13:45:30 ('arr:' h:m t) arr ->: 1:45 P|  
|%|Aşağıdaki karakteri özel biçim belirticisi olarak tanımlar.<br /><br /> Daha fazla bilgi:[kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers).|2009-06-15T13:45:30 (%h) -> 1|  
|\\| Kaçış karakteri.<br /><br /> Daha fazla bilgi: [karakter değişmez değerleri](#Literals) ve [kaçış karakteri kullanarak](#escape).|2009-06-15T13:45:30 (h \h) -> 1 h|  
|Başka bir karakter|Karakter, değişmeyen sonuç dizesine kopyalanır.<br /><br /> Daha fazla bilgi: [karakter değişmez değerleri](#Literals).|2009-06-15T01:45:30 (arr ss: dd t) -> arr 01: 45 A|  
  
 Aşağıdaki bölümlerde, her özel tarih ve saat biçim belirticisi hakkında ek bilgi sağlanır. Aksi belirtilmediği sürece, her tanımlayıcısı ile mi kullanılacağını bakılmaksızın bir aynı dize gösterimini üreten bir <xref:System.DateTime> değeri veya <xref:System.DateTimeOffset> değeri.  
  
<a name="dSpecifier"></a>   
## <a name="the-d-custom-format-specifier"></a>"D" özel biçim belirticisi  
 "d" özel biçim belirticisi, 1 ile 31 arasında bir sayı olarak ayın gününü temsil eder. Tek basamaklı gün önünde sıfır olmadan biçimlendirilir.  
  
 "d" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, "d" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 Aşağıdaki örnek birçok biçim dizesinde "d" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#1)]
 [!code-vb[Formatting.DateAndTime.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#1)]  
  
 [Tablo dön](#table)  
  
<a name="ddSpecifier"></a>   
## <a name="the-dd-custom-format-specifier"></a>"Aa" özel biçim belirticisi  
 "dd" özel biçim dizesi, 01 ile 31 arasında bir sayı olarak ayın gününü temsil eder. Tek basamaklı gün önünde sıfır ile biçimlendirilir.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "dd" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]  
  
 [Tablo dön](#table)  
  
<a name="dddSpecifier"></a>   
## <a name="the-ddd-custom-format-specifier"></a>"Ggg" özel biçim belirticisi  
 "ddd" özel biçim belirticisi haftanın gününün kısaltılmış adını temsil eder. Haftanın günü yerelleştirilmiş kısaltılmış adı alınır <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültür özelliği.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "ddd" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
 [!code-vb[Formatting.DateAndTime.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]  
  
 [Tablo dön](#table)  
  
<a name="ddddSpecifier"></a>   
## <a name="the-dddd-custom-format-specifier"></a>"Dddd" özel biçim belirticisi  
 "dddd" özel biçim belirticisi (artı herhangi bir sayıda ek "d" tanımlayıcısı) haftanın gününün tam adını temsil eder. Haftanın günü yerelleştirilmiş adı alınır <xref:System.Globalization.DateTimeFormatInfo.DayNames%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültür özelliği.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "dddd" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
 [!code-vb[Formatting.DateAndTime.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]  
  
 [Tablo dön](#table)  
  
<a name="fSpecifier"></a>   
## <a name="the-f-custom-format-specifier"></a>"F" özel biçim belirticisi  
 "f" özel biçim belirticisi saniye bölümünün en önemli basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin onda birini temsil eder.  
  
 "f" biçim belirticisi diğer biçim belirticileri olmadan kullanıldığında, "f" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 Kullandığınızda, "f" biçim belirticileri için sağlanan biçim dizesi bir parçası olarak <xref:System.DateTime.ParseExact%2A>, <xref:System.DateTime.TryParseExact%2A>, <xref:System.DateTimeOffset.ParseExact%2A>, veya <xref:System.DateTimeOffset.TryParseExact%2A> yöntemi, "f" biçim belirticileri sayısı saniye kesir, çoğu önemli basamak sayısını belirtir başarılı bir şekilde dizesini ayrıştırmak için mevcut olması gerekir.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "f" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Tablo dön](#table)  
  
<a name="ffSpecifier"></a>   
## <a name="the-ff-custom-format-specifier"></a>"Ff" özel biçim belirticisi  
 "ff" özel biçim belirticisi saniye bölümünün en önemli iki basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüzde birini temsil eder.  
  
 Aşağıdaki örnek, özel biçim dizesindeki "ff" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Tablo dön](#table)  
  
<a name="fffSpecifier"></a>   
## <a name="the-fff-custom-format-specifier"></a>"Fff" özel biçim belirticisi  
 "fff" özel biçim belirticisi saniye bölümünün en önemli üç basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin binde birini temsil eder.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "fff" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Tablo dön](#table)  
  
<a name="ffffSpecifier"></a>   
## <a name="the-ffff-custom-format-specifier"></a>"Ffff" özel biçim belirticisi  
 "ffff" özel biçim belirticisi saniye bölümünün en önemli dört basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on binde birini temsil eder.  
  
 Bir zaman değerinin saniye bileşenini, on binde bir duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 sürümünde (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.  
  
 [Tablo dön](#table)  
  
<a name="fffffSpecifier"></a>   
## <a name="the-fffff-custom-format-specifier"></a>"Fffff" özel biçim belirticisi  
 "fffff" özel biçim belirticisi saniye bölümünün en önemli beş basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüz binde birini temsil eder.  
  
 Bir zaman değerine ait saniye bileşenini binde yüz duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.  
  
 [Tablo dön](#table)  
  
<a name="ffffffSpecifier"></a>   
## <a name="the-ffffff-custom-format-specifier"></a>"Ffffff" özel biçim belirticisi  
 "ffffff" özel biçim belirticisi saniye bölümünün en önemli altı basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin milyonda birini temsil eder.  
  
 Bir zaman değerine ait saniye bileşenini milyonda bir duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.  
  
 [Tablo dön](#table)  
  
<a name="fffffffSpecifier"></a>   
## <a name="the-fffffff-custom-format-specifier"></a>"Fffffff" özel biçim belirticisi  
 "fffffff" özel biçim belirticisi saniye bölümünün en önemli yedi basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on milyonda birini temsil eder.  
  
 Bir zaman değerine ait saniye bileşenini on milyonda bir duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.  
  
 [Tablo dön](#table)  
  
<a name="F_Specifier"></a>   
## <a name="the-f-custom-format-specifier"></a>"F" özel biçim belirticisi  
 "F" özel biçim belirticisi saniye bölümünün en önemli basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin onda birini temsil eder. Basamak sıfırsa hiçbir şey görüntülenmez.  
  
 "F" biçim belirticisi diğer biçim belirticileri olmadan kullanıldığında, "f" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 "F" biçim belirticileri ile kullanılan sayısı <xref:System.DateTime.ParseExact%2A>, <xref:System.DateTime.TryParseExact%2A>, <xref:System.DateTimeOffset.ParseExact%2A>, veya <xref:System.DateTimeOffset.TryParseExact%2A> yöntemi başarıyla dizesini ayrıştırmak için mevcut olabilecek saniye kesir, çoğu önemli basamak sayısını gösterir.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "F" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Tablo dön](#table)  
  
<a name="FF_Specifier"></a>   
## <a name="the-ff-custom-format-specifier"></a>"FF" özel biçim belirticisi  
 "FF" özel biçim belirticisi saniye bölümünün en önemli iki basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüzde birini temsil eder. Ancak öndeki sıfırlar veya iki sıfır basamak görüntülenmez.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "FF" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Tablo dön](#table)  
  
<a name="FFF_Specifier"></a>   
## <a name="the-fff-custom-format-specifier"></a>"FFF" özel biçim belirticisi  
 "FFF" özel biçim belirticisi saniye bölümünün en önemli üç basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin binde birini temsil eder. Ancak öndeki sıfırlar veya üç sıfır basamak görüntülenmez.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "FFF" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Tablo dön](#table)  
  
<a name="FFFF_Specifier"></a>   
## <a name="the-ffff-custom-format-specifier"></a>"FFFF" özel biçim belirticisi  
 "FFFF" özel biçim belirticisi saniye bölümünün en önemli dört basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on binde birini temsil eder. Ancak öndeki sıfırlar veya dört sıfır basamak görüntülenmez.  
  
 Bir zaman değerinin saniye bileşenini, on binde bir duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.  
  
 [Tablo dön](#table)  
  
<a name="FFFFF_Specifier"></a>   
## <a name="the-fffff-custom-format-specifier"></a>"FFFFF" özel biçim belirticisi  
 "FFFFF" özel biçim belirticisi saniye bölümünün en önemli beş basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüz binde birini temsil eder. Ancak öndeki sıfırlar veya beş sıfır basamak görüntülenmez.  
  
 Bir zaman değerine ait saniye bileşenini binde yüz duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.  
  
 [Tablo dön](#table)  
  
<a name="FFFFFF_Specifier"></a>   
## <a name="the-ffffff-custom-format-specifier"></a>"FFFFFF" özel biçim belirticisi  
 "FFFFFF" özel biçim belirticisi saniye bölümünün en önemli altı basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin milyonda birini temsil eder. Ancak öndeki sıfırlar veya altı sıfır basamak görüntülenmez.  
  
 Bir zaman değerine ait saniye bileşenini milyonda bir duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.  
  
 [Tablo dön](#table)  
  
<a name="FFFFFFF_Specifier"></a>   
## <a name="the-fffffff-custom-format-specifier"></a>"FFFFFFF" özel biçim belirticisi  
 "FFFFFFF" özel biçim belirticisi saniye bölümünün en önemli yedi basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on milyonda birini temsil eder. Ancak öndeki sıfırlar veya yedi sıfır basamak görüntülenmez.  
  
 Bir zaman değerine ait saniye bileşenini on milyonda bir duyarlılığıyla görüntülemek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.  
  
 [Tablo dön](#table)  
  
<a name="gSpecifier"></a>   
## <a name="the-g-or-gg-custom-format-specifier"></a>"G" veya "gg" özel biçim belirticisi  
 "g" veya "gg" özel biçim belirticileri (artı herhangi bir sayıda ek "g" belirticisi) M.S. gibi bir dönem veya çağı temsil eder Biçimlendirilecek tarih ilişkili bir dönem veya çağ dizesine sahip değilse, biçimlendirme işlemi bu belirticiyi yok sayar.  
  
 "g" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, "g" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "g" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#6)]
 [!code-vb[Formatting.DateAndTime.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#6)]  
  
 [Tablo dön](#table)  
  
<a name="hSpecifier"></a>   
## <a name="the-h-custom-format-specifier"></a>"Y" özel biçim belirticisi  
 "h" özel biçim belirticisi 1 ile 12 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, saatleri gece yarısından veya öğleden itibaren tam saatleri sayan 12 saatlik zaman biçimi ile temsil edilir. Gece yarısından sonraki bir saat, öğleden sonraki aynı saatle ayırt edilemez. Saat yuvarlanmaz ve önünde sıfır olmadan tek basamaklı bir saat biçimlendirilir. Örneğin, sabah veya öğleden sonra 5:43 saati verildiğinde bu özel biçim belirtici "5" görüntüler.  
  
 "H" biçim belirteci diğer özel biçim belirticileri kullanılırsa, standart tarih ve saat biçim belirticisi yorumlanır ve oluşturur bir <xref:System.FormatException>. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "h" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]  
  
 [Tablo dön](#table)  
  
<a name="hhSpecifier"></a>   
## <a name="the-hh-custom-format-specifier"></a>"Hh" özel biçim belirticisi  
 "hh" özel biçim belirticisi (artı herhangi bir sayıda ek "h" belirticisi) 01 ile 12 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, tam saatleri gece yarısından veya öğleden itibaren sayan 12 saatlik zaman biçimi ile temsil edilir. Gece yarısından sonraki bir saat, öğleden sonraki aynı saatle ayırt edilemez. Saat yuvarlanmaz ve önünde sıfır ile birlikte tek basamaklı bir saat biçimlendirilir. Örneğin, sabah veya öğleden sonra 5:43 saati verildiğinde bu biçim belirtici "05" görüntüler.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "hh" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]  
  
 [Tablo dön](#table)  
  
<a name="H_Specifier"></a>   
## <a name="the-h-custom-format-specifier"></a>"Y" özel biçim belirticisi  
 "H" özel biçim belirticisi 0 ile 23 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, saatleri gece yarısından itibaren sayan sıfır tabanlı bir 24 saatlik zaman biçimi ile temsil edilir. Tek basamaklı saat önünde sıfır olmadan biçimlendirilir.  
  
 "Y" biçim belirticisi diğer özel biçim belirticileri kullanılırsa, standart tarih ve saat biçim belirticisi yorumlanır ve oluşturur bir <xref:System.FormatException>. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "H" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#9)]
 [!code-vb[Formatting.DateAndTime.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#9)]  
  
 [Tablo dön](#table)  
  
<a name="HH_Specifier"></a>   
## <a name="the-hh-custom-format-specifier"></a>"HH" özel biçim belirticisi  
 "HH" özel biçim belirticisi (artı herhangi bir sayıda ek "H" belirticisi) 00 ile 23 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, saatleri gece yarısından itibaren sayan sıfır tabanlı bir 24 saatlik zaman biçimi ile temsil edilir. Tek basamaklı saat önünde sıfır ile biçimlendirilir.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "HH" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#10)]
 [!code-vb[Formatting.DateAndTime.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#10)]  
  
 [Tablo dön](#table)  
  
<a name="KSpecifier"></a>   
## <a name="the-k-custom-format-specifier"></a>"K" özel biçim belirticisi  
 "K" özel biçim belirticisi bir tarih ve saat değerinin saat dilimi bilgisini temsil eder. İle birlikte bu biçim belirticisi kullanıldığında <xref:System.DateTime> değerleri, sonuç dize değeri tarafından tanımlanan <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği:  
  
-   Yerel saat dilimi için (bir <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik değerinin <xref:System.DateTimeKind.Local?displayProperty=nameWithType>), bu belirticisi "zzz" belirticisi eşdeğerdir ve Eşgüdümlü Evrensel Saat (UTC gelen); uzaklık yerel içeren bir sonuç dizesini üretir Örneğin, "-07: 00".  
  
-   UTC saati için (bir <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik değerinin <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), UTC tarihi temsil etmek için "Z" karakteri Sonuç dizesini içerir.  
  
-   Belirtilmeyen bir saat dilimi zamandan için (bir saat olan <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği eşittir <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>), sonuç eşdeğerdir <xref:System.String.Empty?displayProperty=nameWithType>.  
  
 İçin <xref:System.DateTimeOffset> değerleri, "K" biçim belirticisi "zzz" biçim belirteci eşdeğerdir ve bir sonuç dizeyi içeren üretir <xref:System.DateTimeOffset> değer UTC uzaklığı.  
  
 "K" biçim belirticisi diğer özel biçim belirticileri kullanılırsa, standart tarih ve saat biçim belirticisi yorumlanır ve oluşturur bir <xref:System.FormatException>. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 Aşağıdaki örnek sonuçları çeşitli "K" özel biçim tanımlayıcısı kullanılarak dize görüntüler <xref:System.DateTime> ve <xref:System.DateTimeOffset> ABD sisteminde değerleri Pasifik Saat dilimi.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#12)]
 [!code-vb[Formatting.DateAndTime.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#12)]  
  
 [Tablo dön](#table)  
  
<a name="mSpecifier"></a>   
## <a name="the-m-custom-format-specifier"></a>"M" özel biçim belirticisi  
 "m" özel biçim belirticisi, 0 ile 59 arasında bir sayı olarak dakikayı temsil eder. Dakika, son saatten beri geçen tam dakikaları temsil eder. Tek basamaklı dakika önünde sıfır olmadan biçimlendirilir.  
  
 "m" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, "m" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "m" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]  
  
 [Tablo dön](#table)  
  
<a name="mmSpecifier"></a>   
## <a name="the-mm-custom-format-specifier"></a>"Aa" özel belirleyici biçimlendirme  
 "m" özel biçim belirticisi (artı herhangi bir sayıda ek "m" belirticisi) 00 ile 59 arasında bir sayı olarak dakikayı temsil eder. Dakika, son saatten beri geçen tam dakikaları temsil eder. Tek basamaklı dakika önünde sıfır ile biçimlendirilir.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "mm" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]  
  
 [Tablo dön](#table)  
  
<a name="M_Specifier"></a>   
## <a name="the-m-custom-format-specifier"></a>"M" özel biçim belirticisi  
 "M" özel biçim belirticisi, 1 ile 12 arasında (veya 13 ay içeren takvimler için 1 ile 13 arasında) bir sayı olarak ayı temsil eder. Tek basamaklı ay önünde sıfır olmadan biçimlendirilir.  
  
 "M" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, "M" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "M" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#11)]
 [!code-vb[Formatting.DateAndTime.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#11)]  
  
 [Tablo dön](#table)  
  
<a name="MM_Specifier"></a>   
## <a name="the-mm-custom-format-specifier"></a>"Aa" özel biçim belirticisi  
 "MM" özel biçim belirticisi, 01 ile 12 arasında (veya 13 ay içeren takvimler için 1 ile 13 arasında) bir sayı olarak ayı temsil eder. Tek basamaklı ay önünde sıfır ile biçimlendirilir.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "MM" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]  
  
 [Tablo dön](#table)  
  
<a name="MMM_Specifier"></a>   
## <a name="the-mmm-custom-format-specifier"></a>"Aaa" özel biçim belirticisi  
 "MMM" özel biçim belirticisi ayın gününün kısaltılmış adını temsil eder. Ayın yerelleştirilmiş kısaltılmış adı alınır <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültür özelliği.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "MMM" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
 [!code-vb[Formatting.DateAndTime.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]  
  
 [Tablo dön](#table)  
  
<a name="MMMM_Specifier"></a>   
## <a name="the-mmmm-custom-format-specifier"></a>"Aaaa" özel biçim belirticisi  
 "MMMM" özel biçim belirticisi ayın gününün tam adını temsil eder. Ayın yerelleştirilmiş adı alınır <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültür özelliği.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "MMMM" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
 [!code-vb[Formatting.DateAndTime.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]  
  
 [Tablo dön](#table)  
  
<a name="sSpecifier"></a>   
## <a name="the-s-custom-format-specifier"></a>"S" özel biçim belirticisi  
 "s" özel biçim belirticisi, 0 ile 59 arasında bir sayı olarak saniyeyi temsil eder. Sonuç, son dakikadan beri geçen tam saniyeleri temsil eder. Tek basamaklı saniye önünde sıfır olmadan biçimlendirilir.  
  
 "s" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, "s" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "s" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]  
  
 [Tablo dön](#table)  
  
<a name="ssSpecifier"></a>   
## <a name="the-ss-custom-format-specifier"></a>"Ss" özel biçim belirticisi  
 "ss" özel biçim belirticisi (artı herhangi bir sayıda ek "s" belirticisi) 00 ile 59 arasında bir sayı olarak saniyeyi temsil eder. Sonuç, son dakikadan beri geçen tam saniyeleri temsil eder. Tek basamaklı saniye önünde sıfır ile biçimlendirilir.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "ss" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]  
  
 [Tablo dön](#table)  
  
<a name="tSpecifier"></a>   
## <a name="the-t-custom-format-specifier"></a>"T" özel biçim belirticisi  
 "t" özel biçim belirticisi AM/PM göstergelerinin ilk karakterini temsil eder. Uygun yerelleştirilmiş Belirleyicisi alınır <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> veya <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> geçerli ya da belirli kültür özelliği. AM göstergesi, 0:00:00 (gece yarısı) ile 11:59:59.999 arasındaki tüm zamanlar için kullanılır. PM göstergesi, 12:00:00 (öğlen) ile 23:59:59.999 arasındaki tüm zamanlar için kullanılır.  
  
 "t" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, "t" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "t" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]  
  
 [Tablo dön](#table)  
  
<a name="ttSpecifier"></a>   
## <a name="the-tt-custom-format-specifier"></a>"Tt" özel biçim belirticisi  
 "tt" özel biçim belirticisi (artı herhangi bir sayıda ek "t" belirticisi) tüm AM/PM göstergelerini temsil eder. Uygun yerelleştirilmiş Belirleyicisi alınır <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> veya <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> geçerli ya da belirli kültür özelliği. AM göstergesi, 0:00:00 (gece yarısı) ile 11:59:59.999 arasındaki tüm zamanlar için kullanılır. PM göstergesi, 12:00:00 (öğlen) ile 23:59:59.999 arasındaki tüm zamanlar için kullanılır.  
  
 AM ve PM arasında ayrım yapılması gereken diller için "tt" belirticisini kullandığınızdan emin olun. Japonca buna bir örnektir; AM ve PM göstergeleri birinci karakter yerine ikinci karakterde farklılık gösterir.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "tt" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]  
  
 [Tablo dön](#table)  
  
<a name="ySpecifier"></a>   
## <a name="the-y-custom-format-specifier"></a>"Y" özel biçim belirticisi  
 "y" özel biçim belirticisi tek basamaklı veya iki basamaklı bir sayı olarak yılı temsil eder. Yılda ikiden fazla basamak varsa, yalnızca son kısımdaki iki basamak sonuçta görünür. İki basamaklı yılın ilk basamağı sıfır ise (örneğin, 2008), sayı önünde sıfır olmadan biçimlendirilir.  
  
 "y" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, "y" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "y" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Tablo dön](#table)  
  
<a name="yySpecifier"></a>   
## <a name="the-yy-custom-format-specifier"></a>"Yy" özel biçim belirticisi  
 "yy" özel biçim belirticisi iki basamaklı bir sayı olarak yılı temsil eder. Yılda ikiden fazla basamak varsa, yalnızca son kısımdaki iki basamak sonuçta görünür. İki basamaklı yılda ikiden az belirtici basamak varsa, iki basamak oluşturulabilmesi için sayının önüne sıfır eklenir.  
  
 Bir ayrıştırma işlemi "yy" özel biçim tanımlayıcısı kullanılarak ayrıştırılır iki rakamlı yıl dayalı olarak yorumlanır <xref:System.Globalization.Calendar.TwoDigitYearMax%2A?displayProperty=nameWithType> biçimi sağlayıcının geçerli Takvim özelliği. Aşağıdaki örnek, bu durumda en-US kültürü olan geçerli kültürün varsayılan Gregoryen takvimini kullanarak iki basamaklı yıl içeren bir tarih dize gösterimini ayrıştırır. Ardından geçerli kültürün değiştirir <xref:System.Globalization.CultureInfo> nesnesi bir <xref:System.Globalization.GregorianCalendar> nesnesindeki <xref:System.Globalization.GregorianCalendar.TwoDigitYearMax%2A> özelliğini değiştirdi.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#19](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/parseexact2digityear1.cs#19)]
 [!code-vb[Formatting.DateAndTime.Custom#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/parseexact2digityear1.vb#19)]  
  
 Aşağıdaki örnek bir özel biçim dizesinde "yy" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Tablo dön](#table)  
  
<a name="yyySpecifier"></a>   
## <a name="the-yyy-custom-format-specifier"></a>"Yyy" özel biçim belirticisi  
 "yyy" özel biçim belirticisi en az üç basamakla yılı temsil eder. Yılda üçten fazla belirtici basamak varsa, bunlar sonuç dizesine eklenir. Yıl üçten az basamaktan oluşuyorsa, üç basamak oluşturulabilmesi için sayının önüne sıfır eklenir.  
  
> [!NOTE]
>  Beş basamaklı yıllar içeren Thai Budist takvimi için bu biçim belirtici tüm basamakları görüntüler.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "yyy" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Tablo dön](#table)  
  
<a name="yyyySpecifier"></a>   
## <a name="the-yyyy-custom-format-specifier"></a>"Yyyy" özel biçim belirticisi  
 "yyyy" özel biçim belirticisi en az dört basamakla yılı temsil eder. Yılda dörtten fazla belirtici basamak varsa, bunlar sonuç dizesine eklenir. Yıl dörtten az basamaktan oluşuyorsa, dört basamak oluşturulabilmesi için sayının önüne sıfır eklenir.  
  
> [!NOTE]
>  Beş basamaklı yıllar içeren Thai Budist takvimi için bu biçim belirtici en az dört basamak görüntüler.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "yyyy" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Tablo dön](#table)  
  
<a name="yyyyySpecifier"></a>   
## <a name="the-yyyyy-custom-format-specifier"></a>"Yyyyy" özel biçim belirticisi  
 "yyyyy" özel biçim belirticisi (artı herhangi bir sayıda ek "y" belirticisi) en az beş basamakla yılı temsil eder. Yılda beşten fazla belirtici basamak varsa, bunlar sonuç dizesine eklenir. Yıl beşten az basamaktan oluşuyorsa, beş basamak oluşturulabilmesi için sayının önüne sıfır eklenir.  
  
 Ek "y" belirticileri varsa sayının önüne "y" belirticileriyle aynı sayıda olacak kadar sıfır eklenir.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "yyyyy" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Tablo dön](#table)  
  
<a name="zSpecifier"></a>   
## <a name="the-z-custom-format-specifier"></a>"Z" özel biçim belirticisi  
 İle <xref:System.DateTime> değerleri, "z" özel biçim belirticisi temsil yerel işletim sisteminin saat dilimi imzalı uzaklığını gelen Eşgüdümlü Evrensel Saat saat cinsinden ölçülen, (UTC). Bir örneğinin değerini yansıtmaz <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği. Bu nedenle, "z" biçim belirteci ile kullanım için önerilmez <xref:System.DateTime> değerleri.  
  
 İle <xref:System.DateTimeOffset> değerleri, bu biçim belirticisi temsil <xref:System.DateTimeOffset> aralık değeri UTC saat.  
  
 Uzaklık her zaman önünde bir işaretle görüntülenir. Artı işareti (+) UTC'den önceki saatleri belirtir, eksi işareti (-) UTC'den sonraki saatleri belirtir. Tek basamaklı sapma önünde sıfır olmadan biçimlendirilir.  
  
 "Z" biçim belirticisi diğer özel biçim belirticileri kullanılırsa, standart tarih ve saat biçim belirticisi yorumlanır ve oluşturur bir <xref:System.FormatException>. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "z" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]  
  
 [Tablo dön](#table)  
  
<a name="zzSpecifier"></a>   
## <a name="the-zz-custom-format-specifier"></a>"Zz" özel biçim belirticisi  
 İle <xref:System.DateTime> değerleri, "zz" özel biçim belirleyici temsil yerel işletim sisteminin saat dilimi imzalı uzaklığı, UTC saat cinsinden ölçülür. Bir örneğinin değerini yansıtmaz <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği. Bu nedenle, "zz" biçim belirteci ile kullanım için önerilmez <xref:System.DateTime> değerleri.  
  
 İle <xref:System.DateTimeOffset> değerleri, bu biçim belirticisi temsil <xref:System.DateTimeOffset> aralık değeri UTC saat.  
  
 Uzaklık her zaman önünde bir işaretle görüntülenir. Artı işareti (+) UTC'den önceki saatleri belirtir, eksi işareti (-) UTC'den sonraki saatleri belirtir. Tek basamaklı sapma önünde sıfır ile biçimlendirilir.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "zz" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]  
  
 [Tablo dön](#table)  
  
<a name="zzzSpecifier"></a>   
## <a name="the-zzz-custom-format-specifier"></a>"Zzz" özel biçim belirticisi  
 İle <xref:System.DateTime> değerleri, "zzz" özel biçim belirticisi temsil yerel işletim sisteminin saat dilimi imzalı uzaklığını UTC, saat ve dakika olarak ölçülür. Bir örneğinin değerini yansıtmaz <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği. Bu nedenle, "zzz" biçim belirteci ile kullanım için önerilmez <xref:System.DateTime> değerleri.  
  
 İle <xref:System.DateTimeOffset> değerleri, bu biçim belirticisi temsil <xref:System.DateTimeOffset> aralık değeri UTC saat ve dakika olarak.  
  
 Uzaklık her zaman önünde bir işaretle görüntülenir. Artı işareti (+) UTC'den önceki saatleri belirtir, eksi işareti (-) UTC'den sonraki saatleri belirtir. Tek basamaklı sapma önünde sıfır ile biçimlendirilir.  
  
 Aşağıdaki örnek bir özel biçim dizesinde "zzz" özel biçim belirticisini içerir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]  
  
 [Tablo dön](#table)  
  
<a name="timeSeparator"></a>   
## <a name="the--custom-format-specifier"></a>":" Özel biçim belirticisi  
 ":" özel biçim belirticisi, saat, dakika ve saniyeyi ayırt etmek için kullanılan zaman ayırıcıyı temsil eder. Uygun yerelleştirilmiş zaman ayırıcı alınır <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültür özelliği.  
  
> [!NOTE]
>  Belirli bir tarih ve saat dizesi için zaman ayırıcı değiştirmek için değişmez değer dize sınırlayıcı içinde ayırıcı karakter belirtin. Örneğin, özel biçim dizesi `hh'_'dd'_'ss` bir sonuç dizesinde üreten "\_" (alt çizgi) her zaman zaman ayırıcı olarak kullanılır. Bir kültür için tüm tarihler için zaman ayırıcı değiştirmek için ya da değerini değiştirmeniz <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> özelliği geçerli kültür ya da örneği bir <xref:System.Globalization.DateTimeFormatInfo> nesnesi, karakteri Ata kendi <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A> özelliği ve bir aşırı yüklemesini çağırın içeren yöntem biçimlendirmeyi bir <xref:System.IFormatProvider> parametresi.  
  
 Varsa ":" standart tarih ve saat biçim belirticisi yorumlanır ve oluşturur biçim belirticisi diğer özel biçim belirticileri kullanıldığında, bir <xref:System.FormatException>. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 [Tablo dön](#table)  
  
<a name="dateSeparator"></a>   
## <a name="the--custom-format-specifier"></a>"/" Özel biçim belirticisi  
 "/" özel biçim belirticisi, yıl, ay ve günü ayırt etmek için kullanılan tarih ayırıcıyı temsil eder. Uygun yerelleştirilmiş tarih ayırıcı alınır <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültür özelliği.  
  
> [!NOTE]
>  Belirli bir tarih ve saat dizesi için tarih ayırıcı değiştirmek için değişmez değer dize sınırlayıcı içinde ayırıcı karakter belirtin. Örneğin, özel biçim dizesi `mm'/'dd'/'yyyy` bir sonuç dizesinde üreten "/" tarih ayırıcı olarak her zaman kullanılır. Bir kültür için tüm tarihler için tarih ayırıcı değiştirmek için ya da değerini değiştirmeniz <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> özelliği geçerli kültür ya da örneği bir <xref:System.Globalization.DateTimeFormatInfo> nesnesi, karakteri Ata kendi <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A> özelliği ve bir aşırı yüklemesini çağırın içeren yöntem biçimlendirmeyi bir <xref:System.IFormatProvider> parametresi.  
  
 "/" Biçim belirticisi diğer özel biçim belirticileri kullanılırsa, standart tarih ve saat biçim belirticisi yorumlanır ve oluşturur bir <xref:System.FormatException>. Tek biçim belirticisi kullanma hakkında daha fazla bilgi için bkz: [kullanarak tek özel biçim belirticileri](#UsingSingleSpecifiers) bu konuda daha sonra.  
  
 [Tablo dön](#table)  
  
<a name="Literals"></a>   
## <a name="character-literals"></a>Karakter değişmez değerleri  
 Aşağıdaki karakterleri özel bir tarih ve saat biçim dizesi ayrılmış ve her zaman yorumlanır olarak biçimlendirme karakterlerini veya durumunda ", ', /, ve \\, özel karakter olarak.  
  
||||||  
|-|-|-|-|-|  
|F|H|K|M|d|  
|F|G|h|m|s|  
|t|y|z|%|:|  
|/|"|'|\||  
  
 Diğer tüm karakterler her zaman karakter değişmez değerleri yorumlanır ve bir biçimlendirme işleminde değiştirmeden sonuç dizesinde dahil edilir.  Ayrıştırma işleminde, bunlar giriş dizedeki karakter tam olarak eşleşmelidir; Karşılaştırma büyük/küçük harf duyarlıdır.  
  
 Aşağıdaki örnek, bir biçim dizesi yerel saat diliminizde temsil etmek için (Pasifik Standart Saati için) "PST" ve "Saati" (Pasifik Yaz Saati için) değişmez değer karakter içerir. Dize sonuç dizesinde eklenir ve yerel saat dilimi dizesini içeren bir dize de başarıyla ayrıştırmak için kullandığı unutmayın.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx1.cs#20)]
 [!code-vb[Formatting.DateAndTime.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx1.vb#20)]  
  
 Karakterlerin böylece sonuç dizesinde veya başarılı bir şekilde bir giriş dizesi içinde Ayrıştırılan ayırma karakterleri değil de, değişmez değer karakter olarak yorumlanacağını olduğunu göstermek için iki yol vardır:  
  
-   Her kaçış karakteri saklıdır. Daha fazla bilgi için bkz: [kaçış karakteri kullanarak](#escape).  
  
     Aşağıdaki örnekte "pst" değişmez değer karakter (Pasifik Standart Saati için) bir biçim dizesi yerel saat diliminizde temsil etmek için içerir. "S" ve "t" özel biçim dizeleri olduğundan, her iki karakterleri karakter değişmez değerleri yorumlanması için kaçış uygulanmalıdır.  
  
     [!code-csharp[Formatting.DateAndTime.Custom#21](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx2.cs#21)]
     [!code-vb[Formatting.DateAndTime.Custom#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx2.vb#21)]  
  
-   Tüm değişmez değer dize tırnak veya kesme kapsayan tarafından. Tüm ayrılmış dize karakter değişmez değerleri yorumlanması gerektiğini belirtmek için tırnak işaretleri içindeki "pst" arasına aşağıdaki örnek önceki bir gibi olmasıdır.  
  
     [!code-csharp[Formatting.DateAndTime.Custom#22](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx3.cs#22)]
     [!code-vb[Formatting.DateAndTime.Custom#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx3.vb#22)]  
  
<a name="Notes"></a>   
## <a name="notes"></a>Notlar  
  
<a name="UsingSingleSpecifiers"></a>   
### <a name="using-single-custom-format-specifiers"></a>Tek özel biçim belirticilerini kullanma  
 Özel tarih ve saat biçimi dizesi iki veya daha fazla karakterden oluşur. Tarih ve saat biçimlendirme yöntemleri, herhangi tek karakterli dizeyi standart tarih ve saat biçim dizesi olarak yorumlar. Geçerli bir biçim tanımlayıcısı karakterin tanımıyorsanız varsa, bunlar throw bir <xref:System.FormatException>. Örneğin, yalnızca belirleyici "h" içeren bir biçim dizesi standart tarih ve saat biçimi dizesi olarak yorumlanır. Ancak, hiçbir "h" standart tarih ve timeformat belirticisi olduğundan bu örnekte özel durum oluşur.  
  
 Bir biçim dizesinde tek belirleyici olarak özel tarih ve saat biçimi belirleyicilerinden birini kullanmak için ("d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" veya "/" özel biçim belirleyicisinin kendisi), belirleyiciden önce veya sonra bir boşluk bırakın veya tek özel tarih ve saat belirleyicisinden önce yüzde ("%") biçim belirleyicisi ekleyin.  
  
 Örneğin, "`%h"` özel tarih ve saati geçerli tarih ve saat değeri tarafından temsil edilen görüntüler saat biçim dizesi olarak yorumlanır. Sonuç dizesinde saatin yanında bir boşluk içerse de " h" veya "h " biçimlendirme dizisini de kullanabilirsiniz. Aşağıdaki örnek bu üç biçim dizesini gösterir.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/literal1.cs#16)]
 [!code-vb[Formatting.DateAndTime.Custom#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/literal1.vb#16)]  
  
<a name="escape"></a>   
### <a name="using-the-escape-character"></a>Çıkış Karakterini Kullanma  
 Bir biçim dizesindeki "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" veya "/" karakterleri, değişmez karakterler olarak değil özel biçim belirticileri olarak yorumlanır. Bir biçim belirticisi yorumlanan bir karakter önlemek için onu ters bölü işareti koyun (\\), kaçış karakteri olduğu. Çıkış karakteri, aşağıdaki karakterin değiştirilmeden sonuç dizesini dahil edilmesi gereken bir karakter sabiti olduğunu belirtir.  
  
 Bir sonuç dizesi bir ters eğik çizgi eklemek için bunu başka bir ters eğik çizgi kaçış gerekir (`\\`).  
  
> [!NOTE]
>  C++ ve C# derleyicileri gibi bazı derleyiciler, tek bir ters eğik çizgiyi çıkış karakteri olarak yorumlayabilir. Bir dizenin yalnızca düzgün biçimlendirildiğinde yorumlanmasını sağlamak için C# içinde dizeden önce değişmez değer karakterini (@ karakteri) kullanabilirsiniz veya C# ve C++ içinde her ters eğik çizgiden önce bir ters eğik çizgi daha ekleyebilirsiniz. Aşağıdaki C# örneği her iki yaklaşımı da gösterir.  
  
 Aşağıdaki örnek, biçimlendirme işleminin "h" ve "m" karakterlerini biçim belirticileri olarak yorumlamasını önlemek için çıkış karakteri kullanır.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/escape1.cs#15)]
 [!code-vb[Formatting.DateAndTime.Custom#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/escape1.vb#15)]  
  
### <a name="control-panel-settings"></a>Denetim Masası Ayarları  
 **Bölge ve Dil Seçenekleri** ayarlarını Denetim Masası'nda özel tarih ve saat biçim belirticileri çoğunu içeren biçimlendirme bir işlem tarafından üretilen Sonuç dizesini etkiler. Bu ayarları başlatmak için kullanılan <xref:System.Globalization.DateTimeFormatInfo> biçimlendirme yönetmek için kullanılan değerleri sağlayan geçerli iş parçacığı kültürünü ile ilişkili nesne. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.  
  
 Kullanırsanız, ayrıca, <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> yeni bir örneğini oluşturmak için Oluşturucusu <xref:System.Globalization.CultureInfo> aynı kültür geçerli sistem kültürü tarafından oluşturulan tüm özelleştirmeler olarak temsil eden nesnesi **bölge ve Dil Seçenekleri** Denetim Masası uygulanacak yeni <xref:System.Globalization.CultureInfo> nesnesi. Kullanabileceğiniz <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Oluşturucusu oluşturmak için bir <xref:System.Globalization.CultureInfo> sistemin özelleştirmeleri yansıtmaz nesnesi.  
  
### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo özellikleri  
 Biçimlendirme geçerli özellikleri tarafından Etkileyenler <xref:System.Globalization.DateTimeFormatInfo> örtük olarak geçerli iş parçacığı kültürünü veya açıkça tarafından sağlanan nesne <xref:System.IFormatProvider> biçimlendirme çağıran yönteminin parametresi. İçin <xref:System.IFormatProvider> parametresini belirtmeniz gerekir bir <xref:System.Globalization.CultureInfo> bir kültür temsil eder, nesne veya <xref:System.Globalization.DateTimeFormatInfo> nesnesi.  
  
 Birçok özel tarih ve saat biçim belirticileri tarafından üretilen Sonuç dizesini de geçerli özelliklerine bağlıdır <xref:System.Globalization.DateTimeFormatInfo> nesnesi. Uygulamanızı karşılık gelen değiştirerek bazı özel tarih ve saat biçim belirticileri tarafından üretilen sonuç değiştirebilirsiniz <xref:System.Globalization.DateTimeFormatInfo> özelliği. Örneğin, "ggg" biçim belirticisi bulunan bir kısaltılmış haftanın günü adı ekler <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A> sonuç dizesi için dize dizisi. Benzer şekilde, bulunan tam ay adı "Aaaa" biçim belirticisi ekler <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A> sonuç dizesi için dize dizisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.DateTime?displayProperty=nameWithType>  
 <xref:System.IFormatProvider?displayProperty=nameWithType>  
 [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)  
 [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Örnek: .NET Framework 4 yardımcı biçimlendirme](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
