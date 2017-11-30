---
title: "Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüşümler Uygulama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7d86cbd48347e6951f6b6883a385d80d68697c9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a>Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüşümler Uygulama (C# Programlama Kılavuzu)
Bu örnek iki yapılar tanımlar `RomanNumeral` ve `BinaryNumeral`, aralarında dönüşümleri gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
-   Önceki örnekte, deyim:  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     bir dönüştürme işlemini gerçekleştiren bir `RomanNumeral` için bir `BinaryNumeral`. Doğrudan dönüştürme yok olduğundan `RomanNumeral` için `BinaryNumeral`, bir cast dönüştürmek için kullanılan bir `RomanNumeral` için bir `int`ve dönüştürmek için başka bir cast bir `int` için bir `BinaryNumeral`.  
  
-   Ayrıca deyimi  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     bir dönüştürme işlemini gerçekleştiren bir `BinaryNumeral` için bir `RomanNumeral`. Çünkü `RomanNumeral` örtük bir dönüştürme tanımlar `BinaryNumeral`, tür atama yok gereklidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dönüştürme işleçleri](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
