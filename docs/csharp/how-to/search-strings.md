---
title: 'Nasıl yapılır: arama dizeleri (C# Kılavuzu)'
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: b6d5ab1c4588e72bf49c5ca2f859b9996c0d3834
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857160"
---
# <a name="how-to-search-strings"></a>Nasıl yapılır: dizeleri arama

Dizeleri metin arama için iki ana stratejiler kullanabilirsiniz. Yöntemlerinin <xref:System.String> sınıfı belirli bir metni arayın. Normal ifadeler, metin desenleri arayın.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

[Dize](../language-reference/keywords/string.md) bir diğer ad türü için <xref:System.String?displayProperty=nameWithType> sınıfı, bir dizenin içeriklerini aramak için kullanışlı yöntemler sunar. Bunlar arasında olan <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>. <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> SAX metin kalıpları aramak için zengin bir sözlük. Bu makalede, bu teknikler ve ihtiyaçlarınızı en iyi yöntemi seçme öğrenin.

## <a name="does-a-string-contain-text"></a>Bir dizeyi metin içeriyor mu?

<xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> Ve <xref:System.String.EndsWith%2A?displayProperty=nameWithType> yöntemleri aramak için belirli bir metni bir dize. Aşağıdaki örnek, her biri bu yöntemleri ve büyük küçük harfe duyarlı arama kullanan bir değişim gösterir:

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

Yukarıdaki örnekte, bu yöntemler için önemli bir nokta gösterir. Aramalar **büyük/küçük harfe** varsayılan olarak. Kullandığınız <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> büyük küçük harfe duyarlı bir arama belirtmek için sabit listesi değeri.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Aranan metin dizesi içinde nerede gerçekleşiyor?

<xref:System.String.IndexOf%2A> Ve <xref:System.String.LastIndexOf%2A> yöntemleri ayrıca arama metin dizeleri. Bu yöntemler aranan metnin konumunu döndürür. Döndürmeleri metni, bulunamadığında, `-1`. Aşağıdaki örnek, arama "yöntemleri" sözcüğü ilk ve son oluşumunu gösterir ve metin arasında görüntüler.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Belirli bir normal ifadeler kullanarak metin bulma

<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Sınıfı, dizeleri aramak için kullanılabilir. Bu aramaları, basit karmaşıklığı karmaşık metin desenleri için değişebilir.

Aşağıdaki kod örneği, "" veya bir tümcedeki çalışması yok sayılıyor "their" sözcüğü için arar. Statik yöntem <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> arama gerçekleştirir. Bu dize arama ve arama deseni için size. Bu durumda, büyük küçük harf duyarsız arama üçüncü bir bağımsız değişken belirtir. Daha fazla bilgi için bkz. <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Arama metin arama deseni açıklar. Aşağıdaki tabloda, her öğe için arama deseni açıklar. (Aşağıdaki tabloda tek kullanan `\` , atlanan, olarak `\\` bir C# dizedeki).

| deseni  | Açıklama     |
| -------- |-------------|
| ,      | metinle eşleşen "" |
| (EIR)?   | 0 veya 1 "EIR" oluşumunu eşleşmesi |
| \s       | bir boşluk karakteri eşleştir    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> `string` Yöntemleri, tam bir dize ararken genellikle daha iyi bir seçenek şunlardır. Normal ifadeler, daha iyi bir kaynak dizesi bazı deseni için zaman aradığınız olan.

## <a name="does-a-string-follow-a-pattern"></a>Bir dizeyi bir desenle takip ediyor mu?

Aşağıdaki kod, bir dizideki her bir dizenin biçimi doğrulamak için normal ifadeler kullanır. Doğrulama, her bir dizenin üç rakamlar grupları çizgilerle ayrılmış bir telefon numarası biçiminin olmasını gerektirir, ilk iki grupları üç basamak içeren ve üçüncü Grup dört basamak içerir. Arama deseni normal ifadeyi kullanan `^\\d{3}-\\d{3}-\\d{4}$`. Daha fazla bilgi için [normal ifade dili - hızlı başvuru](../../standard/base-types/regular-expression-language-quick-reference.md).

| deseni  | Açıklama                             |
| -------- |-------------------------------------|
| ^        | dizenin başlangıcıyla eşleşir |
| \d{3}    | tam olarak 3 basamak karakter ile eşleşir  |
| -        | eşleşen '-' karakteri           |
| \d{3}    | tam olarak 3 basamak karakter ile eşleşir  |
| -        | eşleşen '-' karakteri           |
| \d{4}    | tam olarak 4 basamaklı karakter ile eşleşir  |
| $        | Dize sonu ile eşleşir       |

[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Bu tek arama deseni ile eşleşir birçok geçerli dizesi. Normal ifadeler için arama yapın ya da tek bir metin dizesi yerine desen karşı doğrulamak daha uygundur.

Bu örnekler kodda bakarak deneyebilirsiniz bizim [GitHub deposu](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Örnekleri indirebilirsiniz [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Programlama Kılavuzu](../programming-guide/index.md)  
- [Dizeler](../programming-guide/strings/index.md)  
- [LINQ ve Dizeler](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [.NET framework normal ifadeleri](../../standard/base-types/regular-expressions.md)
- [Normal İfade Dili - Hızlı Başvuru](../../standard/base-types/regular-expression-language-quick-reference.md)
- [. NET'te dizeleri kullanmak için en iyi uygulamalar](../../standard/base-types/best-practices-strings.md)  
