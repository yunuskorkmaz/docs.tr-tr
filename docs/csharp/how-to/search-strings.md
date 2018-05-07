---
title: 'Nasıl yapılır: arama dizeleri (C# Kılavuzu)'
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: d1e132093cc59c7b41a3f7d5b522fca2e224f779
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-search-strings"></a>Nasıl yapılır: dizeleri arama

Dizelerdeki metni aramak için iki ana stratejileri kullanabilirsiniz. Yöntemlerinin <xref:System.String> belirli bir metni sınıfı arayın. Normal ifadeler metin düzenleri arayın.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

[Dize](../language-reference/keywords/string.md) türü olan bir diğer ad için <xref:System.String?displayProperty=nameWithType> sınıfı, çeşitli dize içeriğini aramak için kullanışlı yöntemler sağlar. Bunlar arasında olan <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>. <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Sınıfı metin kalıpları aramak için zengin bir sözlüğünü sağlar. Bu makalede, bu teknikler ve gereksinimleriniz için en iyi yöntem seçme öğrenin.

## <a name="does-a-string-contain-text"></a>Bir dize metin içeriyor mu?

<xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> Ve <xref:System.String.EndsWith%2A?displayProperty=nameWithType> yöntemleri arama belirli bir metin dizesi. Aşağıdaki örnek, her biri bu yöntemleri ve büyük küçük harfe duyarlı arama kullanan bir değişim gösterir:

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

Önceki örnekte, bu yöntemleri kullanarak için önemli olan bir nokta gösterir. Aramalar **büyük küçük harfe duyarlı** varsayılan olarak. Kullandığınız <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> enum değeri büyük küçük harfe duyarlı arama belirtin.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Aranan metin dizesi içinde gerçekleştiği?

<xref:System.String.IndexOf%2A> Ve <xref:System.String.LastIndexOf%2A> yöntemleri de arama metni dizelerinde için. Bu yöntemler Aranan metin konumunu döndürür. Döndürmeleri metin varsa bulunamadıysa, `-1`. Aşağıdaki örnekte "yöntemleri" sözcüğü ilk ve son geçtiği için bir arama gösterir ve metin arasında görüntüler.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Normal ifadeler kullanarak belirli bir metin bulma

<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Sınıfı, dizeleri aramak için kullanılabilir. Bu aramalar basit karmaşıklığı karmaşık metin kalıplarını için değişebilir.

Aşağıdaki kod örneğinde "" veya bir tümcedeki durumu yok "," sözcüğü arar. Statik yöntemi <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> arama gerçekleştirir. Bu dizeyi arama ve arama deseni verin. Bu durumda, üçüncü bağımsız değişken büyük küçük harf duyarsız arama belirtir. Daha fazla bilgi için bkz. <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Arama deseni arama metni tanımlar. Aşağıdaki tabloda her öğeye arama deseni açıklar. (Aşağıdaki tabloda tek kullanan `\` hangi konulmalıdır olarak `\\` C# dizesinde).

| deseni  | Açıklama     |
| -------- |-------------|
| ,      | metinle eşleşen "" |
| (EIR)?   | 0 veya 1 geçişi "EIR" ile eşleşmesi |
| \s       | boşluk karakteri eşleştirmek    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> `string` Yöntemleridir genellikle daha iyi seçimler tam bir dize ararken. Normal ifadeler daha iyi bir kaynak dizesi bazı düzeni için ne zaman aradığınız var.

## <a name="does-a-string-follow-a-pattern"></a>Bir dizeyi bir desenle takip ediyor mu?

Aşağıdaki kod, bir dizideki her dizesinin biçimi doğrulamak için normal ifadeler kullanır. Doğrulama her dize basamak üç grup çizgilerle ayrılır bir telefon numarası form sahip olmasını gerektirir, ilk iki grupları üç rakam ve dört basamak üçüncü grubunu içerir. Normal ifade arama deseni kullanır `^\\d{3}-\\d{3}-\\d{4}$`. Daha fazla bilgi için bkz: [normal ifade dili - hızlı başvuru](../../standard/base-types/regular-expression-language-quick-reference.md).

| deseni  | Açıklama                             |
| -------- |-------------------------------------|
| ^        | Dize başlangıcı ile eşleşir |
| \d{3}    | tam olarak 3 basamak karakterle eşleşir  |
| -        | eşleşen '-' karakteri           |
| \d{3}    | tam olarak 3 basamak karakterle eşleşir  |
| -        | eşleşen '-' karakteri           |
| \d{4}    | tam olarak 4 basamaklı karakterle eşleşir  |
| $        | Dize sonu ile eşleşir       |


[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Bu tek arama deseni birçok geçerli dizeler eşleştirir. Normal ifadeler için arama yapın ya da tek bir metin dizesi yerine bir desen karşı doğrulamak daha uygundur.

Kodda bakarak bu örnekleri deneyebilirsiniz bizim [GitHub deposunu](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Veya örnekleri indirebilirsiniz [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Ayrıca Bkz.  

 [C# Programlama Kılavuzu](../programming-guide/index.md)  
 [Dizeler](../programming-guide/strings/index.md)  
 [LINQ ve dizeler](../programming-guide/concepts/linq/linq-and-strings.md)   
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>     
 [.NET framework normal ifadeleri](../../standard/base-types/regular-expressions.md)   
 [Normal ifade dili - hızlı başvuru](../../standard/base-types/regular-expression-language-quick-reference.md)   
 [.NET dizeleri kullanmak için en iyi uygulamalar](../../standard/base-types/best-practices-strings.md)  
