---
title: implicit (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: 160d9f7c0d58abd685bf1d799b53cc96a26aebe8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215023"
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)  
 [İşleci (C# Başvurusu)](../../../csharp/language-reference/keywords/operator.md)  
 [Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
