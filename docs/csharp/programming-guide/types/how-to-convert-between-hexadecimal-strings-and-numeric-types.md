---
title: 'Nasıl yapılır: Onaltılık Dizeler ve Sayısal Türler Arasında Dönüştürme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 0f7502bc0f14c85d207c313646f26c7787bd46b3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484093"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Nasıl yapılır: Onaltılık Dizeler ve Sayısal Türler Arasında Dönüştürme (C# Programlama Kılavuzu)
Bu örnekler, aşağıdaki görevlerin nasıl gerçekleştirileceğini gösterir:  
  
-   Her bir karakteri onaltılık değerini almak bir [dize](../../../csharp/language-reference/keywords/string.md).  
  
-   Elde [char](../../../csharp/language-reference/keywords/char.md) karşılık gelen her değeri bir onaltılık dize.  
  
-   On altılı dönüştürme `string` için bir [int](../../../csharp/language-reference/keywords/int.md).  
  
-   On altılı dönüştürme `string` için bir [float](../../../csharp/language-reference/keywords/float.md).  
  
-   Dönüştürme bir [bayt](../../../csharp/language-reference/keywords/byte.md) dizi için bir onaltılık `string`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte her bir karakteri onaltılık değerini çıkarır bir `string`. İlk ayrıştırır `string` karakter dizisi. Çağrı sonra <xref:System.Convert.ToInt32%28System.Char%29> üzerinde sayısal değerini almak için her bir karakter. Son olarak, onaltılı gösterimine olarak sayı biçimlendiren bir `string`.  
  
 [!code-csharp[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte ayrıştırmak için bir `string` , on altılık değerleri ve her onaltılı değerine karşılık gelen karakteri çıkarır. İlk çağrı [bölme (Char\[\])](xref:System.String.Split(System.Char[])) bireysel olarak her bir onaltılık değer elde etmek için yöntemi `string` dizi. Çağrı sonra <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> olarak temsil edilen bir ondalık değer onaltılı değerine dönüştürmek için bir [int](../../../csharp/language-reference/keywords/int.md). Bu, o karakteri koduna karşılık gelen karakteri almak için iki farklı şekilde gösterir. İlk tekniği kullanan <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, tamsayı bağımsız değişken olarak karşılık gelen karakteri döndürür bir `string`. İkinci yöntem açıkça bıraktığı `int` için bir [char](../../../csharp/language-reference/keywords/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnek bir onaltılık dönüştürmek için başka bir yolunu gösterir `string` çağırarak bir tamsayıya <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> yöntemi.  
  
 [!code-csharp[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir onaltılık dönüştürülecek gösterilmektedir `string` için bir [float](../../../csharp/language-reference/keywords/float.md) kullanarak <xref:System.BitConverter?displayProperty=nameWithType> sınıfı ve <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> yöntemi.  
  
 [!code-csharp[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl dönüştürüleceğini gösterir bir [bayt](../../../csharp/language-reference/keywords/byte.md) kullanarak bir onaltılık dize dizisine <xref:System.BitConverter?displayProperty=nameWithType> sınıfı.  
  
 [!code-csharp[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Standart Sayısal Biçim Dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)  
 [Türler](../../../csharp/programming-guide/types/index.md)  
 [Nasıl yapılır: Bir Dizenin Sayısal bir Değeri Temsil Edip Etmediğini Belirleme](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
