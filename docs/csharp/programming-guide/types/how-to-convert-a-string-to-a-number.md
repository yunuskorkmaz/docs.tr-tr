---
title: Bir dizeyi bir Number-C# programlama kılavuzuna dönüştürme
description: Parse, Trypari veya Convert Class yöntemlerini çağırarak bir dizeyi C# ' de bir sayıya dönüştürmeyi öğrenin.
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 8c46117579a5b787e5d9f3f317296d33bdd1cce1
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381976"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Bir dizeyi sayıya dönüştürme (C# Programlama Kılavuzu)

[string](../../language-reference/builtin-types/reference-types.md) `Parse` `TryParse` Çeşitli sayısal türlerde ( `int` , `long` , vb.) bulunan veya yöntemini çağırarak `double` veya sınıfındaki yöntemleri kullanarak <xref:System.Convert?displayProperty=nameWithType> bir dizeyi sayıya dönüştürebilirsiniz.  
  
 Bir dizeniz varsa, bir yöntemi (örneğin,) `TryParse` [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A) veya yöntemi (örneğin `Parse` , [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A) ) çağırmak biraz daha etkilidir ve kolaydır.  Yöntemi kullanmak <xref:System.Convert> , uygulayan genel nesneler için daha yararlıdır <xref:System.IConvertible> .  
  
 Ya da türü gibi, `Parse` `TryParse` dizeyi içeren sayısal tür üzerinde veya yöntemlerini kullanabilirsiniz <xref:System.Int32?displayProperty=nameWithType> .  <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>Yöntemi <xref:System.Int32.Parse%2A> dahili olarak kullanır.  `Parse`Yöntemi, dönüştürülmüş sayıyı döndürür; `TryParse` Yöntem <xref:System.Boolean> dönüştürmenin başarılı olup olmadığını belirten bir değer döndürür ve bir [ `out` parametrede](../../language-reference/keywords/out.md)dönüştürülmüş sayıyı döndürür. Dize geçerli bir biçimde değilse, `Parse` bir özel durum oluşturur, ancak `TryParse` döndürür `false` . Bir yöntemi çağırırken `Parse` , <xref:System.FormatException> ayrıştırma işleminin başarısız olduğu olayda bir yakalamak için özel durum işlemeyi her zaman kullanmanız gerekir.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Parse ve Trypari yöntemlerini çağırma

`Parse`Ve `TryParse` yöntemleri, dizenin başındaki ve sonundaki boşluğu yoksayar, ancak diğer tüm karakterler uygun sayısal türü ( `int` ,,,, `long` `ulong` `float` `decimal` vb.) oluşturan karakterler olmalıdır.  Dizeyi oluşturan dize içindeki tüm boşluklar hataya neden olur.  Örneğin, " `decimal.TryParse` 10", "10,3" veya "10" öğesini ayrıştırmak için kullanabilirsiniz, ancak bu yöntemi "10X", "1 0" (katıştırılmış alanı), "10 .3" (katıştırılmış alanı notta), "10E1" ( `float.TryParse` burada çalışmalar), vb. ayrıştırarak kullanamazsınız. Buna ek olarak, değeri `null` <xref:System.String.Empty?displayProperty=nameWithType> başarıyla ayrıştırılamaz bir dize olur. Metodu çağırarak, ayrıştırmaya çalışmadan önce null veya boş bir dize kontrol edebilirsiniz <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> .

Aşağıdaki örnek, ve için başarılı ve başarısız çağrıları gösterir `Parse` `TryParse` .  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

Aşağıdaki örnekte, baştaki sayısal karakterler (onaltılık karakterler dahil) ve sondaki sayısal olmayan karakterler içermesi beklenen bir dizeyi ayrıştırmak için bir yaklaşım gösterilmektedir. Metodu çağırmadan önce bir dizenin başından yeni bir dizeye geçerli karakterler atar <xref:System.Int32.TryParse%2A> . Ayrıştırılacak dizeler az sayıda karakter içerdiğinden, örnek <xref:System.String.Concat%2A?displayProperty=nameWithType> Yeni bir dizeye geçerli karakterler atamak için yöntemini çağırır. Daha büyük bir dize için <xref:System.Text.StringBuilder> bunun yerine sınıfı kullanılabilir.
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Convert yöntemlerini çağırma

Aşağıdaki tabloda, <xref:System.Convert> bir dizeyi bir sayıya dönüştürmek için kullanabileceğiniz sınıfından bazı yöntemler listelenmiştir.  
  
|Sayısal Tür|Yöntem|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 Aşağıdaki örnek, <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> bir girdi dizesini [int](../../language-reference/builtin-types/integral-numeric-types.md)'e dönüştürmek için yöntemini çağırır. Örnek, bu yöntem ve tarafından oluşturulabilecek en yaygın iki özel durumu yakalar <xref:System.FormatException> <xref:System.OverflowException> . Elde edilen sayı aşılmadan arttırılabiliyorsa <xref:System.Int32.MaxValue?displayProperty=nameWithType> örnek, sonuca 1 ekler ve çıktıyı görüntüler.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Türler](./index.md)
- [Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Örnek: .NET Core WinForms biçimlendirme yardımcı programı (C#)](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-cs)
