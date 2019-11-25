---
title: Dizeleri arama (C# kılavuz)
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: 4a1eb818dfd8fb48b003ca184dd533f73d342662
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973100"
---
# <a name="how-to-search-strings"></a>Dizeleri arama

Dizelerde metin aramak için iki ana strateji kullanabilirsiniz. <xref:System.String> sınıfının yöntemleri belirli metni arar. Normal ifadeler metin halinde desenler arar.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<xref:System.String?displayProperty=nameWithType> sınıfı için bir diğer ad olan [dize](../language-reference/builtin-types/reference-types.md#the-string-type) türü, bir dizenin içeriğini aramak için bir dizi yararlı yöntem sağlar. Bunlar arasında <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A><xref:System.String.LastIndexOf%2A>. <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıfı, metinlerdeki desenleri aramak için zengin bir sözlük sağlar. Bu makalede, bu teknikleri ve gereksinimleriniz için en iyi yöntemi nasıl seçebileceğinizi öğreneceksiniz.

## <a name="does-a-string-contain-text"></a>Dize metin içeriyor mu?

<xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> ve <xref:System.String.EndsWith%2A?displayProperty=nameWithType> yöntemleri belirli metin için bir dize arar. Aşağıdaki örnek, bu yöntemlerin ve büyük/küçük harfe duyarsız arama kullanan bir varyasyonın her birini göstermektedir:

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

Yukarıdaki örnekte bu yöntemlerin kullanılması için önemli bir nokta gösterilmektedir. Aramalar, varsayılan olarak **büyük/küçük harfe duyarlıdır** . Büyük/küçük harfe duyarsız arama belirtmek için <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> enum değerini kullanırsınız.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Aranan metin bir dizede nerede oluşuyor?

<xref:System.String.IndexOf%2A> ve <xref:System.String.LastIndexOf%2A> yöntemleri, dizelerde metin de arar. Bu yöntemler, aranan metnin konumunu döndürür. Metin bulunmazsa `-1`döndürür. Aşağıdaki örnek, "Methods" sözcüğünün ilk ve son oluşumu için bir arama gösterir ve içindeki metni görüntüler.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Normal ifadeler kullanarak belirli bir metni bulma

<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıfı, dizelerde arama yapmak için kullanılabilir. Bu aramalar, basit ve karmaşık metin desenlerinden karmaşıklığa göre değişebilir.

Aşağıdaki kod örneği, bir tümcede "The" veya "onların" sözcüğünü arar, büyük/küçük harf durumunu yoksayar. Statik yöntem <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> aramayı gerçekleştirir. Aranacak dizeyi ve arama düzenlerini verirsiniz. Bu durumda, üçüncü bir bağımsız değişken büyük/küçük harfe duyarsız arama belirler. Daha fazla bilgi için bkz. <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Arama deseninin aranacağı metin açıklanır. Aşağıdaki tabloda, arama deseninin her bir öğesi açıklanmaktadır. (Aşağıdaki tablo, bir C# dizede `\\` olarak kaçılması gereken tek `\` kullanır).

| Kalıp  | Açıklama     |
| -------- |-------------|
| için      | "The" metni Eşleştir |
| (EIR)?   | 0 veya 1 "EIR" tekrarını Eşleştir |
| \s       | boşluk karakteriyle Eşleştir    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> Tam bir dizeyi ararken `string` yöntemler genellikle daha iyi seçimlerdir. Normal ifadeler, bazı desenler aranırken bir kaynak dizeniz daha iyidir.

## <a name="does-a-string-follow-a-pattern"></a>Bir dize bir düzene uyar mi?

Aşağıdaki kod, dizideki her bir dizenin biçimini doğrulamak için normal ifadeleri kullanır. Doğrulama, her bir dizenin üç basamaklı rakam ile ayrıldığı bir telefon numarası biçimine sahip olmasını gerektirir, ilk iki grup üç basamak içerir ve üçüncü grup dört basamak içerir. Arama deseninin `^\\d{3}-\\d{3}-\\d{4}$`normal ifadesi kullanılır. Daha fazla bilgi için bkz. [normal Ifade dili-hızlı başvuru](../../standard/base-types/regular-expression-language-quick-reference.md).

| Kalıp  | Açıklama                             |
| -------- |-------------------------------------|
| ^        | dizenin başlangıcını eşleştirir |
| \d{3}    | tam 3 basamaklı karakterle eşleşir  |
| -        | '-' karakteriyle eşleşir           |
| \d{3}    | tam 3 basamaklı karakterle eşleşir  |
| -        | '-' karakteriyle eşleşir           |
| \d{4}    | tam 4 basamaklı karakterle eşleşir  |
| $        | dizenin sonuyla eşleşir       |

[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Bu tek arama deseninin birçok geçerli dizesi eşleşiyor. Normal ifadeler, tek bir metin dizesi yerine bir düzene göre arama veya doğrulama için daha iyidir.

Bu örnekleri, [GitHub deponuzdaki](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings)koda bakarak deneyebilirsiniz. Ya da örnekleri [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip)indirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../programming-guide/index.md)
- [Dizeler](../programming-guide/strings/index.md)
- [LINQ ve Dizeler](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [Normal Ifadeleri .NET Framework](../../standard/base-types/regular-expressions.md)
- [Normal İfade Dili - Hızlı Başvuru](../../standard/base-types/regular-expression-language-quick-reference.md)
- [.NET 'teki dizeleri kullanmak için en iyi uygulamalar](../../standard/base-types/best-practices-strings.md)
