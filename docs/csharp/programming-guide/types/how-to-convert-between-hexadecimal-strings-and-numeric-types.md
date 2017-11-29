---
title: "Nasıl yapılır: Onaltılık Dizeler ve Sayısal Türler Arasında Dönüştürme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 91e5cff52c67e1e7930d92da7c87ab1f4a3120af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Nasıl yapılır: Onaltılık Dizeler ve Sayısal Türler Arasında Dönüştürme (C# Programlama Kılavuzu)
Bu örnekler aşağıdaki görevlerin nasıl gerçekleştirileceğini gösterir:  
  
-   Her karakteri on altılık değeri elde bir [dize](../../../csharp/language-reference/keywords/string.md).  
  
-   Elde [char](../../../csharp/language-reference/keywords/char.md) , her bir onaltılık dize değerine karşılık gelir.  
  
-   On altılı Dönüştür `string` için bir [int](../../../csharp/language-reference/keywords/int.md).  
  
-   On altılı Dönüştür `string` için bir [float](../../../csharp/language-reference/keywords/float.md).  
  
-   Dönüştürme bir [bayt](../../../csharp/language-reference/keywords/byte.md) on altılı dizisine `string`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte her karakter on altılık değeri çıkarır bir `string`. İlk ayrıştırır `string` karakterden oluşan bir dizi. Çağırır sonra <xref:System.Convert.ToInt32%28System.Char%29> sayısal değerini almak için her karakter üzerinde. Son olarak, kendi onaltılık gösterimi olarak sayıyı biçimler bir `string`.  
  
 [!code-csharp[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnek ayrıştırır bir `string` , onaltılık değerler ve her bir onaltılı değere karşılık gelen karakter çıkarır. İlk çağıran [bölme (Char\[\])](xref:System.String.Split(System.Char[])) her on altılık değeri tek bir olarak elde etmek için yöntemi `string` dizi. Çağırır sonra <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> on altılık değeri olarak gösterilen bir ondalık değer dönüştürmek için bir [int](../../../csharp/language-reference/keywords/int.md). Bu karakter koduna karşılık gelen karakter almak için iki farklı yolunu gösterir. İlk tekniği kullanan <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, tamsayı bağımsız değişken olarak karşılık gelen karakter döndüren bir `string`. İkinci tekniği açıkça bıraktığı `int` için bir [char](../../../csharp/language-reference/keywords/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnek bir onaltılık dönüştürmek için başka bir yolunu gösterir `string` çağırarak bir tamsayıya <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> yöntemi.  
  
 [!code-csharp[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir onaltılık dönüştürmek gösterilmiştir `string` için bir [float](../../../csharp/language-reference/keywords/float.md) kullanarak <xref:System.BitConverter?displayProperty=nameWithType> sınıfı ve <xref:System.Int32.Parse%2A?displayProperty=nameWithType> yöntemi.  
  
 [!code-csharp[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl dönüştürüleceğini gösterir bir [bayt](../../../csharp/language-reference/keywords/byte.md) kullanarak bir onaltılık dize dizisine <xref:System.BitConverter?displayProperty=nameWithType> sınıfı.  
  
 [!code-csharp[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)  
 [Türler](../../../csharp/programming-guide/types/index.md)  
 [Nasıl yapılır: bir dizenin sayısal bir değeri temsil edip etmediğini belirleme](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
