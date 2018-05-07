---
title: 'Nasıl yapılır: Bir Dizeyi Sayıya Dönüştürme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 55ff87ef51f00a803276083052d4d86960e702e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Nasıl yapılır: Bir Dizeyi Sayıya Dönüştürme (C# Programlama Kılavuzu)
Dönüştürebilir bir [dize](../../../csharp/language-reference/keywords/string.md) yöntemleri kullanarak bir sayıya <xref:System.Convert> kullanarak veya sınıf `TryParse` yöntemi (int, uzun, float, vb.) çeşitli sayısal türler üzerinde bulunamadı.  
  
 Bir dize varsa, biraz daha etkili ve doğrudan çağırmak, bir `TryParse` yöntemi (örneğin, `int.TryParse("11")`).  Kullanarak bir `Convert` yöntemdir uygulayan genel nesneler için daha kullanışlı <xref:System.IConvertible>.  
  
 Kullanabileceğiniz `Parse` veya `TryParse` beklediğiniz gibi dizesini içeren sayısal türündeki yöntemlere <xref:System.Int32?displayProperty=nameWithType> türü.  <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> Yöntemi kullanan <xref:System.Int32.Parse%2A> dahili olarak.  Dizesi geçerli bir biçimde değilse `Parse` ancak aykırı `TryParse` döndürür [false](../../../csharp/language-reference/keywords/false.md).  
  
## <a name="example"></a>Örnek  
 `Parse` Ve `TryParse` yöntemleri beyaz alan başında ve sonunda dizesinin yoksay, ancak diğer tüm karakterler uygun sayısal türün form karakter olmalıdır (int, uzun, ulong, float, ondalık, vs.).  Sayı form karakterleri içinde herhangi bir boşluk neden bir hata oluştu.  Örneğin, kullanabileceğiniz `decimal.TryParse` "10", "10.3", "10", ancak ayrıştırmak için bu yöntemi "10 X", 10 ayrıştırmak için kullanamazsınız "1 0" (Not alanı), "10. 3" (Not alanı), "10e1" (`float.TryParse` burada çalışır) ve benzeri.  
  
 Aşağıdaki örneklerde başarılı ve başarısız çağrılar göstermek `Parse` ve `TryParse`.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki tabloda bazı yöntemleri listelenmiştir <xref:System.Convert> kullanabileceğiniz sınıfı.  
  
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
  
 Bu örnek çağırır <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> giriş dönüştürmek için yöntem [dize](../../../csharp/language-reference/keywords/string.md) için bir [int](../../../csharp/language-reference/keywords/int.md) . Kod bu yöntem tarafından oluşturulan iki en yaygın özel durumları yakalar <xref:System.FormatException> ve <xref:System.OverflowException>. Sayı, tamsayı depolama konumunda taşma olmadan artırılabiliyorsa program sonuca 1 ekler ve sonucu yazdırır.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Türler](../../../csharp/programming-guide/types/index.md)  
 [Nasıl yapılır: Bir Dizenin Sayısal bir Değeri Temsil Edip Etmediğini Belirleme](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
 [.NET framework 4 biçimlendirme yardımcı programı](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
