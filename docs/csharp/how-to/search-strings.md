---
title: Dizeleri arama (C# Guide)
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

Dizelerdeki metni aramak için iki ana strateji kullanabilirsiniz. <xref:System.String> Belirli bir metin için sınıf arama yöntemleri. Normal ifadeler metindeki desenleri arar.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<xref:System.String?displayProperty=nameWithType> Sınıfın diğer adı olan [dize](../language-reference/builtin-types/reference-types.md#the-string-type) türü, bir dize içeriğini aramak için yararlı yöntemler bir dizi sağlar. Aralarında <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A> <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>, . Sınıf <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> metindesenleri aramak için zengin bir kelime sağlar. Bu makalede, bu teknikleri ve nasıl ihtiyaçlarınız için en iyi yöntemi seçmek için öğrenirler.

## <a name="does-a-string-contain-text"></a>Dize metin içeriyor mu?

, <xref:System.String.Contains%2A?displayProperty=nameWithType> <xref:System.String.StartsWith%2A?displayProperty=nameWithType> ve <xref:System.String.EndsWith%2A?displayProperty=nameWithType> yöntemler belirli bir metin için bir dize arama. Aşağıdaki örnek, bu yöntemlerin her birini ve duyarlı olmayan bir arama örneği kullanan bir varyasyonu gösterir:

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

Önceki örnek, bu yöntemleri kullanmak için önemli bir nokta göstermektedir. Aramalar varsayılan olarak **büyük/küçük harf duyarlıdır.** <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> Enum değerini, hassas olmayan bir arama örneği belirtmek için kullanırsınız.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Aranan metin bir dizede nerede oluşur?

Ve <xref:System.String.IndexOf%2A> <xref:System.String.LastIndexOf%2A> yöntemler de dizeleri metin aramak. Bu yöntemler, aranan metnin konumunu döndürer. Metin bulunmazsa, geri dönerler. `-1` Aşağıdaki örnekte, "yöntemler" sözcüğünün ilk ve son oluşumunu gösteren bir arama görüntülenir ve aradaki metni görüntüler.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Normal ifadeleri kullanarak belirli bir metni bulma

Sınıf <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> dizeleri aramak için kullanılabilir. Bu aramalar basitten karmaşık metin desenlerine kadar karmaşıklık taslayabilir.

Aşağıdaki kod örneği, bir cümledeki "the" veya "their" sözcüklerini arar ve büyük/küçük harf göz ardı eder. Statik yöntem <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> aramayı gerçekleştirir. Arama için dize ve arama deseni verirsiniz. Bu durumda, üçüncü bir bağımsız değişken büyük/küçük harf duyarsız arama belirtir. Daha fazla bilgi için bkz. <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Arama deseni, aradığınız metni açıklar. Aşağıdaki tabloda arama deseninin her öğesi açıklanmaktadır. (Aşağıdaki tabloda C# dizesinde `\\` olduğu gibi kaçması gereken tek `\` limadde kullanır).

| Desen  | Anlamı     |
| -------- |-------------|
| şunu      | "the" metnini eşleştirin |
| (eir)?   | maç 0 veya 1 "eir" oluşumu |
| \s       | bir boşluk karakterini eşleştirme    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> Tam `string` bir dize ararken yöntemler genellikle daha iyi seçeneklerdir. Bir kaynak dizesinde bazı desenler ararken normal ifadeler daha iyidir.

## <a name="does-a-string-follow-a-pattern"></a>Bir dize bir desen izler mi?

Aşağıdaki kod, bir dizideki her dizenin biçimini doğrulamak için düzenli ifadeler kullanır. Doğrulama, her dize, üç basamak grubunun tirelerle ayrıldığı, ilk iki grubun üç basamak içerdiği ve üçüncü grubun dört basamak içerdiği bir telefon numarası biçimine sahip olması gerekir. Arama deseni normal `^\\d{3}-\\d{3}-\\d{4}$`ifadeyi kullanır. Daha fazla bilgi için [Bkz. Normal İfade Dili - Hızlı Başvuru](../../standard/base-types/regular-expression-language-quick-reference.md).

| Desen  | Anlamı                             |
| -------- |-------------------------------------|
| ^        | dize başlangıcıyla eşleşir |
| \d{3}    | tam olarak 3 basamaklı karakterlerle eşleşir  |
| -        | '-' karakteriyle eşleşir           |
| \d{3}    | tam olarak 3 basamaklı karakterlerle eşleşir  |
| -        | '-' karakteriyle eşleşir           |
| \d{4}    | tam 4 basamaklı karakterlerle eşleşir  |
| $        | dize sonu eşleşir       |

[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Bu tek arama deseni birçok geçerli dizeyle eşleşir. Normal ifadeler, tek bir metin dizesini aramak veya bir desene karşı doğrulamak için daha iyidir.

Bu örnekleri [GitHub depomuzdaki](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)koda bakarak deneyebilirsiniz. Veya bir zip [dosyası olarak](../../../samples/snippets/csharp/how-to/strings.zip)örnekleri indirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../programming-guide/index.md)
- [Dizeler](../programming-guide/strings/index.md)
- [LINQ ve Dizeler](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [.NET Framework Normal İfadeleri](../../standard/base-types/regular-expressions.md)
- [Normal İfade Dili - Hızlı Başvuru](../../standard/base-types/regular-expression-language-quick-reference.md)
- [.NET'te dizeleri kullanmak için en iyi uygulamalar](../../standard/base-types/best-practices-strings.md)
