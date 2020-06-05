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
ms.openlocfilehash: 01816b5730cf4fda61f1737ce3ce00ab82f57da8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403401"
---
# <a name="value-comparisons-visual-basic"></a>Değer Karşılaştırmaları (Visual Basic)
Karşılaştırma işleçleri, sayısal değişkenlerin değerlerini karşılaştıran ifadeler oluşturmak için kullanılabilir. Bu ifadeler `Boolean` , karşılaştırmanın doğru veya yanlış olduğunu temel alarak bir değer döndürür. Bu tür bir ifadeye örnekler aşağıda verilmiştir.  
  
 `45 > 26`  
  
 `26 > 45`  
  
 `True`45, 26 ' dan büyük olduğu için ilk ifade olarak değerlendirilir. İkinci örnek olarak değerlendirilir `False` , çünkü 26 45 ' den büyük değildir.  
  
 Ayrıca, sayısal ifadeleri bu şekilde karşılaştırabilirsiniz. Karşılaştırılan ifadeler, aşağıdaki örnekte olduğu gibi karmaşık ifadeler olabilir.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 Önceki karmaşık ifade, değişmez değerler, değişkenler ve işlev çağrıları içerir. Karşılaştırma işlecinin her iki tarafındaki ifadeler değerlendirilir ve elde edilen değerler `>=` karşılaştırma işleci kullanılarak karşılaştırılır. Sol taraftaki ifadenin değeri sağdaki ifadenin değerinden büyükse veya eşitse, tüm ifade olarak değerlendirilir `True` ; Aksi takdirde, olarak değerlendirilir `False` .  
  
 Değerleri karşılaştıran ifadeler `If...Then` , aşağıdaki örnekte olduğu gibi en yaygın olarak kurulumlarını ' de kullanılır.  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 İşaret, bir `=` karşılaştırma operatörünün yanı sıra bir atama işleçtir. Karşılaştırma işleci olarak kullanıldığında, aşağıdaki örnekte gösterildiği gibi soldaki değerin sağdaki değere eşit olup olmadığını değerlendirir.  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 Bir karşılaştırma ifadesini, bir `Boolean` `If` ,, veya deyiminde, ya da bir `While` `Loop` `ElseIf` değişkene atama ya da bir değere geçirilerek olduğu `Boolean` gibi her yerde bir değer gerekli olduğunda da kullanabilirsiniz. Aşağıdaki örnekte, karşılaştırma ifadesinin döndürdüğü değer bir `Boolean` değişkene atanır.  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Boole Ifadeleri](boolean-expressions.md)
- [İşleçler ve Ifadeler](index.md)
- [Visual Basic'de Karşılaştırma İşleçleri](comparison-operators.md)
- [Nasıl yapılır: Sayısal Değerleri Hesaplama](how-to-calculate-numeric-values.md)
- [Visual Basic'de İşleç Önceliği](../../../language-reference/operators/operator-precedence.md)
