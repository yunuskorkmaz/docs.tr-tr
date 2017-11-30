---
title: "?: İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9abfe4ca6be29b54edd591b503069c15e02c3532
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>?: İşleci (C# Başvurusu)
Koşullu işleç (`?:`) Boole ifadesi değerine bağlı olarak iki değerden birini döndürür. Aşağıda, koşullu işlecin sözdizimi belirtilmiştir.  
  
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
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# işleçleri](../../../csharp/language-reference/operators/index.md)  
 [if-else](../../../csharp/language-reference/keywords/if-else.md)  
 [?. ve? İşleçler](../../../csharp/language-reference/operators/null-conditional-operators.md)  
 [?? İşleci](../../../csharp/language-reference/operators/null-conditional-operator.md)
