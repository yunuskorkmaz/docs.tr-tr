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
ms.openlocfilehash: 68e7daac63a5f7d9bd1f48adfdee973bd695a13e
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
---
# <a name="-operator-c-reference"></a>?: İşleci (C# Başvurusu)
Koşullu işleç (`?:`), yaygın olarak bilinen Üçlü koşullu işleç Boole ifadesi değerine bağlı olarak iki değerden birini döndürür. Aşağıda, koşullu işlecin sözdizimi belirtilmiştir.  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `condition` Değerlendirilmelidir `true` veya `false`. Varsa `condition` olan `true`, `first_expression` değerlendirilir ve sonucu olur. Varsa `condition` olan `false`, `second_expression` değerlendirilir ve sonucu olur. İki ifadeden yalnızca biri değerlendirilir.  
  
 İki tür `first_expression` ve `second_expression` aynı olmalı ya da örtük bir dönüştürme bir türden diğerine bulunmalıdır.  
  
 Aksi takdirde gerektirebilir hesaplamalar express bir `if-else` koşullu işleç kullanarak daha az ama öz oluşturma. Örneğin, aşağıdaki kodu ilk kullanan bir `if` deyimi ve tamsayı olumlu veya olumsuz olarak sınıflandırmak için koşullu bir işleç.  
  
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
  
 Koşullu işleç, sağa ilişkilendirilir. İfade `a ? b : c ? d : e` olarak değerlendirilir `a ? b : (c ? d : e)`, olarak değil `(a ? b : c) ? d : e`.  
  
 Koşullu işleç aşırı yüklenemez.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)  
 [if-else](../../../csharp/language-reference/keywords/if-else.md)  
 [?. and ?[] İşleçleri](../../../csharp/language-reference/operators/null-conditional-operators.md)  
 [?? İşleç](../../../csharp/language-reference/operators/null-coalescing-operator.md)
