---
title: İşleçler ve İfadeler
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: fa410a739be2da8802e76a35068448263ddec1fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343606"
---
# <a name="operators-and-expressions-in-visual-basic"></a>Visual Basic'de İşleçler ve İfadeler
*İşleç* , değerleri tutan bir veya daha fazla kod öğesi üzerinde bir işlem gerçekleştiren bir kod öğesidir. Değer öğeleri arasında değişkenler, sabitler, sabit değerler, özellikler, `Function` ve `Operator` yordamlarından ve ifadelerden döndürülür.  
  
 *İfade* , yeni bir değer veren işleçlerle birleştirilmiş bir değer öğeleri dizisidir. İşleçler, hesaplamalar, karşılaştırmalar veya diğer işlemleri gerçekleştirerek değer öğelerine davranır.  
  
## <a name="types-of-operators"></a>Işleç türleri  
 Visual Basic aşağıdaki işleç türlerini sağlar:  
  
- [Aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) , bit desenlerini kaydırma da dahil olmak üzere sayısal değerlerde tanıdık hesaplamalar gerçekleştirir.  
  
- [Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) iki ifadeyi karşılaştırır ve karşılaştırmanın sonucunu temsil eden bir `Boolean` değeri döndürür.  
  
- [Birleştirme işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) birden çok dizeyi tek bir dizeye birleştirir.  
  
- [Visual Basic mantıksal ve bit düzeyinde işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) `Boolean` veya sayısal değerleri birleştirir ve değerlerle aynı veri türünün bir sonucunu döndürür.  
  
 Bir işleçle birleştirilmiş değer öğelerine, bu işlecin *işlenenleri* adı verilir. İşleç, bir *deyimi*oluşturan atama işleci dışında, değer öğeleri form ifadeleriyle birleştirilir. Daha fazla bilgi için bkz. [deyimler](../../../../visual-basic/programming-guide/language-features/statements.md).  
  
## <a name="evaluation-of-expressions"></a>Ifadelerin değerlendirmesi  
 Bir ifadenin nihai sonucu, genellikle `Boolean`, `String`veya sayısal bir tür gibi tanıdık bir veri türü olan bir değeri temsil eder.  
  
 Aşağıda ifade örnekleri verilmiştir.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Aşağıdaki örnekte gösterildiği gibi, birkaç işleç tek bir ifadede veya deyimde eylemler gerçekleştirebilir.  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 Yukarıdaki örnekte, Visual Basic atama işlecinin sağ tarafındaki ifadedeki işlemleri gerçekleştirir (`=`), ardından sonuç değerini soldaki değişkene `x` atar. Bir ifadede birleştirilebilecek işleç sayısında pratik bir sınır yoktur, ancak istediğiniz sonuçları aldığınızdan emin olmak için [Visual Basic operatör önceliğin](../../../../visual-basic/language-reference/operators/operator-precedence.md) anlaşılmasına gerek kalmaz.  

## <a name="see-also"></a>Ayrıca bkz.

- [işleçler](../../../../visual-basic/language-reference/operators/index.md)
- [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Deyimler](../../../../visual-basic/language-reference/statements/index.md)
