---
title: '?: İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 150149453a67d8e5319461266865cb25be180347
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506438"
---
# <a name="-operator-c-reference"></a>?: İşleci (C# Başvurusu)
Koşullu işleç (`?:`), yaygın olarak bilinen bir Üçlü koşullu işleç, bir Boolean ifadesinin değerine bağlı olarak iki değerden birini döndürür. Aşağıda, koşullu işlecin sözdizimi belirtilmiştir.  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `condition` Değerlendirilmelidir `true` veya `false`. Varsa `condition` olduğu `true`, `first_expression` değerlendirilir ve sonuç olur. Varsa `condition` olduğu `false`, `second_expression` değerlendirilir ve sonuç olur. İki ifadeden yalnızca biri değerlendirilir.  
  
 İki tür `first_expression` ve `second_expression` aynı olmalıdır veya bir örtük dönüştürme bir türden diğerine bulunmalıdır.  
  
 Aksi takdirde gerektirebilecek hesaplamaları ifade edebilirsiniz bir `if-else` koşullu işleç kullanarak daha kısaca oluşturma. Örneğin, aşağıdaki kod önce kullanan bir `if` deyimi ve sonra bir tamsayı artı veya eksi olarak sınıflandırmak için koşullu bir işleç.  
  
```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```  
  
 Koşullu işleç, sağa ilişkilendirilir. İfade `a ? b : c ? d : e` değerlendirmesinde `a ? b : (c ? d : e)`, olarak değil `(a ? b : c) ? d : e`.  
  
 Koşullu işleç aşırı yüklenemez.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)  
- [if-else](../../../csharp/language-reference/keywords/if-else.md)  
- [?. and ?[] İşleçleri](../../../csharp/language-reference/operators/null-conditional-operators.md)  
- [?? İşleç](../../../csharp/language-reference/operators/null-coalescing-operator.md)
