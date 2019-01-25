---
title: Boolean İfadeleri (Visual Basic)
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
ms.openlocfilehash: a86df2734d315e5fed0784b0394bb305b15562a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562758"
---
# <a name="boolean-expressions-visual-basic"></a>Boolean İfadeleri (Visual Basic)
A *Boole ifadesi* değeri olarak değerlendirilen bir ifade olan [Boole veri türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` veya `False`. `Boolean` ifadeler çeşitli biçimlerde olabilir. Basit doğrudan karşılaştırma değeri olan bir `Boolean` değişkenini bir `Boolean` sabit değer, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## <a name="two-meanings-of-the--operator"></a>İki anlamı = işleci  
 Dikkat atama ifadesi `newCustomer = True` önceki örnekte ifade olarak aynı görünür, ancak farklı bir işlev gerçekleştirir ve farklı şekilde kullanılır. Yukarıdaki örnekte, ifade `newCustomer = True` bir Boolean değeri temsil eder ve `=` oturum bir karşılaştırma işleci yorumlanır. Tek başına bir deyimde `=` oturum bir atama işleci yorumlanır ve sağdaki sol değişkenine bir değer atar. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 Daha fazla bilgi için bkz: [değer karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) ve [deyimleri](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Karşılaştırma İşleçleri  
 Karşılaştırma işleçleri gibi `=`, `<`, `>`, `<>`, `<=`, ve `>=` işlecin sağ tarafındaki ifade işlecinin sol tarafındaki ifade karşılaştırarak Boolean ifadeler üretmek işleç ve sonuç olarak değerlendiriliyor `True` veya `False`. Aşağıdaki örnek bunu göstermektedir.  
  
 `42 < 81`  
  
 42 81'den az olduğundan, önceki örnekte Boole ifadenin değerlendirdiği `True`. Bu tür bir ifade hakkında daha fazla bilgi için bkz. [değer karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Mantıksal işleçleri ile birlikte Karşılaştırma işleçleri  
 Karşılaştırma ifadeleri, daha karmaşık mantıksal ifadeleri oluşturmak için mantıksal işleçler kullanılarak birleştirilebilir. Aşağıdaki örnek, bir mantıksal işleci ile Karşılaştırma işleçleri birlikte kullanımını gösterir.  
  
 `x > y And x < 1000`  
  
 Önceki örnekte, her iki tarafındaki ifadeleri değerlerini genel ifadenin değerine bağımlı `And` işleci. Her iki ifade ise `True`, genel ifadenin değerlendirdiği sonra `True`. Her iki ifade ise `False`, ardından tüm ifadenin değerlendirdiği `False`.  
  
## <a name="short-circuiting-operators"></a>Kısa devre işleçleri  
 Mantıksal işleçler `AndAlso` ve `OrElse` olarak bilinen davranışlar *kısa devre*. Short-circuiting işleci sol işlenenin önce değerlendirir. Sol işlenen tüm ifadenin değerini belirlerse, program yürütme sağ ifade değerlendirmeden ilerler. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 Önceki örnekte, işlecin sol ifade değerlendirir `45 < 12`. Sol ifade için değerlendirdiğinden `False`, tüm mantıksal ifade değerlendirilmelidir `False`. Program yürütme, bu nedenle kodun içinde atlar `If` sağ ifade değerlendirme olmadan blok `testFunction(3)`. Bu örnek arama `testFunction()` tüm deyimin sol ifade falsifies olduğundan.  
  
 Benzer şekilde, varsa bir mantıksal ifade kullanarak sol ifade `OrElse` değerlendiren `True`, yürütme devam eder kodun sonraki satırına sağ ifade değerlendirmeden sol ifade zaten tüm doğruladı çünkü ifade.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Karşılaştırma işleçleri olmayan--kestirmeler  
 Bunun aksine, mantıksal işlecinin iki tarafı değerlendirilir, mantıksal işleçler `And` ve `Or` kullanılır. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 Önceki örneği çağrıları `testFunction()` sol ifadenin değerlendirdiği olsa bile `False`.  
  
## <a name="parenthetical-expressions"></a>Parantez içinde ifadeler  
 Boolean ifadelerin değerlendirilme sırasını denetlemek için parantez kullanabilirsiniz. İlk olarak parantez ifadeleri değerlendirin. Birden çok iç içe geçme düzeyi için en derin iç içe geçmiş ifadeler için öncelik verilir. Parantezler içinde İşleç önceliği kurallarına göre değerlendirme devam eder. Daha fazla bilgi için [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Değer Karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Deyimler](../../../../visual-basic/programming-guide/language-features/statements.md)
- [Karşılaştırma İşleçleri](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Boolean Veri Türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
