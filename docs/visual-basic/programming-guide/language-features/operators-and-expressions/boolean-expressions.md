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
ms.openlocfilehash: ff5843c815658468ac69fe5d62a9ea4cac2be830
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655804"
---
# <a name="boolean-expressions-visual-basic"></a>Boolean İfadeleri (Visual Basic)
A *Boole ifadesi* değeri veren ifade [Boole veri türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` veya `False`. `Boolean` ifadeler çeşitli biçimlerde olabilir. Değerini doğrudan karşılaştırması kolayıdır bir `Boolean` için değişken bir `Boolean` değişmez değeri, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## <a name="two-meanings-of-the--operator"></a>İki anlamı = işleci  
 Dikkat atama ifadesi `newCustomer = True` aynı önceki örnekte ifade olarak görünür, ancak farklı bir işlevi gerçekleştirir ve farklı bir şekilde kullanılır. Önceki örnekte, ifade `newCustomer = True` bir Boole değeri temsil eder ve `=` oturum bir karşılaştırma işleci yorumlanır. Tek başına bir deyimde `=` oturum atama işleci yorumlanır ve değer sağındaki soldaki değişkenine atar. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 Daha fazla bilgi için bkz: [değer karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) ve [deyimleri](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Karşılaştırma İşleçleri  
 Karşılaştırma işleçleri gibi `=`, `<`, `>`, `<>`, `<=`, ve `>=` sol tarafındaki ifade işlecinin sağ tarafında ifadeye karşılaştırarak Boole ifadeleri oluşturmak işleç ve sonuç olarak değerlendiriliyor `True` veya `False`. Aşağıdaki örnek bunu göstermektedir.  
  
 `42 < 81`  
  
 Önceki örnekte Boole ifadesi 42 81'den az olduğundan, değerlendiren `True`. Bu tür bir ifade hakkında daha fazla bilgi için bkz: [değer karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Mantıksal işleçlerle birleştirilmiş Karşılaştırma işleçleri  
 Karşılaştırma ifadeleri, daha karmaşık Boole ifadeleri oluşturmak için mantıksal işleçleri kullanılarak birleştirilebilir. Aşağıdaki örnek, bir mantıksal işleç ile birlikte Karşılaştırma işleçleri kullanımını göstermektedir.  
  
 `x > y And x < 1000`  
  
 Önceki örnekte, her tarafında ifadelerin değerlerini genel ifadesinin değerini bağlıdır `And` işleci. Her iki ifadeler `True`, genel ifade değerlendiren sonra `True`. Ya da ifade ise `False`, tüm deyimin değerlendiren sonra `False`.  
  
## <a name="short-circuiting-operators"></a>İşleçler kısa devre  
 Mantıksal işleçler `AndAlso` ve `OrElse` olarak bilinen davranışlar *kısa devre*. Short-circuiting işleci sol işleneni önce değerlendirir. Tüm ifadenin değerini sol işleneni karar verirse, program yürütme sağ ifade değerlendirmeden ilerler. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 Önceki örnekte, sol ifade işleci değerlendirir `45 < 12`. Sol ifade için değerlendirildiği `False`, tüm mantıksal ifade değerlendirilmelidir `False`. Program yürütme böylece içindeki kod yürütülmesi atlanıyor `If` sağ ifade değerlendirme olmadan blok `testFunction(3)`. Bu örnek arama `testFunction()` tüm deyimin sol ifade falsifies olduğundan.  
  
 Benzer şekilde, mantıksal ifade kullanarak sol ifade `OrElse` değerlendiren `True`, yürütme devam eder kodunun bir sonraki satıra sağ ifade değerlendirmeden sol ifade zaten tüm doğruladı olduğundan ifade.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Olmayan--kestirmeler işleçleri ile karşılaştırma  
 Bunun aksine, mantıksal işlecinin iki tarafı da değerlendirilir zaman mantıksal işleçler `And` ve `Or` kullanılır. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 Yukarıdaki örnek çağrıları `testFunction()` sol ifade değerlendiren olsa bile `False`.  
  
## <a name="parenthetical-expressions"></a>Parantez içinde ifadeler  
 Boole ifadeleri Değerlendirme sırasını denetlemek için parantez kullanabilirsiniz. Parantez ifadeleri ilk değerlendirin. Birden çok iç içe geçme düzeyi için en fazla iç içe geçmiş ifadeler öncelik verilir. Parantez içinde İşleç önceliği kurallarına göre değerlendirme devam eder. Daha fazla bilgi için bkz: [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Değer Karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Deyimler](../../../../visual-basic/programming-guide/language-features/statements.md)  
 [Karşılaştırma İşleçleri](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Boolean Veri Türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
