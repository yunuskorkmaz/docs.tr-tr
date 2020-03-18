---
title: Sayısal Dizeleri .NET'te ayrıştatma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parsing strings, numeric strings
- numeric strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
ms.assetid: e39324ee-72e5-42d4-a80d-bf3ee7fc6c59
ms.openlocfilehash: ac44282a06b2b3710d3a9e5390c7a514c1632c3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127593"
---
# <a name="parsing-numeric-strings-in-net"></a>Net'te Sayısal Dizeleri Ayrıştma
Tüm sayısal türlerin iki statik ayrışma `Parse` `TryParse`yöntemi vardır ve , bir sayının dize temsilini sayısal bir türe dönüştürmek için kullanabilirsiniz. Bu yöntemler, [Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md) ve Özel [Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)belgelenen biçim dizeleri kullanılarak üretilen dizeleri ayrıştamanızı sağlar. Varsayılan olarak, `Parse` `TryParse` ve yöntemler, integral ondalık basamaklar içeren dizeleri yalnızca gerçek sayılara başarıyla dönüştürebilir. İntegral ve kesirli ondalık basamaklar, grup ayırıcıları ve ondalık ayırıcıiçeren dizeleri kayan nokta değerlerine başarıyla dönüştürebilirler. Yöntem, `Parse` işlem başarısız olursa bir özel durum `TryParse` atar, yöntem ise . `false`  
  
## <a name="parsing-and-format-providers"></a>Ayrıştırma ve Biçim Sağlayıcıları  
 Genellikle, sayısal değerlerin dize gösterimleri kültüre göre farklılık gösterir. Para birimi sembolleri, grup (veya binlerce) ayırıcılar ve ondalık ayırıcılar gibi sayısal dizelerin öğeleri kültüre göre değişir. Ayrışdırma yöntemleri, bu kültüre özgü varyasyonları tanıyan bir biçim sağlayıcısını zımni veya açık olarak kullanır. Bir çağrıda `Parse` biçim `TryParse` sağlayıcısı belirtilmemişse, geçerli iş parçacığı kültürüyle ilişkili <xref:System.Globalization.NumberFormatInfo> biçim sağlayıcısı <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> (özellik tarafından döndürülen nesne) kullanılır.  
  
 Biçim sağlayıcısı bir <xref:System.IFormatProvider> uygulama tarafından temsil edilir. Bu arabirim, tek <xref:System.IFormatProvider.GetFormat%2A> bir parametresi biçimlendirilecek türü temsil eden bir nesne olan yöntem olan tek bir <xref:System.Type> üyeye sahiptir. Bu yöntem, biçimlendirme bilgileri sağlayan nesneyi döndürür. .NET, sayısal <xref:System.IFormatProvider> dizeleri ayrışdırma için aşağıdaki iki uygulamayı destekler:  
  
- Yöntem kültüre özgü <xref:System.Globalization.NumberFormatInfo> biçimlendirme bilgileri sağlayan bir nesne döndüren bir <xref:System.Globalization.CultureInfo> nesne. <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType>  
  
- Yöntemi kendi kendine dönen bir <xref:System.Globalization.NumberFormatInfo> nesne. <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType>  
  
 Aşağıdaki örnek, dizideki her dizeyi <xref:System.Double> bir değere dönüştürmeye çalışır. İlk olarak, İngilizce (ABD) kültürünün kurallarını yansıtan bir biçim sağlayıcısı kullanarak dizeyi ayrıştırmaya çalışır. Bu işlem bir <xref:System.FormatException>atar, fransız (Fransa) kültürünün kurallarını yansıtan bir biçim sağlayıcısı kullanarak dize ayrıştırmak için çalışır.  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Ayrıştırma ve NumberStyles Değerleri  
 Ayrıştırma işleminin işleyebileceği stil öğeleri (beyaz boşluk, grup ayırıcıları ve ondalık <xref:System.Globalization.NumberStyles> ayırıcılar gibi) bir numaralandırma değeriyle tanımlanır. Varsayılan olarak, tamsayı değerlerini temsil eden dizeleri yalnızca <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> sayısal basamak, satır ve sonda beyaz boşluk ve bir satır işareti izin verir değeri kullanılarak ayrıştırılır. Kayan nokta değerlerini temsil eden dizeleri <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> ve <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> değerlerin bir birleşimi kullanılarak ayrıştırılır; Bu bileşik stil, satır aralığı ve sondaki beyaz boşluk, bir satır işareti, ondalık ayırıcı, bir grup ayırıcı ve bir üs ile birlikte ondalık basamaklara izin verir. Bir `Parse` tür `TryParse` <xref:System.Globalization.NumberStyles> parametresi içeren veya yöntemin aşırı yüklenmesini çağırarak ve bir veya daha fazla <xref:System.Globalization.NumberStyles> bayrak ayarlayarak, ayrıştı işleminin başarılı olması için dizede bulunabilecek stil öğelerini denetleyebilirsiniz.  
  
 Örneğin, grup ayırıcısı içeren bir dize <xref:System.Int32> <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> yöntemi kullanılarak bir değere dönüştürülemez. Ancak, aşağıdaki örnekte gösterildiği <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> gibi, bayrağı kullanırsanız dönüştürme başarılı olur.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
> Ayrışdırma işlemi her zaman belirli bir kültürün biçimlendirme kurallarını kullanır. Bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.NumberFormatInfo> nesneyi geçirerek bir kültür belirtmezseniz, geçerli iş parçacığıyla ilişkili kültür kullanılır.  
  
 Aşağıdaki tabloda numaralandırma <xref:System.Globalization.NumberStyles> üyeleri listelanır ve ayrıştırma işlemi üzerindeki etkilerini açıklar.  
  
|NumberStyles değeri|Ayrışdırılacak dize üzerindeki etkisi|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Yalnızca sayısal basamaklara izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Ondalık ayırıcı ve kesirli basamakizin verilir. Tamsayı değerleri için, kesirli basamak olarak yalnızca sıfıra izin verilir. Geçerli ondalık ayırıcılar veya <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> özellik tarafından belirlenir.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|"E" veya "E" karakteri üstel gösterimi belirtmek için kullanılabilir. Ek <xref:System.Globalization.NumberStyles> bilgi için bkz.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Önde gelen beyaz alana izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|İzleyen beyaz alan izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Pozitif veya negatif bir işaret sayısal basamaklardan önce gelebilir.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Pozitif veya negatif bir işaret sayısal basamakları izleyebilir.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Paranteznegatif değerleri belirtmek için kullanılabilir.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Grup ayırıcıya izin verilir. Grup ayırıcı karakteri veya <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> özelliği tarafından belirlenir.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Para birimi simgesine izin verilir. Para birimi simgesi <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> özellik tarafından tanımlanır.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Ayrıştırılacak dize hexadecimal sayı olarak yorumlanır. Hexadecimal basamak0-9, A-F ve a-f içerebilir. Bu bayrak yalnızca tamsayı değerlerini ayrıştırmak için kullanılabilir.|  
  
 Buna ek <xref:System.Globalization.NumberStyles> olarak, numaralandırma, birden çok <xref:System.Globalization.NumberStyles> bayrak içeren aşağıdaki bileşik stilleri sağlar.  
  
|Bileşik NumberStyles değeri|Üyeleri içerir|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, ve <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> stilleri içerir. Bu, tamsayı değerlerini ayrıştırmak için kullanılan varsayılan stildir.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, , <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> , ve stilleri içerir.|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, , <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> ve stilleri içerir.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Hariç <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> tüm stilleri <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>içerir ve.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Hariç <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>tüm stilleri içerir.|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, ve <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> stilleri içerir.|  
  
## <a name="parsing-and-unicode-digits"></a>Ayrıştırma ve Unicode Rakamları  
 Unicode standardı, çeşitli yazı sistemlerindeki basamaklar için kod noktalarını tanımlar. Örneğin, U+0030'dan U+0039'a kadar olan kod noktaları 0'dan 9'a kadar olan temel Latin rakamlarını, U+09E6'dan U+09EF'e kadar olan kod noktaları 0'dan 9'a kadar Olan Bangla rakamlarını, U+FF10'dan U+FF19'a kadar olan kod noktaları 0'dan 9'a kadar olan tam genişlik rakamlarını temsil eder. Ancak, ayrışdırma yöntemleriyle tanınan tek sayısal basamak, U+0030 ile U+0039 kod noktalarıiçeren 0-9 temel Latin rakamlarıdır. Sayısal ayrıştırma yöntemi başka basamaklar içeren bir dize geçirilirse, yöntem bir <xref:System.FormatException>.  
  
 Aşağıdaki örnek, <xref:System.Int32.Parse%2A?displayProperty=nameWithType> farklı yazı sistemlerinde basamaklardan oluşan dizeleri ayrıştırmak için yöntemi kullanır. Örnekteki çıktının gösterdiği gibi, temel Latin basamaklarını ayrıştırma girişimi başarılı olur, ancak Tam genişlik, Arapça-Hint çesitli ve Bangla rakamlarını ayrıştırma girişimi başarısız olur.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.NumberStyles>
- [Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
