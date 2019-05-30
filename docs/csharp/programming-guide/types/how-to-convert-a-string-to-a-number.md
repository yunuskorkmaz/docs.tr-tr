---
title: 'Nasıl yapılır: Bir dizeyi sayıya - dönüştürme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 25f6fb5e8780611a6ca7396873d0a33684b65a48
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301378"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Nasıl yapılır: Bir dizeyi sayıya dönüştürme (C# Programlama Kılavuzu)

Dönüştürebilir bir [dize](../../../csharp/language-reference/keywords/string.md) çağırarak bir sayı `Parse` veya `TryParse` çeşitli sayısal türlerde yöntemi bulunamadı (`int`, `long`, `double`, vs.), veya içinde yöntemlerikullanarak<xref:System.Convert?displayProperty=nameWithType>sınıfı.  
  
 Bir dize varsa, biraz daha verimli ve doğrudan çağırmak onu bir `TryParse` yöntemi (örneğin, [ `int.TryParse("11", out number)` ](xref:System.Int32.TryParse%2A)) veya `Parse` yöntemi (örneğin, [ `var number = int.Parse("11")` ](xref:System.Int32.Parse%2A)).  Kullanarak bir <xref:System.Convert> yöntemi uygulamak, genel nesneler için daha faydalı <xref:System.IConvertible>.  
  
 Kullanabileceğiniz `Parse` veya `TryParse` beklediğiniz gibi dize içeren sayısal türün yöntemleri <xref:System.Int32?displayProperty=nameWithType> türü.  <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> Yöntemi kullanan <xref:System.Int32.Parse%2A> dahili olarak.  `Parse` Yöntemi dönüştürülmüş sayıyı döndürür; `TryParse` yöntemi döndürür bir <xref:System.Boolean> dönüştürme başarılı oldu ve dönüştürülen numarasını getirir olup olmadığını gösteren değer bir [ `out` parametre](../../../csharp/language-reference/keywords/out.md). Dize geçerli bir biçimde değilse `Parse` bir özel durum oluşturur `TryParse` döndürür [false](../../../csharp/language-reference/keywords/false-literal.md). Çağrılırken bir `Parse` yöntemi, her zaman kullanmanız gerektiğini özel durum işleme yakalamak için bir <xref:System.FormatException> ayrıştırma işleminin başarısız olması durumunda olmasıdır.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Ayrıştırma ve TryParse metotları çağırma

`Parse` Ve `TryParse` yöntemleri başında ve sonunda dize, beyaz boşluğu yoksay, ancak tüm diğer karakterler uygun sayısal türle form karakter olmalıdır (`int`, `long`, `ulong`, `float`, `decimal`vb..).  Sayı dizedeki herhangi bir boşluğu bir hataya neden olur.  Örneğin, kullanabileceğiniz `decimal.TryParse` "10", "10.3" veya "10", ancak ayrıştırmak için bu yöntem "10 X", 10 ayrıştırmak için kullanamazsınız "1 0 (embedded alanı unutmayın)", "10. 3 (embedded alanı unutmayın)", "10e1" (`float.TryParse` burada) ve benzeri. Ayrıca, bir dize değeri `null` veya <xref:System.String.Empty?displayProperty=nameWithType> başarıyla ayrıştırmak başarısız olur. Çağırarak ayrıştırmak çalışmadan önce bir null veya boş dize denetleyebilirsiniz <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> yöntemi. 

Aşağıdaki örnek, başarılı ve başarısız çağrıları gösterir `Parse` ve `TryParse`.  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

Aşağıdaki örnek bir baştaki sayısal karakterleri (onaltılık karakter de dahil olmak üzere) ve sonunda sayısal olmayan karakterler içerecek şekilde beklenen bir dizesini ayrıştırmak için bir yaklaşımı gösterir. Geçerli karakterler bir dize başından çağırmadan önce yeni bir dize atar <xref:System.Int32.TryParse%2A> yöntemi. Ayrıştırılacak dize az sayıda karakter içerdiğinden, örnek çağırır <xref:System.String.Concat%2A?displayProperty=nameWithType> geçerli karakterler için yeni bir dize atamak için yöntemi. Daha büyük bir dizeyi <xref:System.Text.StringBuilder> sınıfı yerine kullanılabilir. 
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Dönüştürme yöntemleri çağırma

Aşağıdaki tabloda yöntemlerden bazıları listelenmiştir <xref:System.Convert> bir dizeyi sayıya dönüştürmek için kullanabileceğiniz sınıfı.  
  
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
  
 Aşağıdaki örnek çağrıları <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> yöntemi Giriş bir dizeye dönüştürmek için bir [int](../../../csharp/language-reference/keywords/int.md). Bu yöntem tarafından oluşturması muhtemel en yaygın iki özel örnek yakalar <xref:System.FormatException> ve <xref:System.OverflowException>. Sonuçta elde edilen sayı aşmadan 'er artırılabilir, <xref:System.Int32.MaxValue?displayProperty=nameWithType>, örnek program sonuca 1 ekler ve çıktıyı görüntüler.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Türler](../../../csharp/programming-guide/types/index.md)
- [Nasıl yapılır: Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [.NET framework 4 biçimlendirme yardımcı programı](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
