---
title: 'Nasıl yapılır: -Yapılar arasında kullanıcı tanımlı Dönüşümler Uygulama C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: bc792562b4849d402e03328e50dedac030520011
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710049"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a>Nasıl yapılır: Yapılar arasında kullanıcı tanımlı Dönüşümler Uygulama (C# Programlama Kılavuzu)
Bu örnek iki yapıları tanımlar `RomanNumeral` ve `BinaryNumeral`ve bunlar arasında dönüştürmeler gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideStatements#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#13)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
- Önceki örnekte, deyim:  
  
     [!code-csharp[csProgGuideStatements#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#14)]  
  
     bir dönüştürme gerçekleştiren bir `RomanNumeral` için bir `BinaryNumeral`. Doğrudan dönüşüm yok olduğundan `RomanNumeral` için `BinaryNumeral`, bir yayın dönüştürmek için kullanılan bir `RomanNumeral` için bir `int`ve dönüştürmek için başka bir tür dönüştürme bir `int` için bir `BinaryNumeral`.  
  
- Ayrıca deyimi  
  
     [!code-csharp[csProgGuideStatements#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#15)]  
  
     bir dönüştürme gerçekleştiren bir `BinaryNumeral` için bir `RomanNumeral`. Çünkü `RomanNumeral` örtük bir dönüştürme tanımlar `BinaryNumeral`, atama gereklidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Dönüştürme İşleçleri](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
