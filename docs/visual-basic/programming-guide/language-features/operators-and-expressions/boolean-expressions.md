---
title: "Boolean İfadeleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 48071c6833f9841fa42311dda59d6959c0645ff4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="boolean-expressions-visual-basic"></a>Boolean İfadeleri (Visual Basic)
A *Boole ifadesi* değeri veren ifade [Boole veri türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` veya `False`. `Boolean`ifadeler çeşitli biçimlerde olabilir. Değerini doğrudan karşılaştırması kolayıdır bir `Boolean` için değişken bir `Boolean` değişmez değeri, aşağıdaki örnekte gösterildiği gibi.  
  
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
 [Değer karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Deyimleri](../../../../visual-basic/programming-guide/language-features/statements.md)  
 [Karşılaştırma işleçleri](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [İşleçlerin etkili bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Boole veri türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
