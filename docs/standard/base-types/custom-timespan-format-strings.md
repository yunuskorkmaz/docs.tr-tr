---
title: Özel TimeSpan Biçim Dizeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format spexifiers, custom time interval
- format strings
- formatting [.NET Framework], time interval
- custom time interval format strings
- formatting [.NET Framework], time
- custom TimeSpan format strings
ms.assetid: a63ebf55-7269-416b-b4f5-286f6c03bf0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c75f9ffe17d04ad4b8e41a6e1402a3cf4be7e07f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722718"
---
# <a name="custom-timespan-format-strings"></a>Özel TimeSpan Biçim Dizeleri

A <xref:System.TimeSpan> biçim dizesi tanımlar dize gösterimini bir <xref:System.TimeSpan> bir biçimlendirme işleminden kaynaklanan değeri. Bir özel biçim dizesi bir veya daha fazla özel oluşur <xref:System.TimeSpan> biçim belirleyiciler herhangi bir sayıda değişmez karakterlerin yanı sıra. Herhangi bir dize değil bir [standart TimeSpan biçim dizesi](standard-timespan-format-strings.md) özel olarak yorumlanır <xref:System.TimeSpan> biçimlendirme dizesi.

> [!IMPORTANT]
> Özel <xref:System.TimeSpan> biçim belirticileri gün ayrı saat, saat, dakika veya saniye Kesirli saniye ile semboller gibi yer tutucu ayırıcı semboller içermez. Bunun yerine, bu sembolleri özel biçim dizesinde dize değişmez değer olarak eklenmelidir. Örneğin, `"dd\.hh\:mm"` saat ve dakika arasında ayıraç olarak gün, saat ve iki nokta üst üste (:) arasındaki ayırıcısı olarak nokta (.) tanımlar.
>
> Özel <xref:System.TimeSpan> biçim belirticileri da dahil, negatif ve pozitif zaman aralıkları arasında ayırt etmenize olanak sağlayan bir işareti simgesi. İşareti simgesi eklemek için koşullu mantık kullanarak bir biçim dizesi oluşturmanız gerekir. [Diğer karakterler](#Other) bölüm bir örnek içerir.

Dize temsillerini <xref:System.TimeSpan> değerleri aşırı yüküne yapılan çağrılar tarafından üretilmektedir <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> yöntemi ve yöntemlerle bileşik, aşağıdakiler gibi biçimlendirme desteği <xref:System.String.Format%2A?displayProperty=nameWithType>. Daha fazla bilgi için [biçimlendirme türleri](formatting-types.md) ve [bileşik biçimlendirme](composite-formatting.md). Aşağıdaki örnek, biçimlendirme işlemlerinde, özel biçim dizeleri kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customformatexample1.cs#1)]
[!code-vb[Conceptual.TimeSpan.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customformatexample1.vb#1)]

Özel <xref:System.TimeSpan> biçim dizeleri tarafından da kullanılır <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ve <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> istenilen biçime tanımlamak için yöntemleri ayrıştırma işlemlerinde dizelerini giriş. (Ayrıştırma bir değerin dize temsilini bu değere dönüştürür.) Aşağıdaki örnek, standart biçim dizeleri ayrıştırma işlemlerinde, kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customparseexample1.cs#2)]
[!code-vb[Conceptual.TimeSpan.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customparseexample1.vb#2)]

<a name="table"></a> Aşağıdaki tabloda özel tarih ve saat biçim tanımlayıcılarının açıklanmaktadır.

| Biçim belirteci | Açıklama | Örnek |
|----------------------|-----------------|-------------|
|"d", "%d"|Zaman aralığındaki tam gün sayısı.<br /><br /> Daha fazla bilgi: ["D" özel Biçim belirleyicisi](#dSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%d` --> "6"<br /><br /> `d\.hh\:mm` --> "6.14:32"|
|"dd"-"dddddddd"|Gerekirse sayının önüne sıfır tam gün cinsinden zaman aralığı.<br /><br /> Daha fazla bilgi: ["dd"-"dddddddd" özel biçim Belirleyicilerini](#ddSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `ddd` --> "006"<br /><br /> `dd\.hh\:mm` --> "06.14:32"|
|"h", "%h"|Tüm saat sayısı zaman aralığındaki gün bir parçası olarak sayılmaz. Tek basamaklı saat önünde sıfır yok.<br /><br /> Daha fazla bilgi: ["H" özel biçim belirticisi](#hSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%h` --> "14"<br /><br /> `hh\:mm` --> "14:32"|
|"hh"|Tüm saat sayısı zaman aralığındaki gün bir parçası olarak sayılmaz. Tek basamaklı saat önünde sıfır var.<br /><br /> Daha fazla bilgi: ["Hh" özel Biçim belirleyicisi](#hhSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `hh` --> "14"<br /><br /> `new TimeSpan(6, 8, 32, 17, 685):`<br /><br /> `hh` --> 08|
|"m", "%m"|Tüm dakika sayısını zaman aralığındaki bir parçası olarak saat veya gün dahil değildir. Tek basamaklı dakika önünde sıfır yok.<br /><br /> Daha fazla bilgi: ["M" özel Biçim belirleyicisi](#mSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `%m` --> "8"<br /><br /> `h\:m` --> "14:8"|
|"mm"|Tüm dakika sayısını zaman aralığındaki bir parçası olarak saat veya gün dahil değildir. Tek basamaklı dakika önünde sıfır gerekir.<br /><br /> Daha fazla bilgi: ["Mm" özel Biçim belirleyicisi](#mmSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `mm` --> "08"<br /><br /> `new TimeSpan(6, 8, 5, 17, 685):`<br /><br /> `d\.hh\:mm\:ss` --> 6.08:05:17|
|"s", "%s"|Tüm saniye sayısını zaman aralığındaki parçası olarak saat, gün veya dakika dahil edilmez. Tek basamaklı saniye önünde sıfır yok.<br /><br /> Daha fazla bilgi: ["S" özel biçim belirticisi](#sSpecifier).|`TimeSpan.FromSeconds(12.965)`:<br /><br /> `%s` --> 12<br /><br /> `s\.fff` --> 12.965|
|"ss"|Tüm saniye sayısını zaman aralığındaki parçası olarak saat, gün veya dakika dahil edilmez.  Tek basamaklı saniye önünde sıfır var.<br /><br /> Daha fazla bilgi: ["Ss" özel biçim belirticisi](#ssSpecifier).|`TimeSpan.FromSeconds(6.965)`:<br /><br /> `ss` --> 06<br /><br /> `ss\.fff` --> 06.965|
|"f", "%f"|Saniyenin onda biri bir zaman aralığı içinde.<br /><br /> Daha fazla bilgi: ["F" özel Biçim belirleyicisi](#fSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `f` --> 8<br /><br /> `ss\.f` --> 06.8|
|"ff"|Bir zaman aralığındaki saniyenin yüzde biri.<br /><br /> Daha fazla bilgi:["Ff" özel Biçim belirleyicisi](#ffSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `ff` --> 89<br /><br /> `ss\.ff` --> 06.89|
|"fff"|Milisaniye cinsinden zaman aralığı.<br /><br /> Daha fazla bilgi: ["Fff" özel Biçim belirleyicisi](#f3Specifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `fff` --> 895<br /><br /> `ss\.fff` --> 06.895|
|"ffff"|On binde biri ikinci bir zaman aralığı içinde.<br /><br /> Daha fazla bilgi: ["Ffff" özel Biçim belirleyicisi](#f4Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffff` --> 8954<br /><br /> `ss\.ffff` --> 06.8954|
|"fffff"|Yüz binde biri ikinci bir zaman aralığı içinde.<br /><br /> Daha fazla bilgi: ["Fffff" özel Biçim belirleyicisi](#f5Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffff` --> 89543<br /><br /> `ss\.fffff` --> 06.89543|
|"ffffff"|Saniyenin milyonda bir zaman aralığı içinde.<br /><br /> Daha fazla bilgi: ["Ffffff" özel Biçim belirleyicisi](#f6Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffffff` --> 895432<br /><br /> `ss\.ffffff` --> 06.895432|
|"fffffff"|On-milyonda bir zaman aralığında ikinci (veya kesir işaretleri).<br /><br /> Daha fazla bilgi: ["Fffffff" özel Biçim belirleyicisi](#f7Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffffff` --> 8954321<br /><br /> `ss\.fffffff` --> 06.8954321|
|"F", "%F"|Saniyenin onda biri bir zaman aralığı içinde. Basamak sıfırsa hiçbir şey görüntülenmez.<br /><br /> Daha fazla bilgi: ["F" özel Biçim belirleyicisi](#F_Specifier).|`TimeSpan.Parse("00:00:06.32")`:<br /><br /> `%F`: 3<br /><br /> `TimeSpan.Parse("0:0:3.091")`:<br /><br /> `ss\.F`: 03.|
|"FF"|Bir zaman aralığındaki saniyenin yüzde biri. Her kesirli öndeki sıfırlar veya iki sıfır basamak dahil edilmez.<br /><br /> Daha fazla bilgi: ["FF" özel Biçim belirleyicisi](#FF_Specifier).|`TimeSpan.Parse("00:00:06.329")`:<br /><br /> `FF`: 32<br /><br /> `TimeSpan.Parse("0:0:3.101")`:<br /><br /> `ss\.FF`: 03.1|
|"FFF"|Milisaniye cinsinden zaman aralığı. Kesirli sonundaki sıfırları dahil edilmez.<br /><br /> Daha fazla bilgi:|`TimeSpan.Parse("00:00:06.3291")`:<br /><br /> `FFF`: 329<br /><br /> `TimeSpan.Parse("0:0:3.1009")`:<br /><br /> `ss\.FFF`: 03.1|
|"FFFF"|On binde biri ikinci bir zaman aralığı içinde. Kesirli sonundaki sıfırları dahil edilmez.<br /><br /> Daha fazla bilgi: ["FFFF" özel Biçim belirleyicisi](#F4_Specifier).|`TimeSpan.Parse("00:00:06.32917")`:<br /><br /> `FFFFF`: 3291<br /><br /> `TimeSpan.Parse("0:0:3.10009")`:<br /><br /> `ss\.FFFF`: 03.1|
|"FFFFF"|Yüz binde biri ikinci bir zaman aralığı içinde. Kesirli sonundaki sıfırları dahil edilmez.<br /><br /> Daha fazla bilgi: ["FFFFF" özel Biçim belirleyicisi](#F5_Specifier).|`TimeSpan.Parse("00:00:06.329179")`:<br /><br /> `FFFFF`: 32917<br /><br /> `TimeSpan.Parse("0:0:3.100009")`:<br /><br /> `ss\.FFFFF`: 03.1|
|"FFFFFF"|Saniyenin milyonda bir zaman aralığı içinde. Kesirli sonundaki sıfırları görüntülenmez.<br /><br /> Daha fazla bilgi: ["FFFFFF" özel Biçim belirleyicisi](#F6_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 329179<br /><br /> `TimeSpan.Parse("0:0:3.1000009")`:<br /><br /> `ss\.FFFFFF`: 03.1|
|"FFFFFFF"|On milyonlarca ikinci bir zaman aralığı içinde. Kesirli sıfırlar veya yedi sıfır görüntülenmez.<br /><br /> Daha fazla bilgi: ["FFFFFFF" özel Biçim belirleyicisi](#F7_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 3291791<br /><br /> `TimeSpan.Parse("0:0:3.1900000")`:<br /><br /> `ss\.FFFFFF`: 03.19|
|'*dize*'|Değişmez dize sınırlayıcısı.<br /><br /> Daha fazla bilgi: [Diğer karakterler](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh':'mm':'ss` --> "14:32:17"|
|\\| Kaçış karakteri.<br /><br /> Daha fazla bilgi:[diğer karakterler](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|
|Başka bir karakter|Atlanmayan herhangi bir karakter, bir özel biçim Belirleyicisi olarak yorumlanır.<br /><br /> Daha fazla bilgi: [Diğer karakterler](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|

<a name="dSpecifier"></a> 

## <a name="the-d-custom-format-specifier"></a>"d" Özel Biçim Belirleyicisi

"D" özel Biçim belirleyicisi değerini çıkarır <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> özelliği zaman aralığındaki tam gün sayısını temsil eder. Tam gün sayısını çıkaran bir <xref:System.TimeSpan> değer birden fazla basamak olsa bile, değer. Varsa değerini <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> özelliği sıfır, "0" belirticisi çıkarır.

"D" özel biçim belirticisi tek başına kullanıldığında, "%d" standart biçim dizesi yanlış değil şekilde belirtin. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#3)]
[!code-vb[Conceptual.TimeSpan.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#3)]

Aşağıdaki örnek "d" özel Biçim belirleyicisi kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#4)]
[!code-vb[Conceptual.TimeSpan.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#4)]

[Tabloya dön](#table)

<a name="ddSpecifier"></a> 

## <a name="the-dd-dddddddd-custom-format-specifiers"></a>"dd"-"dddddddd" özel biçim belirticileri
"Dd", "ddd", "dddd", "GGGGG", "GGGGGG", "ddddddd" ve "dddddddd" özel biçim belirticileri değerini çıkış <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> özelliği zaman aralığındaki tam gün sayısını temsil eder.

Gerekirse sayının önüne sıfır eklenir ve bir biçim belirtici "d" karakter sayısı tarafından belirtilen basamak sayısı alt sınırını çıkış dizesi içerir. "D" biçim belirtici karakter sayısı en fazla gün sayısı cinsinden rakamdan, tam gün sayısını çıkış sonuç dizesindeki ' dir.

Aşağıdaki örnek, iki dize gösterimini görüntülemek için bu biçim tanımlayıcıları kullanır. <xref:System.TimeSpan> değerleri. İlk zaman aralığını gün bileşeninin sıfır değeri; 365 gün bileşeni saniyenin değeridir.

[!code-csharp[Conceptual.TimeSpan.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#5)]
[!code-vb[Conceptual.TimeSpan.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#5)]

[Tabloya dön](#table)

<a name="hSpecifier"></a> 

## <a name="the-h-custom-format-specifier"></a>"h" Özel Biçim Belirleyicisi
"H" özel biçim belirticisi değerini çıkarır <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> özelliği, gün bileşenini bir parçası olarak sayılmaz zaman aralığındaki tüm saat sayısını temsil eder. Bir tek basamaklı string değeri döndürür değerini <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> özelliği 0-9 ve iki basamaklı dize değeri varsa döndürür değerini <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> özelliği aralıklarına 10'dan 23.

"H" özel biçim belirticisi tek başına kullanıldığında, "%h" standart biçim dizesi yanlış değil şekilde belirtin. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Normalde, bir ayrıştırma işleminde yalnızca bir tek sayı içeren bir Giriş dizesinin gün sayısı yorumlanır. Sayısal dize saat sayısı yorumlamak için "%h" özel Biçim belirleyicisi yerine kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#8)]
[!code-vb[Conceptual.TimeSpan.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#8)]

Aşağıdaki örnek, "h" özel biçim belirticisi kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#7)]
[!code-vb[Conceptual.TimeSpan.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#7)]

[Tabloya dön](#table)

<a name="hhSpecifier"></a> 

## <a name="the-hh-custom-format-specifier"></a>"hh" Özel Biçim Belirleyicisi
"Hh" özel Biçim belirleyicisi değerini çıkarır <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> özelliği, gün bileşenini bir parçası olarak sayılmaz zaman aralığındaki tüm saat sayısını temsil eder. 0 ile 9 arasında değerleri için önünde sıfır çıkış dizesi içerir.

Normalde, bir ayrıştırma işleminde yalnızca bir tek sayı içeren bir Giriş dizesinin gün sayısı yorumlanır. Sayısal dize saat sayısı yorumlamak için "hh" özel Biçim belirleyicisi yerine kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#9)]
[!code-vb[Conceptual.TimeSpan.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#9)]

Aşağıdaki örnek, "hh" özel Biçim belirleyicisi kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#10)]
[!code-vb[Conceptual.TimeSpan.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#10)]

[Tabloya dön](#table)

<a name="mSpecifier"></a> 

## <a name="the-m-custom-format-specifier"></a>"m" Özel Biçim Belirleyicisi
"M" özel Biçim belirleyicisi değerini çıkarır <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> özelliği, gün bileşenini bir parçası olarak sayılmaz zaman aralığındaki tam dakika sayısını temsil eder. Bir tek basamaklı string değeri döndürür değerini <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> özelliği 0-9 ve iki basamaklı dize değeri varsa döndürür değerini <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> 10'dan 59 özelliği aralıkları.

"M" özel biçim belirticisi tek başına kullanıldığında, "%m" standart biçim dizesi yanlış değil şekilde belirtin. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Normalde, bir ayrıştırma işleminde yalnızca bir tek sayı içeren bir Giriş dizesinin gün sayısı yorumlanır. Sayısal dize dakika sayısı yorumlamak için "%m" özel Biçim belirleyicisi yerine kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#11)]
[!code-vb[Conceptual.TimeSpan.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#11)]

Aşağıdaki örnek, "m" özel Biçim belirleyicisi kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#12)]
[!code-vb[Conceptual.TimeSpan.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#12)]

[Tabloya dön](#table)

<a name="mmSpecifier"></a> 

## <a name="the-mm-custom-format-specifier"></a>"mm" Özel Biçim Belirleyicisi
"Mm" özel Biçim belirleyicisi değerini çıkarır <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> özelliği, saat veya gün bileşeninin bir parçası olarak dahil edilmez zaman aralığındaki tam dakika sayısını temsil eder. 0 ile 9 arasında değerleri için önünde sıfır çıkış dizesi içerir.

Normalde, bir ayrıştırma işleminde yalnızca bir tek sayı içeren bir Giriş dizesinin gün sayısı yorumlanır. Sayısal dize dakika sayısı yorumlamak için "mm" özel Biçim belirleyicisi yerine kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#13)]
[!code-vb[Conceptual.TimeSpan.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#13)]

Aşağıdaki örnek, "mm" özel Biçim belirleyicisi kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#14)]
[!code-vb[Conceptual.TimeSpan.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#14)]

[Tabloya dön](#table)

<a name="sSpecifier"></a> 

## <a name="the-s-custom-format-specifier"></a>"s" Özel Biçim Belirleyicisi
"S" özel biçim belirticisi değerini çıkarır <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> özelliğini bir parçası olarak, saat, gün veya dakika bileşenini dahil değil zaman aralığındaki tüm saniye sayısını temsil eder. Bir tek basamaklı string değeri döndürür değerini <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> özelliği 0-9 ve iki basamaklı dize değeri varsa döndürür değerini <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> 10'dan 59 özelliği aralıkları.

"S" özel biçim belirticisi tek başına kullanıldığında, "%s" standart biçim dizesi yanlış değil, belirtin. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#15)]
[!code-vb[Conceptual.TimeSpan.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#15)]

Normalde, bir ayrıştırma işleminde yalnızca bir tek sayı içeren bir Giriş dizesinin gün sayısı yorumlanır. Sayısal dize saniye sayısı yorumlamak için "%s" özel Biçim belirleyicisi yerine kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#17)]
[!code-vb[Conceptual.TimeSpan.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#17)]

Aşağıdaki örnek, "s" özel biçim belirticisi kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#16)]
[!code-vb[Conceptual.TimeSpan.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#16)]

[Tabloya dön](#table)

<a name="ssSpecifier"></a> 

## <a name="the-ss-custom-format-specifier"></a>"ss" Özel Biçim Belirleyicisi
"Ss" özel biçim belirticisi değerini çıkarır <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> özelliğini bir parçası olarak, saat, gün veya dakika bileşenini dahil değil zaman aralığındaki tüm saniye sayısını temsil eder. 0 ile 9 arasında değerleri için önünde sıfır çıkış dizesi içerir.

Normalde, bir ayrıştırma işleminde yalnızca bir tek sayı içeren bir Giriş dizesinin gün sayısı yorumlanır. Sayısal dize saniye sayısı yorumlamak için "ss" özel Biçim belirleyicisi yerine kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#18)]
[!code-vb[Conceptual.TimeSpan.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#18)]

Aşağıdaki örnek, "ss" özel biçim belirticisi kullanımını gösterir.

[!code-csharp[Conceptual.TimeSpan.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#19)]
[!code-vb[Conceptual.TimeSpan.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#19)]

[Tabloya dön](#table)

<a name="fSpecifier"></a> 

## <a name="thef-custom-format-specifier"></a>"F" özel biçim Belirleyicisi
"F" özel Biçim belirleyicisi saniyenin onda biri bir zaman aralığındaki çıkarır. Bir biçimlendirme işleminde, kalan tüm kesirli basamaklar kesilir. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, Giriş dizesinin tam olarak bir kesirli rakam içermelidir.

"F" özel biçim belirticisi tek başına kullanıldığında, "%f" standart biçim dizesi yanlış değil şekilde belirtin.

Aşağıdaki örnek, onda biri cinsinden görüntülemek için "f" özel Biçim belirleyicisi kullanır. bir <xref:System.TimeSpan> değeri. "f" tek biçim belirticisi olarak ilk kullanıldığı ve sonra da bir özel biçim dizesinde "s" belirticisi ile birleştirilmiş.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya dön](#table)

<a name="ffSpecifier"></a> 

## <a name="the-ff-custom-format-specifier"></a>"ff" Özel Biçim Belirleyicisi
"Ff" özel Biçim belirleyicisi saniyenin yüzde biri bir zaman aralığındaki çıkarır. Bir biçimlendirme işleminde, kalan tüm kesirli basamaklar kesilir. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, Giriş dizesinin tam olarak iki kesirli bir basamak içermelidir.

Aşağıdaki örnek, saniyenin yüzde biri cinsinden görüntülemek için "ff" özel Biçim belirleyicisi kullanır. bir <xref:System.TimeSpan> değeri. "ff" tek biçim belirticisi olarak ilk kullanıldığı ve sonra da bir özel biçim dizesinde "s" belirticisi ile birleştirilmiş.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya dön](#table)

<a name="f3Specifier"></a> 

## <a name="the-fff-custom-format-specifier"></a>"fff" Özel Biçim Belirleyicisi
"Fff" özel biçim belirticisi (karakterlerle üç "f"), bir zaman aralığını milisaniye çıkarır. Bir biçimlendirme işleminde, kalan tüm kesirli basamaklar kesilir. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, Giriş dizesinin tam olarak üç kesirli rakam içermelidir.

Aşağıdaki örnek, milisaniye cinsinden görüntülemek için "fff" özel Biçim belirleyicisi kullanır. bir <xref:System.TimeSpan> değeri. "fff" tek biçim belirticisi olarak ilk kullanıldığı ve sonra da bir özel biçim dizesinde "s" belirticisi ile birleştirilmiş.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya dön](#table)

<a name="f4Specifier"></a> 

## <a name="the-ffff-custom-format-specifier"></a>"ffff" Özel Biçim Belirleyicisi
"Ffff" özel biçim belirticisi (karakterlerle dört "f"), on binde biri ikinci bir zaman aralığındaki çıkarır. Bir biçimlendirme işleminde, kalan tüm kesirli basamaklar kesilir. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, Giriş dizesinin tam olarak dört kesirli rakam içermelidir.

Aşağıdaki örnek, on binde biri cinsinden görüntülemek için "ffff" özel Biçim belirleyicisi kullanır. bir <xref:System.TimeSpan> değeri. "ffff" tek biçim belirticisi olarak ilk kullanıldığı ve sonra da bir özel biçim dizesinde "s" belirticisi ile birleştirilmiş.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya dön](#table)

<a name="f5Specifier"></a> 

## <a name="the-fffff-custom-format-specifier"></a>"fffff" Özel Biçim Belirleyicisi
Yüz binde biri ikinci bir zaman aralığında "fffff" özel biçim belirticisi (karakterlerle beş "f") çıkarır. Bir biçimlendirme işleminde, kalan tüm kesirli basamaklar kesilir. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, Giriş dizesinin tam olarak beş kesirli rakam içermelidir.

Aşağıdaki örnek, yüz binde biri cinsinden görüntülemek için "fffff" özel Biçim belirleyicisi kullanır. bir <xref:System.TimeSpan> değeri. "fffff" tek biçim belirticisi olarak ilk kullanıldığı ve sonra da bir özel biçim dizesinde "s" belirticisi ile birleştirilmiş.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya dön](#table)

<a name="f6Specifier"></a> 

## <a name="the-ffffff-custom-format-specifier"></a>"ffffff" Özel Biçim Belirleyicisi
(Karakterlerle altı "f") "ffffff" özel biçim tanımlayıcısı bir saniyenin milyonda bir zaman aralığındaki çıkarır. Bir biçimlendirme işleminde, kalan tüm kesirli basamaklar kesilir. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, Giriş dizesinin tam olarak altı kesirli rakam içermelidir.

Aşağıdaki örnek, milyonda biri cinsinden görüntülemek için "ffffff" özel Biçim belirleyicisi kullanır. bir <xref:System.TimeSpan> değeri. Bu ilk tek biçim belirticisi olarak kullanıldığı ve sonra da bir özel biçim dizesinde "s" belirticisi ile birleştirilmiş.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya dön](#table)

<a name="f7Specifier"></a> 

## <a name="the-fffffff-custom-format-specifier"></a>"fffffff" Özel Biçim Belirleyicisi
"Fffffff" özel biçim belirticisi (karakterlerle yedi "f"), ikinci (veya kesir tıklarının sayısını) on milyonda bir zaman aralığında çıkarır. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, Giriş dizesinin tam olarak yedi kesirli rakam içermelidir.

Aşağıdaki örnek, kesirli dalgalanmasındaki sayısını görüntülemek için "fffffff" özel Biçim belirleyicisi kullanır. bir <xref:System.TimeSpan> değeri. Bu ilk tek biçim belirticisi olarak kullanıldığı ve sonra da bir özel biçim dizesinde "s" belirticisi ile birleştirilmiş.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya dön](#table)

<a name="F_Specifier"></a> 

## <a name="the-f-custom-format-specifier"></a>"F" Özel Biçim Belirleyicisi
"F" özel Biçim belirleyicisi saniyenin onda biri bir zaman aralığındaki çıkarır. Bir biçimlendirme işleminde, kalan tüm kesirli basamaklar kesilir. Zaman aralığı onda biri bir değeri sıfır ise, sonuç dizesinde bulunmaz. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, ikinci bir basamak onda varlığını, isteğe bağlıdır.

"F" özel biçim belirticisi tek başına kullanıldığında, "%F" standart biçim dizesi yanlış değil şekilde belirtin.

Aşağıdaki örnek, onda biri cinsinden görüntülemek için "F" özel Biçim belirleyicisi kullanır. bir <xref:System.TimeSpan> değeri. Ayrıca bu özel biçim belirticisi bir ayrıştırma işleminde kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#21)]
[!code-vb[Conceptual.TimeSpan.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#21)]

[Tabloya dön](#table)

<a name="FF_Specifier"></a> 

## <a name="the-ff-custom-format-specifier"></a>"FF" Özel Biçim Belirleyicisi
"FF" özel Biçim belirleyicisi saniyenin yüzde biri bir zaman aralığındaki çıkarır. Bir biçimlendirme işleminde, kalan tüm kesirli basamaklar kesilir. Kesirli sonundaki sıfırları varsa, bunlar sonuç dizesine dahil edilmez. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> onda varlığını ve ikinci bir basamak yüzdesine yöntemidir isteğe bağlı.

Aşağıdaki örnek, saniyenin yüzde biri cinsinden görüntülemek için "FF" özel Biçim belirleyicisi kullanır. bir <xref:System.TimeSpan> değeri. Ayrıca bu özel biçim belirticisi bir ayrıştırma işleminde kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#22)]
[!code-vb[Conceptual.TimeSpan.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#22)]

[Tabloya dön](#table)

<a name="F3_Specifier"></a> 

## <a name="the-fff-custom-format-specifier"></a>"FFF" Özel Biçim Belirleyicisi
"FFF" özel biçim belirticisi (karakterlerle üç "F"), bir zaman aralığını milisaniye çıkarır. Bir biçimlendirme işleminde, kalan tüm kesirli basamaklar kesilir. Kesirli sonundaki sıfırları varsa, bunlar sonuç dizesine dahil edilmez. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi onda, saniyenin yüzde ve ikinci bir basamak binde varlığı, isteğe bağlıdır.

Aşağıdaki örnek, binde biri cinsinden görüntülemek için "FFF" özel Biçim belirleyicisi kullanır. bir <xref:System.TimeSpan> değeri. Ayrıca bu özel biçim belirticisi bir ayrıştırma işleminde kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#23)]
[!code-vb[Conceptual.TimeSpan.Custom#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#23)]

[Tabloya dön](#table)

<a name="F4_Specifier"></a> 

## <a name="the-ffff-custom-format-specifier"></a>"FFFF" Özel Biçim Belirleyicisi
"FFFF" özel biçim belirticisi (karakterlerle dört "F"), on binde biri ikinci bir zaman aralığındaki çıkarır. Bir biçimlendirme işleminde, kalan tüm kesirli basamaklar kesilir. Kesirli sonundaki sıfırları varsa, bunlar sonuç dizesine dahil edilmez. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi onda, saniyenin yüzde, binde ve ikinci bir basamak on binde varlığını, isteğe bağlıdır.

Aşağıdaki örnek, on binde biri cinsinden görüntülemek için "FFFF" özel Biçim belirleyicisi kullanır. bir <xref:System.TimeSpan> değeri. Bir ayrıştırma işleminde "FFFF" özel Biçim belirleyicisi de kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#24)]
[!code-vb[Conceptual.TimeSpan.Custom#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#24)]

[Tabloya dön](#table)

<a name="F5_Specifier"></a> 

## <a name="the-fffff-custom-format-specifier"></a>"FFFFF" Özel Biçim Belirleyicisi
Yüz binde biri ikinci bir zaman aralığında "FFFFF" özel biçim belirticisi (karakterlerle beş "F") çıkarır. Bir biçimlendirme işleminde, kalan tüm kesirli basamaklar kesilir. Kesirli sonundaki sıfırları varsa, bunlar sonuç dizesine dahil edilmez. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi onda, saniyenin yüzde, binde, on binde ve yüz binde biri ikinci basamağını varlığı, isteğe bağlıdır.

Aşağıdaki örnek, yüz binde biri cinsinden görüntülemek için "FFFFF" özel Biçim belirleyicisi kullanır. bir <xref:System.TimeSpan> değeri. Bir ayrıştırma işleminde "FFFFF" özel Biçim belirleyicisi de kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#25)]
[!code-vb[Conceptual.TimeSpan.Custom#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#25)]

[Tabloya dön](#table)

<a name="F6_Specifier"></a> 

## <a name="the-ffffff-custom-format-specifier"></a>"FFFFFF" Özel Biçim Belirleyicisi
(Karakterlerle altı "F") "FFFFFF" özel biçim tanımlayıcısı bir saniyenin milyonda bir zaman aralığındaki çıkarır. Bir biçimlendirme işleminde, kalan tüm kesirli basamaklar kesilir. Kesirli sonundaki sıfırları varsa, bunlar sonuç dizesine dahil edilmez. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi onda, saniyenin yüzde, binde, on binde, yüz binde ve ikinci bir basamak milyonda varlığını, isteğe bağlıdır.

Aşağıdaki örnek, milyonda biri cinsinden görüntülemek için "FFFFFF" özel Biçim belirleyicisi kullanır. bir <xref:System.TimeSpan> değeri. Ayrıca bu özel biçim belirticisi bir ayrıştırma işleminde kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#26](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#26)]
[!code-vb[Conceptual.TimeSpan.Custom#26](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#26)]

[Tabloya dön](#table)

<a name="F7_Specifier"></a> 

## <a name="the-fffffff-custom-format-specifier"></a>"FFFFFFF" Özel Biçim Belirleyicisi
"FFFFFFF" özel biçim belirticisi (karakterlerle yedi "F"), ikinci (veya kesir tıklarının sayısını) on milyonda bir zaman aralığında çıkarır. Kesirli sonundaki sıfırları varsa, bunlar sonuç dizesine dahil edilmez. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, yedi kesirli basamaklar giriş dizesinde bulunması, isteğe bağlıdır.

Aşağıdaki örnek, bir saniye içinde kesirli bölümleri görüntülemek için "FFFFFFF" özel Biçim belirleyicisi kullanır. bir <xref:System.TimeSpan> değeri. Ayrıca bu özel biçim belirticisi bir ayrıştırma işleminde kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#27](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#27)]
[!code-vb[Conceptual.TimeSpan.Custom#27](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#27)]

[Tabloya dön](#table)

<a name="Other"></a> 

## <a name="other-characters"></a>Diğer karakterler

Biçim dizesindeki bir boşluk karakteri dahil olmak üzere, başka bir atlanmayan karakter, bir özel biçim Belirleyicisi olarak yorumlanır. Çoğu durumda, diğer varlığını atlanmayan karakter sonuçları bir <xref:System.FormatException>.

Biçim dizesindeki değişmez bir karakter içerecek şekilde iki yolu vardır:

- Bu, tek tırnak işaretleri (değişmez dize sınırlayıcısı) içine alın.

- Ters eğik çizgi ile önünde ("\\"), bir kaçış karakteri yorumlanır. C# dilinde biçim dizesi ya da olmalıdır, yani @-quoted, veya ek bir ters eğik çizgi değişmez bir karakter gelmelidir.

  Bazı durumlarda, Biçim dizesinde kaçan bir sabit değer eklemek için koşullu mantığı kullanmak zorunda kalabilirsiniz. Aşağıdaki örnek, negatif bir zaman aralıkları için işareti simgesi eklemek için koşullu mantığı kullanır.

  [!code-csharp[Conceptual.TimeSpan.Custom#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/negativevalues1.cs#29)]
  [!code-vb[Conceptual.TimeSpan.Custom#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/negativevalues1.vb#29)]

.NET ayırıcılar için bir dil bilgisi, zaman aralıkları tanımlamıyor. Başka bir deyişle, gün ve saat, saat ve dakika, dakika ve saniye ve saniye ve ikinci bölümleri arasındaki ayırıcı tüm biçim dizesindeki karakter değişmez değerleri olarak değerlendirilmesini gerekir.

Aşağıdaki örnek çıktı dizesinde "dakika" sözcüğünü içeren bir özel biçim dizesinde tanımlamak için kaçış karakteri hem tek tırnak işareti kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/literal1.cs#28)]
[!code-vb[Conceptual.TimeSpan.Custom#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/literal1.vb#28)]

[Tabloya dön](#table)

## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme Türleri](formatting-types.md)
- [Standart TimeSpan Biçim Dizeleri](standard-timespan-format-strings.md)
