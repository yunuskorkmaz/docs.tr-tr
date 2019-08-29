---
title: 'Nasıl yapılır: Bir dizeyi sayı C# programlama kılavuzuna dönüştürme'
ms.custom: seodec18
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 377074bf09cf1e24ec022cee506588a9dcb8cb80
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133712"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Nasıl yapılır: Bir dizeyi sayıya dönüştürme (C# Programlama Kılavuzu)

Çeşitli sayısal türlerde ( `TryParse` `Parse` ,`int` <xref:System.Convert?displayProperty=nameWithType> [](../../language-reference/keywords/string.md) ,`long`vb.) bulunan veya yöntemini çağırarak veya sınıfındaki yöntemleri kullanarak bir dizeyi sayıya dönüştürebilirsiniz. `double`  
  
 Bir `TryParse` dizeniz varsa, bir yöntemi ( [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)Örneğin,) veya `Parse` yöntemi (örneğin, [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)) çağırmak biraz daha etkilidir ve kolaydır.  Yöntemi kullanmak, uygulayan <xref:System.IConvertible>genel nesneler için daha yararlıdır. <xref:System.Convert>  
  
 Ya da <xref:System.Int32?displayProperty=nameWithType> türü `Parse` gibi `TryParse` , dizeyi içeren sayısal tür üzerinde veya yöntemlerini kullanabilirsiniz.  Yöntemi dahili olarak <xref:System.Int32.Parse%2A>kullanır. <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>  Yöntemi, dönüştürülmüş sayıyı döndürür `TryParse` ; Yöntem dönüştürmenin başarılı olup olmadığını <xref:System.Boolean> belirten bir değer döndürür ve bir [ `out` parametrede](../../language-reference/keywords/out.md)dönüştürülmüş sayıyı döndürür. `Parse` Dize geçerli bir biçimde değilse, `Parse` bir özel durum oluşturur, ancak [](../../language-reference/keywords/false-literal.md) `TryParse` false döndürür. Bir `Parse` yöntemi çağırırken, ayrıştırma işleminin başarısız olduğu olayda bir <xref:System.FormatException> yakalamak için özel durum işlemeyi her zaman kullanmanız gerekir.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Parse ve Trypari yöntemlerini çağırma

`ulong` `long``int`Ve yöntemleri, dizenin başındaki ve sonundaki boşluğu yoksayar, ancak diğer tüm karakterler uygun sayısal türü (,,, `TryParse` `Parse` `float` ,`decimal`vb.).  Dizeyi oluşturan dize içindeki tüm boşluklar hataya neden olur.  Örneğin, "10", `decimal.TryParse` "10,3" veya "10" öğesini ayrıştırmak için kullanabilirsiniz, ancak bu yöntemi "10X", "1 0" (katıştırılmış alanı), "10 .3" (katıştırılmış alanı notta), "10E1" (`float.TryParse` burada çalışmalar), vb. ayrıştırarak kullanamazsınız. Buna ek olarak, değeri `null` <xref:System.String.Empty?displayProperty=nameWithType> başarıyla ayrıştırılamaz bir dize olur. Metodu çağırarak, <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> ayrıştırmaya çalışmadan önce null veya boş bir dize kontrol edebilirsiniz. 

Aşağıdaki örnek, ve `Parse` `TryParse`için başarılı ve başarısız çağrıları gösterir.  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

Aşağıdaki örnekte, baştaki sayısal karakterler (onaltılık karakterler dahil) ve sondaki sayısal olmayan karakterler içermesi beklenen bir dizeyi ayrıştırmak için bir yaklaşım gösterilmektedir. <xref:System.Int32.TryParse%2A> Metodu çağırmadan önce bir dizenin başından yeni bir dizeye geçerli karakterler atar. Ayrıştırılacak dizeler az sayıda karakter içerdiğinden, örnek yeni bir dizeye geçerli karakterler atamak için <xref:System.String.Concat%2A?displayProperty=nameWithType> yöntemini çağırır. Daha büyük bir dize <xref:System.Text.StringBuilder> için bunun yerine sınıfı kullanılabilir. 
  
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
  
 Aşağıdaki örnek, bir girdi <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> dizesini [int](../../language-reference/builtin-types/integral-numeric-types.md)'e dönüştürmek için yöntemini çağırır. Örnek, bu yöntem <xref:System.FormatException> ve <xref:System.OverflowException>tarafından oluşturulabilecek en yaygın iki özel durumu yakalar. Elde edilen sayı aşılmadan <xref:System.Int32.MaxValue?displayProperty=nameWithType>arttırılabiliyorsa örnek, sonuca 1 ekler ve çıktıyı görüntüler.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Türler](./index.md)
- [Nasıl yapılır: Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Örnek: .NET Core WinForms biçimlendirme yardımcı programıC#()](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
