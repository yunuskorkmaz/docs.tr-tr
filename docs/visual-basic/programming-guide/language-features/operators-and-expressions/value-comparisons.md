---
title: Değer Karşılaştırmaları (Visual Basic)
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
ms.openlocfilehash: 23733741a79506730187d5735a20f3848e43da1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724820"
---
# <a name="value-comparisons-visual-basic"></a>Değer Karşılaştırmaları (Visual Basic)
Karşılaştırma işleçleri, sayısal değişkenlerin değerleri karşılaştırma ifadeleri oluşturmak için kullanılabilir. Bu ifadeler dönüş bir `Boolean` değerine göre karşılaştırma doğru olmasına göre ya da yanlış. Böyle bir ifade örnekleri aşağıdaki gibidir.  
  
 `45 > 26`  
  
 `26 > 45`  
  
 İlk ifadenin değerlendirdiği `True`45 26 büyük olduğu için. İkinci örnek değerlendiren `False`, 26 45 büyük değil.  
  
 Sayısal ifadeler bu şekilde de karşılaştırabilirsiniz. Aşağıdaki örnekte olduğu gibi karmaşık ifadeler, karşılaştırma ifadeleri kendilerini olabilir.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 Önceki karmaşık ifadesi, değişmez değerleri ve değişkenleri işlev çağrılarını içerir. Karşılaştırma işlecinin her iki tarafında ifadeler değerlendirilir ve elde edilen değerleri, ardından kullanılarak karşılaştırılır `>=` karşılaştırma işleci. Sol tarafta bir ifadenin değerine büyüktür veya sağdaki ifadesinin değerine eşit tüm ifadenin değerlendirdiği `True`; Aksi takdirde olarak değerlendirilen `False`.  
  
 Değerleri karşılaştırma ifadeleri en yaygın olarak kullanılır `If...Then` yapılarını aşağıdaki örnekte olduğu gibi.  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 `=` İşaretidir bir atama işleci yanı sıra bir karşılaştırma işleci. Aşağıdaki örnekte gösterildiği gibi soldaki değerin sağdaki değerine eşit olup olmadığını bir karşılaştırma işleci kullanıldığında, değerlendirir.  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 Karşılaştırma ifadesindeki her yerde kullanabilirsiniz bir `Boolean` değerdir gerekli, olduğu gibi bir `If`, `While`, `Loop`, veya `ElseIf` deyimi, atama veya bir değere geçirerek bir `Boolean` değişkeni. Aşağıdaki örnekte, karşılaştırma ifadesi tarafından döndürülen değer atanmış bir `Boolean` değişkeni.  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Boole İfadeleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [İşleçler ve İfadeler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Visual Basic'de Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Nasıl yapılır: Sayısal değerleri hesaplama](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)
