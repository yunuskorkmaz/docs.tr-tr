---
title: "Standart Sayısal Biçim Dizeleri"
ms.date: 09/10/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- standard format strings, numeric
- format strings
- numbers [.NET Framework], formatting
- format specifiers, numeric
- standard numeric format strings
- formatting numbers [.NET Framework]
- format specifiers, standard numeric format strings
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 81547bbcdbae5b4cc8dc1f20e829dfb5ede08963
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="standard-numeric-format-strings"></a>Standart Sayısal Biçim Dizeleri
Standart sayısal biçim dizeleri, genel sayısal türleri biçimlendirmek için kullanılır. Standart sayısal biçim dizesi biçimi alır `Axx`, burada:  
  
-   `A`tek bir alfasayısal karakter adlı *belirticisi biçimlendirmek*. Beyaz boşluk da dahil olmak üzere birden fazla alfabetik karakter içeren herhangi bir sayısal biçim dizesi, özel bir sayısal biçim dizesi olarak yorumlanır. Daha fazla bilgi için bkz: [özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
-   `xx`İsteğe bağlı bir tamsayı olarak adlandırılan *duyarlık Belirleyicisi*. Precision belirleyici 0'dan 99'a kadar uzanır ve sonuç basamak sayısını etkiler. Not duyarlık Belirleyicisi birkaç dize gösterimini basamak sayısını denetler. Sayının kendisini yuvarlamaz. Bir yuvarlama işlemi gerçekleştirmek için <xref:System.Math.Ceiling%2A?displayProperty=nameWithType>, <xref:System.Math.Floor%2A?displayProperty=nameWithType>, veya <xref:System.Math.Round%2A?displayProperty=nameWithType> yöntemi.  
  
     Zaman *duyarlık Belirleyicisi* sayısını kontrol sonuç dizesinde kesir basamakları sıfırdan uzağa doğru yuvarlanan sayıları sonuç dizeleri yansıtacak (diğer bir deyişle, kullanarak <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType>).  
  
    > [!NOTE]
    >  Duyarlık Belirleyicisi, sonuç dizesinde basamak sayısını belirler. Başında veya sonunda boşluk içeren bir sonuç dizesini paneli için kullanmak [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md) özellik ve tanımlayın bir *hizalama bileşen* biçimi öğesi.  
  
Standart sayısal biçim dizeleri tarafından desteklenir:

- Bazı aşırı `ToString` tüm sayısal türler yöntemi. Örneğin, bir sayısal biçim dizesi belirtebilirsiniz <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> ve <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemleri. 
 
- .NET [bileşik biçimlendirme özelliği](../../../docs/standard/base-types/composite-formatting.md), kullanılan bazı tarafından `Write` ve `WriteLine` yöntemlerinin <xref:System.Console> ve <xref:System.IO.StreamWriter> sınıfları <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi ve <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> yöntemi. Bileşik biçimlendirme özelliğini tek bir dizede, alan genişliği belirtmek ve alanına sayı hizalamak için birden çok veri öğeleri dize gösterimini eklemenizi sağlar. Daha fazla bilgi için bkz: [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).  

- [Ara değerli dizeler](../../csharp/language-reference/keywords/interpolated-strings.md) , C# ve Visual Basic sağlayan bileşik biçim dizeleri karşılaştırıldığında basitleştirilmiş bir sözdizimi.
 
> [!TIP]
>  İndirebilirsiniz [biçimlendirme yardımcı programı](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), biçimi uygulamanıza olanak sağlayan bir uygulama dizeleri sayısal veya tarih ve saat değerleri ve sonuç dizesini görüntüler.  
  
<a name="table"></a>Aşağıdaki tabloda standart sayısal biçim belirticileri açıklar ve her biçim belirticisi tarafından üretilen örnek çıktı görüntüler. Bkz: [notları](#NotesStandardFormatting) bölüm standart sayısal biçim dizeleri kullanma hakkında ek bilgi için ve [örnek](#example) kullanımlarını kapsamlı bir çizimi için bölüm.  
  
|Biçim belirteci|Ad|Açıklama|Örnekler|  
|----------------------|----------|-----------------|--------------|  
|"C" ya da "c"|Para Birimi|Sonuç: Bir para birimi değeri.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık Belirleyicisi: tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Daha fazla bilgi: [para birimi ("C") biçim belirticisi](#CFormatString).|123.456 ("C" en-US) $123.46 -><br /><br /> 123.456 ("C", fr-FR) 123,46 -> €<br /><br /> 123.456 ("C", ja-JP) ¥ 123 -><br /><br /> -123.456 ("C3", en-US) ($123.456) -><br /><br /> -123.456 ("C3", fr-FR)-123,456 € -><br /><br /> -123.456 ("C3", ja-JP) ->-¥ 123.456|  
|"D" veya "d"|Ondalık|Sonuç: İsteğe bağlı eksi işaretli tamsayı basamaklar.<br /><br /> Desteklenen: sadece integral türleri.<br /><br /> Duyarlık belirtici: Minimum basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: En az gereken basamak sayısı.<br /><br /> Daha fazla bilgi: [Decimal("D") biçim belirticisi](#DFormatString).|1234 ("D") 1234 -><br /><br /> -1234 ("D6")-001234 ->|  
|"E" ya da "e"|Üstsel (bilimsel)|Sonuç: Üstel simgeleme.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: 6.<br /><br /> Daha fazla bilgi: [üstel ("E") biçim belirticisi](#EFormatString).|1052.0329112756 ("E" en-US) 1.052033E + 003 -><br /><br /> 1052.0329112756 ("e", fr-FR), 1, 052033e -> + 003<br /><br /> -1052.0329112756 ("e2", en-US) -> - 1.05e + 003<br /><br /> -1052.0329112756 ("E2", fr_FR) -> -1, 05E + 003|  
|"F" ya da "f"|Sabit nokta|Sonuç: İsteğe bağlı eksi işaretli tamsayı ve ondalık basamaklar.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık Belirleyicisi: tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Daha fazla bilgi: [sabit noktalı ("F") biçim belirticisi](#FFormatString).|1234.567 ("F" en-US) 1234.57 -><br /><br /> 1234.567 ("F", de-DE) 1234,57 -><br /><br /> 1234 ("F1" en-US) 1234.0 -><br /><br /> 1234 ("F1", de-DE) 1234,0 -><br /><br /> -1234.56 ("F4", en-US)-1234.5600 -><br /><br /> -1234.56 ("F4", de-DE) -> - 1234,5600|  
|"G" ya da "g"|Genel|Sonuç: Daha fazla sabit noktalı ya da bilimsel gösterim sıkıştırın.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Anlamlı basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: Sayısal türe bağlıdır.<br /><br /> Daha fazla bilgi: [genel ("G") biçim belirticisi](#GFormatString).|-123.456 ("G", en-US)-123.456 -><br /><br /> -123.456 ("G", sv-SE)-123,456 -><br /><br /> 123.4546 ("G4" en-US) 123.5 -><br /><br /> 123.4546 ("G4" sv-SE) 123,5 -><br /><br /> -1.234567890e-25 ("G", en-US) -> - 1.23456789E-25<br /><br /> -1.234567890e-25 ("G", sv-SE) -1, 23456789E 25->|  
|"N" ya da "n"|Sayı|Sonuç: Integral ve ondalık basamaklar, grup ayırıcılar ve isteğe bağlı eksi işaretli ondalık ayırıcı.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: İstenen ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık Belirleyicisi: tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Daha fazla bilgi: [sayısal ("N") biçim belirticisi](#NFormatString).|1234.567 ("N" en-US) 1,234.57 -><br /><br /> 1234.567 ("N", ru-RU) 1 234,57 -><br /><br /> 1234 ("N1" en-US) 1,234.0 -><br /><br /> 1234 ("N1" ru-RU) 1 234,0 -><br /><br /> -1234.56 ("N3", en-US)-1,234.560 -><br /><br /> -1 234,560-1234.56 ("N3", ru-RU) ->|  
|"P" ya da "p"|Yüzde|Sonuç: Sayı 100 ile çarpılır ve yüzde simgesi ile görüntülenir.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: İstenen ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık Belirleyicisi: tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Daha fazla bilgi: [yüzde ("P") biçim belirticisi](#PFormatString).|1 ("P" en-US) %100,00 -><br /><br /> 1 ("P", fr-FR) 100,00 -> %<br /><br /> -0.39678 ("P1", en-US)-39.7 -> %<br /><br /> -0.39678 ("P1", fr-FR) -> - %39,7|  
|"R" ya da "r"|Gidiş|Sonuç: Aynı numaraya gidiş dönüş yapabilen bir dize.<br /><br /> Tarafından desteklenen: <xref:System.Single>, <xref:System.Double>, ve <xref:System.Numerics.BigInteger>.<br /><br /> Not: önerilen <xref:System.Numerics.BigInteger> yalnızca yazın. İçin <xref:System.Double> türlerini kullanan "G17" için; <xref:System.Single> türleri, "G9" kullanın. </br> Duyarlık belirtici: Yoksayıldı.<br /><br /> Daha fazla bilgi: [gidiş ("R") biçim belirticisi](#RFormatString).|123456789.12345678 ("R") 123456789.12345678 -><br /><br /> -1234567890.12345678 ("R")-1234567890.1234567 ->|  
|"X" ya da "x"|Onaltılık|Sonuç: Bir onaltılık dize.<br /><br /> Desteklenen: sadece integral türleri.<br /><br /> Duyarlık belirtici: Sonuç dizesindeki basamak sayısı.<br /><br /> Daha fazla bilgi: [onaltılık ("X") biçim belirticisi](#XFormatString).|255 ("X") FF -><br /><br /> -1 ("x") ff -><br /><br /> 255 ("x4") 00ff -><br /><br /> -1 ("X4") 00FF ->|  
|Başka bir tek karakter|Bilinmeyen tanımlayıcı|Sonuç: Oluşturur bir <xref:System.FormatException> çalışma zamanında.||  
  
<a name="Using"></a>   
## <a name="using-standard-numeric-format-strings"></a>Standart Sayısal Biçim Dizeleri Kullanma  
 Standart bir sayısal biçimli dize, şu iki yoldan biriyle sayısal bir değerin biçimlendirmesini tanımlamak için kullanılabilir:  
  
-   Bir aşırı yüklemesini geçirilebilir `ToString` sahip yöntemi bir `format` parametresi. Aşağıdaki örnekte bir sayısal değer bir para birimi dize geçerli kültürün (Bu durumda, en-US kültür) olarak biçimlendirir.  
  
     [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
     [!code-csharp[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
     [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]  
  
-   Olarak sağlanabilir `formatString` bağımsız değişkeni tür yöntemleri olarak kullanılan bir biçim öğesinde <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, ve <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>. Daha fazla bilgi için bkz: [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md). Aşağıdaki örnek, bir dizeye bir para birimi değeri eklemek için bir biçim öğesi kullanmaktadır.  
  
     [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
     [!code-csharp[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
     [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]  
  
     İsteğe bağlı olarak, sağlayabilir bir `alignment` sayısal alana ve sağa veya sola hizalı değerini olup genişliğini belirlemek için bağımsız değişken. Aşağıdaki örnek sol-28 karakter alanındaki para birimi değeri, ve onu sağ-14 karakter alanındaki para birimi değeri hizalar.  
  
     [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
     [!code-csharp[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
     [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]  
  
 Aşağıdaki bölümlerde her standart sayısal biçim dizesi hakkında ayrıntılı bilgi sağlanmaktadır.  
  
<a name="CFormatString"></a>   
## <a name="the-currency-c-format-specifier"></a>Para Birimi ("C") Biçim Belirleyicisi  
 "C" (ya da para birimi) biçim belirticisi, bir sayıyı para birimi tutarını gösteren bir dizeye dönüştürür. Duyarlık belirtici, sonuç dizesindeki istenen ondalık basamak sayısını gösterir. Duyarlık Belirleyicisi atlanırsa, varsayılan duyarlık tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> özelliği.  
  
 Biçimlendirilecek değer, belirtilen veya varsayılan ondalık basamak sayısından fazlasına sahipse, sonuç dizesinde kesirli değer yuvarlanır. Belirtilen ondalık basamak sayısının sağındaki değer 5 veya daha büyükse, sonuç dizesindeki son basamak, sıfırdan uzağa yuvarlanır.  
  
 Sonuç dizesini geçerli biçimlendirme bilgilerini tarafından etkilenen <xref:System.Globalization.NumberFormatInfo> nesnesi. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> döndürülen dizesinin biçimlendirmesinde denetleyen özellikler.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|Pozitif değerler için para birimi sembolünün yerleşimini tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|Negatif değerler para birimi simgesi yerleşimini tanımlar ve eksi işareti parantez tarafından temsil edilen belirtir veya <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> özelliği.|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Kullanılan eksi işareti tanımlar <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> parantez kullanılmayan gösterir.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|Para birimi sembolünü tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|Para birimi değerindeki varsayılan ondalık basamak sayısını tanımlar. B değeri hassasiyet belirleyici kullanılarak geçersiz kılınabilir.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|Tamsayı ve ondalık basamakları ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|Tam sayı gruplarını ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|Bir grup içinde görüntülenen tamsayı basamak sayısını tanımlar.|  
  
 Aşağıdaki örnek biçimlerinden bir <xref:System.Double> para birimi biçimi tanımlayıcısı değeri.  
  
 [!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
 [!code-csharp[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
 [!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]  
  
 [Tablo dön](#table)  
  
<a name="DFormatString"></a>   
## <a name="the-decimal-d-format-specifier"></a>Ondalık ("D") Biçim Belirleyicisi  
 "D" (veya ondalık) biçim belirticisi, sayıyı, sayı negatifse eksi işaretiyle önekli bir ondalık basamaklı (0-9) bir dizeye dönüştürür. Bu biçim yalnızca tam sayı türleri için desteklenir.  
  
 Duyarlık belirtici, sonuç dizesindeki istenen minimum basamak sayısını gösterir. Gerekirse, duyarlık belirtici tarafından verilen basamak sayısını üretmek için sayının sol tarafı sıfırlarla doldurulur Bir duyarlık belirtici belirtilmezse varsayılan, başta sıfır bulunmadan tamsayıyı temsil etmek için gerekli minimum değerdir.  
  
 Sonuç dizesini geçerli biçimlendirme bilgilerini tarafından etkilenen <xref:System.Globalization.NumberFormatInfo> nesnesi. Aşağıdaki tabloda gösterildiği gibi tek bir özellik, sonuç dizesinin biçimlendirmesini etkiler.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek biçimlerinden bir <xref:System.Int32> değeri ondalık biçim belirteci ile.  
  
 [!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
 [!code-csharp[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
 [!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]  
  
 [Tablo dön](#table)  
  
<a name="EFormatString"></a>   
## <a name="the-exponential-e-format-specifier"></a>Üstel ("E") Biçim Belirleyicisi  
 Üstel ("E") biçim belirteci bir sayıyı "-d.ddd...E + ggg" veya "-d.ddd...e+ddd" biçiminde bir dizeye dönüştürür; burada her "d" bir basamağı (0-9) gösterir. Sayı negatifse, dize eksi işaretiyle başlar. Ondalık işaretinden önce her zaman tam bir basamak gelir.  
  
 Duyarlık belirtici, ondalık noktasından sonraki istenen basamak sayısını gösterir. Duyarlık belirtici atlanırsa, ondalık işaretinden sonra varsayılan olarak altı basamak kullanılır.  
  
 Biçim belirticisinin durumu üsse "E" veya "e" önekinin getirilip getirilmeyeceğini gösterir. Üs her zaman bir artı veya eksi işareti ile en az üç basamaktan oluşur. Üs bu minimum şartı karşılamak için gerekirse sıfırlarla doldurulur.  
  
 Sonuç dizesini geçerli biçimlendirme bilgilerini tarafından etkilenen <xref:System.Globalization.NumberFormatInfo> nesnesi. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> döndürülen dizesinin biçimlendirmesinde denetleyen özellikler.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının hem katsayı hem de üs için negatif olduğunu belirten dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamağını, katsayıdaki ondalık basamaklardan ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Bir üssün pozitif olduğunu belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek biçimlerinden bir <xref:System.Double> üstel biçimde belirleyici değerle.  
  
 [!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
 [!code-csharp[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
 [!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]  
  
 [Tablo dön](#table)  
  
<a name="FFormatString"></a>   
## <a name="the-fixed-point-f-format-specifier"></a>Sabit Nokta ("F") Biçim Belirleyicisi  
 Sabit noktalı ("F") biçimi belirleyici bir sayı biçiminde bir dizeye dönüştürür. "-bbb.bbb…" Burada her "d" bir basamağı (0-9) belirtir. Sayı negatifse, dize eksi işaretiyle başlar.  
  
 Duyarlık belirtici, istenen ondalık basamak sayısını gösterir. Duyarlık Belirleyicisi atlanırsa, geçerli <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> özelliği sayısal duyarlık sağlar.  
  
 Sonuç dizesini geçerli biçimlendirme bilgilerini tarafından etkilenen <xref:System.Globalization.NumberFormatInfo> nesnesi. Aşağıdaki tabloda özelliklerini <xref:System.Globalization.NumberFormatInfo> sonuç dizesinin biçimlendirmesinde denetim nesnesi.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamaklarını ondalık basamaklardan ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Varsayılan ondalık basamak sayısını tanımlar. B değeri hassasiyet belirleyici kullanılarak geçersiz kılınabilir.|  
  
 Aşağıdaki örnek biçimlerinden bir <xref:System.Double> ve bir <xref:System.Int32> sabit noktalı biçim belirteci değeri.  
  
 [!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
 [!code-csharp[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
 [!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]  
  
 [Tablo dön](#table)  
  
<a name="GFormatString"></a>   
## <a name="the-general-g-format-specifier"></a>Genel ("G") Biçim Belirleyicisi  
 Genel ("G") biçimi belirleyici bir sayıyı sayı türüne bağlı olarak sabit noktalı ya da bilimsel gösterim, daha fazla compact ve duyarlık Belirleyicisi bulunup bulunmadığını dönüştürür. Duyarlık belirtici, sonuç dizesindeki görünebilir maksimum anlamlı basamak sayısını tanımlar. Duyarlık belirtici atlanırsa veya sıfır olursa, sayının türü, aşağıdaki tabloda gösterildiği gibi varsayılan duyarlığı belirler.  
  
|Sayısal tür|Varsayılan duyarlık|  
|------------------|-----------------------|  
|<xref:System.Byte>veya<xref:System.SByte>|3 basamak|  
|<xref:System.Int16>veya<xref:System.UInt16>|5 rakamlı|  
|<xref:System.Int32>veya<xref:System.UInt32>|10 rakam|  
|<xref:System.Int64>|19 basamak|  
|<xref:System.UInt64>|20 basamak|  
|<xref:System.Numerics.BigInteger>|Sınırsız (aynı ["R"](#RFormatString))|  
|<xref:System.Single>|7 basamağa|  
|<xref:System.Double>|15 basamağa|  
|<xref:System.Decimal>|29 basamağa|  
  
 Sayı bilimsel gösterimde ifade edildiğinde elde edilen üs -5'ten büyükse ve duyarlık belirticiden küçükse sabit noktalı gösterim kullanılır; aksi takdirde bilimsel gösterim kullanılır. Sonuç gerekirse bir ondalık noktası içerir ve ondalık noktadan sonra gelen sıfırlar atlanır. Duyarlık belirtici varsa ve sonuçtaki anlamlı basamak sayısı, belirtilen duyarlığı aşarsa, sondaki fazlalık basamaklar yuvarlama tarafından kaldırılır.  
  
 Ancak, sayı ise bir <xref:System.Decimal> ve duyarlık Belirleyicisi girilmezse, sabit noktalı gösterim her zaman kullanılır ve sondaki sıfırlar korunur.  
  
 Bilimsel gösterim kullanılırsa, biçim belirtici "G" olduğunda sonuçtaki üssün başına "E", biçim belirtici "g" olduğunda "e" eklenir. Üs, en az iki basamak içerir. Bu, üs değerinde en az üç basamak içeren üssel biçim belirleyici tarafından üretilen bilimsel gösterim biçiminden farklıdır.  
 
İle kullanıldığında unutmayın bir <xref:System.Double> değeri, "G17" biçim belirticisi sağlar, özgün <xref:System.Double> başarıyla gidiş dönüş değeri. Bunun nedeni, <xref:System.Double> bir IEEE 754 2008-uyumlu çift duyarlık (`binary64`) kayan noktalı sayı, en fazla 17 önemli basamak duyarlık sağlar. Kullanımını yerine öneririz ["R" format belirleyici](#RFormatString), bazı durumlarda "R" başarıyla gidiş dönüş çift duyarlıklı kayan nokta değerlerine başarısız olduğundan. Aşağıdaki örnek, böyle bir durumda gösterilmektedir.

[!code-csharp[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs)]   
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]   

İle kullanıldığında bir <xref:System.Single> değeri, "G9" biçim belirticisi sağlar, özgün <xref:System.Single> başarıyla gidiş dönüş değeri. Bunun nedeni, <xref:System.Single> bir IEEE 754 2008-uyumlu tek duyarlılık (`binary32`) kayan noktalı sayı, en fazla dokuz önemli basamak duyarlık sağlar. Kullanımını yerine öneririz ["R" format belirleyici](#RFormatString), bazı durumlarda "R" başarıyla gidiş dönüş tek duyarlıklı kayan nokta değerlerine başarısız olduğundan.

 Sonuç dizesini geçerli biçimlendirme bilgilerini tarafından etkilenen <xref:System.Globalization.NumberFormatInfo> nesnesi. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> sonuç dizesinin biçimlendirmesinde denetleyen özellikler.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamaklarını ondalık basamaklardan ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Bir üssün pozitif olduğunu belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek, çeşitli kayan nokta değerlerini genel biçim belirteci ile biçimlendirir.  
  
 [!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
 [!code-csharp[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
 [!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]  
  
 [Tablo dön](#table)  
  
<a name="NFormatString"></a>   
## <a name="the-numeric-n-format-specifier"></a>Sayısal ("N") Biçim Belirleyicisi  
 Sayısal ("N") biçim belirteci bir sayıyı "-d,ddd,ddd.ddd…" biçiminde bir dizeye dönüştürür; burada "-" gerekirse negatif bir sayı simgesini, "d" bir basamağı (0-9) gösterir, "," bir grup ayırıcıyı gösterir ve "." bir ondalık simgesini gösterir. Duyarlık belirtici, ondalık noktasından sonraki istenen basamak sayısını gösterir. Duyarlık Belirleyicisi atlanırsa, ondalık basamak sayısını geçerli tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> özelliği.  
  
 Sonuç dizesini geçerli biçimlendirme bilgilerini tarafından etkilenen <xref:System.Globalization.NumberFormatInfo> nesnesi. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> sonuç dizesinin biçimlendirmesinde denetleyen özellikler.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|Negatif değerler biçimini tanımlar ve eksi işareti parantez tarafından temsil edilen belirtir veya <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> özelliği.|  
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|Grup ayırıcıları arasında görüntülenen tam sayı basamak sayısını tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|Tam sayı gruplarını ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı ve ondalık basamakları ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Varsayılan ondalık basamak sayısını tanımlar. B değeri bir hassasiyet belirleyici kullanılarak geçersiz kılınabilir.|  
  
 Aşağıdaki örnek, çeşitli kayan nokta değerlerini sayı biçim belirteci ile biçimlendirir.  
  
 [!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
 [!code-csharp[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
 [!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]  
  
 [Tablo dön](#table)  
  
<a name="PFormatString"></a>   
## <a name="the-percent-p-format-specifier"></a>Yüzde ("p") Biçim Belirleyicisi  
 Yüzde ("P") biçim belirticisi sayıyı 100 ile çarpar ve yüzde temsil eden bir dizeye dönüştürür. Duyarlık belirtici, istenen ondalık basamak sayısını gösterir. Duyarlık Belirleyicisi atlanırsa, geçerli tarafından sağlanan varsayılan sayısal duyarlık <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> özelliği kullanılır.  
  
 Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> döndürülen dizesinin biçimlendirmesinde denetleyen özellikler.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.PercentPositivePattern%2A>|Pozitif değerler için yüzde sembolünün yerleşimini tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.PercentNegativePattern%2A>|Negatif değerler için yüzde sembolünün ve eksi sembolünün yerleşimini tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A>|Yüzde sembolünü tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A>|Yüzde değerindeki varsayılan ondalık basamak sayısını tanımlar. B değeri hassasiyet belirleyici kullanılarak geçersiz kılınabilir.|  
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalSeparator%2A>|Tamsayı ve ondalık basamakları ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSeparator%2A>|Tam sayı gruplarını ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSizes%2A>|Bir grup içinde görüntülenen tamsayı basamak sayısını tanımlar.|  
  
 Aşağıdaki örnek, kayan nokta değerlerini yüzdelik biçim belirteci ile biçimlendirir.  
  
 [!code-cpp[Formatting.Numeric.Standard#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#7)]
 [!code-csharp[Formatting.Numeric.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#7)]
 [!code-vb[Formatting.Numeric.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#7)]  
  
 [Tablo dön](#table)  
  
<a name="RFormatString"></a>   
## <a name="the-round-trip-r-format-specifier"></a>Gidiş Dönüş ("R") Biçim Belirleyicisi  
 Gidiş dönüş ("R") biçimi belirleyici bir dizeye dönüştürülür sayısal bir değer geri aynı sayısal değer ayrıştırılır emin olmak çalışır. Bu biçim yalnızca desteklenen <xref:System.Single>, <xref:System.Double>, ve <xref:System.Numerics.BigInteger> türleri.  

İçin <xref:System.Double> ve <xref:System.Single> değerleri, bazı durumlarda "R" biçim belirticisi özgün değeri için başarıyla gidiş dönüş başarısız olur ve ayrıca nispeten düşük performans sunar. Bunun yerine, kullanmanızı öneririz ["G17"](#GFormatString) tanımlayıcısı için biçimlendirme <xref:System.Double> değerleri ve ["G9"](#GFormatString) başarıyla gidiş dönüş için belirleyici biçimlendirmek <xref:System.Single> değerleri.

 Zaman bir <xref:System.Numerics.BigInteger> değeri bu tanımlayıcısı kullanılarak biçimlendirilmiş, içindeki tüm önemli basamak dize gösterimini içeren <xref:System.Numerics.BigInteger> değeri.  
  
 Bir duyarlık belirtici ekleyebilirsiniz, ancak bu yoksayılır. Bu belirleyici kullanırken gidiş dönüşlere duyarlılık üzerinde öncelik verilir.    
 Sonuç dizesini geçerli biçimlendirme bilgilerini tarafından etkilenen <xref:System.Globalization.NumberFormatInfo> nesnesi. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> sonuç dizesinin biçimlendirmesinde denetleyen özellikler.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamaklarını ondalık basamaklardan ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Bir üssün pozitif olduğunu belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek biçimlerinden bir <xref:System.Numerics.BigInteger> gidiş dönüş biçim belirteci değeri.  
  
 [!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
 [!code-csharp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
 [!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]  
  
> [!IMPORTANT]
>  Bazı durumlarda, <xref:System.Double> kullanarak derlenmiş ise "R" standart sayısal biçim dizesi do ile başarıyla gidiş-dönüş yapmaz biçimlendirilen değerleri `/platform:x64` veya `/platform:anycpu` anahtarları ve çalıştırılacak 64 bit sistemler. Aşağıdaki paragraf daha fazla bilgi için bkz.  
  
 Sorunu çözmek için <xref:System.Double> "R" standart sayısal biçim ile biçimlendirilen değerleri kullanarak derlenmiş ise gidiş başarıyla dize `/platform:x64` veya `/platform:anycpu` anahtarları ve çalıştırılacak 64 bit sistemler., Biçim <xref:System.Double> "G17" standart sayısal biçim dizesi kullanarak değerleri. Aşağıdaki örnekte "R" biçim dizesine kullanan bir <xref:System.Double> gidiş-dönüş yapmaz o mu başarıyla değer ve ayrıca kullanır "G17" biçim dizesi için başarıyla gidiş dönüş özgün değeri.  
  
 [!code-csharp[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#5)]
 [!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]  
  
 [Tablo dön](#table)  
  
<a name="XFormatString"></a>   
## <a name="the-hexadecimal-x-format-specifier"></a>Onaltılı ("X") Biçim Belirleyicisi  
 ("X") onaltılı biçim belirticisi bir sayıyı onaltı basamaklı bir dizeye dönüştürür. Biçim belirticisinin durumu, 9'dan büyük onaltılık basamak için büyük veya küçük harf kullanılıp kullanılmayacağını belirtir. Örneğin, "ABCDEF" üretmek için "X" ve "abcdef" üretmek için "x" kullanın. Bu biçim yalnızca tam sayı türleri için desteklenir.  
  
 Duyarlık belirtici, sonuç dizesindeki istenen minimum basamak sayısını gösterir. Gerekirse, duyarlık belirtici tarafından verilen basamak sayısını üretmek için sayının sol tarafı sıfırlarla doldurulur  
  
 Sonuç dizesini geçerli biçimlendirme bilgileriyle etkilenmez <xref:System.Globalization.NumberFormatInfo> nesnesi.  
  
 Aşağıdaki örnek biçimleri <xref:System.Int32> onaltılı değerlerini biçimlendirir tanımlayıcısı.  
  
 [!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
 [!code-csharp[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
 [!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]  
  
 [Tablo dön](#table)  
  
<a name="NotesStandardFormatting"></a>   
## <a name="notes"></a>Notlar  
  
### <a name="control-panel-settings"></a>Denetim Masası Ayarları  
 Ayarlarında **bölge ve Dil Seçenekleri** Sonuç dizesini biçimlendirme bir işlem tarafından üretilen Denetim Masası etkisi öğesinde. Bu ayarları başlatmak için kullanılan <xref:System.Globalization.NumberFormatInfo> biçimlendirme yönetmek için kullanılan değerleri sağlayan geçerli iş parçacığı kültürünü ile ilişkili nesne. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.  
  
 Ayrıca, varsa <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> Oluşturucusu yeni bir örneğini oluşturmak için kullanılan <xref:System.Globalization.CultureInfo> aynı kültür geçerli sistem kültürü tarafından oluşturulan tüm özelleştirmeler olarak temsil eden nesnesi **bölge ve Dil Seçenekleri** Denetim Masası uygulanacak yeni <xref:System.Globalization.CultureInfo> nesnesi. Kullanabileceğiniz <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Oluşturucusu oluşturmak için bir <xref:System.Globalization.CultureInfo> sistemin özelleştirmeleri yansıtmaz nesnesi.  
  
### <a name="numberformatinfo-properties"></a>NumberFormatInfo Özellikleri  
 Biçimlendirme geçerli özellikleri tarafından Etkileyenler <xref:System.Globalization.NumberFormatInfo> örtük olarak geçerli iş parçacığı kültürünü veya açıkça tarafından sağlanan nesne <xref:System.IFormatProvider> biçimlendirme çağıran yönteminin parametresi. Belirtin bir <xref:System.Globalization.NumberFormatInfo> veya <xref:System.Globalization.CultureInfo> Bu parametre için nesne.  
  
> [!NOTE]
>  Desenler veya biçimlendirme sayısal değerleri kullanılan dizeleri özelleştirme hakkında daha fazla bilgi için bkz: <xref:System.Globalization.NumberFormatInfo> sınıfı konu.  
  
### <a name="integral-and-floating-point-numeric-types"></a>Tam Sayı ve Kayan Nokta Sayısal Türleri  
 Bazı standart sayısal biçim belirticilerinin açıklamaları, ayrılmaz veya kayan nokta sayısal türlere başvurur. Tam Sayı sayısal türler <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, ve <xref:System.Numerics.BigInteger>. Kayan nokta sayısal türler <xref:System.Decimal>, <xref:System.Single>, ve <xref:System.Double>.  
  
### <a name="floating-point-infinities-and-nan"></a>Kayan Nokta Sonsuz ve NaN  
 Biçim dizesi bağımsız olarak, değeri bir <xref:System.Single> veya <xref:System.Double> kayan nokta türdür pozitif sonsuzluk, negatif sonsuz veya sayı olmayan (NaN), biçimlendirilmiş dize değeri ilgili <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>, <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>, veya <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> tarafından şu anda geçerli olarak belirtilen özellik <xref:System.Globalization.NumberFormatInfo> nesnesi.  
  
<a name="example"></a>   
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir tamsayı ve kayan nokta sayısal değerini ing-ABD kültürü ve tüm standart sayısal biçim tanımlayıcılarını kullanarak biçimlendirir. Bu örnek iki belirli sayısal türler kullanır (<xref:System.Double> ve <xref:System.Int32>), diğer sayısal temel türlerinden herhangi birini için benzer sonuçlar verir ancak (<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Numerics.BigInteger>, <xref:System.Decimal>, ve <xref:System.Single>).  
  
 [!code-csharp[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#1)]
 [!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Globalization.NumberFormatInfo>  
 [Özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [Biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md)  
 [Nasıl yapılır: sayıyı baştaki sıfırlarla doldurur](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)  
 [Örnek: .NET Framework 4 yardımcı biçimlendirme](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)  
 [Bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)
