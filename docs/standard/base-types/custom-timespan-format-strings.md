---
title: Özel TimeSpan Biçim dizeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, custom time interval
- format strings
- formatting [.NET Framework], time interval
- custom time interval format strings
- formatting [.NET Framework], time
- custom TimeSpan format strings
ms.assetid: a63ebf55-7269-416b-b4f5-286f6c03bf0e
ms.openlocfilehash: a5963f9afe422206627a1baea47339ecb81becf0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348315"
---
# <a name="custom-timespan-format-strings"></a>Özel TimeSpan Biçim dizeleri

<xref:System.TimeSpan> biçim dizesi, biçimlendirme işleminden kaynaklanan bir <xref:System.TimeSpan> değerin dize gösterimini tanımlar. Özel biçim dizesi, bir veya daha fazla özel <xref:System.TimeSpan> biçim belirticisinden ve herhangi bir sayıda değişmez karakterle oluşur. [Standart TimeSpan Biçim dizesi](standard-timespan-format-strings.md) olmayan herhangi bir dize, özel bir <xref:System.TimeSpan> biçim dizesi olarak yorumlanır.

> [!IMPORTANT]
> Özel <xref:System.TimeSpan> biçim belirticileri, günleri saat, saat, dakika veya kesirli saniyeden saniye olarak ayıran semboller gibi yer tutucu ayırıcı sembolleri içermez. Bunun yerine, bu simgelerin dize sabit değerleri olarak özel biçim dizesine dahil olması gerekir. Örneğin, `"dd\.hh\:mm"` günler ve saatler arasındaki ayırıcı olarak bir nokta (.) ve iki nokta üst üste (:) Saat ve dakika arasında ayırıcı olarak.
>
> Özel <xref:System.TimeSpan> biçim belirticileri ayrıca negatif ve pozitif zaman aralıklarını ayırt etmenizi sağlayan bir işaret simgesi de içermez. Bir işaret simgesi eklemek için, koşullu mantığı kullanarak bir biçim dizesi oluşturmanız gerekir. [Diğer karakterler](#other-characters) bölümü bir örnek içerir.

<xref:System.TimeSpan> değerlerinin dize temsilleri, <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> yönteminin aşırı yüklerini ve <xref:System.String.Format%2A?displayProperty=nameWithType>gibi bileşik biçimlendirmeyi destekleyen yöntemleri tarafından üretilir. Daha fazla bilgi için bkz. [biçimlendirme türleri](formatting-types.md) ve [Bileşik biçimlendirme](composite-formatting.md). Aşağıdaki örnek biçimlendirme işlemlerinde özel biçim dizelerinin kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customformatexample1.cs#1)]
[!code-vb[Conceptual.TimeSpan.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customformatexample1.vb#1)]

Özel <xref:System.TimeSpan> biçim dizeleri, <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ve <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemleri tarafından, ayrıştırma işlemleri için gereken giriş dizeleri biçimini tanımlamak için de kullanılır. (Ayrıştırma bir değerin dize temsilini bu değere dönüştürür.) Aşağıdaki örnek, ayrıştırma işlemlerinde standart biçim dizelerinin kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customparseexample1.cs#2)]
[!code-vb[Conceptual.TimeSpan.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customparseexample1.vb#2)]

<a name="table"></a>Aşağıdaki tabloda özel tarih ve saat biçimi belirticileri açıklanmaktadır.

| Biçim belirteci | Açıklama | Örnek |
|----------------------|-----------------|-------------|
|"d", "% d"|Zaman aralığındaki tüm gün sayısı.<br /><br /> Daha fazla bilgi: ["d" Özel Biçim belirleyicisi](#dSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%d` --> "6"<br /><br /> `d\.hh\:mm` --> "6.14:32"|
|"gg"-"dddddddd"|Zaman aralığındaki tüm gün sayısı, gerektiği şekilde önde sıfır ile doldurulmuştur.<br /><br /> Daha fazla bilgi: ["gg"-"dddddddd" özel biçim belirticileri](#ddSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `ddd` --> "006"<br /><br /> `dd\.hh\:mm` --> "06.14:32"|
|"h", "% h"|Zaman aralığındaki, günlerin bir parçası olarak sayılmayan tüm saatlerin sayısı. Tek basamaklı saatlerin önünde sıfır yok.<br /><br /> Daha fazla bilgi: ["h" Özel Biçim belirleyicisi](#hSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%h` --> "14"<br /><br /> `hh\:mm` --> "14:32"|
|"hh"|Zaman aralığındaki, günlerin bir parçası olarak sayılmayan tüm saatlerin sayısı. Tek basamaklı saatlerin önünde sıfır vardır.<br /><br /> Daha fazla bilgi: ["hh" Özel Biçim belirleyicisi](#hhSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `hh` --> "14"<br /><br /> `new TimeSpan(6, 8, 32, 17, 685):`<br /><br /> `hh` --> 08|
|"a", "% d"|Zaman aralığındaki saatlerin veya günlerin bir parçası olarak dahil olmayan tam dakika sayısı. Tek basamaklı dakikalar önünde sıfır yok.<br /><br /> Daha fazla bilgi: ["d" Özel Biçim belirleyicisi](#mSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `%m` --> "8"<br /><br /> `h\:m` --> "14:8"|
|"mm"|Zaman aralığındaki saatlerin veya günlerin bir parçası olarak dahil olmayan tam dakika sayısı. Tek basamaklı dakikalar önünde sıfır vardır.<br /><br /> Daha fazla bilgi: ["mm" Özel Biçim belirleyicisi](#mmSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `mm` --> "08"<br /><br /> `new TimeSpan(6, 8, 5, 17, 685):`<br /><br /> `d\.hh\:mm\:ss` --> 6.08:05:17|
|"s", "% s"|Zaman aralığındaki saat, gün veya dakika parçası olarak dahil olmayan tüm saniye sayısı. Tek basamaklı saniyeler önünde sıfır yok.<br /><br /> Daha fazla bilgi: ["s" Özel Biçim belirleyicisi](#sSpecifier).|`TimeSpan.FromSeconds(12.965)`:<br /><br /> `%s` --> 12<br /><br /> `s\.fff` --> 12.965|
|"ss"|Zaman aralığındaki saat, gün veya dakika parçası olarak dahil olmayan tüm saniye sayısı.  Tek basamaklı saniyeler önünde sıfır vardır.<br /><br /> Daha fazla bilgi: ["ss" Özel Biçim belirleyicisi](#ssSpecifier).|`TimeSpan.FromSeconds(6.965)`:<br /><br /> `ss` --> 06<br /><br /> `ss\.fff` --> 06.965|
|"f", "% f"|Bir zaman aralığında saniyenin onda biri.<br /><br /> Daha fazla bilgi: ["f" Özel Biçim belirleyicisi](#fSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `f` --> 8<br /><br /> `ss\.f` --> 06.8|
|"ff"|Bir zaman aralığında saniyenin yüzde biri.<br /><br /> Daha fazla bilgi: ["FF" Özel Biçim belirleyicisi](#ffSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `ff` --> 89<br /><br /> `ss\.ff` --> 06.89|
|"fff"|Bir zaman aralığındaki milisaniyedir.<br /><br /> Daha fazla bilgi: ["fff" Özel Biçim belirleyicisi](#f3Specifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `fff` --> 895<br /><br /> `ss\.fff` --> 06.895|
|"ffff"|İkinci bir zaman aralığında on-binde.<br /><br /> Daha fazla bilgi: ["ffff" Özel Biçim belirleyicisi](#f4Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffff` --> 8954<br /><br /> `ss\.ffff` --> 06.8954|
|"fffff"|Bir zaman aralığı içinde saniyenin yüz binde.<br /><br /> Daha fazla bilgi: ["fffff" Özel Biçim belirleyicisi](#f5Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffff` --> 89543<br /><br /> `ss\.fffff` --> 06.89543|
|"ffffff"|Saniyenin bir zaman aralığı içinde milionaltı.<br /><br /> Daha fazla bilgi: ["FFFFFF" Özel Biçim belirleyicisi](#f6Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffffff` --> 895432<br /><br /> `ss\.ffffff` --> 06.895432|
|"fffffff"|Bir saniye (veya kesirli Ticks) bir zaman aralığında On milimetre onda.<br /><br /> Daha fazla bilgi: ["fffffff" Özel Biçim belirleyicisi](#f7Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffffff` --> 8954321<br /><br /> `ss\.fffffff` --> 06.8954321|
|"F", "% F"|Bir zaman aralığında saniyenin onda biri. Basamak sıfırsa hiçbir şey görüntülenmez.<br /><br /> Daha fazla bilgi: ["F" Özel Biçim belirleyicisi](#F_Specifier).|`TimeSpan.Parse("00:00:06.32")`:<br /><br /> `%F`: 3<br /><br /> `TimeSpan.Parse("0:0:3.091")`:<br /><br /> `ss\.F`: 03.|
|"FF"|Bir zaman aralığında saniyenin yüzde biri. Tüm kesirli sondaki sıfırlar veya iki sıfır basamak dahil değildir.<br /><br /> Daha fazla bilgi: ["FF" Özel Biçim belirleyicisi](#FF_Specifier).|`TimeSpan.Parse("00:00:06.329")`:<br /><br /> `FF`: 32<br /><br /> `TimeSpan.Parse("0:0:3.101")`:<br /><br /> `ss\.FF`: 03.1|
|"FFF"|Bir zaman aralığındaki milisaniyedir. Tüm kesirli sondaki sıfırlar dahil edilmez.<br /><br /> Ek bilgi:|`TimeSpan.Parse("00:00:06.3291")`:<br /><br /> `FFF`: 329<br /><br /> `TimeSpan.Parse("0:0:3.1009")`:<br /><br /> `ss\.FFF`: 03.1|
|"FFFF"|İkinci bir zaman aralığında on-binde. Tüm kesirli sondaki sıfırlar dahil edilmez.<br /><br /> Daha fazla bilgi: ["ffff" Özel Biçim belirleyicisi](#F4_Specifier).|`TimeSpan.Parse("00:00:06.32917")`:<br /><br /> `FFFFF`: 3291<br /><br /> `TimeSpan.Parse("0:0:3.10009")`:<br /><br /> `ss\.FFFF`: 03.1|
|"FFFFF"|Bir zaman aralığı içinde saniyenin yüz binde. Tüm kesirli sondaki sıfırlar dahil edilmez.<br /><br /> Daha fazla bilgi: ["FFFFF" Özel Biçim belirleyicisi](#F5_Specifier).|`TimeSpan.Parse("00:00:06.329179")`:<br /><br /> `FFFFF`: 32917<br /><br /> `TimeSpan.Parse("0:0:3.100009")`:<br /><br /> `ss\.FFFFF`: 03.1|
|"FFFFFF"|Saniyenin bir zaman aralığı içinde milionaltı. Tüm kesirli sondaki sıfırlar gösterilmez.<br /><br /> Daha fazla bilgi: ["FFFFFF" Özel Biçim belirleyicisi](#F6_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 329179<br /><br /> `TimeSpan.Parse("0:0:3.1000009")`:<br /><br /> `ss\.FFFFFF`: 03.1|
|"FFFFFFF"|Bir zaman aralığında on milyonlarca bir saniye. Tüm kesirli sondaki sıfırlar veya yedi sıfır gösterilmez.<br /><br /> Daha fazla bilgi: ["fffffff" Özel Biçim belirleyicisi](#F7_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 3291791<br /><br /> `TimeSpan.Parse("0:0:3.1900000")`:<br /><br /> `ss\.FFFFFF`: 03.19|
|'*String*'|Değişmez dize sınırlayıcısı.<br /><br /> Daha fazla bilgi: [diğer karakterler](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh':'mm':'ss` --> "14:32:17"|
|&#92;|"\" çıkış karakteri.<br /><br /> Daha fazla bilgi: [diğer karakterler](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|
|Başka bir karakter|Atlamayan herhangi bir karakter, Özel Biçim belirleyicisi olarak yorumlanır.<br /><br /> Daha fazla bilgi: [diğer karakterler](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|

## <a name="dSpecifier"></a>"D" Özel Biçim belirleyicisi

"D" özel biçim belirticisi, zaman aralığındaki tüm gün sayısını temsil eden <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> özelliğinin değerini çıkarır. Değer birden fazla basamağa sahip olsa bile, bir <xref:System.TimeSpan> değerindeki tüm gün sayısını verir. <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> özelliğinin değeri sıfırsa, belirtici "0" verir.

"D" Özel Biçim belirleyicisi tek başına kullanılırsa, "% d" öğesini bir standart biçim dizesi olarak yanlış yorumlanmaması için belirtin. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#3)]
[!code-vb[Conceptual.TimeSpan.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#3)]

Aşağıdaki örnek, "d" Özel Biçim belirticisinin kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#4)]
[!code-vb[Conceptual.TimeSpan.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#4)]

[Tabloya dön](#table)

## <a name="ddSpecifier"></a>"Gg"-"dddddddd" özel biçim belirticileri

"Gg", "ddd", "gggg", "ddddd", "dddddd", "ddddddd" ve "dddddddd" özel biçim belirticileri, zaman aralığındaki tam gün sayısını temsil eden <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> özelliğinin değerini çıktı.

Çıktı dizesi, biçim tanımlayıcıda "d" karakter sayısı ile belirtilen en az basamak sayısını içerir ve gerektiğinde öndeki sıfırlar ile doldurulur. Gün sayısı içindeki rakamlar, biçim tanımlayıcısındaki "d" karakter sayısını aşarsa, gün sayısının tamamı sonuç dizesinde çıkış olur.

Aşağıdaki örnek, iki <xref:System.TimeSpan> değerin dize gösterimini göstermek için bu biçim belirticilerini kullanır. İlk zaman aralığının günler bileşeninin değeri sıfırdır; saniyenin gün bileşeni değeri 365 ' dir.

[!code-csharp[Conceptual.TimeSpan.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#5)]
[!code-vb[Conceptual.TimeSpan.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#5)]

[Tabloya dön](#table)

## <a name="hSpecifier"></a>"H" Özel Biçim belirleyicisi

"H" özel biçim belirticisi, kendi gün bileşeninin bir parçası olarak sayılmayan zaman aralığındaki tüm saatlerin sayısını temsil eden <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> özelliğinin değerini çıkarır. <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> özelliğinin değeri 0 ' dan 9 ' a kadar ise, tek basamaklı bir dize değeri döndürür ve <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> özelliğinin değeri 10 ile 23 arasında bir değer döndürürse iki basamaklı bir dize değeri döndürür.

"H" Özel Biçim belirleyicisi tek başına kullanılırsa, standart biçim dizesi olarak yanlış yorumlanmaması için "% h" belirtin. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Genellikle, bir ayrıştırma işleminde, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Sayısal dizeyi saat sayısı olarak yorumlamak yerine "% h" özel biçim belirticisini kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#8)]
[!code-vb[Conceptual.TimeSpan.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#8)]

Aşağıdaki örnek, "h" Özel Biçim belirticisinin kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#7)]
[!code-vb[Conceptual.TimeSpan.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#7)]

[Tabloya dön](#table)

## <a name="hhSpecifier"></a>"Hh" Özel Biçim belirleyicisi

"Hh" özel biçim belirticisi, kendi gün bileşeninin bir parçası olarak sayılmayan zaman aralığındaki tüm saatlerin sayısını temsil eden <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> özelliğinin değerini çıkarır. 0 ile 9 arasında değerler için, çıkış dizesi önünde sıfır değeri içerir.

Genellikle, bir ayrıştırma işleminde, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Sayısal dizeyi saat sayısı olarak yorumlamak yerine "hh" özel biçim belirticisini kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#9)]
[!code-vb[Conceptual.TimeSpan.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#9)]

Aşağıdaki örnek, "hh" Özel Biçim belirticisinin kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#10)]
[!code-vb[Conceptual.TimeSpan.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#10)]

[Tabloya dön](#table)

## <a name="mSpecifier"></a>"D" Özel Biçim belirleyicisi

"M" özel biçim belirticisi, kendi gün bileşeninin bir parçası olarak sayılmayan zaman aralığındaki tüm dakikaların sayısını temsil eden <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> özelliğinin değerini çıkarır. <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> özelliğinin değeri 0 ile 9 arasında olursa tek basamaklı bir dize değeri döndürür ve <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> özelliğinin değeri 10 ile 59 arasında bir değer döndürürse iki basamaklı bir dize değeri döndürür.

"D" Özel Biçim belirleyicisi tek başına kullanılırsa, standart biçim dizesi olarak yanlış yorumlanmaması için "% d" belirtin. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Genellikle, bir ayrıştırma işleminde, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Sayısal dizeyi dakika sayısı olarak yorumlamak yerine "% d" özel biçim belirticisini kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#11)]
[!code-vb[Conceptual.TimeSpan.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#11)]

Aşağıdaki örnek, "d" Özel Biçim belirticisinin kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#12)]
[!code-vb[Conceptual.TimeSpan.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#12)]

[Tabloya dön](#table)

## <a name="mmSpecifier"></a>"Mm" Özel Biçim belirleyicisi

"Mm" özel biçim Belirleyicisi, saat veya gün bileşeninin bir parçası olarak dahil olmayan zaman aralığındaki tüm dakikaların sayısını temsil eden <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> özelliğinin değerini çıkarır. 0 ile 9 arasında değerler için, çıkış dizesi önünde sıfır değeri içerir.

Genellikle, bir ayrıştırma işleminde, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Sayısal dizeyi dakika sayısı olarak yorumlamak yerine "mm" özel biçim belirticisini kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#13)]
[!code-vb[Conceptual.TimeSpan.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#13)]

Aşağıdaki örnek, "mm" Özel Biçim belirticisinin kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#14)]
[!code-vb[Conceptual.TimeSpan.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#14)]

[Tabloya dön](#table)

## <a name="sSpecifier"></a>"S" Özel Biçim belirleyicisi

"S" özel biçim Belirleyicisi, saat, gün veya dakika bileşeninin bir parçası olarak dahil olmayan zaman aralığındaki tüm saniye sayısını temsil eden <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> özelliğinin değerini verir. <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> özelliğinin değeri 0 ile 9 arasında olursa tek basamaklı bir dize değeri döndürür ve <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> özelliğinin değeri 10 ile 59 arasında bir değer döndürürse iki basamaklı bir dize değeri döndürür.

"S" Özel Biçim belirleyicisi tek başına kullanılırsa, "% s" öğesini bir standart biçim dizesi olarak yanlış yorumlanmaması için belirtin. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#15)]
[!code-vb[Conceptual.TimeSpan.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#15)]

Genellikle, bir ayrıştırma işleminde, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Sayısal dizeyi saniye sayısı olarak yorumlamak yerine "% s" özel biçim belirticisini kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#17)]
[!code-vb[Conceptual.TimeSpan.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#17)]

Aşağıdaki örnek, "s" Özel Biçim belirticisinin kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#16)]
[!code-vb[Conceptual.TimeSpan.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#16)]

[Tabloya dön](#table)

## <a name="ssSpecifier"></a>"Ss" Özel Biçim belirleyicisi

"Ss" özel biçim Belirleyicisi, saat, gün veya dakika bileşeninin bir parçası olarak dahil olmayan zaman aralığındaki tüm saniye sayısını temsil eden <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> özelliğinin değerini verir. 0 ile 9 arasında değerler için, çıkış dizesi önünde sıfır değeri içerir.

Genellikle, bir ayrıştırma işleminde, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Sayısal dizeyi saniye sayısı olarak yorumlamak yerine "ss" özel biçim belirticisini kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#18)]
[!code-vb[Conceptual.TimeSpan.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#18)]

Aşağıdaki örnek, "ss" Özel Biçim belirticisinin kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#19)]
[!code-vb[Conceptual.TimeSpan.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#19)]

[Tabloya dön](#table)

## <a name="fSpecifier"></a>"F" Özel Biçim belirleyicisi

"F" özel biçim belirticisi bir saniyenin onda birini bir zaman aralığında verir. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemini çağıran bir ayrıştırma işleminde, giriş dizesinin tam olarak bir kesirli basamak içermesi gerekir.

"F" Özel Biçim belirleyicisi tek başına kullanılırsa, standart biçim dizesi olarak yanlış yorumlanmaması için "% f" belirtin.

Aşağıdaki örnek, bir <xref:System.TimeSpan> değerinde saniyenin onda birini göstermek için "f" özel biçim belirticisini kullanır. "f" ilk olarak tek Biçim belirleyicisi olarak kullanılır ve ardından bir özel biçim dizesinde "s" belirticisi ile birleştirilir.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya dön](#table)

## <a name="ffSpecifier"></a>"FF" Özel Biçim belirleyicisi

"FF" özel biçim belirticisi saniye cinsinden bir zaman aralığına çıkış verir. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemini çağıran bir ayrıştırma işleminde, giriş dizesinin tam olarak iki kesirli basamak içermesi gerekir.

Aşağıdaki örnek, bir <xref:System.TimeSpan> değerindeki saniyenin yüzde birini göstermek için "FF" özel biçim belirticisini kullanır. önce tek Biçim belirleyicisi olarak "FF" kullanılır ve ardından özel biçim dizesinde "s" belirticisi ile birleştirilir.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya dön](#table)

## <a name="f3Specifier"></a>"Fff" Özel Biçim belirleyicisi

"Fff" özel biçim Belirleyicisi (üç "f" karakteri ile), bir zaman aralığındaki milisaniyeyi verir. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemini çağıran bir ayrıştırma işleminde, giriş dizesinin tam olarak üç kesirli basamak içermesi gerekir.

Aşağıdaki örnek, bir <xref:System.TimeSpan> değerindeki milisaniyeyi göstermek için "fff" özel biçim belirticisini kullanır. önce tek Biçim belirleyicisi olarak "fff" kullanılır ve ardından özel biçim dizesinde "s" belirticisi ile birleştirilir.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya dön](#table)

## <a name="f4Specifier"></a>"Ffff" Özel Biçim belirleyicisi

"Ffff" özel biçim belirticisi (dört "f" karakterle birlikte), bir zaman aralığında saniyenin on-binde sayısını verir. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemini çağıran bir ayrıştırma işleminde, giriş dizesinin tam olarak dört kesirli basamak içermesi gerekir.

Aşağıdaki örnek, bir <xref:System.TimeSpan> değerindeki bir saniyenin on-binde ' unu göstermek için "ffff" özel biçim belirticisini kullanır. "ffff" ilk olarak tek Biçim belirleyicisi olarak kullanılır ve ardından özel bir biçim dizesinde "s" belirticisi ile birleştirilir.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya dön](#table)

## <a name="f5Specifier"></a>"Fffff" Özel Biçim belirleyicisi

"Fffff" özel biçim Belirleyicisi (beş "f" karakterle birlikte), bir zaman aralığındaki yüz-binde ' i gösterir. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemini çağıran bir ayrıştırma işleminde, giriş dizesinin tam olarak beş kesirli basamak içermesi gerekir.

Aşağıdaki örnek, bir <xref:System.TimeSpan> değerinde saniyenin yüz binde ' ni göstermek için "fffff" özel biçim belirticisini kullanır. önce tek Biçim belirticisi olarak "fffff" kullanılır ve ardından bir özel biçim dizesinde "s" belirticisi ile birleştirilir.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya dön](#table)

## <a name="f6Specifier"></a>"FFFFFF" Özel Biçim belirleyicisi

"FFFFFF" özel biçim Belirleyicisi (altı "f" karakteriyle birlikte), bir zaman aralığında saniyenin her birinin milionda çıkışını çıkarır. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemini çağıran bir ayrıştırma işleminde, giriş dizesinin tam olarak altı kesirli basamak içermesi gerekir.

Aşağıdaki örnek, bir <xref:System.TimeSpan> değerindeki bir saniyenin milionkesini göstermek için "FFFFFF" özel biçim belirticisini kullanır. İlk olarak tek Biçim belirleyicisi olarak kullanılır ve ardından özel bir biçim dizesinde "s" belirticisi ile birleştirilir.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya dön](#table)

## <a name="f7Specifier"></a>"Fffffff" Özel Biçim belirleyicisi

"Fffffff" özel biçim belirticisi (yedi "f" karakteriyle birlikte), saniyenin on milyonda biri (veya kesir sayısı) bir zaman aralığında çıktı. <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemini çağıran bir ayrıştırma işleminde, giriş dizesinin tam olarak yedi kesirli basamak içermesi gerekir.

Aşağıdaki örnek, bir <xref:System.TimeSpan> değerindeki onay işareti sayısını göstermek için "fffffff" özel biçim belirticisini kullanır. İlk olarak tek Biçim belirleyicisi olarak kullanılır ve ardından özel bir biçim dizesinde "s" belirticisi ile birleştirilir.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya dön](#table)

## <a name="F_Specifier"></a>"F" Özel Biçim belirleyicisi

"F" özel biçim belirticisi bir saniyenin onda birini bir zaman aralığında verir. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Saniyenin ondaki zaman aralığı değeri sıfırsa, sonuç dizesine dahil değildir. <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemini çağıran bir ayrıştırma işleminde, ikinci bir basamağın onunun varlığı isteğe bağlıdır.

"F" Özel Biçim belirleyicisi tek başına kullanılırsa, standart biçim dizesi olarak yanlış yorumlanmaması için "% F" belirtin.

Aşağıdaki örnek, bir <xref:System.TimeSpan> değerinde saniyenin onda birini göstermek için "F" özel biçim belirticisini kullanır. Bu özel biçim belirticisini bir ayrıştırma işleminde de kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#21)]
[!code-vb[Conceptual.TimeSpan.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#21)]

[Tabloya dön](#table)

## <a name="FF_Specifier"></a>"FF" Özel Biçim belirleyicisi

"FF" özel biçim belirticisi saniye cinsinden bir zaman aralığına çıkış verir. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Sondaki kesirli sıfırları varsa, sonuç dizesine dahil edilmez. <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemini çağıran bir ayrıştırma işleminde, ikinci bir basamağın onun ve yüzde birinin varlığı isteğe bağlıdır.

Aşağıdaki örnek, bir <xref:System.TimeSpan> değerindeki saniyenin yüzde birini göstermek için "FF" özel biçim belirticisini kullanır. Bu özel biçim belirticisini bir ayrıştırma işleminde de kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#22)]
[!code-vb[Conceptual.TimeSpan.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#22)]

[Tabloya dön](#table)

## <a name="F3_Specifier"></a>"FFF" Özel Biçim belirleyicisi

"FFF" özel biçim Belirleyicisi (üç "F" karakteri ile), bir zaman aralığındaki milisaniyeyi verir. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Sondaki kesirli sıfırları varsa, sonuç dizesine dahil edilmez. <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemini çağıran bir ayrıştırma işleminde, ikinci bir basamağın onda, yüzde ve binde varlığı isteğe bağlıdır.

Aşağıdaki örnek, bir <xref:System.TimeSpan> değerindeki bir saniyenin binde göstermek için "FFF" özel biçim belirticisini kullanır. Bu özel biçim belirticisini bir ayrıştırma işleminde de kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#23)]
[!code-vb[Conceptual.TimeSpan.Custom#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#23)]

[Tabloya dön](#table)

## <a name="F4_Specifier"></a>"FFFF" Özel Biçim belirleyicisi

"FFFF" özel biçim belirticisi (dört "F" karakterle birlikte), bir zaman aralığında saniyenin on-binde sayısını verir. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Sondaki kesirli sıfırları varsa, sonuç dizesine dahil edilmez. <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemini çağıran bir ayrıştırma işleminde, ikinci bir basamağın onda, yüzde, binde ve on-binde bulunması isteğe bağlıdır.

Aşağıdaki örnek, bir <xref:System.TimeSpan> değerindeki bir saniyenin on-binde ' unu göstermek için "FFFF" özel biçim belirticisini kullanır. Ayrıca, bir ayrıştırma işleminde "FFFF" özel biçim belirticisini kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#24)]
[!code-vb[Conceptual.TimeSpan.Custom#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#24)]

[Tabloya dön](#table)

## <a name="F5_Specifier"></a>"FFFFF" Özel Biçim belirleyicisi

"FFFFF" özel biçim Belirleyicisi (beş "F" karakterle birlikte), bir zaman aralığındaki yüz-binde ' i gösterir. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Sondaki kesirli sıfırları varsa, sonuç dizesine dahil edilmez. <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemini çağıran bir ayrıştırma işleminde, ikinci bir basamağın onda, yüzde, binde, on-binde ve yüz-binde varlığı isteğe bağlıdır.

Aşağıdaki örnek, bir <xref:System.TimeSpan> değerinde saniyenin yüz binde ' ni göstermek için "FFFFF" özel biçim belirticisini kullanır. Ayrıca bir ayrıştırma işleminde "FFFFF" özel biçim belirticisini kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#25)]
[!code-vb[Conceptual.TimeSpan.Custom#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#25)]

[Tabloya dön](#table)

## <a name="F6_Specifier"></a>"FFFFFF" Özel Biçim belirleyicisi

"FFFFFF" özel biçim Belirleyicisi (altı "F" karakteriyle birlikte), bir zaman aralığında saniyenin her birinin milionda çıkışını çıkarır. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Sondaki kesirli sıfırları varsa, sonuç dizesine dahil edilmez. <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemini çağıran bir ayrıştırma işleminde, ikinci bir basamağın onda, yüzde, binde, on-binde, yüz-binde ve milionon 'un varlığı isteğe bağlıdır.

Aşağıdaki örnek, bir <xref:System.TimeSpan> değerindeki bir saniyenin milionkesini göstermek için "FFFFFF" özel biçim belirticisini kullanır. Bu özel biçim belirticisini bir ayrıştırma işleminde de kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#26](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#26)]
[!code-vb[Conceptual.TimeSpan.Custom#26](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#26)]

[Tabloya dön](#table)

## <a name="F7_Specifier"></a>"FFFFFFF" Özel Biçim belirleyicisi

"FFFFFFF" özel biçim belirticisi (yedi "F" karakteriyle birlikte), saniyenin on milyonda biri (veya kesir sayısı) bir zaman aralığında çıktı. Sondaki kesirli sıfırları varsa, sonuç dizesine dahil edilmez. <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemini çağıran bir ayrıştırma işleminde, giriş dizesindeki yedi kesirli basamakların varlığı isteğe bağlıdır.

Aşağıdaki örnek, bir <xref:System.TimeSpan> değerindeki bir saniyenin kesirli parçalarını göstermek için "FFFFFFF" özel biçim belirticisini kullanır. Bu özel biçim belirticisini bir ayrıştırma işleminde de kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#27](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#27)]
[!code-vb[Conceptual.TimeSpan.Custom#27](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#27)]

[Tabloya dön](#table)

## <a name="other-characters"></a>Diğer karakterler

Bir biçim dizesindeki bir boşluk karakteri de dahil olmak üzere herhangi bir kaçış karakteri özel Biçim belirleyicisi olarak yorumlanır. Çoğu durumda, başka bir kaçışsız karakter bulunması <xref:System.FormatException>oluşur.

Biçim dizesine bir sabit karakter dahil etmenin iki yolu vardır:

- Tek tırnak işareti (sabit dize sınırlayıcısı) içine alın.

- Kaçış karakteri olarak yorumlanan bir ters eğik çizgiyle ("\\") önüne koyun. Bu, içinde C#biçim dizesinin @-quotedolması veya sabit karakterin önünde ek bir ters eğik çizgi olması gerektiği anlamına gelir.

  Bazı durumlarda, bir biçim dizesine kaçan değişmez değer eklemek için koşullu mantığı kullanmanız gerekebilir. Aşağıdaki örnek, negatif zaman aralıkları için bir işaret simgesi eklemek üzere koşullu mantığı kullanır.

  [!code-csharp[Conceptual.TimeSpan.Custom#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/negativevalues1.cs#29)]
  [!code-vb[Conceptual.TimeSpan.Custom#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/negativevalues1.vb#29)]

.NET, zaman aralıklarında ayırıcılar için dilbilgisi tanımlamaz. Bu, gün ve saat, saat ve dakika, dakika ve saniye ve saniye ile kesirleri arasındaki ayırıcıların hepsi bir biçim dizesinde karakter sabit değeri olarak değerlendirilmelidir.

Aşağıdaki örnek, çıkış dizesinde "Minutes" sözcüğünü içeren bir özel biçim dizesi tanımlamak için hem kaçış karakteri hem de tek tırnak kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/literal1.cs#28)]
[!code-vb[Conceptual.TimeSpan.Custom#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/literal1.vb#28)]

[Tabloya dön](#table)

## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme Türleri](formatting-types.md)
- [Standart TimeSpan Biçim Dizeleri](standard-timespan-format-strings.md)
