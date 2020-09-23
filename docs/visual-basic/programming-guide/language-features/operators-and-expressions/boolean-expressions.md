---
title: Boole İfadeleri
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
ms.openlocfilehash: 51340bf95795d837c055df796424f3cad912adc7
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085756"
---
# <a name="boolean-expressions-visual-basic"></a>Boolean İfadeleri (Visual Basic)

*Boole ifadesi* , [Boolean veri türü](../../../language-reference/data-types/boolean-data-type.md)değeri olarak değerlendirilen bir ifadedir: `True` veya `False` . `Boolean` ifadeler birkaç form alabilir. En basit, `Boolean` `Boolean` Aşağıdaki örnekte gösterildiği gibi, bir değişkenin değerinin bir sabit değere doğrudan karşılaştırılmasının en kolayıdır.  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a>= Işlecinin iki anlamı  

 Atama deyiminin `newCustomer = True` önceki örnekteki ifadeyle aynı göründüğünü, ancak farklı bir işlev gerçekleştirdiğini ve farklı şekilde kullanıldığını unutmayın. Yukarıdaki örnekte, ifadesi `newCustomer = True` bir Boolean değeri temsil eder ve `=` işaret bir karşılaştırma işleci olarak yorumlanır. Bağımsız bir ifadede, `=` işaret atama işleci olarak yorumlanır ve sağdaki değeri soldaki değişkene atar. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 Daha fazla bilgi için bkz. [değer karşılaştırmaları](value-comparisons.md) ve [deyimleri](../../../language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Karşılaştırma İşleçleri  

 ,,,, Ve gibi karşılaştırma işleçleri, `=` `<` `>` `<>` `<=` `>=` işlecin sol tarafındaki ifadesini işlecin sağ tarafındaki ifadeye karşılaştıran ve sonucu veya olarak değerlendiren Boolean ifadeler üretir `True` `False` . Aşağıdaki örnek bunu göstermektedir.  
  
 `42 < 81`  
  
 42, 81 ' den az olduğu için, önceki örnekteki Boole ifadesi olarak değerlendirilir `True` . Bu tür bir ifade hakkında daha fazla bilgi için bkz. [değer karşılaştırmaları](value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Mantıksal Işleçlerle birleştirilmiş karşılaştırma Işleçleri  

 Karşılaştırma ifadeleri, daha karmaşık Boole ifadeleri oluşturmak için mantıksal işleçler kullanılarak birleştirilebilir. Aşağıdaki örnek, bir mantıksal işleçle birlikte karşılaştırma işleçleri kullanımını gösterir.  
  
 `x > y And x < 1000`  
  
 Yukarıdaki örnekte, genel ifadenin değeri, işlecin her tarafındaki ifadelerin değerlerine bağlıdır `And` . Her iki ifade de ise `True` , genel ifade olarak değerlendirilir `True` . Her iki ifade ise `False` , tüm ifade olarak değerlendirilir `False` .  
  
## <a name="short-circuiting-operators"></a>Kısa devre dışı Işleçler  

 Mantıksal işleçler `AndAlso` ve `OrElse` *kısa*devre olarak bilinen bir davranış gösterir. Kısa devre dışı bir işleç, önce sol işleneni değerlendirir. Sol işlenen tüm ifadenin değerini belirlerse, program yürütmesi, doğru ifadeyi değerlendirmeden devam eder. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 Önceki örnekte, işleç sol ifadeyi değerlendirir `45 < 12` . Sol ifade olarak değerlendirdiği için `False` , mantıksal ifadenin tamamı olarak değerlendirilmelidir `False` . Böylece program yürütme `If` , sağ ifadeyi değerlendirmeksizin blok içindeki kodun yürütülmesini atlar `testFunction(3)` . `testFunction()`Sol ifade tüm ifadeyi aştığından bu örnek çağırmaz.  
  
 Benzer şekilde, bir mantıksal ifadedeki sol ifade `OrElse` olarak değerlendirilir `True` ,, sol ifade ifadenin tamamını zaten doğrulayan, yürütme, doğru ifadeyi değerlendirmeden bir sonraki kod satırına geçer.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Kısa devre dışı özellikli Işleçlerle karşılaştırma  

 Buna karşılık, mantıksal işlecin her iki tarafı da mantıksal işleçler ve kullanıldığı zaman değerlendirilir `And` `Or` . Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 Yukarıdaki örnek, `testFunction()` sol ifade olarak değerlendirilse de çağırır `False` .  
  
## <a name="parenthetical-expressions"></a>Parantez içinde Ifadeler  

 Boolean ifadelerin değerlendirilme sırasını denetlemek için parantezleri kullanabilirsiniz. Parantez içine alınmış ifadeler ilk olarak değerlendirilir. Birden çok iç içe geçme düzeyi için, en derin iç içe ifadelere öncelik verilir. Parantez içinde, değerlendirme işleç önceliği kurallarına göre devam eder. Daha fazla bilgi için [Visual Basic operatör önceliği](../../../language-reference/operators/operator-precedence.md)bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler](logical-and-bitwise-operators.md)
- [Değer Karşılaştırmaları](value-comparisons.md)
- [Deyimler](../statements.md)
- [Karşılaştırma Işleçleri](../../../language-reference/operators/comparison-operators.md)
- [İşleçlerin Etkili Bileşimi](efficient-combination-of-operators.md)
- [Visual Basic'de İşleç Önceliği](../../../language-reference/operators/operator-precedence.md)
- [Boolean Veri Türü](../../../language-reference/data-types/boolean-data-type.md)
