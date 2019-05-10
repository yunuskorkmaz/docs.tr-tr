---
title: Visual Basic'de İşleçler ve İfadeler
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
ms.openlocfilehash: 40d71c5231b8d278f4ca8d9352e6e3cba5104f9b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649702"
---
# <a name="operators-and-expressions-in-visual-basic"></a>Visual Basic'de İşleçler ve İfadeler
Bir *işleci* değerlerini tutan bir veya daha fazla kod öğeleri üzerinde bir işlem gerçekleştiren bir kod öğedir. Değişkenleri, sabitleri, sabit değerleri, özellikleri, değeri öğeleri dahil döndürür `Function` ve `Operator` yordamları ve ifadeler.  
  
 Bir *ifade* yeni bir değer veren bir dizi değeri öğeleri işleçleri ile birlikte. İşleçler, değeri öğeleri üzerinde hesaplamalar, karşılaştırmaları veya diğer işlemleri gerçekleştirerek işlevi görür.  
  
## <a name="types-of-operators"></a>Tür işleç  
 Visual Basic işleçleri aşağıdaki türlerini sağlar:  
  
- [Aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) , bit düzenleri kaydırma gibi sayısal değerleri üzerinde tanıdık hesaplamalar.  
  
- [Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) iki ifadeden karşılaştırın ve dönüş bir `Boolean` Karşılaştırmanın sonucu temsil eden değer.  
  
- [Birleştirme işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) tek bir dize olarak birden çok dizeyi birleştirme.  
  
- [Mantıksal ve bit düzeyinde işleçler Visual Basic'te](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) birleştirmek `Boolean` veya sayısal değerler ve değerlerin aynı veri türünde bir sonuç döndürür.  
  
 Operatör ile birleştirilmiş değer öğeleri adlı *işlenenler* bu işleci. İşleçleri birleşik atama işleci hariç değer öğeleri form ifadeleri ile hangi formların bir *deyimi*. Daha fazla bilgi için [deyimleri](../../../../visual-basic/programming-guide/language-features/statements.md).  
  
## <a name="evaluation-of-expressions"></a>İfade değerlendirme  
 Bir ifadenin sonuç genellikle tanıdık veri türünde olduğu gibi bir değeri temsil eder `Boolean`, `String`, veya bir sayısal tür.  
  
 Örnekleri aşağıda verilmiştir.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Aşağıdaki örnekte gösterildiği gibi birkaç işleç bir tek ifadesi veya deyimi, eylemler gerçekleştirebilirsiniz.  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 Önceki örnekte, Visual Basic ifade işlemlerinde atama işlecinin sağ tarafında gerçekleştirir (`=`), ardından sonuç değerini değişkenine atar `x` soldaki. Bir ifade ancak bir anlayış birleştirilebilir işleçleri dizi pratik bir sınır yoktur [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md) beklediğiniz sonuçları aldığınızdan emin olmak gereklidir.  

## <a name="see-also"></a>Ayrıca bkz.

- [İşleçler](../../../../visual-basic/language-reference/operators/index.md)
- [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Deyimler](../../../../visual-basic/language-reference/statements/index.md)
