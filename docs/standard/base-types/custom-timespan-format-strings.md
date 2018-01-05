---
title: "Özel TimeSpan Biçim Dizeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f86aeab5a024c463dbfbf0a0d0ff198cef80f7ac
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="custom-timespan-format-strings"></a>Özel TimeSpan Biçim Dizeleri
A <xref:System.TimeSpan> biçim dizesi tanımlayan dize gösterimini bir <xref:System.TimeSpan> bir biçimlendirme işleminin sonuçları değeri. Özel bir biçim dizesi bir veya daha fazla özel oluşur <xref:System.TimeSpan> biçimlendirmek değişmez değer karakter herhangi bir sayıda birlikte tanımlayıcıları. Değil herhangi bir dize bir [standart TimeSpan biçim dizesi](../../../docs/standard/base-types/standard-timespan-format-strings.md) özel olarak yorumlanır <xref:System.TimeSpan> biçim dizesi.  
  
> [!IMPORTANT]
>  Özel <xref:System.TimeSpan> biçim belirticileri günü ayırmak saat, dakika saat veya kesirli saniye saniyeden simgeler gibi yer tutucu ayırıcı simgeleri içermez. Bunun yerine, bu simgeleri özel biçim dizesini dize değişmez değerleri eklenmesi gerekir. Örneğin, `"dd\.hh\:mm"` saat ve dakika arasında ayırıcı olarak günleri ve saatleri ve iki nokta üst üste (:) arasındaki ayırıcı olarak bir nokta (.) tanımlar.  
>   
>  Özel <xref:System.TimeSpan> biçim belirticileri de dahil pozitif ve negatif zaman aralıkları arasında ayırt olanak tanıyan bir oturum simge. Bir oturum simge eklemek için koşullu mantık kullanarak bir biçim dizesi oluşturmak zorunda. [Diğer karakterler](#Other) bölüm bir örnek içerir.  
  
 Dize gösterimlerini <xref:System.TimeSpan> değerleri aşırı yapılan çağrılar tarafından üretilen <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> yöntemi ile bileşik gibi biçimlendirme, destek yöntemleri <xref:System.String.Format%2A?displayProperty=nameWithType>. Daha fazla bilgi için bkz: [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md) ve [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md). Aşağıdaki örnek işlemleri biçimlendirmesindeki özel biçim dizeleri kullanımını göstermektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customformatexample1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customformatexample1.vb#1)]  
  
 Özel <xref:System.TimeSpan> biçim dizeleri tarafından da kullanılır <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ve <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> ilişkin gerekli biçime tanımlamak için yöntemleri giriş işlemleri ayrıştırması dizeleri. (Ayrıştırma değeri dize gösterimini bu değerine dönüştürür.) Aşağıdaki örnek işlemleri ayrıştırılırken standart biçim dizeleri kullanımını göstermektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customparseexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customparseexample1.vb#2)]  
  
<a name="table"></a>Aşağıdaki tabloda özel tarih ve saat biçim belirticileri açıklanmaktadır.  
  
|Biçim belirteci|Açıklama|Örnek|  
|----------------------|-----------------|-------------|  
|"d", "%d"|Tam gün sayısını zaman aralığı içinde.<br /><br /> Daha fazla bilgi: ["D" özel biçim belirticisi](#dSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%d` --> "6"<br /><br /> `d\.hh\:mm` --> "6.14:32"|  
|"aa"-"dddddddd"|Gerektiğinde baştaki sıfırlarla ile doldurulan tam gün sayısını zaman aralığı içinde.<br /><br /> Daha fazla bilgi: ["Aa"-"dddddddd" özel biçim belirticileri](#ddSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `ddd` --> "006"<br /><br /> `dd\.hh\:mm` --> "06.14:32"|  
|"h", "%s"|Tüm saat sayısını zaman aralığındaki gün bir parçası olarak sayılmaz. Tek basamaklı saat başına sıfır gerekmez.<br /><br /> Daha fazla bilgi: ["H" özel biçim belirticisi](#hSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%h` --> "14"<br /><br /> `hh\:mm` --> "14:32"|  
|"hh"|Tüm saat sayısını zaman aralığındaki gün bir parçası olarak sayılmaz. Tek basamaklı saat başına sıfır vardır.<br /><br /> Daha fazla bilgi: ["Hh" özel biçim belirticisi](#hhSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `hh` --> "14"<br /><br /> `new TimeSpan(6, 8, 32, 17, 685):`<br /><br /> `hh` --> 08|  
|"m", "%m"|Tüm dakika sayısını zaman aralığındaki bir parçası olarak saat veya gün dahil değildir. Tek basamaklı dakika başına sıfır gerekmez.<br /><br /> Daha fazla bilgi: ["M" özel biçim belirticisi](#mSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `%m` --> "8"<br /><br /> `h\:m` --> "14:8"|  
|"mm"|Tüm dakika sayısını zaman aralığındaki bir parçası olarak saat veya gün dahil değildir. Tek basamaklı dakika başına sıfır gerekir.<br /><br /> Daha fazla bilgi: ["Aa" özel biçim belirticisi](#mmSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `mm` --> "08"<br /><br /> `new TimeSpan(6, 8, 5, 17, 685):`<br /><br /> `d\.hh\:mm\:ss` --> 6.08:05:17|  
|"s", "%s"|Saat, gün, bir parçası olarak dahil edilmez zaman aralığında saniye veya dakikada bir tam sayısı. Tek basamaklı saniye başına sıfır gerekmez.<br /><br /> Daha fazla bilgi: ["S" özel biçim belirticisi](#sSpecifier).|`TimeSpan.FromSeconds(12.965)`:<br /><br /> `%s` --> 12<br /><br /> `s\.fff` --> 12.965|  
|"ss"|Saat, gün, bir parçası olarak dahil edilmez zaman aralığında saniye veya dakikada bir tam sayısı.  Tek basamaklı saniye başına sıfır vardır.<br /><br /> Daha fazla bilgi: ["Ss" özel biçim belirticisi](#ssSpecifier).|`TimeSpan.FromSeconds(6.965)`:<br /><br /> `ss` --> 06<br /><br /> `ss\.fff` --> 06.965|  
|"f", "%f"|İkinci bir onda bir zaman aralığı içinde.<br /><br /> Daha fazla bilgi: ["F" özel biçim belirticisi](#fSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `f` --> 8<br /><br /> `ss\.f` --> 06.8|  
|"ff"|İkinci bir saniyenin yüzde cinsinden bir zaman aralığı.<br /><br /> Daha fazla bilgi:["Ff" özel biçim belirticisi](#ffSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `ff` --> 89<br /><br /> `ss\.ff` --> 06.89|  
|"fff"|Milisaniye cinsinden bir zaman aralığı.<br /><br /> Daha fazla bilgi: ["Fff" özel biçim belirticisi](#f3Specifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `fff` --> 895<br /><br /> `ss\.fff` --> 06.895|  
|"ffff"|On-duyarlığıyla saniyede bir zaman aralığı içinde.<br /><br /> Daha fazla bilgi: ["Ffff" özel biçim belirticisi](#f4Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffff` --> 8954<br /><br /> `ss\.ffff` --> 06.8954|  
|"fffff"|Yüz-duyarlığıyla saniyede bir zaman aralığı içinde.<br /><br /> Daha fazla bilgi: ["Fffff" özel biçim belirticisi](#f5Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffff` --> 89543<br /><br /> `ss\.fffff` --> 06.89543|  
|"ffffff"|İkinci bir milyonda bir zaman aralığı içinde.<br /><br /> Daha fazla bilgi: ["Ffffff" özel biçim belirticisi](#f6Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffffff` --> 895432<br /><br /> `ss\.ffffff` --> 06.895432|  
|"fffffff"|On-milyonda bir zaman aralığı içinde bir ikinci (veya kesirli çizgilerine).<br /><br /> Daha fazla bilgi: ["Fffffff" özel biçim belirticisi](#f7Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffffff` --> 8954321<br /><br /> `ss\.fffffff` --> 06.8954321|  
|"F", "%F"|İkinci bir onda bir zaman aralığı içinde. Basamak sıfırsa hiçbir şey görüntülenmez.<br /><br /> Daha fazla bilgi: ["F" özel biçim belirticisi](#F_Specifier).|`TimeSpan.Parse("00:00:06.32")`:<br /><br /> `%F`: 3<br /><br /> `TimeSpan.Parse("0:0:3.091")`:<br /><br /> `ss\.F`: 03.|  
|"FF"|İkinci bir saniyenin yüzde cinsinden bir zaman aralığı. Her kesirli sıfır veya iki sondaki sıfır basamak dahil edilmez.<br /><br /> Daha fazla bilgi: ["FF" özel biçim belirticisi](#FF_Specifier).|`TimeSpan.Parse("00:00:06.329")`:<br /><br /> `FF`: 32<br /><br /> `TimeSpan.Parse("0:0:3.101")`:<br /><br /> `ss\.FF`: 03.1|  
|"FFF"|Milisaniye cinsinden bir zaman aralığı. Kesirli sıfırları dahil edilmez.<br /><br /> Daha fazla bilgi:|`TimeSpan.Parse("00:00:06.3291")`:<br /><br /> `FFF`: 329<br /><br /> `TimeSpan.Parse("0:0:3.1009")`:<br /><br /> `ss\.FFF`: 03.1|  
|"FFFF"|On-duyarlığıyla saniyede bir zaman aralığı içinde. Kesirli sıfırları dahil edilmez.<br /><br /> Daha fazla bilgi: ["FFFF" özel biçim belirticisi](#F4_Specifier).|`TimeSpan.Parse("00:00:06.32917")`:<br /><br /> `FFFFF`: 3291<br /><br /> `TimeSpan.Parse("0:0:3.10009")`:<br /><br /> `ss\.FFFF`: 03.1|  
|"FFFFF"|Yüz-duyarlığıyla saniyede bir zaman aralığı içinde. Kesirli sıfırları dahil edilmez.<br /><br /> Daha fazla bilgi: ["FFFFF" özel biçim belirticisi](#F5_Specifier).|`TimeSpan.Parse("00:00:06.329179")`:<br /><br /> `FFFFF`: 32917<br /><br /> `TimeSpan.Parse("0:0:3.100009")`:<br /><br /> `ss\.FFFFF`: 03.1|  
|"FFFFFF"|İkinci bir milyonda bir zaman aralığı içinde. Kesirli sıfırları görüntülenmez.<br /><br /> Daha fazla bilgi: ["FFFFFF" özel biçim belirticisi](#F6_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 329179<br /><br /> `TimeSpan.Parse("0:0:3.1000009")`:<br /><br /> `ss\.FFFFFF`: 03.1|  
|"FFFFFFF"|On-milyonlarca ikinci bir zaman aralığı içinde. Kesirli sıfırları veya yedi sıfırları görüntülenmez.<br /><br /> Daha fazla bilgi: ["FFFFFFF" özel biçim belirticisi](#F7_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 3291791<br /><br /> `TimeSpan.Parse("0:0:3.1900000")`:<br /><br /> `ss\.FFFFFF`: 03.19|  
|*' dize*'|Değişmez dize sınırlayıcısı.<br /><br /> Daha fazla bilgi: [diğer karakterleri](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh':'mm':'ss` --> "14:32:17"|  
|\|"\" çıkış karakteri.<br /><br /> Daha fazla bilgi:[diğer karakterleri](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|  
|Başka bir karakter|Atlanmayan herhangi bir karakter özel biçim tanımlayıcısı yorumlanır.<br /><br /> Daha fazla bilgi: [diğer karakterleri](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|  
  
<a name="dSpecifier"></a>   
## <a name="the-d-custom-format-specifier"></a>"d" Özel Biçim Belirleyicisi  
 "D" özel biçim tanımlayıcısı değeri çıkarır <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> zaman aralığında tam gün sayısını temsil eden özellik. Tam gün sayısını çıkartır bir <xref:System.TimeSpan> değeri birden fazla basamaklı olsa bile, değer. Varsa değerini <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> özelliği sıfır, belirleyici "0" çıkarır.  
  
 "D" özel biçim belirticisi tek başına kullanılırsa, böylece bu standart biçim dizesi olarak yanlış yorumlayan değil "%d" belirtin. Aşağıdaki örnek, bir gösterim sağlar.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#3)]  
  
 Aşağıdaki örnekte, "d" özel biçim belirticisi kullanımını göstermektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#4)]  
  
 [Tablo dön](#table)  
  
<a name="ddSpecifier"></a>   
## <a name="the-dd-dddddddd-custom-format-specifiers"></a>"Aa"-"dddddddd" özel biçim belirticileri  
 "Aa", "ggg", "dddd", "GGGGG", "GGGGGG", "ddddddd" ve "dddddddd" özel biçim belirticileri değerini çıktı <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> zaman aralığında tam gün sayısını temsil eden özellik.  
  
 Gerektiğinde baştaki sıfırlarla ile doldurulan ve biçim belirteci "d" karakter sayısı tarafından belirtilen basamak sayısı alt sınırını çıkış dizesi içerir. Gün sayısını rakamları biçim belirteci "d" karakter sayısını aşarsa, tam gün Sonuç dizesini çıktısında sayısıdır.  
  
 Aşağıdaki örnek, iki dize gösterimini görüntülemek için bu biçim belirticileri kullanır <xref:System.TimeSpan> değerleri. İlk zaman aralığını gün bileşeninin sıfır değeri; İkinci gün bileşeninin 365 değerdir.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#5)]  
  
 [Tablo dön](#table)  
  
<a name="hSpecifier"></a>   
## <a name="the-h-custom-format-specifier"></a>"h" Özel Biçim Belirleyicisi  
 "Y" özel biçim tanımlayıcısı değeri çıkarır <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> gün bileşenini bir parçası olarak sayılmaz zaman aralığındaki tüm saat sayısını temsil eden özellik. Bir tek basamaklı string değeri döndürür değerini <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> 0-9 arası bir özelliktir ve ise iki rakamlı dize değeri döndürür değerini <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> 23 10 özelliği aralıkları.  
  
 "Y" özel biçim belirticisi tek başına kullanılırsa, böylece bu standart biçim dizesi olarak yanlış yorumlayan değil "%s" belirtin. Aşağıdaki örnek, bir gösterim sağlar.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
 [!code-vb[Conceptual.TimeSpan.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]  
  
 Normalde, bir ayrıştırma işlemi, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Bunun yerine sayısal dize saat sayısını yorumlayabilir için "%s" özel biçim belirteci kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#8)]
 [!code-vb[Conceptual.TimeSpan.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#8)]  
  
 Aşağıdaki örnekte "h" özel biçim belirticisi kullanımını göstermektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#7)]
 [!code-vb[Conceptual.TimeSpan.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#7)]  
  
 [Tablo dön](#table)  
  
<a name="hhSpecifier"></a>   
## <a name="the-hh-custom-format-specifier"></a>"hh" Özel Biçim Belirleyicisi  
 "Hh" özel biçim tanımlayıcısı değeri çıkarır <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> gün bileşenini bir parçası olarak sayılmaz zaman aralığındaki tüm saat sayısını temsil eden özellik. 0 ile 9 arasında değerleri için baştaki sıfır çıkış dizesi içerir.  
  
 Normalde, bir ayrıştırma işlemi, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Bunun yerine sayısal dize saat sayısını yorumlayabilir için "hh" özel biçim belirticisi kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#9)]
 [!code-vb[Conceptual.TimeSpan.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#9)]  
  
 Aşağıdaki örnekte "hh" özel biçim belirticisi kullanımını göstermektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#10)]
 [!code-vb[Conceptual.TimeSpan.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#10)]  
  
 [Tablo dön](#table)  
  
<a name="mSpecifier"></a>   
## <a name="the-m-custom-format-specifier"></a>"m" Özel Biçim Belirleyicisi  
 "M" özel biçim tanımlayıcısı değeri çıkarır <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> gün bileşenini bir parçası olarak sayılmaz zaman aralığındaki tüm dakika sayısını temsil eden özellik. Varsa bir basamaklı bir string değeri döndürür değerini <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> 0-9 arası bir özelliktir ve ise iki rakamlı dize değeri döndürür değerini <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> 59 10 özelliği aralıkları.  
  
 "M" özel biçim belirticisi tek başına kullanılırsa, böylece bu standart biçim dizesi olarak yanlış yorumlayan değil "%m" belirtin. Aşağıdaki örnek, bir gösterim sağlar.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
 [!code-vb[Conceptual.TimeSpan.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]  
  
 Normalde, bir ayrıştırma işlemi, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Bunun yerine sayısal dize dakika sayısını yorumlayabilir için "%m" özel biçim belirteci kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#11)]
 [!code-vb[Conceptual.TimeSpan.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#11)]  
  
 Aşağıdaki örnekte, "m" özel biçim belirticisi kullanımını göstermektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#12)]
 [!code-vb[Conceptual.TimeSpan.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#12)]  
  
 [Tablo dön](#table)  
  
<a name="mmSpecifier"></a>   
## <a name="the-mm-custom-format-specifier"></a>"mm" Özel Biçim Belirleyicisi  
 "Aa" özel biçim tanımlayıcısı değeri çıkarır <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> özelliği, saat veya gün bileşeninin bir parçası olarak dahil değil zaman aralığındaki tüm dakika sayısını temsil eder. 0 ile 9 arasında değerleri için baştaki sıfır çıkış dizesi içerir.  
  
 Normalde, bir ayrıştırma işlemi, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Bunun yerine sayısal dize dakika sayısını yorumlayabilir için "aa" özel biçim belirteci kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#13)]
 [!code-vb[Conceptual.TimeSpan.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#13)]  
  
 Aşağıdaki örnekte "aa" özel biçim belirticisi kullanımını göstermektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#14)]
 [!code-vb[Conceptual.TimeSpan.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#14)]  
  
 [Tablo dön](#table)  
  
<a name="sSpecifier"></a>   
## <a name="the-s-custom-format-specifier"></a>"s" Özel Biçim Belirleyicisi  
 Değeri, "s" özel biçim belirteci çıkarır <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> zaman aralığındaki bir parçası olarak, saat, gün veya dakika bileşenini dahil değil tüm saniye sayısını temsil eden özellik. Varsa bir basamaklı bir string değeri döndürür değerini <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> 0-9 arası bir özelliktir ve ise iki rakamlı dize değeri döndürür değerini <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> 59 10 özelliği aralıkları.  
  
 "S" özel biçim belirticisi tek başına kullanılırsa, böylece bu standart biçim dizesi olarak yanlış yorumlayan değil "%s" belirtin. Aşağıdaki örnek, bir gösterim sağlar.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#15)]
 [!code-vb[Conceptual.TimeSpan.Custom#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#15)]  
  
 Normalde, bir ayrıştırma işlemi, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Bunun yerine sayısal dize saniye sayısını yorumlayabilir için "%s" özel biçim belirteci kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#17)]
 [!code-vb[Conceptual.TimeSpan.Custom#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#17)]  
  
 Aşağıdaki örnekte, "s" özel biçim belirticisi kullanımını göstermektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#16)]
 [!code-vb[Conceptual.TimeSpan.Custom#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#16)]  
  
 [Tablo dön](#table)  
  
<a name="ssSpecifier"></a>   
## <a name="the-ss-custom-format-specifier"></a>"ss" Özel Biçim Belirleyicisi  
 "Ss" özel biçim tanımlayıcısı değeri çıkarır <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> zaman aralığındaki bir parçası olarak, saat, gün veya dakika bileşenini dahil değil tüm saniye sayısını temsil eden özellik. 0 ile 9 arasında değerleri için baştaki sıfır çıkış dizesi içerir.  
  
 Normalde, bir ayrıştırma işlemi, yalnızca tek bir sayı içeren bir giriş dizesi gün sayısı olarak yorumlanır. Bunun yerine sayısal dize saniye sayısını yorumlayabilir için "ss" özel biçim belirteci kullanabilirsiniz. Aşağıdaki örnek, bir gösterim sağlar.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#18)]
 [!code-vb[Conceptual.TimeSpan.Custom#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#18)]  
  
 Aşağıdaki örnekte "ss" özel biçim belirticisi kullanımını göstermektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#19)]
 [!code-vb[Conceptual.TimeSpan.Custom#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#19)]  
  
 [Tablo dön](#table)  
  
<a name="fSpecifier"></a>   
## <a name="thef-custom-format-specifier"></a>"F" özel biçim belirticisi  
 "F" özel biçim belirticisi saniyenin onda bir zaman aralığı içinde çıkarır. Biçimlendirme işleminde, kalan tüm kesir basamakları kesilir. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, giriş dizesi tam olarak bir kesirli rakam içermelidir.  
  
 "F" özel biçim belirticisi tek başına kullanılırsa, böylece bu standart biçim dizesi olarak yanlış yorumlayan değil "%f" belirtin.  
  
 Aşağıdaki örnek, bir saniyede onda görüntülemek için "f" özel biçim belirticisi kullanır. bir <xref:System.TimeSpan> değeri. "f" ilk yalnızca biçimi tanımlayıcısı olarak kullanılan ve özel bir biçim dizesi "s" belirticisinin ile birleştirilmiş.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Tablo dön](#table)  
  
<a name="ffSpecifier"></a>   
## <a name="the-ff-custom-format-specifier"></a>"ff" Özel Biçim Belirleyicisi  
 İkinci bir yüzde bir zaman aralığı içinde "ff" özel biçim belirteci çıkarır. Biçimlendirme işleminde, kalan tüm kesir basamakları kesilir. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, giriş dizesi tam olarak iki kesirli rakam içermelidir.  
  
 Aşağıdaki örnek, bir saniyede yüzdesine görüntülemek için "ff" özel biçim belirticisi kullanır. bir <xref:System.TimeSpan> değeri. "ff" ilk yalnızca biçimi tanımlayıcısı olarak kullanılan ve özel bir biçim dizesi "s" belirticisinin ile birleştirilmiş.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Tablo dön](#table)  
  
<a name="f3Specifier"></a>   
## <a name="the-fff-custom-format-specifier"></a>"fff" Özel Biçim Belirleyicisi  
 (Karakterlerle üç "f") "fff" özel biçim belirleyici bir zaman aralığı içinde milisaniye çıkarır. Biçimlendirme işleminde, kalan tüm kesir basamakları kesilir. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, giriş dizesi tam olarak üç kesirli rakam içermelidir.  
  
 Aşağıdaki örnek, milisaniye cinsinden görüntülemek için "fff" özel biçim belirticisi kullanır. bir <xref:System.TimeSpan> değeri. "fff" ilk yalnızca biçimi tanımlayıcısı olarak kullanılan ve özel bir biçim dizesi "s" belirticisinin ile birleştirilmiş.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Tablo dön](#table)  
  
<a name="f4Specifier"></a>   
## <a name="the-ffff-custom-format-specifier"></a>"ffff" Özel Biçim Belirleyicisi  
 On-duyarlığıyla saniyede bir zaman aralığı içinde (karakterlerle dört "f") "ffff" özel biçim belirteci çıkarır. Biçimlendirme işleminde, kalan tüm kesir basamakları kesilir. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, giriş dizesi tam olarak dört kesirli rakam içermelidir.  
  
 Aşağıdaki örnek, bir saniye içinde on duyarlığıyla görüntülemek için "ffff" özel biçim belirticisi kullanır. bir <xref:System.TimeSpan> değeri. "ffff" ilk yalnızca biçimi tanımlayıcısı olarak kullanılan ve özel bir biçim dizesi "s" belirticisinin ile birleştirilmiş.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Tablo dön](#table)  
  
<a name="f5Specifier"></a>   
## <a name="the-fffff-custom-format-specifier"></a>"fffff" Özel Biçim Belirleyicisi  
 Yüz-duyarlığıyla saniyede bir zaman aralığı içinde (beş "f" karakter ile) "fffff" özel biçim belirteci çıkarır. Biçimlendirme işleminde, kalan tüm kesir basamakları kesilir. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, giriş dizesi tam olarak beş kesirli rakam içermelidir.  
  
 Aşağıdaki örnek, bir saniyede yüz-duyarlığıyla görüntülemek için "fffff" özel biçim belirticisi kullanır. bir <xref:System.TimeSpan> değeri. "fffff" ilk yalnızca biçimi tanımlayıcısı olarak kullanılan ve özel bir biçim dizesi "s" belirticisinin ile birleştirilmiş.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Tablo dön](#table)  
  
<a name="f6Specifier"></a>   
## <a name="the-ffffff-custom-format-specifier"></a>"ffffff" Özel Biçim Belirleyicisi  
 İkinci bir milyonda bir zaman aralığı içinde (karakterlerle altı "f") "ffffff" özel biçim belirteci çıkarır. Biçimlendirme işleminde, kalan tüm kesir basamakları kesilir. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, giriş dizesi tam olarak altı kesirli rakam içermelidir.  
  
 Aşağıdaki örnek, bir saniyede milyonda görüntülemek için "ffffff" özel biçim belirticisi kullanır. bir <xref:System.TimeSpan> değeri. Bunu yalnızca biçim belirteci olarak ilk kullanıldığı ve özel bir biçim dizesi "s" belirticisinin ile birleştirilmiş.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Tablo dön](#table)  
  
<a name="f7Specifier"></a>   
## <a name="the-fffffff-custom-format-specifier"></a>"fffffff" Özel Biçim Belirleyicisi  
 (Karakterlerle yedi "f") "fffffff" özel biçim belirleyici bir zaman aralığı içinde bir ikinci (veya kesirli sayısı) on milyonda çıkarır. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, giriş dizesi tam olarak yedi kesirli rakam içermelidir.  
  
 Aşağıdaki örnek, çizgilerine içinde kesirli sayısını görüntülemek için "fffffff" özel biçim belirticisi kullanır. bir <xref:System.TimeSpan> değeri. Bunu yalnızca biçim belirteci olarak ilk kullanıldığı ve özel bir biçim dizesi "s" belirticisinin ile birleştirilmiş.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Tablo dön](#table)  
  
<a name="F_Specifier"></a>   
## <a name="the-f-custom-format-specifier"></a>"F" Özel Biçim Belirleyicisi  
 "F" özel biçim belirticisi saniyenin onda bir zaman aralığı içinde çıkarır. Biçimlendirme işleminde, kalan tüm kesir basamakları kesilir. Zaman aralığı saniyenin onda biri değeri sıfır ise, sonuç dizesinde bulunmaz. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemi, ikinci bir basamak onda varlığını isteğe bağlıdır.  
  
 "F" özel biçim belirticisi tek başına kullanılırsa, böylece bu standart biçim dizesi olarak yanlış yorumlayan değil "%F" belirtin.  
  
 Aşağıdaki örnek, bir saniyede onda görüntülemek için "F" özel biçim belirticisi kullanır. bir <xref:System.TimeSpan> değeri. Ayrıca bu özel biçim belirleyici bir ayrıştırma işlemi kullanır.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#21)]
 [!code-vb[Conceptual.TimeSpan.Custom#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#21)]  
  
 [Tablo dön](#table)  
  
<a name="FF_Specifier"></a>   
## <a name="the-ff-custom-format-specifier"></a>"FF" Özel Biçim Belirleyicisi  
 İkinci bir yüzde bir zaman aralığı içinde "FF" özel biçim belirteci çıkarır. Biçimlendirme işleminde, kalan tüm kesir basamakları kesilir. Sondaki kesirli sıfırları varsa, bunlar sonuç dizesinde dahil edilmez. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> onda varlığını ve ikinci basamaklı yüzdesi yöntemidir isteğe bağlıdır.  
  
 Aşağıdaki örnek, bir saniyede yüzdesine görüntülemek için "FF" özel biçim belirticisi kullanır. bir <xref:System.TimeSpan> değeri. Ayrıca bu özel biçim belirleyici bir ayrıştırma işlemi kullanır.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#22)]
 [!code-vb[Conceptual.TimeSpan.Custom#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#22)]  
  
 [Tablo dön](#table)  
  
<a name="F3_Specifier"></a>   
## <a name="the-fff-custom-format-specifier"></a>"FFF" Özel Biçim Belirleyicisi  
 (Karakterlerle üç "F") "FFF" özel biçim belirleyici bir zaman aralığı içinde milisaniye çıkarır. Biçimlendirme işleminde, kalan tüm kesir basamakları kesilir. Sondaki kesirli sıfırları varsa, bunlar sonuç dizesinde dahil edilmez. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> onda, yüzde ve ikinci bir basamak duyarlığıyla varlığını yöntemidir isteğe bağlıdır.  
  
 Aşağıdaki örnek, bir saniyede duyarlığıyla görüntülemek için "FFF" özel biçim belirticisi kullanır. bir <xref:System.TimeSpan> değeri. Ayrıca bu özel biçim belirleyici bir ayrıştırma işlemi kullanır.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#23)]
 [!code-vb[Conceptual.TimeSpan.Custom#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#23)]  
  
 [Tablo dön](#table)  
  
<a name="F4_Specifier"></a>   
## <a name="the-ffff-custom-format-specifier"></a>"FFFF" Özel Biçim Belirleyicisi  
 On-duyarlığıyla saniyede bir zaman aralığı içinde (karakterlerle dört "F") "FFFF" özel biçim belirteci çıkarır. Biçimlendirme işleminde, kalan tüm kesir basamakları kesilir. Sondaki kesirli sıfırları varsa, bunlar sonuç dizesinde dahil edilmez. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> onda, yüzde, duyarlığıyla ve ikinci bir rakam, on duyarlığıyla varlığını yöntemidir isteğe bağlıdır.  
  
 Aşağıdaki örnek, bir saniye içinde on duyarlığıyla görüntülemek için "FFFF" özel biçim belirticisi kullanır. bir <xref:System.TimeSpan> değeri. Ayrıca "FFFF" özel biçim belirleyici bir ayrıştırma işlemi kullanır.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#24)]
 [!code-vb[Conceptual.TimeSpan.Custom#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#24)]  
  
 [Tablo dön](#table)  
  
<a name="F5_Specifier"></a>   
## <a name="the-fffff-custom-format-specifier"></a>"FFFFF" Özel Biçim Belirleyicisi  
 Yüz-duyarlığıyla saniyede bir zaman aralığı içinde (beş "F" karakter ile) "FFFFF" özel biçim belirteci çıkarır. Biçimlendirme işleminde, kalan tüm kesir basamakları kesilir. Sondaki kesirli sıfırları varsa, bunlar sonuç dizesinde dahil edilmez. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> onda, yüzde, duyarlığıyla, on-duyarlığıyla ve ikinci bir rakam, yüz duyarlığıyla varlığını yöntemidir isteğe bağlıdır.  
  
 Aşağıdaki örnek, bir saniyede yüz-duyarlığıyla görüntülemek için "FFFFF" özel biçim belirticisi kullanır. bir <xref:System.TimeSpan> değeri. Ayrıca "FFFFF" özel biçim belirleyici bir ayrıştırma işlemi kullanır.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#25)]
 [!code-vb[Conceptual.TimeSpan.Custom#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#25)]  
  
 [Tablo dön](#table)  
  
<a name="F6_Specifier"></a>   
## <a name="the-ffffff-custom-format-specifier"></a>"FFFFFF" Özel Biçim Belirleyicisi  
 İkinci bir milyonda bir zaman aralığı içinde (karakterlerle altı "F") "FFFFFF" özel biçim belirteci çıkarır. Biçimlendirme işleminde, kalan tüm kesir basamakları kesilir. Sondaki kesirli sıfırları varsa, bunlar sonuç dizesinde dahil edilmez. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> onda, yüzde, duyarlığıyla, on duyarlığıyla, yüz-duyarlığıyla ve ikinci bir basamak milyonda varlığını yöntemidir isteğe bağlıdır.  
  
 Aşağıdaki örnek, bir saniyede milyonda görüntülemek için "FFFFFF" özel biçim belirticisi kullanır. bir <xref:System.TimeSpan> değeri. Ayrıca bu özel biçim belirleyici bir ayrıştırma işlemi kullanır.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#26](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#26)]
 [!code-vb[Conceptual.TimeSpan.Custom#26](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#26)]  
  
 [Tablo dön](#table)  
  
<a name="F7_Specifier"></a>   
## <a name="the-fffffff-custom-format-specifier"></a>"FFFFFFF" Özel Biçim Belirleyicisi  
 (Karakterlerle yedi "F") "FFFFFFF" özel biçim belirleyici bir zaman aralığı içinde bir ikinci (veya kesirli sayısı) on milyonda çıkarır. Sondaki kesirli sıfırları varsa, bunlar sonuç dizesinde dahil edilmez. Çağıran bir ayrıştırma işleminde <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> veya <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntem, giriş dizisinde yedi kesir basamakları varlığını isteğe bağlı olur.  
  
 Aşağıdaki örnek, bir saniye içinde kesirli bölümlerini görüntülemek için "FFFFFFF" özel biçim belirticisi kullanır. bir <xref:System.TimeSpan> değeri. Ayrıca bu özel biçim belirleyici bir ayrıştırma işlemi kullanır.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#27](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#27)]
 [!code-vb[Conceptual.TimeSpan.Custom#27](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#27)]  
  
 [Tablo dön](#table)  
  
<a name="Other"></a>   
## <a name="other-characters"></a>Diğer karakterler  
 Diğer atlanmayan karakteri boşluk karakterini içeren bir biçim dizesindeki özel biçim tanımlayıcısı yorumlanır. Çoğu durumda, diğer varlığını atlanmayan karakter sonuçlarında bir <xref:System.FormatException>.  
  
 Bir biçim dizesine harf karakter eklemek için iki yol vardır:  
  
-   (Değişmez değer dize sınırlayıcı) tek tırnak işaretleri içine alın.  
  
-   Ters bölü işareti koyun ("\\"), bir kaçış karakteri olarak yorumlanır. C# ' ta biçim dizesi ya da olmalıdır, yani @-quoted, veya ek bir ters eğik çizgi ile karakterinden gelmelidir.  
  
     Bazı durumlarda, bir biçim dizesi kaçış karakterli bir hazır değer eklemek için koşullu mantık kullanmak zorunda kalabilirsiniz. Aşağıdaki örnek koşullu mantık negatif zaman aralıkları için bir oturum simge eklemek için kullanır.  
  
     [!code-csharp[Conceptual.TimeSpan.Custom#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/negativevalues1.cs#29)]
     [!code-vb[Conceptual.TimeSpan.Custom#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/negativevalues1.vb#29)]  
  
 .NET ayırıcıları için dilbilgisi zaman aralıkları tanımlamıyor. Bu gün ve saat, saat ve dakika, dakika ve saniye ve saniye ve ikinci bir kesirlerini arasındaki ayırıcıları tüm biçim dizesindeki karakter değişmez değerleri olarak Muamele görmelidir olduğunu anlamına gelir.  
  
 Aşağıdaki örnek, çıktı dizesindeki "dakika" sözcüğünü içeren özel bir biçim dizesi tanımlamak için kaçış karakteri hem tek tırnak işareti kullanır.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/literal1.cs#28)]
 [!code-vb[Conceptual.TimeSpan.Custom#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/literal1.vb#28)]  
  
 [Tablo dön](#table)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)  
 [Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)
