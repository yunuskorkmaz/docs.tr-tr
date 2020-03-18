---
title: Dize bir sayıya dönüştürme - C# Programlama Kılavuzu
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 54a4562a5cc493fc287bdf2f6bcf9723557f2a05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157045"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Dize bir sayıya dönüştürme (C# Programlama Kılavuzu)

Çeşitli sayısal türlerde (,`int` `long`, `Parse` `TryParse` , `double`vb.) bulunan veya yöntemi arayarak veya sınıftaki yöntemleri <xref:System.Convert?displayProperty=nameWithType> kullanarak bir [dizeyi](../../language-reference/builtin-types/reference-types.md) bir sayıya dönüştürebilirsiniz.  
  
 Bir dizeniz varsa, `TryParse` bir yöntemi (örneğin,) [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)veya `Parse` yöntem (örneğin,) [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)çağırmak biraz daha verimli ve basittir.  Yöntem <xref:System.Convert> kullanmak, uygulayan <xref:System.IConvertible>genel nesneler için daha yararlıdır.  
  
 Dize `Parse` gibi `TryParse` içerdiği <xref:System.Int32?displayProperty=nameWithType> sayısal türü veya yöntemleri kullanabilirsiniz.  Yöntem <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> dahili olarak kullanır. <xref:System.Int32.Parse%2A>  Yöntem `Parse` dönüştürülen sayıyı döndürür; `TryParse` yöntem, dönüştürmenin başarılı olup olmadığını belirten bir <xref:System.Boolean> değer döndürür ve dönüştürülen sayıyı bir [ `out` parametrede](../../language-reference/keywords/out.md)döndürür. Dize geçerli bir biçimde `Parse` değilse, bir özel `TryParse` durum `false`atar, oysa döndürür. Bir `Parse` yöntemi ararken, ayrışdırış <xref:System.FormatException> işleminin başarısız olması durumunda bir yöntem yakalamak için her zaman özel durum işleme kullanmalısınız.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Ayrışdıran ve TryParse yöntemlerini arama

Ve `Parse` `TryParse` yöntemler dize başında ve sonunda beyaz boşluk göz ardı, ancak diğer tüm karakterler uygun sayısal türü`int` `long`oluşturan `ulong` `float`karakterler `decimal`olmalıdır ( , , , , , , vb).  Diziiçinde sayıyı oluşturan herhangi bir beyaz boşluk hataya neden olur.  Örneğin, "10", "10.3", "10.3" veya " 10 "'ı ayrıştırmak için kullanabilirsiniz, `decimal.TryParse` ancak bu yöntemi "10X", "1 0" (gömülü alana dikkat edin),`float.TryParse` "10 .3" (gömülü alana dikkat edin), "10e1" (burada çalışır) vb.nden ayrıştırmak için kullanamazsınız. Buna ek olarak, değeri `null` <xref:System.String.Empty?displayProperty=nameWithType> başarılı bir şekilde ayrıştırmak için başarısız olan bir dize. <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> Yöntemi arayarak ayrışdırmayı denemeden önce null veya boş bir dize için denetleyebilirsiniz.

Aşağıdaki örnek, hem başarılı hem `Parse` de `TryParse`başarısız çağrıları ve .  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

Aşağıdaki örnek, önde gelen sayısal karakterleri (hexadecimal karakterler dahil) ve sayısal olmayan karakterleri içermesi beklenen bir dizeyi ayrıştırma yaklaşımını göstermektedir. <xref:System.Int32.TryParse%2A> Yöntemi çağırmadan önce bir dize başından itibaren yeni bir dize için geçerli karakterler atar. Ayrıştırılacak dizeleri az sayıda karakter içerdiğinden, örnek, <xref:System.String.Concat%2A?displayProperty=nameWithType> geçerli karakterleri yeni bir dize atama yöntemini çağırır. Daha büyük bir <xref:System.Text.StringBuilder> dize için sınıf kullanılabilir.
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Dönüştürme yöntemlerini arama

Aşağıdaki tabloda, bir dizeyi bir sayıya dönüştürmek için kullanabileceğiniz <xref:System.Convert> sınıftaki yöntemlerden bazıları listelenilmiştir.  
  
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
  
 Aşağıdaki örnekte, <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> giriş dizesini [int'e](../../language-reference/builtin-types/integral-numeric-types.md)dönüştürme yöntemi ni çağırır. Örnek, bu yöntem tarafından atılabilir iki en yaygın <xref:System.FormatException> <xref:System.OverflowException>özel durum yakalar ve . Elde edilen sayı aşmadan <xref:System.Int32.MaxValue?displayProperty=nameWithType>artımlı olabilirse, örnek sonuca 1 ekler ve çıktıyı görüntüler.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Türler](./index.md)
- [Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Örnek: .NET Core WinForms Biçimlendirme Programı (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
