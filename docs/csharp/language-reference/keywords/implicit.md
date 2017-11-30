---
title: "implicit (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords: implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c893c7a9afbdc6f715010d537e9ccaf66c5785c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-c-reference"></a>implicit (C# Başvurusu)
`implicit` Anahtar sözcüğü bir örtük kullanıcı tanımlı tür dönüştürme işleci bildirmek için kullanılır. Dönüştürme veri kaybına neden değil garanti, kullanıcı tanımlı bir tür ve başka bir tür arasında örtük dönüşümler etkinleştirmek için kullanın.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 Örtük dönüşümler gereksiz atamalar ortadan kaldırarak, kaynak kodun okunabilirliğini artırabilir. Ancak, örtük dönüşümler açıkça bir türden diğerine dönüştürün programcıların gerektirmediği için beklenmeyen sonuçlara önlemek için dikkatli olunmalıdır. Genel olarak, örtük dönüşüm işleçleri hiçbir zaman özel durumlar oluşturma ve bu böylece Programcı tanıma güvenli bir şekilde kullanılabilir bilgileri hiçbir zaman kaybedersiniz gerekir. Bir dönüşüm işleci Bu ölçütleri karşılayan olamaz, işaretlenmelidir `explicit`. Daha fazla bilgi için bkz: [dönüşüm işleçleri kullanma](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [açık](../../../csharp/language-reference/keywords/explicit.md)  
 [işleci (C# Başvurusu)](../../../csharp/language-reference/keywords/operator.md)  
 [Nasıl yapılır: yapılar arasında kullanıcı tanımlı dönüşümler](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
