---
title: Boolean İfadeleri
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
ms.openlocfilehash: 1000ec6e4b35d0cb2c6232b50f9a9551cb0dfdcd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350806"
---
# <a name="boolean-expressions-visual-basic"></a>Boolean İfadeleri (Visual Basic)
*Boole ifadesi* , [Boolean veri türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)değeri olarak değerlendirilen bir ifadedir: `True` veya `False`. `Boolean` ifadeler birkaç form alabilir. En basit, aşağıdaki örnekte gösterildiği gibi, bir `Boolean` değişkeninin değerinin `Boolean` değişmez değere doğrudan karşılaştırılmasının bir örneğidir.  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a>= Işlecinin iki anlamı  
 Atama deyiminin `newCustomer = True` önceki örnekteki ifadeyle aynı göründüğünden, ancak farklı bir işlev gerçekleştirdiğinden ve farklı şekilde kullanıldığını unutmayın. Önceki örnekte, `newCustomer = True` ifadesi bir Boolean değeri temsil eder ve `=` işareti bir karşılaştırma işleci olarak yorumlanır. Bağımsız bir ifadede, `=` işareti atama işleci olarak yorumlanır ve sağdaki değeri soldaki değişkene atar. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 Daha fazla bilgi için bkz. [değer karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) ve [deyimleri](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Karşılaştırma İşleçleri  
 `=`, `<`, `>`, `<>`, `<=`ve `>=` gibi karşılaştırma işleçleri, işlecin sol tarafındaki ifadesini işlecin sağ tarafındaki ifadeye karşılaştırarak ve sonucu `True` veya `False`olarak değerlendiren Boolean ifadeler üretir. Aşağıdaki örnek bunu göstermektedir.  
  
 `42 < 81`  
  
 42, 81 ' den az olduğu için, önceki örnekteki Boole ifadesi `True`olarak değerlendirilir. Bu tür bir ifade hakkında daha fazla bilgi için bkz. [değer karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Mantıksal Işleçlerle birleştirilmiş karşılaştırma Işleçleri  
 Karşılaştırma ifadeleri, daha karmaşık Boole ifadeleri oluşturmak için mantıksal işleçler kullanılarak birleştirilebilir. Aşağıdaki örnek, bir mantıksal işleçle birlikte karşılaştırma işleçleri kullanımını gösterir.  
  
 `x > y And x < 1000`  
  
 Yukarıdaki örnekte, genel ifadenin değeri, `And` işlecinin her tarafında ifadelerin değerlerine bağlıdır. Her iki ifade de `True`, genel ifade `True`olarak değerlendirilir. Her iki ifade de `False`, tüm ifade `False`olarak değerlendirilir.  
  
## <a name="short-circuiting-operators"></a>Kısa devre dışı Işleçler  
 Mantıksal işleçler `AndAlso` ve `OrElse` *kısa*devre olarak bilinen davranışı gösterir. Kısa devre dışı bir işleç, önce sol işleneni değerlendirir. Sol işlenen tüm ifadenin değerini belirlerse, program yürütmesi, doğru ifadeyi değerlendirmeden devam eder. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 Yukarıdaki örnekte işleç, `45 < 12`sol ifadeyi değerlendirir. Sol ifade `False`değerlendirdiği için, mantıksal ifadenin tamamı `False`olarak değerlendirilmelidir. Program yürütme, `testFunction(3)`doğru ifadeyi değerlendirmeden `If` bloğunda kodun yürütülmesini atlar. Sol ifade tüm ifadeyi aştığından bu örnek `testFunction()` çağırmaz.  
  
 Benzer şekilde, `OrElse` kullanan bir mantıksal ifadede sol ifade `True`değerlendirilirse, sol ifade zaten tüm ifadeyi doğruladı olduğundan, yürütme, doğru ifadeyi değerlendirmeden bir sonraki kod satırına geçer.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Kısa devre dışı özellikli Işleçlerle karşılaştırma  
 Buna karşılık, mantıksal işlecin her iki tarafı da `And` ve `Or` kullanıldığında değerlendirilir. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 Yukarıdaki örnek, sol ifade `False`olarak değerlendirilse de `testFunction()` çağırır.  
  
## <a name="parenthetical-expressions"></a>Parantez içinde Ifadeler  
 Boolean ifadelerin değerlendirilme sırasını denetlemek için parantezleri kullanabilirsiniz. Parantez içine alınmış ifadeler ilk olarak değerlendirilir. Birden çok iç içe geçme düzeyi için, en derin iç içe ifadelere öncelik verilir. Parantez içinde, değerlendirme işleç önceliği kurallarına göre devam eder. Daha fazla bilgi için [Visual Basic operatör önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Değer Karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Deyimler](../../../../visual-basic/programming-guide/language-features/statements.md)
- [Karşılaştırma İşleçleri](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Visual Basic operatör önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Boolean Veri Türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
