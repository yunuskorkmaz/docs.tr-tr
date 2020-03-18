---
title: Özel TimeSpan biçim dizeleri
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75348315"
---
# <a name="custom-timespan-format-strings"></a>Özel TimeSpan biçim dizeleri

Biçimlendirme <xref:System.TimeSpan> dizesi, biçimlendirme <xref:System.TimeSpan> işleminden kaynaklanan bir değerin dize temsilini tanımlar. Özel biçim dizesi, herhangi <xref:System.TimeSpan> bir sayıda gerçek karakterle birlikte bir veya daha fazla özel biçim belirteçlerinden oluşur. [Standart TimeSpan biçim dizesi](standard-timespan-format-strings.md) olmayan herhangi bir dize özel <xref:System.TimeSpan> biçim dizesi olarak yorumlanır.

> [!IMPORTANT]
> Özel <xref:System.TimeSpan> biçim belirteçleri, saat, saat dakika veya kesirli saniyesaniye gün ayıran semboller gibi yer tutucu ayırıcı sembolleri içermez. Bunun yerine, bu semboller dize literals olarak özel biçim dize dahil edilmelidir. Örneğin, `"dd\.hh\:mm"` gün ve saat arasında ayırıcı olarak bir dönem (.) tanımlar ve bir iki nokta üst üste (:) saat ve dakika arasında ayırıcı olarak.
>
> Özel <xref:System.TimeSpan> biçim belirteçleri, negatif ve pozitif zaman aralıkları arasında ayrım yapmanızı sağlayan bir işaret simgesi de içermez. Bir işaret simgesi eklemek için koşullu mantık kullanarak bir biçim dizesi oluşturmanız gerekir. [Diğer karakterler](#other-characters) bölümü bir örnek içerir.

<xref:System.TimeSpan> Değerlerin dize gösterimleri, <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> yöntemin aşırı yüklerine yapılan çağrılar ve <xref:System.String.Format%2A?displayProperty=nameWithType>bileşik biçimlendirmeyi destekleyen yöntemlerle üretilir. Daha fazla bilgi için [bkz.](formatting-types.md) [Composite Formatting](composite-formatting.md) Aşağıdaki örnekte, biçimlendirme işlemlerinde özel biçim dizeleri kullanımı gösteriş verilmiştir.

[!code-csharp[Conceptual.TimeSpan.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customformatexample1.cs#1)]
[!code-vb[Conceptual.TimeSpan.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customformatexample1.vb#1)]

Özel <xref:System.TimeSpan> biçim dizeleri de <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ayrışma işlemleri için giriş dizeleri gerekli biçimini tanımlamak için ve <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemler tarafından kullanılır. (Ayrıştırma, bir değerin dize temsilini bu değere dönüştürür.) Aşağıdaki örnekte, ayrıştma işlemlerinde standart biçim dizeleri kullanımı gösterilmektedir.

[!code-csharp[Conceptual.TimeSpan.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customparseexample1.cs#2)]
[!code-vb[Conceptual.TimeSpan.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customparseexample1.vb#2)]

<a name="table"></a>Aşağıdaki tabloda özel tarih ve saat biçimi belirteciler açıklanmaktadır.

| Biçim belirteci | Açıklama | Örnek |
|----------------------|-----------------|-------------|
|"d", "%d"|Zaman aralığındaki tam gün sayısı.<br /><br /> Daha fazla bilgi: ["d" özel biçim belirtimi.](#dSpecifier)|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%d`--> "6"<br /><br /> `d\.hh\:mm`--> "6.14:32"|
|"dd"-"ddddddd"|Zaman aralığındaki tam gün sayısı, gerektiğinde önde gelen sıfırlarla birlikte yastıklı.<br /><br /> Daha fazla bilgi: ["dd"-"ddddddd" özel format belirteci](#ddSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `ddd`--> "006"<br /><br /> `dd\.hh\:mm`--> "06.14:32"|
|"h", "%h"|Günlerin bir parçası olarak sayılmayan zaman aralığındaki tam saat sayısı. Tek basamaklı saatlerin satır aralığı sıfırı yoktur.<br /><br /> Daha fazla bilgi: ["h" özel biçim belirtimi.](#hSpecifier)|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%h`--> "14"<br /><br /> `hh\:mm`--> "14:32"|
|"hh"|Günlerin bir parçası olarak sayılmayan zaman aralığındaki tam saat sayısı. Tek basamaklı saatlerin satır aralığı sıfırdır.<br /><br /> Daha fazla bilgi: ["hh" özel biçim belirtimi](#hhSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `hh`--> "14"<br /><br /> `new TimeSpan(6, 8, 32, 17, 685):`<br /><br /> `hh`--> 08|
|"m", "%m"|Saat veya günlerin bir parçası olarak dahil olmayan zaman aralığındaki tam dakika sayısı. Tek basamaklı dakikaların satır aralığı sıfırı yoktur.<br /><br /> Daha fazla bilgi: ["m" özel biçim belirticisi.](#mSpecifier)|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `%m`--> "8"<br /><br /> `h\:m`--> "14:8"|
|"mm"|Saat veya günlerin bir parçası olarak dahil olmayan zaman aralığındaki tam dakika sayısı. Tek basamaklı dakikaların bir satır aralığı sıfırı var.<br /><br /> Daha fazla bilgi: ["mm" özel biçim belirtimi.](#mmSpecifier)|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `mm`--> "08"<br /><br /> `new TimeSpan(6, 8, 5, 17, 685):`<br /><br /> `d\.hh\:mm\:ss`--> 6.08:05:17|
|"s", "%s"|Saat, gün veya dakikanın parçası olarak dahil olmayan zaman aralığındaki tam saniye sayısı. Tek basamaklı saniyeler satır aralığı sıfırı yoktur.<br /><br /> Daha fazla bilgi: ["s" özel biçim belirtimi.](#sSpecifier)|`TimeSpan.FromSeconds(12.965)`:<br /><br /> `%s`--> 12<br /><br /> `s\.fff`--> 12.965|
|"ss"|Saat, gün veya dakikanın parçası olarak dahil olmayan zaman aralığındaki tam saniye sayısı.  Tek basamaklı saniyeler bir satır aralığı sıfıra sahiptir.<br /><br /> Daha fazla bilgi: ["ss" özel biçim belirtimi.](#ssSpecifier)|`TimeSpan.FromSeconds(6.965)`:<br /><br /> `ss`--> 06<br /><br /> `ss\.fff`--> 06.965|
|"f", "%f"|Bir zaman aralığında saniyenin onda biri.<br /><br /> Daha fazla bilgi: ["f" özel biçim belirtimi.](#fSpecifier)|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `f`--> 8<br /><br /> `ss\.f`--> 06,8|
|"ff"|Zaman aralığında saniyenin yüzde biri.<br /><br /> Daha fazla bilgi: ["ff" özel biçim belirtimi](#ffSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `ff`--> 89<br /><br /> `ss\.ff`--> 06,89|
|"fff"|Zaman aralığında milisaniye.<br /><br /> Daha fazla bilgi: ["fff" özel biçim belirtimi.](#f3Specifier)|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `fff`--> 895<br /><br /> `ss\.fff`--> 06.895|
|"ffff"|Bir zaman aralığında saniyenin onbinde.<br /><br /> Daha fazla bilgi: ["ffff" özel biçim belirtimi.](#f4Specifier)|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffff`--> 8954<br /><br /> `ss\.ffff`--> 06.8954|
|"fffff"|Bir zaman aralığında saniyenin binde biri.<br /><br /> Daha fazla bilgi: ["fffff" özel biçim belirtimi](#f5Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffff`--> 89543<br /><br /> `ss\.fffff`--> 06.89543|
|"ffffff"|Zaman aralığında saniyenin milyonda biri.<br /><br /> Daha fazla bilgi: ["ffffff" özel format belirtimi](#f6Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffffff`--> 895432<br /><br /> `ss\.ffffff`--> 06.895432|
|"fffffff"|Bir zaman aralığında saniyenin on milyonda biri (veya kesirli keneler).<br /><br /> Daha fazla bilgi: ["fffffff" özel biçim belirtimi](#f7Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffffff`--> 8954321<br /><br /> `ss\.fffffff`--> 06.8954321|
|"F", "%F"|Bir zaman aralığında saniyenin onda biri. Basamak sıfırsa hiçbir şey görüntülenmez.<br /><br /> Daha fazla bilgi: ["F" özel biçim belirtimi.](#F_Specifier)|`TimeSpan.Parse("00:00:06.32")`:<br /><br /> `%F`: 3<br /><br /> `TimeSpan.Parse("0:0:3.091")`:<br /><br /> `ss\.F`: 03.|
|"FF"|Zaman aralığında saniyenin yüzde biri. Herhangi bir kesirli sondaki sıfırlar veya iki sıfır basamak dahil değildir.<br /><br /> Daha fazla bilgi: ["FF" özel biçim belirtimi.](#FF_Specifier)|`TimeSpan.Parse("00:00:06.329")`:<br /><br /> `FF`: 32<br /><br /> `TimeSpan.Parse("0:0:3.101")`:<br /><br /> `ss\.FF`: 03.1|
|"FFF"|Zaman aralığında milisaniye. Herhangi bir kesirli sondaki sıfırlar dahil değildir.<br /><br /> Daha fazla bilgi:|`TimeSpan.Parse("00:00:06.3291")`:<br /><br /> `FFF`: 329<br /><br /> `TimeSpan.Parse("0:0:3.1009")`:<br /><br /> `ss\.FFF`: 03.1|
|"FFFF"|Bir zaman aralığında saniyenin onbinde. Herhangi bir kesirli sondaki sıfırlar dahil değildir.<br /><br /> Daha fazla bilgi: ["FFFF" özel biçim belirtimi.](#F4_Specifier)|`TimeSpan.Parse("00:00:06.32917")`:<br /><br /> `FFFFF`: 3291<br /><br /> `TimeSpan.Parse("0:0:3.10009")`:<br /><br /> `ss\.FFFF`: 03.1|
|"FFFFF"|Bir zaman aralığında saniyenin binde biri. Herhangi bir kesirli sondaki sıfırlar dahil değildir.<br /><br /> Daha fazla bilgi: ["FFFFF" özel biçim belirtimi.](#F5_Specifier)|`TimeSpan.Parse("00:00:06.329179")`:<br /><br /> `FFFFF`: 32917<br /><br /> `TimeSpan.Parse("0:0:3.100009")`:<br /><br /> `ss\.FFFFF`: 03.1|
|"FFFFFF"|Zaman aralığında saniyenin milyonda biri. Kesirli sondaki sıfırlar görüntülenmez.<br /><br /> Daha fazla bilgi: ["FFFFFF" özel format belirtimi.](#F6_Specifier)|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 329179<br /><br /> `TimeSpan.Parse("0:0:3.1000009")`:<br /><br /> `ss\.FFFFFF`: 03.1|
|"FFFFFFF"|Bir zaman aralığında saniyenin on milyonlarcası. Herhangi bir kesirli sondaki sıfırlar veya yedi sıfır görüntülenmez.<br /><br /> Daha fazla bilgi: ["FFFFFFF" özel biçim belirtimi.](#F7_Specifier)|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 3291791<br /><br /> `TimeSpan.Parse("0:0:3.1900000")`:<br /><br /> `ss\.FFFFFF`: 03.19|
|'*dize*'|Değişmez dize sınırlayıcısı.<br /><br /> Daha fazla bilgi: [Diğer karakterler](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh':'mm':'ss`--> "14:32:17"|
|&#92;|"\" çıkış karakteri.<br /><br /> Daha fazla bilgi: [Diğer karakterler](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss`--> "14:32:17"|
|Başka bir karakter|Başka bir unescape karakter özel bir biçim belirteç olarak yorumlanır.<br /><br /> Daha Fazla Bilgi: [Diğer karakterler](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss`--> "14:32:17"|

## <a name="dSpecifier"></a>"d" özel biçim belirtimi

"d" özel biçim belirten özellik, zaman <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> aralığındaki tam gün sayısını temsil eden değer çıktıları belirtir. Değer birden fazla basamaklı olsa <xref:System.TimeSpan> bile, bir değerdeki tam gün sayısını çıkar. <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> Özelliğin değeri sıfır ise, belirtici çıkışları "0".

"d" özel biçim belirticisi tek başına kullanılıyorsa, standart biçim dizesi olarak yanlış yorumlanamasın diye "%d" belirtin. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#3)]
[!code-vb[Conceptual.TimeSpan.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#3)]

Aşağıdaki örnekte "d" özel biçim belirticisinin kullanımı gösteriş verilmiştir.

[!code-csharp[Conceptual.TimeSpan.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#4)]
[!code-vb[Conceptual.TimeSpan.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#4)]

[Tabloya geri dön](#table)

## <a name="ddSpecifier"></a>"dd"-"dddddddd" özel format belirtimleri

"dd", "ddd", "ddddd", "dddddd", "ddddddd", ve "dddddddd" özel formatı, zaman aralığındaki tüm <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> gün sayısını temsil eden özelliğin değerini gösterir.

Çıkış dizesi, biçim belirticideki "d" karakter sayısına göre belirtilen en az sayıda basamak içerir ve gerektiğinde önde gelen sıfırlarla yastıklıdır. Gün sayısındaki basamaklar biçim belirticideki "d" karakter sayısını aşıyorsa, tam gün sayısı sonuç dizesinde çıktıolur.

Aşağıdaki örnekte, iki <xref:System.TimeSpan> değerin dize gösterimini görüntülemek için bu biçim belirteçleri kullanır. İlk zaman aralığının gün bileşeninin değeri sıfırdır; saniyenin gün bileşeninin değeri 365'tir.

[!code-csharp[Conceptual.TimeSpan.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#5)]
[!code-vb[Conceptual.TimeSpan.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#5)]

[Tabloya geri dön](#table)

## <a name="hSpecifier"></a>"h" özel biçim belirtimi

"h" özel biçim, gün bileşeninin bir <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> parçası olarak sayılmayan zaman aralığındaki tam saat sayısını temsil eden özelliğin değerini belirtir. Özelliğin <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> değeri 0'dan 9'a kadar sayılsa tek basamaklı bir dize değeri döndürür ve <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> özelliğin değeri 10 ile 23 arasında değişiyorsa iki basamaklı bir dize değeri döndürür.

"h" özel biçim belirticisi tek başına kullanılıyorsa, standart biçim dizesi olarak yanlış yorumlanmamasın diye "%h" belirtin. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Normalde, bir ayrıştırma işleminde, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Sayısal dizeyi saat sayısı olarak yorumlamak için "%h" özel biçim belirticisini kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#8)]
[!code-vb[Conceptual.TimeSpan.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#8)]

Aşağıdaki örnekte "h" özel biçim belirticisinin kullanımı gösteriş verilmiştir.

[!code-csharp[Conceptual.TimeSpan.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#7)]
[!code-vb[Conceptual.TimeSpan.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#7)]

[Tabloya geri dön](#table)

## <a name="hhSpecifier"></a>"hh" özel biçim belirtimi

"Hh" özel biçim, gün bileşeninin bir <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> parçası olarak sayılmayan zaman aralığındaki tam saat sayısını temsil eden özelliğin değerini belirtir. 0 ile 9 arasında olan değerler için çıkış dizesi bir satır aralığı sıfır içerir.

Normalde, bir ayrıştırma işleminde, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Bunun yerine sayısal dizeyi saat sayısı olarak yorumlamak için "hh" özel biçim belirticisini kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#9)]
[!code-vb[Conceptual.TimeSpan.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#9)]

Aşağıdaki örnekte "hh" özel biçim belirtiminin kullanımı gösteriş verilmiştir.

[!code-csharp[Conceptual.TimeSpan.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#10)]
[!code-vb[Conceptual.TimeSpan.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#10)]

[Tabloya geri dön](#table)

## <a name="mSpecifier"></a>"m" özel biçim belirtimi

"m" özel biçim, gün bileşeninin bir <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> parçası olarak sayılmayan zaman aralığındaki tam dakika sayısını temsil eden özelliğin değerini belirtir. Özelliğin <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> değeri 0'dan 9'a kadar sayılsa tek basamaklı bir dize değeri döndürür ve <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> özelliğin değeri 10 ile 59 arasında değişiyorsa iki basamaklı bir dize değeri döndürür.

"m" özel biçim belirticisi tek başına kullanılıyorsa, standart biçim dizesi olarak yanlış yorumlanmamasın diye "%m" belirtin. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Normalde, bir ayrıştırma işleminde, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Sayısal dizeyi dakika sayısı olarak yorumlamak için "%m" özel biçim belirticisini kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#11)]
[!code-vb[Conceptual.TimeSpan.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#11)]

Aşağıdaki örnekte "m" özel biçim belirticisinin kullanımı gösteriş verilmiştir.

[!code-csharp[Conceptual.TimeSpan.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#12)]
[!code-vb[Conceptual.TimeSpan.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#12)]

[Tabloya geri dön](#table)

## <a name="mmSpecifier"></a>"mm" özel biçim belirtimi

"mm" özel biçim, saat veya gün <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> bileşeninin bir parçası olarak dahil olmayan zaman aralığındaki tam dakika sayısını temsil eden özelliğin değerini belirtir. 0 ile 9 arasında olan değerler için çıkış dizesi bir satır aralığı sıfır içerir.

Normalde, bir ayrıştırma işleminde, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Sayısal dizeyi dakika sayısı olarak yorumlamak için "mm" özel biçim belirticisini kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#13)]
[!code-vb[Conceptual.TimeSpan.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#13)]

Aşağıdaki örnekte "mm" özel biçim belirticisinin kullanımı gösteriş verilmiştir.

[!code-csharp[Conceptual.TimeSpan.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#14)]
[!code-vb[Conceptual.TimeSpan.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#14)]

[Tabloya geri dön](#table)

## <a name="sSpecifier"></a>"s" özel biçim belirtimi

"s" özel biçim, saat, gün veya <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> dakika bileşeninin bir parçası olarak dahil olmayan zaman aralığındaki tam saniye sayısını temsil eden özelliğin değerini belirtir. Özelliğin <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> değeri 0'dan 9'a kadar sayılsa tek basamaklı bir dize değeri döndürür ve <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> özelliğin değeri 10 ile 59 arasında değişiyorsa iki basamaklı bir dize değeri döndürür.

"s" özel biçim belirtici tek başına kullanılırsa, standart biçim dizesi olarak yanlış yorumlanmamasın diye "%s" belirtin. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#15)]
[!code-vb[Conceptual.TimeSpan.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#15)]

Normalde, bir ayrıştırma işleminde, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Sayısal dizeyi saniye sayısı olarak yorumlamak için "%s" özel biçim belirticisini kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#17)]
[!code-vb[Conceptual.TimeSpan.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#17)]

Aşağıdaki örnekte "s" özel biçim belirticisinin kullanımı gösteriş verilmiştir.

[!code-csharp[Conceptual.TimeSpan.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#16)]
[!code-vb[Conceptual.TimeSpan.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#16)]

[Tabloya geri dön](#table)

## <a name="ssSpecifier"></a>"ss" özel biçim belirtimi

"ss" özel biçim belirteçleri, saat, gün veya dakika bileşeninin bir parçası olarak dahil olmayan zaman aralığındaki tam saniye sayısını temsil eden <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> özelliğin değerini belirtir. 0 ile 9 arasında olan değerler için çıkış dizesi bir satır aralığı sıfır içerir.

Normalde, bir ayrıştırma işleminde, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Sayısal dizeyi saniye sayısı olarak yorumlamak için yerine "ss" özel biçim belirticisini kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.TimeSpan.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#18)]
[!code-vb[Conceptual.TimeSpan.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#18)]

Aşağıdaki örnekte "ss" özel biçim belirtiminin kullanımı gösteriş verilmiştir.

[!code-csharp[Conceptual.TimeSpan.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#19)]
[!code-vb[Conceptual.TimeSpan.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#19)]

[Tabloya geri dön](#table)

## <a name="fSpecifier"></a>"f" özel biçim belirtimi

"F" özel biçim, bir zaman aralığında saniyenin onda biri çıktılarını belirtir. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Giriş dizesi, <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya yöntemi <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> çağıran bir ayrıştma işleminde tam olarak bir kesirli basamak içermelidir.

"F" özel biçim belirticisi tek başına kullanılıyorsa, standart biçim dizesi olarak yanlış yorumlanmamasın diye "%f" belirtin.

Aşağıdaki örnekte, saniyenin onda birini bir <xref:System.TimeSpan> değerde görüntülemek için "f" özel biçim belirtimi kullanır. "f" önce tek biçim belirticisi olarak kullanılır, sonra da özel bir biçim dizesinde "s" belirticisi ile birleştirilir.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya geri dön](#table)

## <a name="ffSpecifier"></a>"ff" özel biçim belirtimi

"ff" özel biçim belirtici, bir zaman aralığında saniyenin yüzde biri çıktıları belirtir. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Veya <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi çağıran bir ayrışma işleminde, giriş dizesi tam olarak iki kesirli basamak içermelidir.

Aşağıdaki örnekte, bir <xref:System.TimeSpan> değerde saniyenin yüzde birini görüntülemek için "ff" özel biçim belirtimi kullanır. "ff" önce tek biçim belirticisi olarak kullanılır, sonra da özel bir biçim dizesinde "s" belirticisi ile birleştirilir.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya geri dön](#table)

## <a name="f3Specifier"></a>"fff" özel biçim belirtimi

"Fff" özel biçim belirtici (üç "f" karakterli) milisaniyeleri bir zaman aralığında çıkar. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Veya <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi çağıran bir ayrışma işleminde, giriş dizesi tam olarak üç kesirli basamak içermelidir.

Aşağıdaki örnekte milisaniyeleri bir <xref:System.TimeSpan> değerde görüntülemek için "fff" özel biçim belirtimi kullanır. "fff" önce tek biçim belirticisi olarak kullanılır, sonra da özel bir biçim dizesinde "s" belirticisi ile birleştirilir.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya geri dön](#table)

## <a name="f4Specifier"></a>"Ffff" özel biçim belirtimi

"Ffff" özel biçim belirtici (dört "f" karakteri ile) bir zaman aralığında saniyenin onbinde çıkışları. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Veya <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi çağıran bir ayrışma işleminde, giriş dizesi tam olarak dört kesirli basamak içermelidir.

Aşağıdaki örnekte, saniyenin onbinde birini bir <xref:System.TimeSpan> değerde görüntülemek için "ffff" özel biçim belirtimi kullanır. "ffff" önce tek biçim belirticisi olarak kullanılır, sonra da özel bir biçim dizesinde "s" belirticisi ile birleştirilir.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya geri dön](#table)

## <a name="f5Specifier"></a>"fffff" özel biçim belirtimi

"Fffff" özel biçim belirtici (beş "f" karakterile) bir zaman aralığında saniyenin yüz binde çıkışları. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Veya <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi çağıran bir ayrışma işleminde, giriş dizesi tam olarak beş kesirli basamak içermelidir.

Aşağıdaki örnekte, saniyenin binde birini bir <xref:System.TimeSpan> değerde görüntülemek için "fffff" özel biçim belirtici kullanır. "fffff" önce tek biçim belirticisi olarak kullanılır, sonra da özel bir biçim dizesinde "s" belirticisi ile birleştirilir.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya geri dön](#table)

## <a name="f6Specifier"></a>"ffffff" özel biçim belirtimi

"Ffffff" özel biçim belirtici (altı "f" karakterile) bir zaman aralığında saniyenin milyonda biri çıkar. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Veya <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi çağıran bir ayrışma işleminde, giriş dizesi tam olarak altı kesirli basamak içermelidir.

Aşağıdaki örnekte, saniyenin milyonda birini bir <xref:System.TimeSpan> değerde görüntülemek için "ffffff" özel biçim belirtimi kullanır. Önce tek biçim belirticisi olarak kullanılır ve daha sonra özel bir biçim dizesinde "s" belirticisi ile birleştirilir.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya geri dön](#table)

## <a name="f7Specifier"></a>"Fffffff" özel biçim belirtimi

"Fffffff" özel biçim belirtici (yedi "f" karakteri yle) bir zaman aralığında saniyenin on milyonda biri (veya kesirli kene sayısı) çıkar. Veya <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi çağıran bir ayrışma işleminde, giriş dizesi tam olarak yedi kesirli basamak içermelidir.

Aşağıdaki örnekte, bir <xref:System.TimeSpan> değerdeki kesir sayısını görüntülemek için "fffffff" özel biçim belirtimi kullanır. Önce tek biçim belirticisi olarak kullanılır ve daha sonra özel bir biçim dizesinde "s" belirticisi ile birleştirilir.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Tabloya geri dön](#table)

## <a name="F_Specifier"></a>"F" özel biçim belirtimi

"F" özel biçim, bir zaman aralığında saniyenin onda biri çıktılarını belirtir. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Zaman aralığının saniyenin onda birinin değeri sıfırsa, sonuç dizesi dahil değildir. Yöntemi <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya yöntemi <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> çağıran bir ayrıştırma işleminde, ikinci bir rakamın onda birinin varlığı isteğe bağlıdır.

"F" özel biçim belirticisi tek başına kullanılıyorsa, standart biçim dizesi olarak yanlış yorumlanamasın diye "%F" belirtin.

Aşağıdaki örnekte, saniyenin onda birini bir <xref:System.TimeSpan> değerde görüntülemek için "F" özel biçim belirtimi kullanır. Ayrıca, ayrışdırma işleminde bu özel biçim belirtici kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#21)]
[!code-vb[Conceptual.TimeSpan.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#21)]

[Tabloya geri dön](#table)

## <a name="FF_Specifier"></a>"FF" özel biçim belirtimi

"FF" özel biçim belirtici, bir zaman aralığında saniyenin yüzde biri çıktıları belirtir. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Herhangi bir iz bırakan kesirli sıfırlar varsa, bunlar sonuç dizesi dahil değildir. Yöntemi <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> çağıran <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> bir ayrıştırma işleminde, ikinci bir rakamın onda biri ve yüzdelerinin varlığı isteğe bağlıdır.

Aşağıdaki örnekte, bir <xref:System.TimeSpan> değerde saniyenin yüzde birini görüntülemek için "FF" özel biçim belirtimi kullanır. Ayrıca, ayrışdırma işleminde bu özel biçim belirtici kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#22)]
[!code-vb[Conceptual.TimeSpan.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#22)]

[Tabloya geri dön](#table)

## <a name="F3_Specifier"></a>"FFF" özel biçim belirtimi

"FFF" özel biçim belirtimi (üç "F" karakteriyle) milisaniyeleri bir zaman aralığında çıkar. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Herhangi bir iz bırakan kesirli sıfırlar varsa, bunlar sonuç dizesi dahil değildir. Yöntemi <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> çağıran <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> bir ayrıştırma işleminde, onda, yüzde ve binde bir ikinci rakamın varlığı isteğe bağlıdır.

Aşağıdaki örnekte, saniyenin binde birini bir <xref:System.TimeSpan> değerde görüntülemek için "FFF" özel biçim belirtimi kullanır. Ayrıca, ayrışdırma işleminde bu özel biçim belirtici kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#23)]
[!code-vb[Conceptual.TimeSpan.Custom#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#23)]

[Tabloya geri dön](#table)

## <a name="F4_Specifier"></a>"FFFF" özel biçim belirtimi

"FFFF" özel biçim belirtici (dört "F" karakteri ile) bir zaman aralığında saniyenin onbinde çıkışlar. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Herhangi bir iz bırakan kesirli sıfırlar varsa, bunlar sonuç dizesi dahil değildir. Yöntemi <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> çağıran <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> bir ayrıştırma işleminde, ikinci basamakta onda, yüzde, binde ve onda birinin varlığı isteğe bağlıdır.

Aşağıdaki örnekte, saniyenin onbinde birini bir <xref:System.TimeSpan> değerde görüntülemek için "FFFF" özel biçim belirtimi kullanır. Ayrıca bir ayrıştırma işleminde "FFFF" özel biçim belirtimi kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#24)]
[!code-vb[Conceptual.TimeSpan.Custom#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#24)]

[Tabloya geri dön](#table)

## <a name="F5_Specifier"></a>"FFFFF" özel biçim belirtimi

"FFFFF" özel biçim belirtici (beş "F" karakterile) bir zaman aralığında saniyenin yüz binde çıkışları. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Herhangi bir iz bırakan kesirli sıfırlar varsa, bunlar sonuç dizesi dahil değildir. Bu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> yöntemi veya yöntemi <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> çağıran bir ayrıştırma işleminde, onda, yüzde, binde, onda onda birinin ve ikinci rakamın binde birinin varlığı isteğe bağlıdır.

Aşağıdaki örnekte, saniyenin binde birini bir <xref:System.TimeSpan> değerde görüntülemek için "FFFFF" özel biçim belirtimi kullanır. Ayrıca bir ayrıştırma işleminde "FFFFF" özel biçim belirtimi kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#25)]
[!code-vb[Conceptual.TimeSpan.Custom#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#25)]

[Tabloya geri dön](#table)

## <a name="F6_Specifier"></a>"FFFFFF" özel biçim belirtimi

"FFFFFF" özel biçim belirtici (altı "F" karakteri yle) bir zaman aralığında saniyenin milyonda biri kadar çıkar. Biçimlendirme işleminde, kalan kesirli basamaklar kesilir. Herhangi bir iz bırakan kesirli sıfırlar varsa, bunlar sonuç dizesi dahil değildir. Bu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> yöntemi veya yöntemi <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> çağıran bir ayrıştırma işleminde, onda, yüzde, binde, on binde, yüz binde ve ikinci rakamın milyonda birinin varlığı isteğe bağlıdır.

Aşağıdaki örnekte, saniyenin milyonda birini bir <xref:System.TimeSpan> değerde görüntülemek için "FFFFFF" özel biçim belirtimi kullanır. Ayrıca, ayrışdırma işleminde bu özel biçim belirtici kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#26](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#26)]
[!code-vb[Conceptual.TimeSpan.Custom#26](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#26)]

[Tabloya geri dön](#table)

## <a name="F7_Specifier"></a>"FFFFFFF" özel biçim belirtimi

"FFFFFFF" özel biçim belirtici (yedi "F" karakteri yle) bir zaman aralığında saniyenin on milyonda biri (veya kesirli kene sayısı) çıkar. Herhangi bir iz bırakan kesirli sıfırlar varsa, bunlar sonuç dizesi dahil değildir. Bir ayrıştırma <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> işleminde, <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> giriş dizesinde yedi kesirli basamak bulunursa isteğe bağlıdır.

Aşağıdaki örnekte, bir saniyenin kesirli parçalarını bir <xref:System.TimeSpan> değerde görüntülemek için "FFFFFFF" özel biçim belirtimi kullanır. Ayrıca, ayrışdırma işleminde bu özel biçim belirtici kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#27](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#27)]
[!code-vb[Conceptual.TimeSpan.Custom#27](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#27)]

[Tabloya geri dön](#table)

## <a name="other-characters"></a>Diğer karakterler

Bir biçim lendirme dizesinde, beyaz alan karakteri de dahil olmak üzere, başka bir kaçılmamış karakter, özel biçim belirtimi olarak yorumlanır. Çoğu durumda, başka bir kaçılmamış karakterin varlığı <xref:System.FormatException>bir .

Bir biçim dizesinde gerçek bir karakter eklemenin iki yolu vardır:

- Tek tırnak işaretleri (literal string delimiter) içine.

- Bir kaçış karakteri olarak yorumlanır bir ters eğik çizgi ("\\") ile önce. Bu, C#'da biçim dizesi @-quotedolması gerektiği veya gerçek karakterin ek bir ters eğik çizgiden önce olması gerektiği anlamına gelir.

  Bazı durumlarda, bir biçim dizekaçan bir literal eklemek için koşullu mantık kullanmanız gerekebilir. Aşağıdaki örnek, negatif zaman aralıkları için bir işaret simgesi eklemek için koşullu mantık kullanır.

  [!code-csharp[Conceptual.TimeSpan.Custom#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/negativevalues1.cs#29)]
  [!code-vb[Conceptual.TimeSpan.Custom#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/negativevalues1.vb#29)]

.NET, zaman aralıklarında ayırıcılar için bir dilbilgisi tanımlamaz. Bu, gün ve saat, saat ve dakika, dakika ve saniye arasındaki ayırıcıların, saniyenin saniye ve kesirlerinin tümü bir biçim dizesinde karakter literals olarak ele alınması gerektiği anlamına gelir.

Aşağıdaki örnek, çıkış dizesinde "dakika" sözcüğü içeren özel bir biçim dizesini tanımlamak için hem kaçış karakterini hem de tek teklifi kullanır.

[!code-csharp[Conceptual.TimeSpan.Custom#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/literal1.cs#28)]
[!code-vb[Conceptual.TimeSpan.Custom#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/literal1.vb#28)]

[Tabloya geri dön](#table)

## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme Türleri](formatting-types.md)
- [Standart TimeSpan Biçim Dizeleri](standard-timespan-format-strings.md)
