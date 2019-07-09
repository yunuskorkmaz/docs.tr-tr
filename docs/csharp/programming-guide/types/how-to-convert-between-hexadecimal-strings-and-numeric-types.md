---
title: 'Nasıl yapılır: Onaltılık dizeler ve sayısal türler - arasında dönüştürme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 2b896fb645113bc33b6a320948770947adc16dab
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661150"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Nasıl yapılır: Onaltılık dizeler ve sayısal türler arasında dönüştürme (C# Programlama Kılavuzu)
Bu örnekler, aşağıdaki görevlerin nasıl gerçekleştirileceğini gösterir:  
  
- Her bir karakteri onaltılık değerini almak bir [dize](../../../csharp/language-reference/keywords/string.md).  
  
- Elde [char](../../../csharp/language-reference/keywords/char.md) karşılık gelen her değeri bir onaltılık dize.  
  
- On altılı dönüştürme `string` için bir [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md).  
  
- On altılı dönüştürme `string` için bir [float](../../../csharp/language-reference/builtin-types/floating-point-numeric-types.md).  
  
- Dönüştürme bir [bayt](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) dizi için bir onaltılık `string`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte her bir karakteri onaltılık değerini çıkarır bir `string`. İlk ayrıştırır `string` karakter dizisi. Çağrı sonra <xref:System.Convert.ToInt32%28System.Char%29> üzerinde sayısal değerini almak için her bir karakter. Son olarak, onaltılı gösterimine olarak sayı biçimlendiren bir `string`.  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte ayrıştırmak için bir `string` , on altılık değerleri ve her onaltılı değerine karşılık gelen karakteri çıkarır. İlk çağrı [bölme (Char\[\])](xref:System.String.Split(System.Char[])) bireysel olarak her bir onaltılık değer elde etmek için yöntemi `string` dizi. Çağrı sonra <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> olarak temsil edilen bir ondalık değer onaltılı değerine dönüştürmek için bir [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md). Bu, o karakteri koduna karşılık gelen karakteri almak için iki farklı şekilde gösterir. İlk tekniği kullanan <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, tamsayı bağımsız değişken olarak karşılık gelen karakteri döndürür bir `string`. İkinci yöntem açıkça bıraktığı `int` için bir [char](../../../csharp/language-reference/keywords/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>Örnek  
 Bu örnek bir onaltılık dönüştürmek için başka bir yolunu gösterir `string` çağırarak bir tamsayıya <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> yöntemi.  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir onaltılık dönüştürülecek gösterilmektedir `string` için bir [float](../../../csharp/language-reference/builtin-types/floating-point-numeric-types.md) kullanarak <xref:System.BitConverter?displayProperty=nameWithType> sınıfı ve <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> yöntemi.  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl dönüştürüleceğini gösterir bir [bayt](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) kullanarak bir onaltılık dize dizisine <xref:System.BitConverter?displayProperty=nameWithType> sınıfı.  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Standart Sayısal Biçim Dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)
- [Türler](../../../csharp/programming-guide/types/index.md)
- [Nasıl yapılır: Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
