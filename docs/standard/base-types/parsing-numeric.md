---
title: .NET 'te sayısal dizeleri ayrıştırma
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
ms.openlocfilehash: 000419e63e86607cd76728ae6e15ac6cd67b87f4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277654"
---
# <a name="parsing-numeric-strings-in-net"></a>NET ' te sayısal dizeleri ayrıştırma
Tüm sayısal türlerin iki statik ayrıştırma yöntemi vardır `Parse` ve `TryParse` bir sayının dize gösterimini sayısal bir türe dönüştürmek için kullanabilirsiniz. Bu yöntemler, [Standart sayısal biçim dizeleri](standard-numeric-format-strings.md) ve [özel sayısal biçim dizeleri](custom-numeric-format-strings.md)içinde belgelenen biçim dizeleri kullanılarak üretilmiş dizeleri ayrıştıramanıza olanak sağlar. Varsayılan olarak, `Parse` ve `TryParse` yöntemleri yalnızca tamsayı değerlerine tam sayı ondalık basamakları içeren dizeleri dönüştürebilir. İntegral ve kesirli ondalık basamaklar, Grup ayırıcılar ve bir ondalık ayırıcısı içeren dizeleri kayan nokta değerlerine başarıyla dönüştürebilirler. Yöntemi, `Parse` işlem başarısız olursa bir özel durum oluşturur, ancak `TryParse` Yöntem döndürülür `false` .  
  
## <a name="parsing-and-format-providers"></a>Ayrıştırma ve Biçim Sağlayıcıları  
 Genellikle, sayısal değerlerin dize temsilleri kültüre göre farklılık gösterir. Para birimi sembolleri, Grup (veya binlik) ayırıcılar gibi sayısal dizelerin öğeleri ve tüm ondalık ayırıcıları kültüre göre farklılık gösterir. Yöntemleri ayrıştırarak, kültüre özgü bu çeşitlemeleri tanıyan bir biçim sağlayıcısını örtük veya açık olarak kullanın. Veya yöntemine yapılan bir çağrıda biçim sağlayıcısı belirtilmemişse `Parse` `TryParse` , geçerli iş parçacığı kültürü ( <xref:System.Globalization.NumberFormatInfo> özelliği tarafından döndürülen nesne) ile ilişkili biçim sağlayıcısı <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> kullanılır.  
  
 Biçim sağlayıcısı bir uygulamayla temsil edilir <xref:System.IFormatProvider> . Bu arabirim tek bir üyeye sahiptir, <xref:System.IFormatProvider.GetFormat%2A> tek parametresi, <xref:System.Type> biçimlendirilecek türü temsil eden bir nesnedir. Bu yöntem, biçimlendirme bilgileri sağlayan nesnesini döndürür. .NET, <xref:System.IFormatProvider> sayısal dizeleri ayrıştırmak için aşağıdaki iki uygulama destekler:  
  
- <xref:System.Globalization.CultureInfo> <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> Metodu <xref:System.Globalization.NumberFormatInfo> kültüre özgü biçimlendirme bilgileri sağlayan bir nesne döndüren nesne.  
  
- <xref:System.Globalization.NumberFormatInfo> <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> Yöntemi kendisini döndüren nesne.  
  
 Aşağıdaki örnek, bir dizideki her dizeyi bir değere dönüştürmeye çalışır <xref:System.Double> . Önce, Ingilizce (Birleşik Devletler) kültürün kurallarını yansıtan bir biçim sağlayıcısı kullanarak dizeyi ayrıştırmaya çalışır. Bu işlem bir oluşturursa <xref:System.FormatException> , Fransızca (Fransa) kültürünün kurallarını yansıtan bir biçim sağlayıcısı kullanarak dizeyi ayrıştırmaya çalışır.  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Ayrıştırma ve NumberStyles Değerleri  
 Ayrıştırma işleminin işleyebileceği stil öğeleri (beyaz boşluk, Grup ayırıcıları ve ondalık ayırıcı gibi) bir <xref:System.Globalization.NumberStyles> numaralandırma değeri tarafından tanımlanır. Varsayılan olarak, tam sayı değerlerini temsil eden dizeler değeri kullanılarak ayrıştırılır <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> ve yalnızca sayısal basamaklar, baştaki ve sondaki boşluk ve baştaki işaretine izin verir. Kayan nokta değerlerini temsil eden dizeler ve değerlerinin bir birleşimi kullanılarak ayrıştırılır <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> ; Bu bileşik stil, baştaki ve sondaki boşluk, baştaki işareti, ondalık ayırıcısı, Grup ayırıcısı ve üs ile birlikte ondalık basamakların kullanılmasına izin verir. `Parse` `TryParse` Türünde bir parametre içeren <xref:System.Globalization.NumberStyles> ve bir veya daha fazla bayrak ayarlayarak ya da yönteminin bir aşırı yüklemesini çağırarak <xref:System.Globalization.NumberStyles> , ayrıştırma işleminin başarılı olması için dizedeki mevcut olabilecek stil öğelerini kontrol edebilirsiniz.  
  
 Örneğin, bir grup ayırıcısı içeren bir dize <xref:System.Int32> , yöntemi kullanılarak bir değere dönüştürülemez <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> . Ancak, aşağıdaki örnekte gösterildiği gibi bayrağını kullanırsanız dönüştürme işlemi başarılı olur <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> .  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
> Ayrıştırma işlemi her zaman belirli bir kültürün biçimlendirme kurallarını kullanır. Bir veya nesnesi geçirerek bir kültür belirtmezseniz <xref:System.Globalization.CultureInfo> <xref:System.Globalization.NumberFormatInfo> , geçerli iş parçacığıyla ilişkili kültür kullanılır.  
  
 Aşağıdaki tablo, numaralandırmanın üyelerini listeler <xref:System.Globalization.NumberStyles> ve Ayrıştırma işleminde sahip oldukları etkiyi açıklar.  
  
|NumberStyles değeri|Ayrıştırılacak dize üzerinde etki|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Yalnızca sayısal sayılara izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Ondalık ayırıcıya ve kesirli basamaklar izin verilir. Tamsayı değerleri için kesirli basamak olarak yalnızca sıfıra izin verilir. Geçerli Ondalık ayırıcılar veya özelliği tarafından belirlenir <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> .|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|Üstel gösterimi göstermek için "e" veya "E" karakteri kullanılabilir. Daha <xref:System.Globalization.NumberStyles> fazla bilgi için bkz..|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Baştaki boşluk kullanılmasına izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Sondaki boşluğa izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Pozitif veya negatif bir işaret, sayısal rakamlardan önce olabilir.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Pozitif veya negatif bir işaret, sayısal basamakları izleyebilir.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Parantez, negatif değerleri belirtmek için kullanılabilir.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Grup ayırıcısına izin verilir. Grup ayırıcı karakteri <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> veya özelliği tarafından belirlenir <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> .|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Para birimi simgesine izin verilir. Para birimi sembolü, özelliği tarafından tanımlanır <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> .|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Ayrıştırılacak dize, onaltılık bir sayı olarak yorumlanır. Bu, 0-9, A-F ve A-f onaltılı rakamlarını içerebilir. Bu bayrak yalnızca tamsayı değerlerini ayrıştırmak için kullanılabilir.|  
  
 Ayrıca, <xref:System.Globalization.NumberStyles> sabit listesi birden çok bayrak içeren aşağıdaki bileşik stilleri sağlar <xref:System.Globalization.NumberStyles> .  
  
|Bileşik NumberStyles değeri|Üyeleri içerir|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> Ve <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> stillerini içerir. Bu, tamsayı değerlerini ayrıştırmak için kullanılan varsayılan stildir.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|,,,, <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType> Ve stillerini içerir <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> .|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|,, <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType> , <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType> Ve <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> stillerini içerir.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Ve dışındaki tüm stilleri <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> içerir <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> .|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Dışındaki tüm stilleri içerir <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> .|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> Ve <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> stillerini içerir.|  
  
## <a name="parsing-and-unicode-digits"></a>Ayrıştırma ve Unicode Rakamları  
 Unicode standart, çeşitli yazma sistemlerindeki basamakların kod noktalarını tanımlar. Örneğin, U + 0030 ile U + 0039 arasındaki kod noktaları, 0 ile 9 arasındaki temel Latin rakamlarını temsil ediyorsa, U + 09E6 ' dan U + 09EF 'e ait kod noktaları, 0 ile 9 arasındaki tam sayı rakamlarını temsil eder ve U + FF10 arasındaki kod noktaları, 0 ile 9 arasında tam sayı basamaklarını temsil eder. Ancak, Yöntemler ayrıştırılırken tanınan tek sayısal basamaklar, U + 0030 ile U + 0039 arasında kod noktalarıyla 0-9 temel Latin rakamları. Bir sayısal ayrıştırma yöntemi başka basamaklar içeren bir dize geçirtiyse, yöntem bir oluşturur <xref:System.FormatException> .  
  
 Aşağıdaki örnek, <xref:System.Int32.Parse%2A?displayProperty=nameWithType> farklı yazma sistemlerindeki rakamlardan oluşan dizeleri ayrıştırmak için yöntemini kullanır. Örnekteki Çıktının gösterdiği gibi, temel Latin rakamlarını Ayrıştırma girişimi başarılı olur, ancak tam genişlikli, Arapça Hintçe ve Bangla rakamlarını Ayrıştırma girişimi başarısız olur.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.NumberStyles>
- [Dizeleri Ayrıştırma](parsing-strings.md)
- [Biçimlendirme Türleri](formatting-types.md)
