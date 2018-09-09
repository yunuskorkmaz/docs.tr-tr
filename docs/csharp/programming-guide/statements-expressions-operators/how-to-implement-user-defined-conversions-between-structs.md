---
title: 'Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüşümler Uygulama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: cff85d60c1b59f4d1ca028f8fc02fee5728fa3d6
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44251979"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a>Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüşümler Uygulama (C# Programlama Kılavuzu)
Bu örnek iki yapıları tanımlar `RomanNumeral` ve `BinaryNumeral`ve bunlar arasında dönüştürmeler gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
-   Önceki örnekte, deyim:  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     bir dönüştürme gerçekleştiren bir `RomanNumeral` için bir `BinaryNumeral`. Doğrudan dönüşüm yok olduğundan `RomanNumeral` için `BinaryNumeral`, bir yayın dönüştürmek için kullanılan bir `RomanNumeral` için bir `int`ve dönüştürmek için başka bir tür dönüştürme bir `int` için bir `BinaryNumeral`.  
  
-   Ayrıca deyimi  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     bir dönüştürme gerçekleştiren bir `BinaryNumeral` için bir `RomanNumeral`. Çünkü `RomanNumeral` örtük bir dönüştürme tanımlar `BinaryNumeral`, atama gereklidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Dönüştürme İşleçleri](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
