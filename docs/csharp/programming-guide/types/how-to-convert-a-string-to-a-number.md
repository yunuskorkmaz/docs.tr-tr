---
title: Bir dizeyi bir Number-C# programlama kılavuzuna dönüştürme
description: Parse, Trypari veya Convert Class yöntemlerini çağırarak bir dizeyi C# ' de bir sayıya dönüştürmeyi öğrenin.
ms.date: 02/16/2021
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 011c66d5341d9e2e8032a692385f5f250b6ab9a2
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100639376"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Bir dizeyi sayıya dönüştürme (C# Programlama Kılavuzu)

`string` `Parse` `TryParse` Sayısal türlerde bulunan veya yöntemini (, `int` `long` , `double` , vb.) çağırarak veya sınıfındaki yöntemleri kullanarak <xref:System.Convert?displayProperty=nameWithType> bir sayıya bir sayıya dönüştürürsünüz.
  
Bir yöntemi (örneğin,) veya yöntemi (örneğin `TryParse` [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A) `Parse` ,) çağırmak biraz daha etkilidir ve kolaydır [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A) . Yöntemi kullanmak <xref:System.Convert> , uygulayan genel nesneler için daha yararlıdır <xref:System.IConvertible> .
  
Ya da `Parse` `TryParse` türü gibi, dizenin içerdiğini tahmin ettiğiniz sayısal türde yöntemler kullanın <xref:System.Int32?displayProperty=nameWithType> .  <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>Yöntemi <xref:System.Int32.Parse%2A> dahili olarak kullanır.  `Parse`Yöntemi, dönüştürülmüş sayıyı döndürür; `TryParse` Yöntem dönüştürmenin başarılı olup olmadığını belirten bir Boolean değer döndürür ve bir parametrede dönüştürülmüş sayıyı döndürür `out` . Dize geçerli bir biçimde değilse, `Parse` bir özel durum oluşturur, ancak `TryParse` döndürür `false` . Bir yöntemi çağırırken `Parse` , <xref:System.FormatException> ayrıştırma işlemi başarısız olduğunda bir öğesini yakalamak için her zaman özel durum işlemeyi kullanmanız gerekir.
  
## <a name="call-parse-or-tryparse-methods"></a>Parse veya Trypari yöntemlerini çağırın

`Parse`Ve `TryParse` yöntemleri, dizenin başındaki ve sonundaki boşluğu yoksayar, ancak diğer tüm karakterler uygun sayısal türü (,,,, vb `int` `long` `ulong` `float` `decimal` .) oluşturan karakterler olmalıdır.  Dizeyi oluşturan dize içindeki tüm boşluklar hataya neden olur.  Örneğin, " `decimal.TryParse` 10", "10,3" veya "10" öğesini ayrıştırmak için kullanabilirsiniz, ancak bu yöntemi "10X", "1 0" (katıştırılmış alanı), "10 .3" (katıştırılmış alanı notta), "10E1" ( `float.TryParse` burada çalışmalar), vb. ayrıştırmanıza yönelik olarak kullanamazsınız. Değeri `null` <xref:System.String.Empty?displayProperty=nameWithType> başarıyla ayrıştırılamaz olan bir dize. Metodu çağırarak, ayrıştırmaya çalışmadan önce null veya boş bir dize kontrol edebilirsiniz <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> .

Aşağıdaki örnek, ve için başarılı ve başarısız çağrıları gösterir `Parse` `TryParse` .

[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]

Aşağıdaki örnek, baştaki sayısal karakterler (onaltılık karakterler dahil) ve sondaki sayısal olmayan karakterler içermesi beklenen bir dizeyi ayrıştırmak için bir yaklaşımı gösterir. Metodu çağırmadan önce bir dizenin başından yeni bir dizeye geçerli karakterler atar <xref:System.Int32.TryParse%2A> . Ayrıştırılacak dizeler birkaç karakter içerdiğinden, örnek <xref:System.String.Concat%2A?displayProperty=nameWithType> Yeni bir dizeye geçerli karakterler atamak için yöntemini çağırır. Daha büyük bir dize için <xref:System.Text.StringBuilder> bunun yerine sınıfı kullanılabilir.

[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]

## <a name="call-convert-methods"></a>Çağrı dönüştürme yöntemleri

Aşağıdaki tabloda, <xref:System.Convert> bir dizeyi bir sayıya dönüştürmek için kullanabileceğiniz sınıfından bazı yöntemler listelenmiştir.

| Sayısal tür | Yöntem                                             |
|--------------|----------------------------------------------------|
| `decimal`    | <xref:System.Convert.ToDecimal%28System.String%29> |
| `float`      | <xref:System.Convert.ToSingle%28System.String%29>  |
| `double`     | <xref:System.Convert.ToDouble%28System.String%29>  |
| `short`      | <xref:System.Convert.ToInt16%28System.String%29>   |
| `int`        | <xref:System.Convert.ToInt32%28System.String%29>   |
| `long`       | <xref:System.Convert.ToInt64%28System.String%29>   |
| `ushort`     | <xref:System.Convert.ToUInt16%28System.String%29>  |
| `uint`       | <xref:System.Convert.ToUInt32%28System.String%29>  |
| `ulong`      | <xref:System.Convert.ToUInt64%28System.String%29>  |

Aşağıdaki örnek, <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> bir girdi dizesini [int](../../language-reference/builtin-types/integral-numeric-types.md)'e dönüştürmek için yöntemini çağırır. Örnek, bu yöntem ve tarafından oluşturulabilecek en yaygın iki özel durumu yakalar <xref:System.FormatException> <xref:System.OverflowException> . Elde edilen sayı aşılmadan arttırılabiliyorsa <xref:System.Int32.MaxValue?displayProperty=nameWithType> örnek, sonuca 1 ekler ve çıktıyı görüntüler.

[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]
