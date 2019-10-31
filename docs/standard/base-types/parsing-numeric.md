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
ms.openlocfilehash: ac44282a06b2b3710d3a9e5390c7a514c1632c3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127593"
---
# <a name="parsing-numeric-strings-in-net"></a>NET ' te sayısal dizeleri ayrıştırma
Tüm sayısal türler, bir sayının dize gösterimini sayısal bir türe dönüştürmek için kullanabileceğiniz iki statik ayrıştırma yöntemine sahiptir `Parse` ve `TryParse`. Bu yöntemler, [Standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md) ve [özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)içinde belgelenen biçim dizeleri kullanılarak üretilmiş dizeleri ayrıştıramanıza olanak sağlar. Varsayılan olarak, `Parse` ve `TryParse` yöntemleri yalnızca tamsayı değerlerine tam sayı ondalık basamakları içeren dizeleri dönüştürebilir. İntegral ve kesirli ondalık basamaklar, Grup ayırıcılar ve bir ondalık ayırıcısı içeren dizeleri kayan nokta değerlerine başarıyla dönüştürebilirler. `Parse` yöntemi, işlem başarısız olursa bir özel durum oluşturur, ancak `TryParse` yöntemi `false`döndürür.  
  
## <a name="parsing-and-format-providers"></a>Ayrıştırma ve Biçim Sağlayıcıları  
 Genellikle, sayısal değerlerin dize temsilleri kültüre göre farklılık gösterir. Para birimi sembolleri, Grup (veya binlik) ayırıcılar gibi sayısal dizelerin öğeleri ve tüm ondalık ayırıcıları kültüre göre farklılık gösterir. Yöntemleri ayrıştırarak, kültüre özgü bu çeşitlemeleri tanıyan bir biçim sağlayıcısını örtük veya açık olarak kullanın. `Parse` veya `TryParse` yöntemine yapılan çağrıda biçim sağlayıcısı belirtilmemişse, geçerli iş parçacığı kültürü (<xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Globalization.NumberFormatInfo> nesnesi) ile ilişkili biçim sağlayıcısı kullanılır.  
  
 Biçim sağlayıcısı <xref:System.IFormatProvider> bir uygulamayla temsil edilir. Bu arabirimin tek bir üyesi, tek parametresi biçimlendirilecek türü temsil eden bir <xref:System.Type> nesnesi olan <xref:System.IFormatProvider.GetFormat%2A> yöntemi vardır. Bu yöntem, biçimlendirme bilgileri sağlayan nesnesini döndürür. .NET, sayısal dizeleri ayrıştırmak için aşağıdaki iki <xref:System.IFormatProvider> uygulaması destekler:  
  
- <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> yöntemi kültüre özgü biçimlendirme bilgileri sağlayan bir <xref:System.Globalization.NumberFormatInfo> nesnesi döndüren <xref:System.Globalization.CultureInfo> nesnesi.  
  
- <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> yöntemi kendisini döndüren <xref:System.Globalization.NumberFormatInfo> nesnesi.  
  
 Aşağıdaki örnek, bir dizideki her dizeyi bir <xref:System.Double> değerine dönüştürmeye çalışır. Önce, Ingilizce (Birleşik Devletler) kültürün kurallarını yansıtan bir biçim sağlayıcısı kullanarak dizeyi ayrıştırmaya çalışır. Bu işlem bir <xref:System.FormatException>oluşturursa, Fransızca (Fransa) kültürünün kurallarını yansıtan bir biçim sağlayıcısı kullanarak dizeyi ayrıştırmaya çalışır.  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Ayrıştırma ve NumberStyles Değerleri  
 Ayrıştırma işleminin işleyebileceği stil öğeleri (boşluk, Grup ayırıcıları ve ondalık ayırıcı gibi) <xref:System.Globalization.NumberStyles> numaralandırma değeri tarafından tanımlanır. Varsayılan olarak, tam sayı değerlerini temsil eden dizeler, yalnızca sayısal basamağa, baştaki ve sondaki boşluğa ve baştaki bir işaretine izin veren <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> değeri kullanılarak ayrıştırılır. Kayan nokta değerlerini temsil eden dizeler <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> ve <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> değerlerinin bir birleşimi kullanılarak ayrıştırılır; Bu bileşik stil, baştaki ve sondaki boşluk, baştaki işareti, ondalık ayırıcısı, Grup ayırıcısı ve üs ile birlikte ondalık basamakların kullanılmasına izin verir. <xref:System.Globalization.NumberStyles> türünde bir parametre içeren ve bir veya daha fazla <xref:System.Globalization.NumberStyles> bayrağını ayarlayarak `Parse` veya `TryParse` yönteminin aşırı yüklemesini çağırarak, ayrıştırma işleminin başarılı olması için dizedeki mevcut olabilecek stil öğelerini kontrol edebilirsiniz.  
  
 Örneğin, bir grup ayırıcısı içeren bir dize, <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> yöntemi kullanılarak <xref:System.Int32> değerine dönüştürülemez. Ancak, aşağıdaki örnekte gösterildiği gibi <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> bayrağını kullanırsanız dönüştürme başarılı olur.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
> Ayrıştırma işlemi her zaman belirli bir kültürün biçimlendirme kurallarını kullanır. Bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.NumberFormatInfo> nesnesi geçirerek bir kültür belirtmezseniz, geçerli iş parçacığıyla ilişkili kültür kullanılır.  
  
 Aşağıdaki tablo <xref:System.Globalization.NumberStyles> numaralandırmanın üyelerini listeler ve Ayrıştırma işleminde sahip oldukları etkiyi açıklar.  
  
|NumberStyles değeri|Ayrıştırılacak dize üzerinde etki|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Yalnızca sayısal sayılara izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Ondalık ayırıcıya ve kesirli basamaklar izin verilir. Tamsayı değerleri için kesirli basamak olarak yalnızca sıfıra izin verilir. Geçerli Ondalık ayırıcılar <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> veya <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> özelliği tarafından belirlenir.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|Üstel gösterimi göstermek için "e" veya "E" karakteri kullanılabilir. Daha fazla bilgi için bkz. <xref:System.Globalization.NumberStyles>.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Baştaki boşluk kullanılmasına izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Sondaki boşluğa izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Pozitif veya negatif bir işaret, sayısal rakamlardan önce olabilir.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Pozitif veya negatif bir işaret, sayısal basamakları izleyebilir.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Parantez, negatif değerleri belirtmek için kullanılabilir.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Grup ayırıcısına izin verilir. Grup ayırıcı karakteri <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> veya <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> özelliği tarafından belirlenir.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Para birimi simgesine izin verilir. Para birimi simgesi <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> özelliği tarafından tanımlanır.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Ayrıştırılacak dize, onaltılık bir sayı olarak yorumlanır. Bu, 0-9, A-F ve A-f onaltılı rakamlarını içerebilir. Bu bayrak yalnızca tamsayı değerlerini ayrıştırmak için kullanılabilir.|  
  
 Ayrıca <xref:System.Globalization.NumberStyles> numaralandırması, birden çok <xref:System.Globalization.NumberStyles> bayrağı içeren aşağıdaki bileşik stilleri sağlar.  
  
|Bileşik NumberStyles değeri|Üyeleri içerir|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>ve <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> stillerini içerir. Bu, tamsayı değerlerini ayrıştırmak için kullanılan varsayılan stildir.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>ve <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> stillerini içerir.|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>ve <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> stillerini içerir.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> ve <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>hariç tüm stilleri içerir.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>dışındaki tüm stilleri içerir.|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>ve <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> stillerini içerir.|  
  
## <a name="parsing-and-unicode-digits"></a>Ayrıştırma ve Unicode Rakamları  
 Unicode standart, çeşitli yazma sistemlerindeki basamakların kod noktalarını tanımlar. Örneğin, U + 0030 ile U + 0039 arasındaki kod noktaları, 0 ile 9 arasındaki temel Latin rakamlarını temsil ediyorsa, U + 09E6 ' dan U + 09EF 'e ait kod noktaları, 0 ile 9 arasındaki tam sayı rakamlarını temsil eder ve U + FF10 arasındaki kod noktaları, 0 ile 9 arasında tam sayı basamaklarını temsil eder. Ancak, Yöntemler ayrıştırılırken tanınan tek sayısal basamaklar, U + 0030 ile U + 0039 arasında kod noktalarıyla 0-9 temel Latin rakamları. Sayısal bir ayrıştırma yöntemi başka basamaklar içeren bir dize geçirtiyse, yöntem bir <xref:System.FormatException>oluşturur.  
  
 Aşağıdaki örnek, farklı yazma sistemlerindeki rakamlardan oluşan dizeleri ayrıştırmak için <xref:System.Int32.Parse%2A?displayProperty=nameWithType> yöntemini kullanır. Örnekteki Çıktının gösterdiği gibi, temel Latin rakamlarını Ayrıştırma girişimi başarılı olur, ancak tam genişlikli, Arapça Hintçe ve Bangla rakamlarını Ayrıştırma girişimi başarısız olur.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.NumberStyles>
- [Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
