---
title: .NET sayısal dizeleri ayrıştırma
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
ms.openlocfilehash: 07ad8b278f6a44fce78bccc980acdc0dc93b1a7a
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48261465"
---
# <a name="parsing-numeric-strings-in-net"></a>NET sayısal dizeleri ayrıştırma
İki statik ayrıştırma yöntemlerinin, tüm sayısal türlerin sahip `Parse` ve `TryParse`, bir sayının dize gösterimini bir sayısal türe dönüştürmek için kullanabilirsiniz. Bu yöntemler konusunda belgelenen biçim dizelerini kullanarak üretilmiş olan dizeleri ayrıştırma sağlayan [standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md) ve [özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md). Varsayılan olarak, `Parse` ve `TryParse` yöntemleri yalnızca tamsayı değerleri için tam sayı ondalık basamak içeren dizeleri başarıyla dönüştürebilirsiniz. Bunlar, entegral ve kesirli ondalık basamak grubu ayırıcıları ve kayan nokta değerleri ondalık ayırıcı içeren dizeleri başarıyla dönüştürebilirsiniz. `Parse` Yöntemi bir özel durum oluşturursa işlem başarısız olursa, oysa `TryParse` yöntemi döndürür `false`.  
  
## <a name="parsing-and-format-providers"></a>Ayrıştırma ve Biçim Sağlayıcıları  
 Genellikle, sayısal değerlerinin dize temsillerini kültüre göre farklılık gösterir. Sayısal dizeler gibi para birimi sembolleri, grubuna (veya binlerce) ayırıcı ve ondalık ayırıcılar tüm öğelerin kültüre göre değişir. Yöntemleri ayrıştırma kültüre özgü bu farklılıkları tanıdığı bir biçim sağlayıcısı örtük veya açık olarak kullanın. Biçim sağlayıcısı yok çağrıda belirtilmezse `Parse` veya `TryParse` yöntem, geçerli iş parçacığı kültürüyle ilişkilendirilen biçim sağlayıcısı ( <xref:System.Globalization.NumberFormatInfo> tarafından döndürülen nesne <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> özelliği) kullanılır.  
  
 Bir biçim sağlayıcısı tarafından temsil edilen bir <xref:System.IFormatProvider> uygulaması. Bu arabirim bir tek üyeye sahip <xref:System.IFormatProvider.GetFormat%2A> yöntemi, tek bir parametre, bir <xref:System.Type> Biçimlendirilecek türünü temsil eden nesne. Bu yöntem, biçimlendirme bilgilerini sağlayan nesne döndürür. .NET destekleyen aşağıdaki iki <xref:System.IFormatProvider> sayısal dizeleri ayrıştırma için uygulamaları:  
  
-   A <xref:System.Globalization.CultureInfo> nesnesi <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> yöntemi döndürür bir <xref:System.Globalization.NumberFormatInfo> kültüre özgü biçimlendirme bilgileri sağlayan nesne.  
  
-   A <xref:System.Globalization.NumberFormatInfo> nesnesi <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> yöntemi kendisini döndürür.  
  
 Aşağıdaki örnekte, dizideki her dizeyi dönüştürecek dener bir <xref:System.Double> değeri. İngilizce (ABD) kültürünün kuralları yansıtan bir biçim sağlayıcısı kullanarak dizeyi ayrıştırmak ilk önce çalışır. Bu işlem oluşturursa bir <xref:System.FormatException>, Fransızca (Fransa) kültürü kurallarını yansıtan bir biçim sağlayıcısı kullanarak dizeyi ayrıştırmak çalışır.  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Ayrıştırma ve NumberStyles Değerleri  
 Ayrıştırma işleminin işleyebileceği stil öğelerini (örneğin, boşluk, Grup ayırıcı ve ondalık ayırıcı) tarafından tanımlanan bir <xref:System.Globalization.NumberStyles> numaralandırma değeri. Varsayılan olarak, tamsayı değerlerini temsil eden dizeleri kullanarak Ayrıştırılan <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> değeri yalnızca sayısal basamaklar, baştaki ve sondaki boşluk ve bir im izin verir. Kayan nokta değerlerini temsil eden dizeleri ayrıştırılmış bir birleşimi kullanılarak <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> ve <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> değerleri; baştaki ve sondaki boşluk, önde gelen işareti, ondalık ayırıcı, bir grup yanı sıra bu bileşik bir stili izinleri ondalık basamak ayırıcı ve bir üs. Bir aşırı yüklemesini çağırarak `Parse` veya `TryParse` türünde bir parametre içeren yöntem <xref:System.Globalization.NumberStyles> ve bir veya daha fazla ayar <xref:System.Globalization.NumberStyles> bayrakları, ayrıştırma işleminin için dizesinde mevcut olabilecek stil öğelerini denetleyebilirsiniz başarılı.  
  
 Örneğin, bir grup ayracı içeren bir dize olarak değiştirilemez bir <xref:System.Int32> kullanarak değer <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> yöntemi. Kullanırsanız, ancak, dönüştürme başarılı <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> aşağıdaki örnekte gösterildiği gibi bayrak.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
>  Ayrıştırma işlemi her zaman belirli bir kültürün biçimlendirme kurallarını kullanır. Geçirerek bir kültür belirtmezseniz, bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.NumberFormatInfo> nesnesi, geçerli iş parçacığıyla ilişkilendirilmiş kültürü kullanılır.  
  
 Aşağıdaki tabloda üyelerini listeler <xref:System.Globalization.NumberStyles> numaralandırma ve ayrıştırma işlemi üzerinde sahip oldukları etkisini açıklar.  
  
|NumberStyles değeri|Ayrıştırılacak dize etkisi|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Yalnızca sayısal basamaklar izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Ondalık ayırıcısı ve kesirli basamaklar izin verilir. Tamsayı değerleri için yalnızca sıfır kesirli bir basamak izin verilir. Geçerli bir ondalık ayırıcı tarafından belirlenir <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> veya <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> özelliği.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|"E" veya "E" karakteri üstel gösterimi belirtmek için kullanılabilir. Bkz: <xref:System.Globalization.NumberStyles> ek bilgi için.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Baştaki boşluk izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Sondaki boşlukları izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Bir artı veya eksi işareti Sayısal basamaklar koyabilirsiniz.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Bir artı veya eksi işareti sayı takip edebilirsiniz.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Parantezler negatif değerleri göstermek için kullanılabilir.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Grup ayracı izin verilir. Grup ayracı karakteri tarafından belirlenen <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> veya <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> özelliği.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Para birimi simgesi izin verilir. Para birimi simgesi tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> özelliği.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Ayrıştırılacak dize, onaltılık bir sayı olarak yorumlanır. Onaltılık basamak 0-9, A-F ve a-f içerebilir. Bu bayrağı yalnızca tamsayı değerleri ayrıştırmak için kullanılabilir.|  
  
 Ayrıca, <xref:System.Globalization.NumberStyles> numaralandırma sağlar, birden çok içeren aşağıdaki bileşik stilleri <xref:System.Globalization.NumberStyles> bayrakları.  
  
|Bileşik NumberStyles değeri|Üyeleri içerir|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|İçerir <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, ve <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> stilleri. Tamsayı değerleri ayrıştırmak için kullanılan varsayılan stili budur.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|İçerir <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, ve <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> stilleri.|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|İçerir <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, ve <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> stilleri.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Dışındaki tüm stiller içerir <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> ve <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Dışındaki tüm stiller içerir <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|İçerir <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, ve <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> stilleri.|  
  
## <a name="parsing-and-unicode-digits"></a>Ayrıştırma ve Unicode Rakamları  
 Unicode standardı, çeşitli yazı sistemlerinde basamak için kod noktaları tanımlar. Örneğin, U + 0030 kod noktaları U + 0039 temsil eden 0 ile 9 arasındaki temel Latin basamak, U + 09E6 kod noktaları U + 09EF Bangla 0-9 rakamları temsil eder ve U + FF10 kod noktaları U + FF19 tam Genişlik 0-9 rakamları temsil eder. Ancak, yalnızca sayısal basamaklar yöntemleri ayrıştırma tarafından tanınan temel Latin 0-9 arası rakamları ile U + 0030 kod noktaları U + 0039 uygulanır. Yöntemi ayrıştırılırken bir sayısal bir dize iletilmezse, herhangi bir rakam içeren, çağırılıyorsa yöntem bir <xref:System.FormatException>.  
  
 Aşağıdaki örnekte <xref:System.Int32.Parse%2A?displayProperty=nameWithType> farklı yazı sistemlerinde basamaklardan oluşmalıdır dizelerini ayrıştırmak için yöntemi. Temel Latin basamak başarılı ayrıştırma girişimi, ancak tam genişlik, ayrıştırma girişimi örnekteki çıktının gösterdiği gibi Hint Arapça ve Bangla basamak başarısız olur.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.NumberStyles>  
- [Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)  
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
