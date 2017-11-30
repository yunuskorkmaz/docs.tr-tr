---
title: ".NET sayısal dizeleri ayrıştırma"
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
- parsing strings, numeric strings
- numeric strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
ms.assetid: e39324ee-72e5-42d4-a80d-bf3ee7fc6c59
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c9bb58b0d7b45ca197653742844be01ac3bbe41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-numeric-strings-in-net"></a>NET sayısal dizeleri ayrıştırma
Tüm sayısal türler iki statik ayrıştırma yöntemleri vardır `Parse` ve `TryParse`, bir sayı dize gösterimini sayısal bir türü dönüştürmek için kullanabilirsiniz. Bu yöntemler, içinde belirtilen biçim dizeleri kullanma tarafından üretilen dizeleri ayrıştırma olanak [standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md) ve [özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md). Varsayılan olarak, `Parse` ve `TryParse` yöntemleri yalnızca tamsayı değerleri için tam sayı ondalık basamak içeren dizeleri başarıyla dönüştürebilirsiniz. Bunlar başarıyla Entegral ve kesirli ondalık basamak, Grup ayırıcılar ve kayan nokta değerlerine ondalık ayırıcı içeren dizeleri dönüştürebilirsiniz. `Parse` Yöntemi bir özel durum oluşturur işlemi başarısız olursa, ancak `TryParse` yöntemi döndürür `false`.  
  
## <a name="parsing-and-format-providers"></a>Ayrıştırma ve Biçim Sağlayıcıları  
 Genellikle, sayısal değerleri dize gösterimlerini kültür göre farklılık gösterir. Para birimi sembolleri, Grup (veya gibi binlerce) sayısal dizeleri ayırıcılar ve ondalık ayırıcı tüm öğeleri kültür göre farklılık gösterir. Yöntemleri ayrıştırma ya da örtük veya açık olarak bu kültüre özgü değişimler tanıdığı bir biçim sağlayıcısı kullanın. Biçim sağlayıcısı çağrıda belirtilmiş olup olmadığını `Parse` veya `TryParse` yöntemi, geçerli iş parçacığı kültürünü ile ilişkili Biçim sağlayıcısı ( <xref:System.Globalization.NumberFormatInfo> tarafından döndürülen nesne <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> özelliği) kullanılır.  
  
 Biçim sağlayıcısı tarafından temsil edilen bir <xref:System.IFormatProvider> uygulaması. Bu arabirim tek bir üyeye sahip <xref:System.IFormatProvider.GetFormat%2A> yöntemi, tek parametresi, bir <xref:System.Type> Biçimlendirilecek türünü temsil eden nesne. Bu yöntem biçimlendirme bilgileri sağlayan nesne döndürür. .NET destekleyen aşağıdaki iki <xref:System.IFormatProvider> sayısal dizeleri ayrıştırma için uygulamaları:  
  
-   A <xref:System.Globalization.CultureInfo> nesnesindeki <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> yöntemi döndürür bir <xref:System.Globalization.NumberFormatInfo> kültüre özgü biçimlendirme bilgileri sağlayan nesne.  
  
-   A <xref:System.Globalization.NumberFormatInfo> nesnesindeki <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> yöntemi kendisini döndürür.  
  
 Aşağıdaki örnekte bir diziye her dizesinde değiştirmeye çalıştığında bir <xref:System.Double> değeri. İngilizce (ABD) kültür kuralları yansıtan bir biçim sağlayıcısı kullanarak dizesini ayrıştırmak önce çalışır. Bu işlem oluşturursa bir <xref:System.FormatException>, Fransızca (Fransa) kültür kuralları yansıtan bir biçim sağlayıcısı kullanarak dizesini ayrıştırmak çalışır.  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Ayrıştırma ve NumberStyles Değerleri  
 Ayrıştırma işlemi işleyebilir stil öğeleri (örneğin, boşluk, Grup ayırıcılar ve ondalık ayırıcı) tarafından tanımlanan bir <xref:System.Globalization.NumberStyles> numaralandırma değeri. Varsayılan olarak, tamsayı değerlerini temsil eden dizeleri kullanarak Ayrıştırılan <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> yalnızca sayısal basamaklar, baştaki ve sondaki boşluk ve önde gelen oturum izin verir. değer. Kayan nokta değerlerini temsil eden dizeleri ayrıştırılmış bir birleşimini kullanarak <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> ve <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> değerleri; baştaki ve sondaki boşluk, baştaki işareti, ondalık ayırıcı, bir grup yanı sıra bu bileşik stili verir ondalık basamak ayırıcı ve üs. Bir aşırı yüklemesini çağırarak `Parse` veya `TryParse` türünde bir parametre içeren yöntem <xref:System.Globalization.NumberStyles> ve bir veya daha fazla ayar <xref:System.Globalization.NumberStyles> bayrakları, dizesini ayrıştırma işlemi için mevcut olabilecek stil öğeleri denetleyebilir başarılı.  
  
 Örneğin, bir Grup ayırıcı içeren bir dize için dönüştürülemez bir <xref:System.Int32> kullanarak değer <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> yöntemi. Dönüştürme kullanırsanız, ancak başarılı <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> aşağıdaki örnekte gösterildiği gibi bayrak.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
>  Ayrıştırma işlemi her zaman belirli bir kültür biçimlendirme kuralları kullanır. Geçirerek bir kültür belirtmezseniz, bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.NumberFormatInfo> nesne, geçerli iş parçacığı ile ilişkili kültür kullanılır.  
  
 Aşağıdaki tabloda üyeleri listeler <xref:System.Globalization.NumberStyles> numaralandırma ve ayrıştırma işlemi olan etkisini açıklar.  
  
|NumberStyles değeri|Ayrıştırılacak dize etkisi|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Yalnızca sayısal basamaklar izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Ondalık ayırıcının ve kesirli rakam izin verilir. Tamsayı değerleri için yalnızca sıfır kesirli rakam olarak izin verilir. Geçerli bir ondalık ayırıcısı belirlenir <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> veya <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> özelliği.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|"E" veya "E" karakterini değerini üstel gösterimde belirtmek için kullanılabilir. Bkz: <xref:System.Globalization.NumberStyles> ek bilgi için.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Başında boşluk izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Sondaki boşlukları izin verilir.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Pozitif veya negatif bir oturum Sayısal basamaklar önünde.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Pozitif veya negatif bir oturum Sayısal basamaklar izleyebilirsiniz.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Parantez negatif değerleri belirtmek için kullanılabilir.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Grup ayırıcı izin verilir. Grup ayırıcı karakteri tarafından belirlenen <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> veya <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> özelliği.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Para birimi simgesini izin verilir. Para birimi simgesini tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> özelliği.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Ayrıştırılacak dize bir onaltılık sayı olarak yorumlanır. Onaltılık basamak 0-9, A-F ve a-f içerebilir. Bu bayrak, yalnızca tamsayı değerleri ayrıştırmak için kullanılabilir.|  
  
 Ayrıca, <xref:System.Globalization.NumberStyles> numaralandırma sağlayan birden çok dahil aşağıdaki bileşik stilleri <xref:System.Globalization.NumberStyles> bayrakları.  
  
|Bileşik NumberStyles değeri|Üyeleri içerir|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|İçeren <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, ve <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> stilleri. Tamsayı değerleri ayrıştırmak için kullanılan varsayılan stilini budur.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|İçeren <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, ve <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> stilleri.|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|İçeren <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, ve <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> stilleri.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Dışındaki tüm stiller içerir <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> ve <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Dışındaki tüm stiller içerir <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|İçeren <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, ve <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> stilleri.|  
  
## <a name="parsing-and-unicode-digits"></a>Ayrıştırma ve Unicode Rakamları  
 Unicode standart kod noktaları basamak için çeşitli yazı sistemlerinde tanımlar. Örneğin, U + 0030 kod noktaları U + 0039 için temel Latin basamağı 0-9 arası temsil eden, U + 09E6 kod noktaları U + 09EF Bangla basamağı 0-9 arası temsil eden ve U + FF10 kod noktaları U + FF19 için 0-9 arasındaki tam genişlik basamak temsil eder. Ancak, yöntemleri ayrıştırma tarafından tanınan yalnızca sayısal basamaklar temel Latin 0-9 arası rakamlar U + 0030 kod noktaları U + 0039 ile değildir. Yöntemi ayrıştırılırken bir sayısal dize aktarılırsa, herhangi bir rakam içeren, yöntem oluşturulur bir <xref:System.FormatException>.  
  
 Aşağıdaki örnek kullanır <xref:System.Int32.Parse%2A?displayProperty=nameWithType> farklı yazı sistemlerinde rakamlardan dizeleri ayrıştırma yöntemi. Temel Latin rakamları başarılı ayrıştırma girişimi, ancak tam genişlik ayrıştırma girişimi örnek çıkışı gösterildiği gibi Arapça Hint ve Bangla basamak başarısız olur.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Globalization.NumberStyles>  
 [Dizeleri ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)  
 [Biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md)
