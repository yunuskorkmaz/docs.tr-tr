---
title: Standart Sayısal Biçim Dizeleri
ms.date: 06/10/2018
ms.technology: dotnet-standard
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
ms.openlocfilehash: 0618e9853eea2f4aa6e6a5dfd11b571cb3d7b123
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397182"
---
# <a name="standard-numeric-format-strings"></a>Standart Sayısal Biçim Dizeleri

Standart sayısal biçim dizeleri, genel sayısal türleri biçimlendirmek için kullanılır. Standart sayısal biçim dizesi biçimi alır `Axx`burada:  
  
-   `A` tek bir alfabetik karakter adlı *biçim belirticisi*. Beyaz boşluk da dahil olmak üzere birden fazla alfabetik karakter içeren herhangi bir sayısal biçim dizesi, özel bir sayısal biçim dizesi olarak yorumlanır. Daha fazla bilgi için [özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
-   `xx` İsteğe bağlı bir tamsayı olarak adlandırılan *duyarlık belirtici*. Precision belirleyici 0'dan 99'a kadar uzanır ve sonuç basamak sayısını etkiler. Duyarlık belirtici, sayının dize gösterimindeki basamak sayısını kontrol eder unutmayın. Sayının kendisini yuvarlamaz. Bir yuvarlama işlemi gerçekleştirmek için kullanın <xref:System.Math.Ceiling%2A?displayProperty=nameWithType>, <xref:System.Math.Floor%2A?displayProperty=nameWithType>, veya <xref:System.Math.Round%2A?displayProperty=nameWithType> yöntemi.  
  
    Zaman *duyarlık belirtici* denetimleri, sonuç dizesinin, sonuç dizesinde kesirli basamakların sayısı sonsuz kesin sonucu en yakın olanında gösterilebilen bir sonuç yuvarlanır birkaç yansıtır. Varsa iki eşit yakın gösterilebilir sonuçları:
    - **.NET Framework ve .NET Core ile .NET Core 2.0 kadar**, çalışma zamanı sonucu daha az önemli basamak ile seçer (diğer bir deyişle, kullanarak <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType>).
    - **.NET Core 2.1 ve üzeri**, çalışma zamanı sonucu bir daha az önemli basamak ile seçer (diğer bir deyişle, kullanarak <xref:System.MidpointRounding.ToEven?displayProperty=nameWithType>). 

    > [!NOTE]
    >  Duyarlık belirtici, sonuç dizesindeki basamak sayısını belirler. Başta veya sonda boşluk içeren bir sonuç dizesi paneli için kullanın [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md) özellik ve tanımlayan bir *hizalama bileşeni* biçim öğesindeki.  
  
Standart sayısal biçim dizeleri tarafından desteklenir:

- Bazı aşırı yüklemeleri `ToString` tüm sayısal türlerin yöntemi. Örneğin, bir sayısal biçim dizesi sağlayabilirsiniz <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> ve <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemleri. 
 
- .NET [bileşik biçimlendirme özelliği](../../../docs/standard/base-types/composite-formatting.md), yarafında kullanılır `Write` ve `WriteLine` yöntemlerinin <xref:System.Console> ve <xref:System.IO.StreamWriter> sınıfları <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi ve <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> yöntemi. Bileşik biçimlendirme özelliği, alan genişliğini belirtin ve alanına sayı hizalamak için tek bir dize içinde birden fazla öğe dize gösterimini eklemenizi sağlar. Daha fazla bilgi için [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).  

- [İlişkilendirilmiş dizeler](../../csharp/language-reference/tokens/interpolated.md) hangi, C# ve Visual Basic bileşik biçimli dizeler karşılaştırıldığında basitleştirilmiş bir sözdizimi sağlar.
 
> [!TIP]
>  İndirebileceğiniz [biçimlendirme yardımcı programı](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), biçim sağlayan bir uygulama dizeleri sayısal veya tarih ve saat değerleri ve sonuç dizeyi görüntülemenizi.  
  
<a name="table"></a> Aşağıdaki tablo standart sayısal biçim belirteçlerini açıklar ve her biçim Belirleyicisinin ürettiği örnek çıktıları görüntüler. Bkz: [notları](#NotesStandardFormatting) standart sayısal biçim dizeleri kullanma hakkında ek bilgi bölümü ve [örnek](#example) kullanımlarının kapsamlı anlatımı için bölüm.  
  
|Biçim belirteci|Ad|Açıklama|Örnekler|  
|----------------------|----------|-----------------|--------------|  
|"C" ya da "c"|Para Birimi|Sonuç: Bir para birimi değeri.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Daha fazla bilgi: [para birimi ("C") Biçim belirleyicisi](#CFormatString).|123,456 ("C", en-US) -> 123,46 $<br /><br /> 123,456 ("C", fr-FR) -> 123,46 €<br /><br /> 123,456 ("C", ja-JP) ¥ 123 -><br /><br /> ($123,456)-123.456 ("C3", en-US) -><br /><br /> -123,456 €-123.456 ("C3", fr-FR) -><br /><br /> -123.456 ("C3", ja-JP) ->-¥ 123,456|  
|"D" veya "d"|Ondalık|Sonuç: İsteğe bağlı eksi işaretli tamsayı basamaklar.<br /><br /> Desteklenen: sadece integral türleri.<br /><br /> Duyarlık belirtici: Minimum basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: En az gereken basamak sayısı.<br /><br /> Daha fazla bilgi: [Decimal("D") biçim belirticisi](#DFormatString).|1234 1234 ("D") -&GT;<br /><br /> -001234 ("D6") -1234 -&GT;|  
|"E" ya da "e"|Üstsel (bilimsel)|Sonuç: Üstel simgeleme.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: 6.<br /><br /> Daha fazla bilgi: [üstel ("E") Biçim belirleyicisi](#EFormatString).|1052.0329112756 ("E" en-US) -> 1.052033E + 003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1, 052033e + 003<br /><br /> -1052.0329112756 ("e2", en-US) -> - 1.05e + 003<br /><br /> -1052.0329112756 ("E2", fr-FR) -> -1, 05E + 003|  
|"F" ya da "f"|Sabit nokta|Sonuç: İsteğe bağlı eksi işaretli tamsayı ve ondalık basamaklar.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Daha fazla bilgi: [sabit nokta ("F") Biçim belirleyicisi](#FFormatString).|1234.567 ("F" en-US) -> 1234.57<br /><br /> 1234.567 ("F" de-DE) 1234,57 -><br /><br /> 1234 ("F1" en-US) -> 1234.0<br /><br /> 1234 ("F1" de-DE) 1234,0 -><br /><br /> -1234.5600-1234.56 ("F4", en-US) -><br /><br /> -1234.56 ("F4", de-DE) -> - 1234,5600|  
|"G" ya da "g"|Genel|Sonuç: Daha fazla sabit noktalı veya bilimsel gösterim.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Anlamlı basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: Sayısal türe bağlıdır.<br /><br /> Daha fazla bilgi: [genel ("G") Biçim belirleyicisi](#GFormatString).|-123.456-123.456 ("G", en-US) -><br /><br /> -123,456-123.456 ("G", sv-SE) -><br /><br /> 123.4546 ("G4" en-US) -> 123.5<br /><br /> 123.4546 ("G4" sv-SE) 123,5 -><br /><br /> -1.234567890e-25 ("G", en-US) -> - 1.23456789E-25<br /><br /> -1.234567890e-25 ("G", sv-SE) -> -1, 25 23456789E|  
|"N" ya da "n"|Sayı|Sonuç: Integral ve ondalık basamaklar, grup ayırıcılar ve isteğe bağlı eksi işaretli ondalık ayırıcı.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: İstenen ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Daha fazla bilgi: [sayısal ("N") Biçim belirleyicisi](#NFormatString).|1234.567 ("N" en-US) -> 1,234.57<br /><br /> 1234.567 ("N", ru-RU) 1 234,57 -><br /><br /> 1234 ("N1" en-US) -> 1,234.0<br /><br /> 1234 ("N1", ru-RU) 1 234,0 -><br /><br /> -1,234.560-1234.56 ("N3", en-US) -><br /><br /> -1 234,560-1234.56 ("N3", ru-RU) ->|  
|"P" ya da "p"|Yüzde|Sonuç: Sayı 100 ile çarpılır ve yüzde simgesi ile görüntülenir.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: İstenen ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Daha fazla bilgi: [yüzde ("P") Biçim belirleyicisi](#PFormatString).|1 ("P", en-US) -> % 100,00<br /><br /> 1 ("P", fr-FR) -> %100,00<br /><br /> -0.39678 ("P1", en-US) ->-39.7%<br /><br /> -0.39678 ("P1", fr-FR) -> - %39,7|  
|"R" ya da "r"|Gidiş|Sonuç: Aynı numaraya gidiş dönüş yapabilen bir dize.<br /><br /> Tarafından desteklenen: <xref:System.Single>, <xref:System.Double>, ve <xref:System.Numerics.BigInteger>.<br /><br /> Not: önerilen <xref:System.Numerics.BigInteger> yalnızca yazın. İçin <xref:System.Double> türlerini, "G17" kullanır; <xref:System.Single> türleri "G9" kullanın. </br> Duyarlık belirtici: Yoksayıldı.<br /><br /> Daha fazla bilgi: [gidiş dönüş ("R") Biçim belirleyicisi](#RFormatString).|123456789.12345678 123456789.12345678 ("R") -&GT;<br /><br /> -1234567890.1234567-1234567890.12345678 ("R") -&GT;|  
|"X" ya da "x"|Onaltılık|Sonuç: Bir onaltılık dize.<br /><br /> Desteklenen: sadece integral türleri.<br /><br /> Duyarlık belirtici: Sonuç dizesindeki basamak sayısı.<br /><br /> Daha fazla bilgi: [onaltılı ("X") Biçim belirleyicisi](#XFormatString).|255 ("X") FF -&GT;<br /><br /> -1 ("x") ff -><br /><br /> 00ff 255 ("x4") -><br /><br /> -1 ("X4") 00FF -&GT;|  
|Başka bir tek karakter|Bilinmeyen tanımlayıcı|Sonuç: Oluşturur bir <xref:System.FormatException> çalışma zamanında.||  
  
<a name="Using"></a>   
## <a name="using-standard-numeric-format-strings"></a>Standart Sayısal Biçim Dizeleri Kullanma  

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Standart bir sayısal biçimli dize, şu iki yoldan biriyle sayısal bir değerin biçimlendirmesini tanımlamak için kullanılabilir:  
  
-   Bir aşırı yüklemesini geçirilebilir `ToString` yöntemin bir `format` parametresi. Aşağıdaki örnek, sayısal bir değer (Bu durumda, en-US kültürü) geçerli kültüründeki para birimi dizesi olarak biçimlendirir.  
  
     [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
     [!code-csharp-interactive[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
     [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]  
  
-   Olarak sağlanabilir `formatString` bağımsız değişken yöntemlerle kullanılan biçim öğesinde <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, ve <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>. Daha fazla bilgi için [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md). Aşağıdaki örnek, bir dizeye bir para birimi değeri eklemek için bir biçim öğesi kullanmaktadır.  
  
     [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
     [!code-csharp-interactive[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
     [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]  
  
     İsteğe bağlı olarak, kaynağı bir `alignment` sayısal alan ve değeri sağa veya sola hizalı olup genişliğini belirlemek için bağımsız değişken. Aşağıdaki örnek sol-28-karakter alanı para birimi değeri, ve onu sağ-14 karakterlik alan para birimi değeri hizalar.  
  
     [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
     [!code-csharp-interactive[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
     [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]  
  
-   Olarak sağlanabilir `formatString` bağımsız değişkeni olarak bir aradeğerlendirme dizesinde ilişkilendirilmiş ifade öğesi. Daha fazla bilgi için [dize ilişkilendirme](../../csharp/language-reference/tokens/interpolated.md) konu C# başvurusu veya [Ara değerli dizeler](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) konuda Visual Basic başvurusu.  
  
 Aşağıdaki bölümlerde her standart sayısal biçim dizesi hakkında ayrıntılı bilgi sağlanmaktadır.  
  
<a name="CFormatString"></a>   
## <a name="the-currency-c-format-specifier"></a>Para Birimi ("C") Biçim Belirleyicisi  
 "C" (ya da para birimi) biçim belirticisi, bir sayıyı para birimi tutarını gösteren bir dizeye dönüştürür. Duyarlık belirtici, sonuç dizesindeki istenen ondalık basamak sayısını gösterir. Duyarlık belirtici atlanırsa, tarafından varsayılan duyarlık tanımlanır <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> özelliği.  
  
 Biçimlendirilecek değer, belirtilen veya varsayılan ondalık basamak sayısından fazlasına sahipse, sonuç dizesinde kesirli değer yuvarlanır. Belirtilen ondalık basamak sayısının sağındaki değer 5 veya daha büyükse, sonuç dizesindeki son basamak, sıfırdan uzağa yuvarlanır.  
  
 Sonuç dizesini geçerli biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> nesne. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> döndürülen dizenin biçimlendirilmesini denetleyen özellikler.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|Pozitif değerler için para birimi sembolünün yerleşimini tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|Negatif değerlerin para birimi sembolünün yerleşimini tanımlar ve eksi işaretinin parantezle olup olmadığını belirtir veya <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> özelliği.|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Eksi işaretinin kullanıldığını tanımlar <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> parantez kullanılmadığını gösterir.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|Para birimi sembolünü tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|Para birimi değerindeki varsayılan ondalık basamak sayısını tanımlar. B değeri hassasiyet belirleyici kullanılarak geçersiz kılınabilir.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|Tamsayı ve ondalık basamakları ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|Tam sayı gruplarını ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|Bir grup içinde görüntülenen tamsayı basamak sayısını tanımlar.|  
  
 Aşağıdaki örnek biçimler bir <xref:System.Double> değerini para birimi biçim belirteci ile.  
  
 [!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
 [!code-csharp[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
 [!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]  
  
 [Tabloya dön](#table)  
  
<a name="DFormatString"></a>   
## <a name="the-decimal-d-format-specifier"></a>Ondalık ("D") Biçim Belirleyicisi  
 "D" (veya ondalık) biçim belirticisi, sayıyı, sayı negatifse eksi işaretiyle önekli bir ondalık basamaklı (0-9) bir dizeye dönüştürür. Bu biçim yalnızca tam sayı türleri için desteklenir.  
  
 Duyarlık belirtici, sonuç dizesindeki istenen minimum basamak sayısını gösterir. Gerekirse, duyarlık belirtici tarafından verilen basamak sayısını üretmek için sayının sol tarafı sıfırlarla doldurulur Bir duyarlık belirtici belirtilmezse varsayılan, başta sıfır bulunmadan tamsayıyı temsil etmek için gerekli minimum değerdir.  
  
 Sonuç dizesini geçerli biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> nesne. Aşağıdaki tabloda gösterildiği gibi tek bir özellik, sonuç dizesinin biçimlendirmesini etkiler.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek biçimler bir <xref:System.Int32> değerini ondalık biçim belirteci ile.  
  
 [!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
 [!code-csharp-interactive[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
 [!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]  
  
 [Tabloya dön](#table)  
  
<a name="EFormatString"></a>   
## <a name="the-exponential-e-format-specifier"></a>Üstel ("E") Biçim Belirleyicisi  
 Üstel ("E") biçim belirteci bir sayıyı "-d.ddd...E + ggg" veya "-d.ddd...e+ddd" biçiminde bir dizeye dönüştürür; burada her "d" bir basamağı (0-9) gösterir. Sayı negatifse, dize eksi işaretiyle başlar. Ondalık işaretinden önce her zaman tam bir basamak gelir.  
  
 Duyarlık belirtici, ondalık noktasından sonraki istenen basamak sayısını gösterir. Duyarlık belirtici atlanırsa, ondalık işaretinden sonra varsayılan olarak altı basamak kullanılır.  
  
 Biçim belirticisinin durumu üsse "E" veya "e" önekinin getirilip getirilmeyeceğini gösterir. Üs her zaman bir artı veya eksi işareti ile en az üç basamaktan oluşur. Üs bu minimum şartı karşılamak için gerekirse sıfırlarla doldurulur.  
  
 Sonuç dizesini geçerli biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> nesne. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> döndürülen dizenin biçimlendirilmesini denetleyen özellikler.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının hem katsayı hem de üs için negatif olduğunu belirten dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamağını, katsayıdaki ondalık basamaklardan ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Bir üssün pozitif olduğunu belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek biçimler bir <xref:System.Double> değerini üstel biçim belirteci ile.  
  
 [!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
 [!code-csharp[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
 [!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]  
  
 [Tabloya dön](#table)  
  
<a name="FFormatString"></a>   
## <a name="the-fixed-point-f-format-specifier"></a>Sabit Nokta ("F") Biçim Belirleyicisi  
 Sabit nokta ("F") Biçim belirleyicisi bir sayıyı biçiminde bir dizeye dönüştürür "-bbb.bbb…" burada her "d" bir basamağı (0-9) gösterir. Sayı negatifse, dize eksi işaretiyle başlar.  
  
 Duyarlık belirtici, istenen ondalık basamak sayısını gösterir. Duyarlık belirtici atlanırsa, geçerli <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> özelliği sayısal duyarlık sağlar.  
  
 Sonuç dizesini geçerli biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> nesne. Aşağıdaki tabloda özelliklerini listeler <xref:System.Globalization.NumberFormatInfo> Sonuç dizesini formatlamayı kontrol eden nesne.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamaklarını ondalık basamaklardan ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Varsayılan ondalık basamak sayısını tanımlar. B değeri hassasiyet belirleyici kullanılarak geçersiz kılınabilir.|  
  
 Aşağıdaki örnek biçimler bir <xref:System.Double> ve <xref:System.Int32> değerini sabit noktalı biçim belirteci ile.  
  
 [!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
 [!code-csharp[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
 [!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]  
  
 [Tabloya dön](#table)  
  
<a name="GFormatString"></a>   
## <a name="the-general-g-format-specifier"></a>Genel ("G") Biçim Belirleyicisi  
 Genel ("G") Biçim belirleyicisi bir sayıyı, sayı türüne bağlı olarak sabit noktalı veya bilimsel gösterim daha kompakt ve duyarlık belirtici bulunup bulunmadığını dönüştürür. Duyarlık belirtici, sonuç dizesindeki görünebilir maksimum anlamlı basamak sayısını tanımlar. Duyarlık belirtici atlanırsa veya sıfır olursa, sayının türü, aşağıdaki tabloda gösterildiği gibi varsayılan duyarlığı belirler.  
  
|Sayısal tür|Varsayılan duyarlık|  
|------------------|-----------------------|  
|<xref:System.Byte> veya <xref:System.SByte>|3 basamak|  
|<xref:System.Int16> veya <xref:System.UInt16>|5 rakamlı|  
|<xref:System.Int32> veya <xref:System.UInt32>|10 rakam|  
|<xref:System.Int64>|19 basamaktan|  
|<xref:System.UInt64>|20 basamak|  
|<xref:System.Numerics.BigInteger>|Sınırsız (aynı ["R"](#RFormatString))|  
|<xref:System.Single>|7 basamakla|  
|<xref:System.Double>|15 basamak|  
|<xref:System.Decimal>|29 basamak|  
  
 Sayı bilimsel gösterimde ifade edildiğinde elde edilen üs -5'ten büyükse ve duyarlık belirticiden küçükse sabit noktalı gösterim kullanılır; aksi takdirde bilimsel gösterim kullanılır. Sonuç gerekirse bir ondalık noktası içerir ve ondalık noktadan sonra gelen sıfırlar atlanır. Duyarlık belirtici varsa ve sonuçtaki anlamlı basamak sayısı, belirtilen duyarlığı aşarsa, sondaki fazlalık basamaklar yuvarlama tarafından kaldırılır.  
  
 Ancak, bir sayı ise bir <xref:System.Decimal> ve duyarlık belirtici atlanırsa, her zaman sabit noktalı gösterim kullanılır ve sondaki sıfırlar korunur.  
  
 Bilimsel gösterim kullanılırsa, biçim belirtici "G" olduğunda sonuçtaki üssün başına "E", biçim belirtici "g" olduğunda "e" eklenir. Üs, en az iki basamak içerir. Bu, üs değerinde en az üç basamak içeren üssel biçim belirleyici tarafından üretilen bilimsel gösterim biçiminden farklıdır.  
 
İle kullanıldığında unutmayın bir <xref:System.Double> değeri "G17" biçim belirticisi sağlar, özgün <xref:System.Double> başarıyla gidiş dönüş değeri. Bunun nedeni, <xref:System.Double> bir IEEE 754 2008-uyumlu çift duyarlık (`binary64`) kayan noktalı sayı, en çok 17 anlamlı basamak duyarlılığındadır sağlar. Kullanımını yerine öneririz ["R" biçim belirteci](#RFormatString), bazı durumlarda, başarılı bir şekilde gidiş dönüş çift duyarlıklı kayan nokta değerleri için "R" başarısız olduğundan. Aşağıdaki örnekte, böyle bir durumda gösterilmektedir.

[!code-csharp-interactive[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs)]   
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]   

İle kullanıldığında bir <xref:System.Single> değeri "G9" biçim belirticisi sağlar, özgün <xref:System.Single> başarıyla gidiş dönüş değeri. Bunun nedeni, <xref:System.Single> bir IEEE 754 2008-uyumlu tek duyarlık (`binary32`) kayan noktalı sayı, en çok dokuz anlamlı basamak duyarlılığındadır sağlar. Performansla ilgili nedenlerden dolayı kullanımını yerine öneririz ["R" biçim belirteci](#RFormatString).

 Sonuç dizesini geçerli biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> nesne. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> Sonuç dizesini formatlamayı kontrol eden özellikleri.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamaklarını ondalık basamaklardan ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Bir üssün pozitif olduğunu belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek, çeşitli kayan nokta değerlerini genel biçim belirteci ile biçimlendirir.  
  
 [!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
 [!code-csharp[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
 [!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]  
  
 [Tabloya dön](#table)  
  
<a name="NFormatString"></a>   
## <a name="the-numeric-n-format-specifier"></a>Sayısal ("N") Biçim Belirleyicisi  
 Sayısal ("N") biçim belirteci bir sayıyı "-d,ddd,ddd.ddd…" biçiminde bir dizeye dönüştürür; burada "-" gerekirse negatif bir sayı simgesini, "d" bir basamağı (0-9) gösterir, "," bir grup ayırıcıyı gösterir ve "." bir ondalık simgesini gösterir. Duyarlık belirtici, ondalık noktasından sonraki istenen basamak sayısını gösterir. Duyarlık belirtici atlanırsa, ondalık basamak sayısı geçerli tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> özelliği.  
  
 Sonuç dizesini geçerli biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> nesne. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> Sonuç dizesini formatlamayı kontrol eden özellikleri.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|Negatif değerlerin biçimini tanımlar ve eksi işaretinin parantezle olup olmadığını belirtir veya <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> özelliği.|  
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|Grup ayırıcıları arasında görüntülenen tam sayı basamak sayısını tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|Tam sayı gruplarını ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı ve ondalık basamakları ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Varsayılan ondalık basamak sayısını tanımlar. B değeri bir hassasiyet belirleyici kullanılarak geçersiz kılınabilir.|  
  
 Aşağıdaki örnek, çeşitli kayan nokta değerlerini sayı biçim belirteci ile biçimlendirir.  
  
 [!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
 [!code-csharp[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
 [!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]  
  
 [Tabloya dön](#table)  
  
<a name="PFormatString"></a>   
## <a name="the-percent-p-format-specifier"></a>Yüzde ("p") Biçim Belirleyicisi  
 Yüzde ("P") biçim belirticisi sayıyı 100 ile çarpar ve yüzde temsil eden bir dizeye dönüştürür. Duyarlık belirtici, istenen ondalık basamak sayısını gösterir. Duyarlık belirtici atlanırsa, geçerli tarafından sağlanan varsayılan sayısal duyarlık <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> özelliği kullanılır.  
  
 Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> döndürülen dizenin biçimlendirilmesini denetleyen özellikler.  
  
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
  
 [Tabloya dön](#table)  
  
<a name="RFormatString"></a>   
## <a name="the-round-trip-r-format-specifier"></a>Gidiş Dönüş ("R") Biçim Belirleyicisi  
 Gidiş dönüş ("R") biçim tanımlayıcısı bir dizeye dönüştürülen sayısal bir değer geri aynı sayısal değere ayrıştırılır emin olmak çalışır. Bu biçim yalnızca desteklenen <xref:System.Single>, <xref:System.Double>, ve <xref:System.Numerics.BigInteger> türleri.  

İçin <xref:System.Double> değerleri bazı durumlarda "R" biçim belirtici başarısız için başarılı bir şekilde gidiş dönüş özgün değer. Her ikisi için de <xref:System.Double> ve <xref:System.Single> değerleri de sunduğu nispeten düşük performans. Bunun yerine kullanmanızı öneriyoruz ["G17"](#GFormatString) biçim belirticisi için <xref:System.Double> değerleri ve ["G9"](#GFormatString) biçim belirticisi başarıyla gidiş dönüş için <xref:System.Single> değerleri.

 Olduğunda bir <xref:System.Numerics.BigInteger> değeri bu belirtisi kullanılarak biçimlendirildiğinde, dize gösterimine tüm önemli basamakları içerir <xref:System.Numerics.BigInteger> değeri.  
  
 Bir duyarlık belirtici ekleyebilirsiniz, ancak bu yoksayılır. Bu belirleyici kullanırken gidiş dönüşlere duyarlılık üzerinde öncelik verilir.    
 Sonuç dizesini geçerli biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> nesne. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> Sonuç dizesini formatlamayı kontrol eden özellikleri.  
  
|NumberFormatInfo özellikleri|Açıklama|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamaklarını ondalık basamaklardan ayıran dizeyi tanımlar.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Bir üssün pozitif olduğunu belirten dizeyi tanımlar.|  
  
 Aşağıdaki örnek biçimler bir <xref:System.Numerics.BigInteger> gidiş dönüş biçim belirteci ile değeri.  
  
 [!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
 [!code-csharp-interactive[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
 [!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]  
  
> [!IMPORTANT]
>  Bazı durumlarda, <xref:System.Double> kullanarak derlenmiş ise "R" standart sayısal biçim dizesi başlatma ile başarılı bir şekilde gidiş biçimlendirilen değerleri `/platform:x64` veya `/platform:anycpu` anahtarları ve çalıştırılacak 64-bit sistemler. Daha fazla bilgi için aşağıdaki paragrafa bakın.  
  
 Sorunu gidermek için <xref:System.Double> "R" standart sayısal biçim ile biçimlendirilen değerleri kullanarak derlenmiş ise gidiş dönüşü başarıyla dize `/platform:x64` veya `/platform:anycpu` anahtarları ve çalıştırılacak 64-bit sistemler., Biçim <xref:System.Double> "G17" standart sayısal biçim dizesi kullanarak değerleri. Aşağıdaki örnekte "R" biçim dizesiyle bir <xref:System.Double> dönmez bu mu başarıyla değerini ve ayrıca kullanır "G17" biçim dizesi için başarılı bir şekilde gidiş dönüş özgün değer.  
  
 [!code-csharp[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#5)]
 [!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]  
  
 [Tabloya dön](#table)  
  
<a name="XFormatString"></a>   
## <a name="the-hexadecimal-x-format-specifier"></a>Onaltılı ("X") Biçim Belirleyicisi  
 ("X") onaltılı biçim belirticisi bir sayıyı onaltı basamaklı bir dizeye dönüştürür. Biçim belirticisinin durumu, 9'dan büyük onaltılık basamak için büyük veya küçük harf kullanılıp kullanılmayacağını belirtir. Örneğin, "ABCDEF" üretmek için "X" ve "abcdef" üretmek için "x" kullanın. Bu biçim yalnızca tam sayı türleri için desteklenir.  
  
 Duyarlık belirtici, sonuç dizesindeki istenen minimum basamak sayısını gösterir. Gerekirse, duyarlık belirtici tarafından verilen basamak sayısını üretmek için sayının sol tarafı sıfırlarla doldurulur  
  
 Sonuç dizesini geçerli biçimlendirme bilgileri tarafından etkilenmez <xref:System.Globalization.NumberFormatInfo> nesne.  
  
 Aşağıdaki örnek biçimler <xref:System.Int32> değerlerini onaltılık biçim belirteci.  
  
 [!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
 [!code-csharp-interactive[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
 [!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]  
  
 [Tabloya dön](#table)  
  
<a name="NotesStandardFormatting"></a>   
## <a name="notes"></a>Notlar  
  
### <a name="control-panel-settings"></a>Denetim Masası Ayarları  
 Ayarlarında **bölge ve Dil Seçenekleri** öğesinde bir biçimlendirme işlemiyle oluşturulan Sonuç dizesini Denetim Masası etkiler. Bu ayarları başlatmak için kullanılan <xref:System.Globalization.NumberFormatInfo> biçimlendirmeyi yönetmek için değerler sunar geçerli iş parçacığı kültürüyle ilgili nesne. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.  
  
 Ayrıca, varsa <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> yeni bir örneğini oluşturmak için kullanılan Oluşturucu <xref:System.Globalization.CultureInfo> yapılan her özelleştirme mevcut sistem kültürüyle aynı kültürü temsil eden nesne **bölge ve Dil Seçenekleri** Denetim Masası'ndaki öğesi uygulanacak yeni <xref:System.Globalization.CultureInfo> nesne. Kullanabileceğiniz <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> oluşturmak için bir <xref:System.Globalization.CultureInfo> sistem özelleştirmelerini içermeyen bir nesne.  
  
### <a name="numberformatinfo-properties"></a>NumberFormatInfo Özellikleri  
 Biçimlendirme geçerli özellikleri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> tarafından açık olarak veya geçerli iş parçacığı kültürü tarafından örtük olarak sağlanan nesne <xref:System.IFormatProvider> biçimlendirmeyi çağıran yöntemin parametre. Belirtin bir <xref:System.Globalization.NumberFormatInfo> veya <xref:System.Globalization.CultureInfo> bu parametreye yönelik nesne.  
  
> [!NOTE]
>  Desenleri veya dizeleri, sayısal değerlerin biçimlendirmesinde kullanılan özelleştirme hakkında daha fazla bilgi için bkz: <xref:System.Globalization.NumberFormatInfo> sınıf konusuna.  
  
### <a name="integral-and-floating-point-numeric-types"></a>Tam Sayı ve Kayan Nokta Sayısal Türleri  
 Bazı standart sayısal biçim belirticilerinin açıklamaları, ayrılmaz veya kayan nokta sayısal türlere başvurur. Tamsayı sayısal türleri şunlardır <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, ve <xref:System.Numerics.BigInteger>. Kayan nokta sayısal türleri <xref:System.Decimal>, <xref:System.Single>, ve <xref:System.Double>.  
  
### <a name="floating-point-infinities-and-nan"></a>Kayan Nokta Sonsuz ve NaN  
 Biçim dizesine bakılmaksızın, değeri bir <xref:System.Single> veya <xref:System.Double> kayan nokta türü, Pozitif sonsuz, negatif sonsuz veya sayı olmayan (NaN), biçimlendirilmiş dize ilgili değeri <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>, <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>, veya <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> tarafından şu anda geçerli olarak belirtilen özellik <xref:System.Globalization.NumberFormatInfo> nesne.  
  
## <a name="example"></a>Örnek  
 
[!INCLUDE[interactive-note](~/includes/csharp-interactive-partial-note.md)]
 
 Aşağıdaki örnek, bir tamsayı ve kayan nokta sayısal değerini ing-ABD kültürü ve tüm standart sayısal biçim tanımlayıcılarını kullanarak biçimlendirir. Bu örnekte iki belirli sayısal tür (<xref:System.Double> ve <xref:System.Int32>), fakat diğer sayısal taban türleri için benzer sonuçlar verir (<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Numerics.BigInteger>, <xref:System.Decimal>, ve <xref:System.Single>).  
  
 [!code-csharp-interactive[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#1)]
 [!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.NumberFormatInfo>  
- [Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)  
- [Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)  
- [Örnek: .NET Framework 4 biçimlendirme yardımcı](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)  
- [Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)
