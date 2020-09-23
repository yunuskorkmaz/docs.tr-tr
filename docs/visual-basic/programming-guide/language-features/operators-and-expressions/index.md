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
ms.openlocfilehash: 01e3a53e998774caee8863675b9151a140606852
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071683"
---
# <a name="operators-and-expressions-in-visual-basic"></a>Visual Basic'de İşleçler ve İfadeler

*İşleç* , değerleri tutan bir veya daha fazla kod öğesi üzerinde bir işlem gerçekleştiren bir kod öğesidir. Değer öğeleri arasında değişkenler, sabitler, sabit değerler, özellikler, dönüş `Function` ve `Operator` yordamlar ve ifadeler bulunur.  
  
 *İfade* , yeni bir değer veren işleçlerle birleştirilmiş bir değer öğeleri dizisidir. İşleçler, hesaplamalar, karşılaştırmalar veya diğer işlemleri gerçekleştirerek değer öğelerine davranır.  
  
## <a name="types-of-operators"></a>Işleç türleri  

 Visual Basic aşağıdaki işleç türlerini sağlar:  
  
- [Aritmetik işleçler](arithmetic-operators.md) , bit desenlerini kaydırma da dahil olmak üzere sayısal değerlerde tanıdık hesaplamalar gerçekleştirir.  
  
- [Karşılaştırma işleçleri](comparison-operators.md) iki ifadeyi karşılaştırır ve `Boolean` karşılaştırmanın sonucunu temsil eden bir değer döndürür.  
  
- [Birleştirme işleçleri](concatenation-operators.md) birden çok dizeyi tek bir dizeye birleştirir.  
  
- [Visual Basic birleştiren mantıksal ve bit düzeyinde işleçler](logical-and-bitwise-operators.md) `Boolean` ve değerler ile aynı veri türünde bir sonuç döndürür.  
  
 Bir işleçle birleştirilmiş değer öğelerine, bu işlecin *işlenenleri* adı verilir. İşleç, bir *deyimi*oluşturan atama işleci dışında, değer öğeleri form ifadeleriyle birleştirilir. Daha fazla bilgi için bkz. [deyimler](../statements.md).  
  
## <a name="evaluation-of-expressions"></a>Ifadelerin değerlendirmesi  

 Bir ifadenin nihai sonucu, genellikle,, veya sayısal bir tür gibi tanıdık bir veri türü olan bir değeri temsil eder `Boolean` `String` .  
  
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
  
 Yukarıdaki örnekte, Visual Basic atama işlecinin () sağ tarafındaki ifadedeki işlemleri gerçekleştirir `=` , ardından sonuç değerini soldaki değişkene atar `x` . Bir ifadede birleştirilebilecek işleç sayısında pratik bir sınır yoktur, ancak istediğiniz sonuçları aldığınızdan emin olmak için [Visual Basic operatör önceliğin](../../../language-reference/operators/operator-precedence.md) anlaşılmasına gerek kalmaz.  

## <a name="see-also"></a>Ayrıca bkz.

- [İşleçler](../../../language-reference/operators/index.md)
- [İşleçlerin Etkili Bileşimi](efficient-combination-of-operators.md)
- [Deyimler](../../../language-reference/statements/index.md)
