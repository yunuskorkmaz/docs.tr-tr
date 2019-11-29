---
title: 'Nasıl yapılır: bir dizeyi sayı C# programlama kılavuzuna dönüştürme'
ms.custom: seodec18
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 8cd5a54bead2790d8e6e4c8e4a5649352f12869d
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552408"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Nasıl yapılır: Bir Dizeyi Sayıya Dönüştürme (C# Programlama Kılavuzu)

Çeşitli sayısal türlerde (`int`, `long`, `double`, vb.) bulunan `Parse` veya `TryParse` yöntemini çağırarak veya <xref:System.Convert?displayProperty=nameWithType> sınıfındaki yöntemleri kullanarak bir [dizeyi](../../language-reference/builtin-types/reference-types.md) sayıya dönüştürebilirsiniz.  
  
 Bir dizeniz varsa, bir `TryParse` yöntemi (örneğin, [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)) veya `Parse` yöntemi (örneğin, [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)) çağırmak biraz daha etkilidir ve kolaydır.  <xref:System.Convert> yöntemi kullanmak, <xref:System.IConvertible>uygulayan genel nesneler için daha yararlıdır.  
  
 <xref:System.Int32?displayProperty=nameWithType> türü gibi, dizeyi içeren sayısal türde `Parse` veya `TryParse` yöntemlerini kullanabilirsiniz.  <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> yöntemi dahili olarak <xref:System.Int32.Parse%2A> kullanır.  `Parse` yöntemi, dönüştürülmüş sayıyı döndürür; `TryParse` yöntemi, dönüştürmenin başarılı olup olmadığını belirten bir <xref:System.Boolean> değeri döndürür ve bir [`out` parametresindeki](../../language-reference/keywords/out.md)dönüştürülmüş sayıyı döndürür. Dize geçerli bir biçimde değilse, `Parse` bir özel durum oluşturur, ancak `TryParse` `false`döndürür. Bir `Parse` yöntemi çağrılırken, ayrıştırma işleminin başarısız olduğu olayda bir <xref:System.FormatException> yakalamak için her zaman özel durum işlemeyi kullanmanız gerekir.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Parse ve Trypari yöntemlerini çağırma

`Parse` ve `TryParse` yöntemleri, dizenin başındaki ve sonundaki boşlukları yoksayar, ancak diğer tüm karakterler uygun sayısal türü (`int`, `long`, `ulong`, `float`) biçimli karakterler olmalıdır. , `decimal`vb.).  Dizeyi oluşturan dize içindeki tüm boşluklar hataya neden olur.  Örneğin, "10", "10,3" veya "10" öğesini ayrıştırmak için `decimal.TryParse` kullanabilirsiniz, ancak bu yöntemi, "10X", "1 0" (katıştırılmış alanı notta), "10 .3" (katıştırılmış alanı), "10E1" (`float.TryParse` burada), vb. ayrıştırarak kullanamazsınız. Ayrıca, değeri `null` olan bir dize veya <xref:System.String.Empty?displayProperty=nameWithType> başarıyla ayrıştırılamadı. <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metodunu çağırarak, ayrıştırmayı denemeden önce null veya boş bir dize kontrol edebilirsiniz. 

Aşağıdaki örnek, `Parse` ve `TryParse`için hem başarılı hem de başarısız çağrıları gösterir.  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

Aşağıdaki örnekte, baştaki sayısal karakterler (onaltılık karakterler dahil) ve sondaki sayısal olmayan karakterler içermesi beklenen bir dizeyi ayrıştırmak için bir yaklaşım gösterilmektedir. <xref:System.Int32.TryParse%2A> yöntemi çağrılmadan önce bir dizenin başından yeni bir dizeye geçerli karakterler atar. Ayrıştırılacak dizeler az sayıda karakter içerdiğinden, örnek yeni bir dizeye geçerli karakterler atamak için <xref:System.String.Concat%2A?displayProperty=nameWithType> yöntemini çağırır. Daha büyük bir dize için bunun yerine <xref:System.Text.StringBuilder> sınıfı kullanılabilir. 
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Convert yöntemlerini çağırma

Aşağıdaki tabloda, bir dizeyi sayıya dönüştürmek için kullanabileceğiniz <xref:System.Convert> sınıfından bazı yöntemler listelenmiştir.  
  
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
  
 Aşağıdaki örnek, bir giriş dizesini [int](../../language-reference/builtin-types/integral-numeric-types.md)'e dönüştürmek için <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> yöntemini çağırır. Örnek, bu yöntemle oluşturulabilecek en yaygın iki özel durumu yakalar, <xref:System.FormatException> ve <xref:System.OverflowException>. Elde edilen sayı <xref:System.Int32.MaxValue?displayProperty=nameWithType>aşmadan arttırılabiliyorsa, örnek sonuca 1 ekler ve çıktıyı görüntüler.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Türler](./index.md)
- [Nasıl yapılır: Bir Dizenin Sayısal bir Değeri Temsil Edip Etmediğini Belirleme](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Örnek: .NET Core WinForms biçimlendirme yardımcı programıC#()](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
