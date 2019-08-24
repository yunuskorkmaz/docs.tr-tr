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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8903d0443594885b3b0e8cca716eda8177c60cca
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988817"
---
# <a name="parsing-numeric-strings-in-net"></a>NET ' te sayısal dizeleri ayrıştırma
Tüm sayısal türlerin iki statik ayrıştırma yöntemi `Parse` vardır ve `TryParse`bir sayının dize gösterimini sayısal bir türe dönüştürmek için kullanabilirsiniz. Bu yöntemler, [Standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md) ve [özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)içinde belgelenen biçim dizeleri kullanılarak üretilmiş dizeleri ayrıştıramanıza olanak sağlar. Varsayılan `Parse` olarak, ve `TryParse` yöntemleri yalnızca tamsayı değerlerine tam sayı ondalık basamakları içeren dizeleri dönüştürebilir. İntegral ve kesirli ondalık basamaklar, Grup ayırıcılar ve bir ondalık ayırıcısı içeren dizeleri kayan nokta değerlerine başarıyla dönüştürebilirler. Yöntemi, işlem başarısız olursa bir özel durum oluşturur, `TryParse` ancak yöntem döndürülür `false`. `Parse`  
  
## <a name="parsing-and-format-providers"></a>Ayrıştırma ve Biçim Sağlayıcıları  
 Genellikle, sayısal değerlerin dize temsilleri kültüre göre farklılık gösterir. Para birimi sembolleri, Grup (veya binlik) ayırıcılar gibi sayısal dizelerin öğeleri ve tüm ondalık ayırıcıları kültüre göre farklılık gösterir. Yöntemleri ayrıştırarak, kültüre özgü bu çeşitlemeleri tanıyan bir biçim sağlayıcısını örtük veya açık olarak kullanın. `Parse` Veya <xref:System.Globalization.NumberFormatInfo> <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> yöntemine yapılan bir çağrıda biçim sağlayıcısı belirtilmemişse, geçerli iş parçacığı kültürü (özelliği tarafından döndürülen nesne) ile ilişkili biçim sağlayıcısı kullanılır. `TryParse`  
  
 Biçim sağlayıcısı bir <xref:System.IFormatProvider> uygulamayla temsil edilir. Bu arabirim tek bir üyeye <xref:System.IFormatProvider.GetFormat%2A> sahiptir, tek parametresi, biçimlendirilecek türü temsil eden bir <xref:System.Type> nesnedir. Bu yöntem, biçimlendirme bilgileri sağlayan nesnesini döndürür. .Net, sayısal dizeleri ayrıştırmak <xref:System.IFormatProvider> için aşağıdaki iki uygulama destekler:  
  
- Metodu kültüre özgü biçimlendirme bilgileri sağlayan <xref:System.Globalization.NumberFormatInfo> bir nesne döndüren nesne. <xref:System.Globalization.CultureInfo> <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType>  
  
- <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> Yöntemi kendisini döndüren nesne. <xref:System.Globalization.NumberFormatInfo>  
  
 Aşağıdaki örnek, bir dizideki her dizeyi bir <xref:System.Double> değere dönüştürmeye çalışır. Önce, Ingilizce (Birleşik Devletler) kültürün kurallarını yansıtan bir biçim sağlayıcısı kullanarak dizeyi ayrıştırmaya çalışır. Bu işlem bir <xref:System.FormatException>oluşturursa, Fransızca (Fransa) kültürünün kurallarını yansıtan bir biçim sağlayıcısı kullanarak dizeyi ayrıştırmaya çalışır.  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Ayrıştırma ve NumberStyles Değerleri  
 Ayrıştırma işleminin işleyebileceği stil öğeleri (beyaz boşluk, Grup ayırıcıları ve ondalık ayırıcı gibi) bir <xref:System.Globalization.NumberStyles> numaralandırma değeri tarafından tanımlanır. Varsayılan olarak, tam sayı değerlerini temsil eden dizeler <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> değeri kullanılarak ayrıştırılır ve yalnızca sayısal basamaklar, baştaki ve sondaki boşluk ve baştaki işaretine izin verir. Kayan nokta değerlerini temsil eden dizeler ve <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> değerlerinin bir birleşimi kullanılarak ayrıştırılır; Bu bileşik stil, baştaki ve sondaki boşluk, baştaki işareti, ondalık ayırıcısı, bir grup ile birlikte ondalık basamağa izin verir ayırıcı ve üs. Türünde `Parse` `TryParse` <xref:System.Globalization.NumberStyles> bir parametreiçerenvebirveyadahafazlabayrakayarlayarakyadayöntemininbiraşırıyüklemesiniçağırarak,ayrıştırmaişleminindizeiçindemevcutolabilecekstilöğelerinidenetimaltınaalabilirsiniz<xref:System.Globalization.NumberStyles> başarıya.  
  
 Örneğin, bir grup ayırıcısı içeren bir dize, <xref:System.Int32> <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> yöntemi kullanılarak bir değere dönüştürülemez. Ancak, aşağıdaki örnekte gösterildiği gibi <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> bayrağını kullanırsanız dönüştürme işlemi başarılı olur.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
> Ayrıştırma işlemi her zaman belirli bir kültürün biçimlendirme kurallarını kullanır. Bir <xref:System.Globalization.CultureInfo> veya<xref:System.Globalization.NumberFormatInfo> nesnesi geçirerek bir kültür belirtmezseniz, geçerli iş parçacığıyla ilişkili kültür kullanılır.  
  
 Aşağıdaki tablo, <xref:System.Globalization.NumberStyles> numaralandırmanın üyelerini listeler ve Ayrıştırma işleminde sahip oldukları etkiyi açıklar.  
  
|NumberStyles değeri|Ayrıştırılacak dize üzerinde etki|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Yalnızca sayısal sayılara izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Ondalık ayırıcıya ve kesirli basamaklar izin verilir. Tamsayı değerleri için kesirli basamak olarak yalnızca sıfıra izin verilir. Geçerli Ondalık ayırıcılar <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> veya <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> özelliği tarafından belirlenir.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|Üstel gösterimi göstermek için "e" veya "E" karakteri kullanılabilir. Daha <xref:System.Globalization.NumberStyles> fazla bilgi için bkz.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Baştaki boşluk kullanılmasına izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Sondaki boşluğa izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Pozitif veya negatif bir işaret, sayısal rakamlardan önce olabilir.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Pozitif veya negatif bir işaret, sayısal basamakları izleyebilir.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Parantez, negatif değerleri belirtmek için kullanılabilir.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Grup ayırıcısına izin verilir. Grup ayırıcı karakteri <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> veya <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> özelliği tarafından belirlenir.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Para birimi simgesine izin verilir. Para birimi sembolü, <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> özelliği tarafından tanımlanır.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Ayrıştırılacak dize, onaltılık bir sayı olarak yorumlanır. Bu, 0-9, A-F ve A-f onaltılı rakamlarını içerebilir. Bu bayrak yalnızca tamsayı değerlerini ayrıştırmak için kullanılabilir.|  
  
 Ayrıca, <xref:System.Globalization.NumberStyles> sabit listesi birden çok <xref:System.Globalization.NumberStyles> bayrak içeren aşağıdaki bileşik stilleri sağlar.  
  
|Bileşik NumberStyles değeri|Üyeleri içerir|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType> ,<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>Ve stillerini<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> içerir. Bu, tamsayı değerlerini ayrıştırmak için kullanılan varsayılan stildir.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType> ,<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> ,,<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> , Ve stillerini içerir. <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, ,,<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>Ve stilleriniiçerir<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> . <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> Ve<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>dışındaki tüm stilleri içerir.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Dışındaki <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>tüm stilleri içerir.|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType> ,<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>Ve stillerini<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> içerir.|  
  
## <a name="parsing-and-unicode-digits"></a>Ayrıştırma ve Unicode Rakamları  
 Unicode standart, çeşitli yazma sistemlerindeki basamakların kod noktalarını tanımlar. Örneğin, U + 0030 ile U + 0039 arasındaki kod noktaları, 0 ile 9 arasındaki temel Latin rakamlarını temsil ediyorsa, U + 09E6 ' dan U + 09EF 'e ait kod noktaları, 0 ile 9 arasındaki tam sayı rakamlarını temsil eder ve U + FF10 arasındaki kod noktaları, 0 ile 9 arasında tam sayı basamaklarını temsil eder. Ancak, Yöntemler ayrıştırılırken tanınan tek sayısal basamaklar, U + 0030 ile U + 0039 arasında kod noktalarıyla 0-9 temel Latin rakamları. Bir sayısal ayrıştırma yöntemi başka basamaklar içeren bir dize geçirtiyse, yöntem bir <xref:System.FormatException>oluşturur.  
  
 Aşağıdaki örnek, farklı yazma <xref:System.Int32.Parse%2A?displayProperty=nameWithType> sistemlerindeki rakamlardan oluşan dizeleri ayrıştırmak için yöntemini kullanır. Örnekteki Çıktının gösterdiği gibi, temel Latin rakamlarını Ayrıştırma girişimi başarılı olur, ancak tam genişlikli, Arapça Hintçe ve Bangla rakamlarını Ayrıştırma girişimi başarısız olur.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.NumberStyles>
- [Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
