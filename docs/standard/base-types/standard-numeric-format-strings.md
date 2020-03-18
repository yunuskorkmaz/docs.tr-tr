---
title: Standart sayısal biçim dizeleri
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
ms.openlocfilehash: 04ac99c6b5100c3749eefc219e51b4d0084bef06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400325"
---
# <a name="standard-numeric-format-strings"></a>Standart sayısal biçim dizeleri

Standart sayısal biçim dizeleri, genel sayısal türleri biçimlendirmek için kullanılır. Standart bir sayısal biçim dizesi, aşağıdakileri alır: `Axx`

- `A`*biçim belirtici*olarak adlandırılan tek bir alfabetik karakterdir. Beyaz boşluk da dahil olmak üzere birden fazla alfabetik karakter içeren herhangi bir sayısal biçim dizesi, özel bir sayısal biçim dizesi olarak yorumlanır. Daha fazla bilgi için Bkz. [Özel Sayısal Biçim Dizeleri.](../../../docs/standard/base-types/custom-numeric-format-strings.md)

- `xx`*hassas belirtici*olarak adlandırılan isteğe bağlı bir tümsecidir. Precision belirleyici 0'dan 99'a kadar uzanır ve sonuç basamak sayısını etkiler. Hassas belirticinin bir sayının dize gösterimindeki basamak sayısını kontrol ettiğini unutmayın. Sayının kendisini yuvarlamaz. Yuvarlama işlemini gerçekleştirmek için <xref:System.Math.Ceiling%2A?displayProperty=nameWithType> <xref:System.Math.Floor%2A?displayProperty=nameWithType>, <xref:System.Math.Round%2A?displayProperty=nameWithType> veya yöntemi kullanın.

  *Hassas belirtim,* sonuç dizesindeki kesirli basamak sayısını kontrol ettiğinde, sonuç dizesi sonsuz kesin sonuca en yakın temsil edilebilir bir sonuca yuvarlanan bir sayıyı yansıtır. Temsil edilebilir iki eşit yakın sonuçlar varsa:
  - **.NET Framework ve .NET Core 2.0'a kadar .NET Core'da**çalışma zamanı sonucu en az <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType>anlamlı rakamla (yani kullanarak) seçer.
  - **.NET Core 2.1 ve sonraki**nde, çalışma zamanı sonucu en az anlamlı <xref:System.MidpointRounding.ToEven?displayProperty=nameWithType>rakamla (yani kullanarak) seçer.

  > [!NOTE]
  > Hassas belirtici, sonuç dizesindeki basamak sayısını belirler. Bir sonuç dizesini satır aralığı veya sondaki boşluklarla doldurmak [için, bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md) özelliğini kullanın ve biçim öğesinde bir *hizalama bileşeni* tanımlayın.

Standart sayısal biçim dizeleri tarafından desteklenir:

- Tüm sayısal türlerin `ToString` yönteminin bazı aşırı yükleri. Örneğin, sayısal biçim dizesi <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> ve <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemleri sağlayabilirsiniz.

- .NET [bileşik biçimlendirme özelliği,](../../../docs/standard/base-types/composite-formatting.md) `Write` bazı `WriteLine` <xref:System.Console> ve <xref:System.IO.StreamWriter> sınıflar, <xref:System.String.Format%2A?displayProperty=nameWithType> yöntem ve <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> yöntem tarafından kullanılan. Bileşik biçim özelliği, birden çok veri öğesinin dize gösterimini tek bir dizeye eklemenize, alan genişliğini belirtmenize ve bir alandaki sayıları hizalamanıza olanak tanır. Daha fazla bilgi için [Bkz. Bileşik Biçimlendirme.](../../../docs/standard/base-types/composite-formatting.md)

- Bileşik biçim dizeleri ile karşılaştırıldığında basitleştirilmiş bir sözdizimi sağlayan C# ve Visual Basic'teki [enterpolasyonlu dizeleri.](../../csharp/language-reference/tokens/interpolated.md)

> [!TIP]
> **Biçimlendirme Yardımcı Programı'nı**indirebilirsiniz , bir .NET Core Windows Forms uygulamasını, biçim dizelerini sayısal veya tarih ve saat değerlerine uygulamanızı ve sonuç dizesini görüntülemenizi sağlar. Kaynak kodu [C#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) ve [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)için kullanılabilir.

<a name="table"></a>Aşağıdaki tabloda standart sayısal biçim belirteçleri açıklanır ve her biçim belirtici tarafından üretilen örnek çıktıgörüntüler. Standart sayısal biçim dizelerini kullanma hakkında ek bilgi için [Notlar](#NotesStandardFormatting) bölümüne ve bunların kullanımının kapsamlı bir çizimi için [Örnek](#example) bölümüne bakın.

|Biçim belirteci|Adı|Açıklama|Örnekler|
|----------------------|----------|-----------------|--------------|
|"C" ya da "c"|Para birimi|Sonuç: Bir para birimi değeri.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Ondalık basamak sayısı.<br /><br /> Varsayılan kesinlik belirtici: <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType>Tanımlanır.<br /><br /> Daha fazla bilgi: [Para Birimi ("C") Biçim Belirtici](#CFormatString).|123.456 ("C", en-ABD) \\-> 123,46 $<br /><br /> 123.456 ("C", fr-FR) -> 123,46 €<br /><br /> 123.456 ("C", ja-JP) -> ¥123<br /><br /> -123.456 ("C3", en-ABD)\\-> ( $123.456)<br /><br /> -123.456 ("C3", fr-FR) -> -123.456 €<br /><br /> -123.456 ("C3", ja-JP) -> -¥123.456|
|"D" veya "d"|Ondalık|Sonuç: İsteğe bağlı eksi işaretli tamsayı basamaklar.<br /><br /> Desteklenen: sadece integral türleri.<br /><br /> Duyarlık belirtici: Minimum basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: En az gereken basamak sayısı.<br /><br /> Daha fazla bilgi: [Ondalık("D") Biçim Belirtici](#DFormatString).|1234 ("D") -> 1234<br /><br /> -1234 ("D6") -> -001234|
|"E" ya da "e"|Üstsel (bilimsel)|Sonuç: Üstel simgeleme.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: 6.<br /><br /> Daha fazla bilgi: [Üstel ("E") Biçim Belirtici](#EFormatString).|1052.0329112756 ("E", en-ABD) -> 1,052033E+003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1,052033e+003<br /><br /> -1052.0329112756 ("e2", en-ABD) -> -1.05e+003<br /><br /> -1052.0329112756 ("E2", fr-FR) -> -1,05E+003|
|"F" ya da "f"|Sabit nokta|Sonuç: İsteğe bağlı eksi işaretli tamsayı ve ondalık basamaklar.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Ondalık basamak sayısı.<br /><br /> Varsayılan kesinlik belirtici: <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>Tanımlanır.<br /><br /> Daha fazla bilgi: [Sabit Nokta ("F") Biçim Belirtici](#FFormatString).|1234.567 ("F", en-ABD) -> 1234,57<br /><br /> 1234.567 ("F", de-DE) -> 1234,57<br /><br /> 1234 ("F1", en-ABD) -> 1234,0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234,56 ("F4", en-ABD) -> -1234,5600<br /><br /> -1234,56 ("F4", de-DE) -> -1234,5600|
|"G" ya da "g"|Genel|Sonuç: Sabit nokta lı veya bilimsel gösterimin daha kompakt hale ilmesi.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Anlamlı basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: Sayısal türe bağlıdır.<br /><br /> Daha fazla bilgi: [Genel ("G") Biçim Belirtici](#GFormatString).|-123.456 ("G", en-ABD) -> -123.456<br /><br /> -123.456 ("G", sv-SE) -> -123.456<br /><br /> 123.4546 ("G4", en-ABD) -> 123,5<br /><br /> 123.4546 ("G4", sv-SE) -> 123,5<br /><br /> -1.234567890e-25 ("G", en-ABD) -> -1,23456789E-25<br /><br /> -1.234567890e-25 ("G", sv-SE) -> -1,23456789E-25|
|"N" ya da "n"|Sayı|Sonuç: Integral ve ondalık basamaklar, grup ayırıcılar ve isteğe bağlı eksi işaretli ondalık ayırıcı.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: İstenen ondalık basamak sayısı.<br /><br /> Varsayılan kesinlik belirtici: <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>Tanımlanır.<br /><br /> Daha fazla bilgi: [Sayısal ("N") Biçim Belirtici](#NFormatString).|1234.567 ("N", en-ABD) -> 1.234,57<br /><br /> 1234.567 ("N", ru-RU) -> 1 234,57<br /><br /> 1234 ("N1", en-ABD) -> 1.234,0<br /><br /> 1234 ("N1", ru-RU) -> 1 234,0<br /><br /> -1234,56 ("N3", en-ABD) -> -1.234.560<br /><br /> -1234,56 ("N3", ru-RU) -> -1 234,560|
|"P" ya da "p"|Yüzde|Sonuç: Sayı 100 ile çarpılır ve yüzde simgesi ile görüntülenir.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: İstenen ondalık basamak sayısı.<br /><br /> Varsayılan kesinlik belirtici: <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType>Tanımlanır.<br /><br /> Daha fazla bilgi: [Yüzde ("P") Biçim Belirtici](#PFormatString).|1 ("P", en-US) -> 100,00 %<br /><br /> 1 ("P", fr-FR) -> % 100,00<br /><br /> -0.39678 ("P1", en-ABD) -> -39.7 %<br /><br /> -0,39678 ("P1", fr-FR) -> -39,7 %|
|"R" ya da "r"|Gidiş|Sonuç: Aynı numaraya gidiş dönüş yapabilen bir dize.<br /><br /> Tarafından desteklenen: <xref:System.Single> <xref:System.Double>, <xref:System.Numerics.BigInteger>, ve .<br /><br /> Not: Yalnızca <xref:System.Numerics.BigInteger> tür için önerilir. Türleri <xref:System.Double> için "G17" kullanın; türleri <xref:System.Single> için "G9" kullanın. <br> Duyarlık belirtici: Yoksayıldı.<br /><br /> Daha fazla bilgi: [Gidiş-Dönüş ("R") Format Belirtileyici](#RFormatString).|123456789.12345678 (R) -> 123456789,12345678<br /><br /> -1234567890.12345678 (R) -> -1234567890.1234567|
|"X" ya da "x"|Onaltılık|Sonuç: Bir onaltılık dize.<br /><br /> Desteklenen: sadece integral türleri.<br /><br /> Duyarlık belirtici: Sonuç dizesindeki basamak sayısı.<br /><br /> Daha fazla bilgi: [HexaDecimal ("X") Biçim Belirtici](#XFormatString).|255 ("X") -> FF<br /><br /> -1 ("x") -> ff<br /><br /> 255 ("x4") -> 00ff<br /><br /> -1 ("X4") -> 00FF|
|Başka bir tek karakter|Bilinmeyen tanımlayıcı|Sonuç: Çalışma <xref:System.FormatException> zamanında bir atar.||

<a name="Using"></a>

## <a name="using-standard-numeric-format-strings"></a>Standart Sayısal Biçim Dizeleri Kullanma

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Standart bir sayısal biçimli dize, şu iki yoldan biriyle sayısal bir değerin biçimlendirmesini tanımlamak için kullanılabilir:

- `format` Parametresi olan `ToString` yöntemin aşırı yüklenmesine geçirilebilir. Aşağıdaki örnek, geçerli kültürde (bu durumda, en-ABD kültürü) bir para birimi dizeolarak sayısal bir değer biçimlendirin.

  [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
  [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]

- Bu gibi yöntemlerle `formatString` kullanılan bir biçim öğesinde bağımsız <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>değişken <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>olarak sağlanabilir , , ve . Daha fazla bilgi için [Bkz. Bileşik Biçimlendirme.](../../../docs/standard/base-types/composite-formatting.md) Aşağıdaki örnek, bir dizeye bir para birimi değeri eklemek için bir biçim öğesi kullanmaktadır.

  [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
  [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]

  İsteğe bağlı olarak, `alignment` sayısal alanın genişliğini ve değerinin sağ veya sol ayarı olup olmadığını belirtmek için bir bağımsız değişken sağlayabilirsiniz. Aşağıdaki örnek, 28 karakterlik bir alanda para birimi değerini sola hizalar ve 14 karakterlik bir alanda para birimi değerini sağa hizalar.

  [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
  [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]

- Enterpolasyonlu bir `formatString` dize bir enterpolasyonlu ifade öğesinde bağımsız değişken olarak sağlanabilir. Daha fazla bilgi için C# başvurusundastring [enterpolasyon](../../csharp/language-reference/tokens/interpolated.md) konusuna veya Visual Basic başvurusundaki [Enterpolasyonlu dizeleri](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) konusuna bakın.

Aşağıdaki bölümlerde her standart sayısal biçim dizesi hakkında ayrıntılı bilgi sağlanmaktadır.

<a name="CFormatString"></a>

## <a name="the-currency-c-format-specifier"></a>Para Birimi ("C") Biçim Belirleyicisi

"C" (ya da para birimi) biçim belirticisi, bir sayıyı para birimi tutarını gösteren bir dizeye dönüştürür. Duyarlık belirtici, sonuç dizesindeki istenen ondalık basamak sayısını gösterir. Hassas belirtici atlanırsa, varsayılan kesinlik <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> özellik tarafından tanımlanır.

Biçimlendirilecek değer, belirtilen veya varsayılan ondalık basamak sayısından fazlasına sahipse, sonuç dizesinde kesirli değer yuvarlanır. Belirtilen ondalık basamak sayısının sağındaki değer 5 veya daha büyükse, sonuç dizesindeki son basamak, sıfırdan uzağa yuvarlanır.

Sonuç dizesi, geçerli <xref:System.Globalization.NumberFormatInfo> nesnenin biçimlendirme bilgilerinden etkilenir. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> döndürülen dize biçimlendirmesini denetleyen özellikler listelenmektedir.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|Pozitif değerler için para birimi sembolünün yerleşimini tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|Negatif değerler için para birimi simgesinin yerleşimini tanımlar ve negatif işaretinin parantezler <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> veya özellik tarafından temsil edilip edilemeyeceğini belirtir.|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Parantez kullanılmadığını gösteriyorsa <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> kullanılan negatif işareti tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|Para birimi sembolünü tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|Para birimi değerindeki varsayılan ondalık basamak sayısını tanımlar. B değeri hassasiyet belirleyici kullanılarak geçersiz kılınabilir.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|Tamsayı ve ondalık basamakları ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|Tam sayı gruplarını ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|Bir grup içinde görüntülenen tamsayı basamak sayısını tanımlar.|

Aşağıdaki örnek, para <xref:System.Double> birimi biçimi belirtimi ile bir değeri biçimlendiriyor:

[!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
[!code-csharp[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
[!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]

[Tabloya geri dön](#table)

<a name="DFormatString"></a>

## <a name="the-decimal-d-format-specifier"></a>Ondalık ("D") Biçim Belirleyicisi

"D" (veya ondalık) biçim belirticisi, sayıyı, sayı negatifse eksi işaretiyle önekli bir ondalık basamaklı (0-9) bir dizeye dönüştürür. Bu biçim yalnızca tam sayı türleri için desteklenir.

Duyarlık belirtici, sonuç dizesindeki istenen minimum basamak sayısını gösterir. Gerekirse, duyarlık belirtici tarafından verilen basamak sayısını üretmek için sayının sol tarafı sıfırlarla doldurulur Bir duyarlık belirtici belirtilmezse varsayılan, başta sıfır bulunmadan tamsayıyı temsil etmek için gerekli minimum değerdir.

Sonuç dizesi, geçerli <xref:System.Globalization.NumberFormatInfo> nesnenin biçimlendirme bilgilerinden etkilenir. Aşağıdaki tabloda gösterildiği gibi tek bir özellik, sonuç dizesinin biçimlendirmesini etkiler.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|

Aşağıdaki örnek, ondalık biçim belirteci ile bir <xref:System.Int32> değeri biçimlendirin.

[!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
[!code-csharp-interactive[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
[!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]

[Tabloya geri dön](#table)

<a name="EFormatString"></a>

## <a name="the-exponential-e-format-specifier"></a>Üstel ("E") Biçim Belirleyicisi

Üstel ("E") biçim belirteci bir sayıyı "-d.ddd...E + ggg" veya "-d.ddd...e+ddd" biçiminde bir dizeye dönüştürür; burada her "d" bir basamağı (0-9) gösterir. Sayı negatifse, dize eksi işaretiyle başlar. Ondalık işaretinden önce her zaman tam bir basamak gelir.

Duyarlık belirtici, ondalık noktasından sonraki istenen basamak sayısını gösterir. Duyarlık belirtici atlanırsa, ondalık işaretinden sonra varsayılan olarak altı basamak kullanılır.

Biçim belirticisinin durumu üsse "E" veya "e" önekinin getirilip getirilmeyeceğini gösterir. Üs her zaman bir artı veya eksi işareti ile en az üç basamaktan oluşur. Üs bu minimum şartı karşılamak için gerekirse sıfırlarla doldurulur.

Sonuç dizesi, geçerli <xref:System.Globalization.NumberFormatInfo> nesnenin biçimlendirme bilgilerinden etkilenir. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> döndürülen dize biçimlendirmesini denetleyen özellikler listelenmektedir.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının hem katsayı hem de üs için negatif olduğunu belirten dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamağını, katsayıdaki ondalık basamaklardan ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Bir üssün pozitif olduğunu belirten dizeyi tanımlar.|

Aşağıdaki örnek, üstel biçim belirteci ile bir <xref:System.Double> değeri biçimlendirin:

[!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
[!code-csharp[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
[!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]

[Tabloya geri dön](#table)

<a name="FFormatString"></a>

## <a name="the-fixed-point-f-format-specifier"></a>Sabit Nokta ("F") Biçim Belirleyicisi

Sabit nokta ("F") biçim belirtici bir sayıyı "-ddd.ddd..." formu dizesine dönüştürür. her "d"nin bir basamak (0-9) gösterdiği yer. Sayı negatifse, dize eksi işaretiyle başlar.

Duyarlık belirtici, istenen ondalık basamak sayısını gösterir. Hassas belirtim atlanırsa, geçerli <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> özellik sayısal hassasiyeti sağlar.

Sonuç dizesi, geçerli <xref:System.Globalization.NumberFormatInfo> nesnenin biçimlendirme bilgilerinden etkilenir. Aşağıdaki tabloda, sonuç <xref:System.Globalization.NumberFormatInfo> dizesinin biçimlendirmesini denetleyen nesnenin özellikleri listelenmektedir.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamaklarını ondalık basamaklardan ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Varsayılan ondalık basamak sayısını tanımlar. B değeri hassasiyet belirleyici kullanılarak geçersiz kılınabilir.|

Aşağıdaki örnek, sabit <xref:System.Double> nokta <xref:System.Int32> biçimi belirticiile a ve bir değeri biçimlendirir:

[!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
[!code-csharp[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
[!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]

[Tabloya geri dön](#table)

<a name="GFormatString"></a>

## <a name="the-general-g-format-specifier"></a>Genel ("G") Biçim Belirleyicisi

Genel ("G") biçim belirtici, sayının türüne ve hassas bir belirtimin mevcut olup olmadığına bağlı olarak bir sayıyı sabit noktalı veya bilimsel gösterimin daha kompakt durumuna dönüştürür. Duyarlık belirtici, sonuç dizesindeki görünebilir maksimum anlamlı basamak sayısını tanımlar. Duyarlık belirtici atlanırsa veya sıfır olursa, sayının türü, aşağıdaki tabloda gösterildiği gibi varsayılan duyarlığı belirler.

|Sayısal tür|Varsayılan duyarlık|
|------------------|-----------------------|
|<xref:System.Byte> veya <xref:System.SByte>|3 basamak|
|<xref:System.Int16> veya <xref:System.UInt16>|5 basamaklı|
|<xref:System.Int32> veya <xref:System.UInt32>|10 basamak|
|<xref:System.Int64>|19 basamak|
|<xref:System.UInt64>|20 basamak|
|<xref:System.Numerics.BigInteger>|Sınırsız [("R"](#RFormatString)ile aynı)|
|<xref:System.Single>|7 basamak|
|<xref:System.Double>|15 basamak|
|<xref:System.Decimal>|29 basamak|

Sayı bilimsel gösterimde ifade edildiğinde elde edilen üs -5'ten büyükse ve duyarlık belirticiden küçükse sabit noktalı gösterim kullanılır; aksi takdirde bilimsel gösterim kullanılır. Sonuç gerekirse bir ondalık noktası içerir ve ondalık noktadan sonra gelen sıfırlar atlanır. Duyarlık belirtici varsa ve sonuçtaki anlamlı basamak sayısı, belirtilen duyarlığı aşarsa, sondaki fazlalık basamaklar yuvarlama tarafından kaldırılır.

Ancak, sayı a <xref:System.Decimal> ise ve hassas belirtici atlanırsa, sabit nokta gösterimi her zaman kullanılır ve sondaki sıfırlar korunur.

Bilimsel gösterim kullanılırsa, biçim belirtici "G" olduğunda sonuçtaki üssün başına "E", biçim belirtici "g" olduğunda "e" eklenir. Üs, en az iki basamak içerir. Bu, üs değerinde en az üç basamak içeren üssel biçim belirleyici tarafından üretilen bilimsel gösterim biçiminden farklıdır.

Bir değerle kullanıldığında, <xref:System.Double> "G17" biçim belirticisi, orijinal <xref:System.Double> değerin başarılı bir şekilde gidiş-dönüşler olmasını sağlar. Bunun nedeni, <xref:System.Double> 17 önemli kesinlik basamağı veren bir`binary64`IEEE 754-2008 uyumlu çift duyarlıklı () kayan nokta numarasıdır. Bazı durumlarda "R" başarılı bir şekilde gidiş-dönüş çift duyarlıklı kayan nokta değerleri başarısız olduğundan, ["R" biçimlendirme belirtimi](#RFormatString)yerine kullanılmasını öneririz. Aşağıdaki örnek, böyle bir durumda göstermektedir.

[!code-csharp-interactive[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs#GeneralFormatSpecifier)]
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]

Bir <xref:System.Single> değerle kullanıldığında, "G9" biçim belirtici orijinal <xref:System.Single> değeri başarıyla yuvarlak yolculuklar sağlar. Bunun nedeni, <xref:System.Single> dokuz önemli kesinlik basamağına kadar veren`binary32`bir IEEE 754-2008 uyumlu tek duyarlıklı () kayan nokta numarasıdır. Performans nedenleriyle, ["R" biçim belirticisi](#RFormatString)yerine kullanılmasını öneririz.

Sonuç dizesi, geçerli <xref:System.Globalization.NumberFormatInfo> nesnenin biçimlendirme bilgilerinden etkilenir. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> sonuç dizesini biçimlendirmeyi denetleyen özellikler listelenmektedir.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamaklarını ondalık basamaklardan ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Bir üssün pozitif olduğunu belirten dizeyi tanımlar.|

Aşağıdaki örnek, çeşitli kayan nokta değerlerini genel biçim belirteçli biçimlendirerek biçimlendirin:

[!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
[!code-csharp[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
[!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]

[Tabloya geri dön](#table)

<a name="NFormatString"></a>

## <a name="the-numeric-n-format-specifier"></a>Sayısal ("N") Biçim Belirleyicisi

Sayısal ("N") biçim belirteci bir sayıyı "-d,ddd,ddd.ddd…" biçiminde bir dizeye dönüştürür; burada "-" gerekirse negatif bir sayı simgesini, "d" bir basamağı (0-9) gösterir, "," bir grup ayırıcıyı gösterir ve "." bir ondalık simgesini gösterir. Duyarlık belirtici, ondalık noktasından sonraki istenen basamak sayısını gösterir. Hassas belirtim atlanırsa, ondalık basamak sayısı geçerli <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> özellik tarafından tanımlanır.

Sonuç dizesi, geçerli <xref:System.Globalization.NumberFormatInfo> nesnenin biçimlendirme bilgilerinden etkilenir. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> sonuç dizesini biçimlendirmeyi denetleyen özellikler listelenmektedir.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|Negatif değerlerin biçimini tanımlar ve negatif işaretin parantezler veya <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> özellik tarafından temsil edilip edilemeyeceğini belirtir.|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|Grup ayırıcıları arasında görüntülenen tam sayı basamak sayısını tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|Tam sayı gruplarını ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı ve ondalık basamakları ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Varsayılan ondalık basamak sayısını tanımlar. B değeri bir hassasiyet belirleyici kullanılarak geçersiz kılınabilir.|

Aşağıdaki örnek, çeşitli kayan nokta değerlerini sayı biçimi belirtimi ile biçimlendirin:

[!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
[!code-csharp[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
[!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]

[Tabloya geri dön](#table)

<a name="PFormatString"></a>

## <a name="the-percent-p-format-specifier"></a>Yüzde ("p") Biçim Belirleyicisi

Yüzde ("P") biçim belirticisi sayıyı 100 ile çarpar ve yüzde temsil eden bir dizeye dönüştürür. Duyarlık belirtici, istenen ondalık basamak sayısını gösterir. Hassas belirtim atlanırsa, geçerli <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> özellik tarafından sağlanan varsayılan sayısal kesinlik kullanılır.

Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> döndürülen dize biçimlendirmesini denetleyen özellikler listelenmektedir.

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

Aşağıdaki örnek, kayan nokta değerlerini yüzde biçimi belirticiile biçimlendiriyor:

[!code-cpp[Formatting.Numeric.Standard#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#7)]
[!code-csharp[Formatting.Numeric.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#7)]
[!code-vb[Formatting.Numeric.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#7)]

[Tabloya geri dön](#table)

<a name="RFormatString"></a>

## <a name="the-round-trip-r-format-specifier"></a>Gidiş Dönüş ("R") Biçim Belirleyicisi

Gidiş-dönüş ("R") biçim belirtici, dize dönüştürülen sayısal bir değerin aynı sayısal değere geri ayrıştırılmasını sağlamaya çalışır. Bu biçim yalnızca <xref:System.Single>, , <xref:System.Double>ve <xref:System.Numerics.BigInteger> türleri için desteklenir.

Değerler <xref:System.Double> için, bazı durumlarda "R" biçim belirtimi, orijinal değeri başarıyla yuvarlama başarısız olur. Hem <xref:System.Double> hem <xref:System.Single> de değerler için, aynı zamanda nispeten düşük performans sunuyor. Bunun yerine, değerler için <xref:System.Double> ["G17"](#GFormatString) biçim belirticiyi ve ["G9"](#GFormatString) biçim belirticisini başarılı <xref:System.Single> bir şekilde gidiş-dönüş değerleri için kullanmanızı öneririz.

Bir <xref:System.Numerics.BigInteger> değer bu belirtim kullanılarak biçimlendirildiğinde, dize gösterimi <xref:System.Numerics.BigInteger> değerdeki tüm önemli basamakları içerir.

Bir duyarlık belirtici ekleyebilirsiniz, ancak bu yoksayılır. Bu belirleyici kullanırken gidiş dönüşlere duyarlılık üzerinde öncelik verilir.
Sonuç dizesi, geçerli <xref:System.Globalization.NumberFormatInfo> nesnenin biçimlendirme bilgilerinden etkilenir. Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> sonuç dizesini biçimlendirmeyi denetleyen özellikler listelenmektedir.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamaklarını ondalık basamaklardan ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Bir üssün pozitif olduğunu belirten dizeyi tanımlar.|

Aşağıdaki örnek, gidiş-dönüş biçimlendirmesi ile bir <xref:System.Numerics.BigInteger> değeri biçimlendiriyor.

[!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
[!code-csharp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
[!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]

> [!IMPORTANT]
> Bazı durumlarda, <xref:System.Double> "R" standart sayısal biçim dizesi ile biçimlendirilmiş değerler, anahtarlar `/platform:x64` kullanılarak `/platform:anycpu` derlenmişse ve 64 bit sistemlerde çalıştırılırsa, başarılı bir şekilde gidiş-dönüş yapmaz. Daha fazla bilgi için aşağıdaki paragrafa bakın.

"R" standart <xref:System.Double> sayısal biçim dizesi ile biçimlendirilmiş değerler sorununu çözebilmek için, "G17" standart sayısal biçim dizesini kullanarak <xref:System.Double> derleyip 64 bit sistemlerde çalıştırılırsa `/platform:x64` `/platform:anycpu` başarılı bir şekilde yuvarlama değil. Aşağıdaki örnekte, "R" biçimli <xref:System.Double> dize, gidiş-dönüş başarıyla olmayan bir değere sahip dir ve orijinal değeri başarılı bir şekilde yuvarlamak için "G17" biçim dizesini kullanır:

[!code-csharp[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#RoundTrip)]
[!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]

[Tabloya geri dön](#table)

<a name="XFormatString"></a>

## <a name="the-hexadecimal-x-format-specifier"></a>Onaltılı ("X") Biçim Belirleyicisi

("X") onaltılı biçim belirticisi bir sayıyı onaltı basamaklı bir dizeye dönüştürür. Biçim belirticisinin durumu, 9'dan büyük onaltılık basamak için büyük veya küçük harf kullanılıp kullanılmayacağını belirtir. Örneğin, "ABCDEF" üretmek için "X" ve "abcdef" üretmek için "x" kullanın. Bu biçim yalnızca tam sayı türleri için desteklenir.

Duyarlık belirtici, sonuç dizesindeki istenen minimum basamak sayısını gösterir. Gerekirse, duyarlık belirtici tarafından verilen basamak sayısını üretmek için sayının sol tarafı sıfırlarla doldurulur

Sonuç dizesi geçerli <xref:System.Globalization.NumberFormatInfo> nesnenin biçimlendirme bilgilerinden etkilenmez.

Aşağıdaki örnek, <xref:System.Int32> değerleri hexadecimal format belirtimi ile biçimlendirin.

[!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
[!code-csharp-interactive[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
[!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]

[Tabloya geri dön](#table)

<a name="NotesStandardFormatting"></a>

## <a name="notes"></a>Notlar

### <a name="control-panel-settings"></a>Denetim Masası Ayarları

Denetim Masası'ndaki **Bölgesel ve Dil Seçenekleri** öğesindeki ayarlar, bir biçimlendirme işlemi yle üretilen sonuç dizesini etkiler. Bu ayarlar, biçimlendirmeyi <xref:System.Globalization.NumberFormatInfo> yönetmek için kullanılan değerleri sağlayan geçerli iş parçacığı kültürüyle ilişkili nesneyi başlatmaya kullanılır. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.

<xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> Ayrıca, oluşturucu, geçerli sistem kültürüyle aynı <xref:System.Globalization.CultureInfo> kültürü temsil eden yeni bir nesneyi anında oluşturmak için kullanılırsa, Denetim Masası'ndaki Bölgesel ve <xref:System.Globalization.CultureInfo> Dil **Seçenekleri** öğesi tarafından oluşturulan özelleştirmeler yeni nesneye uygulanır. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Bir sistemin özelleştirmelerini yansıtmayan <xref:System.Globalization.CultureInfo> bir nesne oluşturmak için oluşturucuyu kullanabilirsiniz.

### <a name="numberformatinfo-properties"></a>NumberFormatInfo Özellikleri

Biçimlendirme, geçerli iş parçacığı <xref:System.Globalization.NumberFormatInfo> kültürü tarafından dolaylı olarak sağlanan geçerli nesnenin özelliklerinden <xref:System.IFormatProvider> veya biçimlendirmeyi çağıran yöntemin parametresi tarafından açıkça etkilenir. Bu <xref:System.Globalization.NumberFormatInfo> parametre için bir veya <xref:System.Globalization.CultureInfo> nesne belirtin.

> [!NOTE]
> Sayısal değerleri biçimlendirmede kullanılan desenleri veya dizeleri özelleştirme hakkında <xref:System.Globalization.NumberFormatInfo> bilgi için sınıf konusuna bakın.

### <a name="integral-and-floating-point-numeric-types"></a>Tam Sayı ve Kayan Nokta Sayısal Türleri

Bazı standart sayısal biçim belirticilerinin açıklamaları, ayrılmaz veya kayan nokta sayısal türlere başvurur. İntegral sayısal <xref:System.Byte>türleri <xref:System.SByte> <xref:System.Int16>, <xref:System.Int32> <xref:System.Int64>, <xref:System.UInt16> <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Numerics.BigInteger>, , , ve . Kayan nokta sayısal türleri , <xref:System.Decimal> <xref:System.Single>, <xref:System.Double>ve .

### <a name="floating-point-infinities-and-nan"></a>Kayan Nokta Sonsuz ve NaN

Biçim dizesinden bağımsız olarak, bir <xref:System.Single> <xref:System.Double> veya kayan nokta türünün değeri pozitif sonsuz, negatif sonsuz veya bir sayı (NaN) ise, biçimlendirilmiş dize <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>ilgili nin değeridir, <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>veya <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> geçerli <xref:System.Globalization.NumberFormatInfo> nesne tarafından belirtilen özelliktir.

## <a name="example"></a>Örnek

[!INCLUDE[interactive-note](~/includes/csharp-interactive-partial-note.md)]

Aşağıdaki örnek, bir tamsayı ve kayan nokta sayısal değerini ing-ABD kültürü ve tüm standart sayısal biçim tanımlayıcılarını kullanarak biçimlendirir. Bu örnek, iki özel sayısal<xref:System.Double> <xref:System.Int32>tip kullanır (ve ), ancak diğer sayısal baz<xref:System.Byte>tiplerinden herhangi biri için <xref:System.Numerics.BigInteger> <xref:System.Decimal>benzer <xref:System.Single>sonuçlar verir ( , , <xref:System.SByte> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.UInt16> <xref:System.UInt32> <xref:System.UInt64>, , , , , , ve .

[!code-csharp[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#FinalExample)]
[!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.NumberFormatInfo>
- [Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)
- [Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)
- [Örnek: .NET Core WinForms Biçimlendirme Programı (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Örnek: .NET Core WinForms Biçimlendirme Programı (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
