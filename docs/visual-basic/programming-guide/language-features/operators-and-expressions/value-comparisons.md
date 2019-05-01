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
ms.openlocfilehash: 270b226d0a1aa7d08721e6f9ed36d68492685af3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864397"
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
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 `=` İşaretidir bir atama işleci yanı sıra bir karşılaştırma işleci. Aşağıdaki örnekte gösterildiği gibi soldaki değerin sağdaki değerine eşit olup olmadığını bir karşılaştırma işleci kullanıldığında, değerlendirir.  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 Karşılaştırma ifadesindeki her yerde kullanabilirsiniz bir `Boolean` değerdir gerekli, olduğu gibi bir `If`, `While`, `Loop`, veya `ElseIf` deyimi, atama veya bir değere geçirerek bir `Boolean` değişkeni. Aşağıdaki örnekte, karşılaştırma ifadesi tarafından döndürülen değer atanmış bir `Boolean` değişkeni.  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Boole İfadeleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [İşleçler ve İfadeler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Visual Basic'de Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Nasıl yapılır: Sayısal değerleri hesaplama](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)
