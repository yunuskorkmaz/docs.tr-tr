---
title: Değer Karşılaştırmaları
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: f766eaaada486a0f70838bafb754d25070ff4174
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346282"
---
# <a name="value-comparisons-visual-basic"></a>Değer Karşılaştırmaları (Visual Basic)
Karşılaştırma işleçleri, sayısal değişkenlerin değerlerini karşılaştıran ifadeler oluşturmak için kullanılabilir. Bu ifadeler, karşılaştırmanın doğru veya yanlış olduğunu temel alarak bir `Boolean` değeri döndürür. Bu tür bir ifadeye örnekler aşağıda verilmiştir.  
  
 `45 > 26`  
  
 `26 > 45`  
  
 45, 26 ' dan büyük olduğundan, ilk ifade `True`olarak değerlendirilir. `False`, 26 ' 45 dan büyük olmadığından, ikinci örnek olarak değerlendirilir.  
  
 Ayrıca, sayısal ifadeleri bu şekilde karşılaştırabilirsiniz. Karşılaştırılan ifadeler, aşağıdaki örnekte olduğu gibi karmaşık ifadeler olabilir.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 Önceki karmaşık ifade, değişmez değerler, değişkenler ve işlev çağrıları içerir. Karşılaştırma işlecinin her iki tarafındaki ifadeler değerlendirilir ve elde edilen değerler `>=` karşılaştırma işleci kullanılarak karşılaştırılır. Sol taraftaki ifadenin değeri sağdaki ifadenin değerinden büyükse veya eşitse, tüm ifade `True`olarak değerlendirilir. Aksi takdirde, `False`olarak değerlendirilir.  
  
 Değerleri karşılaştıran ifadeler, aşağıdaki örnekte olduğu gibi `If...Then` kurulumlarını ' de en yaygın olarak kullanılır.  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 `=` işareti, bir karşılaştırma operatörünün yanı sıra atama işleçtir. Karşılaştırma işleci olarak kullanıldığında, aşağıdaki örnekte gösterildiği gibi soldaki değerin sağdaki değere eşit olup olmadığını değerlendirir.  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 Karşılaştırma ifadesini, bir `If`, `While`, `Loop`veya `ElseIf` deyiminde olduğu gibi `Boolean` değerin her yerinde, ya da bir `Boolean` değişkenine atama ya da bir değere geçirilerek de kullanabilirsiniz. Aşağıdaki örnekte, karşılaştırma ifadesi tarafından döndürülen değer bir `Boolean` değişkenine atanır.  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Boole İfadeleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [İşleçler ve İfadeler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Visual Basic karşılaştırma Işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Nasıl yapılır: Sayısal Değerleri Hesaplama](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Visual Basic operatör önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)
