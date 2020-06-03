---
title: Dizeleri arama (C# Kılavuzu)
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: f3e6d95eb4a01d48fac5b5e2c951b9c346206004
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121490"
---
# <a name="how-to-search-strings"></a>Dizeleri arama

Dizelerde metin aramak için iki ana strateji kullanabilirsiniz. <xref:System.String>Sınıfın yöntemleri belirli bir metni arar. Normal ifadeler metin halinde desenler arar.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Sınıf için bir diğer ad olan [dize](../language-reference/builtin-types/reference-types.md#the-string-type) türü, bir <xref:System.String?displayProperty=nameWithType> dizenin içeriğini aramak için bir dizi yararlı yöntem sağlar. Bunlar arasında,,,, <xref:System.String.Contains%2A> <xref:System.String.StartsWith%2A> <xref:System.String.EndsWith%2A> <xref:System.String.IndexOf%2A> <xref:System.String.LastIndexOf%2A> . <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>Sınıfı, metinde desenler aramak için zengin bir sözlük sağlar. Bu makalede, bu teknikleri ve gereksinimleriniz için en iyi yöntemi nasıl seçebileceğinizi öğreneceksiniz.

## <a name="does-a-string-contain-text"></a>Dize metin içeriyor mu?

<xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> Ve <xref:System.String.EndsWith%2A?displayProperty=nameWithType> yöntemleri belirli metin için bir dize arar. Aşağıdaki örnek, bu yöntemlerin ve büyük/küçük harfe duyarsız arama kullanan bir varyasyonın her birini göstermektedir:

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

Yukarıdaki örnekte bu yöntemlerin kullanılması için önemli bir nokta gösterilmektedir. Aramalar, varsayılan olarak **büyük/küçük harfe duyarlıdır** . <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>Büyük/küçük harfe duyarsız arama belirtmek için enum değerini kullanın.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Aranan metin bir dizede nerede oluşuyor?

<xref:System.String.IndexOf%2A>Ve <xref:System.String.LastIndexOf%2A> yöntemleri Ayrıca dizelerde metin arar. Bu yöntemler, aranan metnin konumunu döndürür. Metin bulunamazsa, döndürülür `-1` . Aşağıdaki örnek, "Methods" sözcüğünün ilk ve son oluşumu için bir arama gösterir ve içindeki metni görüntüler.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Normal ifadeler kullanarak belirli bir metni bulma

<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>Sınıfı dizeleri aramak için kullanılabilir. Bu aramalar, basit ve karmaşık metin desenlerinden karmaşıklığa göre değişebilir.

Aşağıdaki kod örneği, bir tümcede "The" veya "onların" sözcüğünü arar, büyük/küçük harf durumunu yoksayar. Statik yöntem <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> aramayı gerçekleştirir. Aranacak dizeyi ve arama düzenlerini verirsiniz. Bu durumda, üçüncü bir bağımsız değişken büyük/küçük harfe duyarsız arama belirler. Daha fazla bilgi için bkz. <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Arama deseninin aranacağı metin açıklanır. Aşağıdaki tabloda, arama deseninin her bir öğesi açıklanmaktadır. (Aşağıdaki tablo, `\` bir C# dizesinde olduğu gibi kaçılması gereken tek kullanır `\\` ).

| kalıp  | Anlamı     |
| -------- |-------------|
| şunu      | "The" metni Eşleştir |
| (EIR)?   | 0 veya 1 "EIR" tekrarını Eşleştir |
| \s       | boşluk karakteriyle Eşleştir    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> `string`Tam bir dizeyi ararken yöntemler genellikle daha iyi seçimlerdir. Normal ifadeler, bir kaynak dizesindeki bazı desenler aranırken daha iyidir.

## <a name="does-a-string-follow-a-pattern"></a>Bir dize bir düzene uyar mi?

Aşağıdaki kod, dizideki her bir dizenin biçimini doğrulamak için normal ifadeleri kullanır. Doğrulama, her bir dizenin üç basamaklı rakam ile ayrıldığı bir telefon numarası biçimine sahip olmasını gerektirir, ilk iki grup üç basamak içerir ve üçüncü grup dört basamak içerir. Arama deseninin normal ifadesi kullanılır `^\\d{3}-\\d{3}-\\d{4}$` . Daha fazla bilgi için bkz. [normal Ifade dili-hızlı başvuru](../../standard/base-types/regular-expression-language-quick-reference.md).

| kalıp  | Anlamı                             |
| -------- |-------------------------------------|
| ^        | dizenin başlangıcını eşleştirir |
| •{3}    | tam 3 basamaklı karakterle eşleşir  |
| -        | '-' karakteriyle eşleşir           |
| •{3}    | tam 3 basamaklı karakterle eşleşir  |
| -        | '-' karakteriyle eşleşir           |
| •{4}    | tam 4 basamaklı karakterle eşleşir  |
| $        | dizenin sonuyla eşleşir       |

[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Bu tek arama deseninin birçok geçerli dizesi eşleşiyor. Normal ifadeler, tek bir metin dizesi yerine bir düzene göre arama veya doğrulama için daha iyidir.

Bu örnekleri, [GitHub deponuzdaki](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)koda bakarak deneyebilirsiniz. Ya da örnekleri [zip dosyası olarak](../../../samples/snippets/csharp/how-to/strings.zip)indirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../programming-guide/index.md)
- [Dizeler](../programming-guide/strings/index.md)
- [LINQ ve Dizeler](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [.NET Framework Normal İfadeleri](../../standard/base-types/regular-expressions.md)
- [Normal İfade Dili - Hızlı Başvuru](../../standard/base-types/regular-expression-language-quick-reference.md)
- [.NET 'teki dizeleri kullanmak için en iyi uygulamalar](../../standard/base-types/best-practices-strings.md)
