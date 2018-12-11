---
title: 'Nasıl Yapılır: Bir dizeyi sayıya - dönüştürme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: a75d6dd5fdb74ca3cb6fe28db7415aeb478e2237
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243224"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Nasıl Yapılır: Bir dizeyi sayıya dönüştürme (C# Programlama Kılavuzu)
Dönüştürebilir bir [dize](../../../csharp/language-reference/keywords/string.md) yöntemleri kullanarak sayıya <xref:System.Convert> kullanarak veya sınıf `TryParse` yöntemi (int, long, float, vb.) çeşitli sayısal türler üzerinde bulunamadı.  
  
 Bir dize varsa, biraz daha verimli ve doğrudan çağırmak onu bir `TryParse` yöntemi (örneğin, [ `int.TryParse("11", out number)` ](xref:System.Int32.TryParse%2A)).  Kullanarak bir <xref:System.Convert> yöntemi uygulamak, genel nesneler için daha faydalı <xref:System.IConvertible>.  
  
 Kullanabileceğiniz `Parse` veya `TryParse` beklediğiniz gibi dize içeren sayısal türün yöntemleri <xref:System.Int32?displayProperty=nameWithType> türü.  <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> Yöntemi kullanan <xref:System.Int32.Parse%2A> dahili olarak.  Dize geçerli bir biçimde değilse `Parse` bir özel durum oluşturur `TryParse` döndürür [false](../../../csharp/language-reference/keywords/false.md).  
  
## <a name="example"></a>Örnek  
 `Parse` Ve `TryParse` yöntemleri başında ve sonunda dize, beyaz boşluğu yoksay, ancak tüm diğer karakterler uygun sayısal türle form karakter olmalıdır (int, long, ulong, float, ondalık, vs.).  Herhangi bir boşluğu sayı form karakteri aşmayan bir hata neden.  Örneğin, kullanabileceğiniz `decimal.TryParse` "10", "10.3", "10", ancak ayrıştırmak için bu yöntem "10 X", 10 ayrıştırmak için kullanamazsınız "1 0" (Not alanı), "10. 3" (Not alanı), "10e1" (`float.TryParse` burada) ve benzeri.  
  
 Aşağıdaki örnekler hem başarılı hem de başarısız çağrılarını gösterir `Parse` ve `TryParse`.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki tabloda yöntemlerden bazıları listelenmiştir <xref:System.Convert> kullanabileceğiniz sınıfı.  
  
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
  
 Bu örnek <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> giriş yöntemi [dize](../../../csharp/language-reference/keywords/string.md) için bir [int](../../../csharp/language-reference/keywords/int.md) . Bu yöntem tarafından oluşturması muhtemel en yaygın iki özel kod yakalar <xref:System.FormatException> ve <xref:System.OverflowException>. Sayı, tamsayı depolama konumunda taşma olmadan artırılabiliyorsa program sonuca 1 ekler ve sonucu yazdırır.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Türler](../../../csharp/programming-guide/types/index.md)  
- [Nasıl yapılır: Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
- [.NET framework 4 biçimlendirme yardımcı programı](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
