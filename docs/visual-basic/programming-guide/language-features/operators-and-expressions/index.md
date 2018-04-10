---
title: Visual Basic'de İşleçler ve İfadeler
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dae47988e27ed4b1a714943ce1fbffe3b815066b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="operators-and-expressions-in-visual-basic"></a>Visual Basic'de İşleçler ve İfadeler
Bir *işleci* değerlerini tutan bir veya daha fazla kod öğeleri üzerinde bir işlemi gerçekleştiren bir kod öğedir. Değer öğeleri dahil değişkenlerinin, sabitleri, değişmez değerleri, özellikler, döndürür `Function` ve `Operator` yordamları ve ifadeler.  
  
 Bir *ifade* yeni bir değer veren bir dizi işleçleri ile birleştirilmiş değer öğeleri. İşleçler hesaplamalar, karşılaştırmaları veya diğer işlemleri gerçekleştirerek değeri öğeleri görür.  
  
## <a name="types-of-operators"></a>İşleçler türleri  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Aşağıdaki işleçleri türlerini sağlar:  
  
-   [Aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) bunların bit şekillerine kaydırma dahil olmak üzere sayısal değerleri tanıdık hesaplamalar.  
  
-   [Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) iki ifadeye karşılaştırır ve dönüş bir `Boolean` karşılaştırma sonucunu temsil eden değer.  
  
-   [Birleştirme işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) tek bir dize halinde birden çok dizeyi birleştirme.  
  
-   [Mantıksal ve bit düzeyinde işleçler Visual Basic'te](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) birleştirmek `Boolean` veya sayısal değerler ve değerlerin aynı veri türünde bir sonuç döndürür.  
  
 Bir operatör ile birleştirilmiş değer öğeleri adlı *işlenenler* bu işleç. İşleçler atama işleci dışında değer öğeleri form ifadeleri hangi formların birlikte bir *deyimi*. Daha fazla bilgi için bkz: [deyimleri](../../../../visual-basic/programming-guide/language-features/statements.md).  
  
## <a name="evaluation-of-expressions"></a>İfade değerlendirme  
 Sonuç ifade genellikle tanıdık veri türü gibi bir değeri temsil eder `Boolean`, `String`, veya sayısal bir tür.  
  
 İfadeleri örnekleri verilmiştir.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Aşağıdaki örnekte gösterildiği gibi çeşitli işleçler bir tek ifadesi veya deyimi, eylemleri gerçekleştirebilirsiniz.  
  
 [!code-vb[VbVbalrOperators#56](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/index_1.vb)]  
  
 Önceki örnekte [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] atama işlecinin sağ tarafındaki ifade işlemleri gerçekleştirir (`=`), ardından sonuç değeri değişkenine atar `x` soldaki. Bir ifade, ancak bir anlayış birleştirilebilir işleçleri sayısına pratik bir sınır yoktur [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md) beklediğiniz sonuçları aldığından emin olmak gereklidir.  
  
 Daha fazla bilgi ve örnekler için bkz: [İşleç aşırı yüklemesi Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşleçler](../../../../visual-basic/language-reference/operators/index.md)  
 [İşleçlerin etkili bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [Deyimleri](../../../../visual-basic/language-reference/statements/index.md)
