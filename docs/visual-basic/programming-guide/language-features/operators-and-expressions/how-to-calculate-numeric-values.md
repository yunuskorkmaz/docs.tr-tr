---
title: "Nasıl yapılır: Sayısal Değerleri Hesaplama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65cd446b99018d029e8a18d69ed33d8b8ac28f8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Nasıl yapılır: Sayısal Değerleri Hesaplama (Visual Basic)
Sayısal ifadeler kullanımıyla sayısal değerleri hesaplayabilirsiniz. A *sayısal ifade* değişmez değerleri, sabitleri ve değişkenleri sayısal değerleri temsil eden içeren bir ifade ve bu değerlere göre hareket işleçler.  
  
## <a name="calculating-numeric-values"></a>Sayısal değerlerini hesaplama  
  
#### <a name="to-calculate-a-numeric-value"></a>Sayısal bir değeri hesaplamak için  
  
-   Bir veya daha fazla sayısal değişmez değerleri, sabitleri ve değişkenleri bir sayısal ifadeye birleştirir. Aşağıdaki örnek, geçerli bazı sayısal ifadeler gösterir.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     İlk üç satırını bir hazır değer, bir sabit ve değişken gösterir. Her biri geçerli bir sayısal ifade tek başına oluşturur. Son satırı iki değişmez değerleri sahip bir değişken bileşimini gösterir.  
  
     Sayısal ifade tam bir form değil, Not [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] deyimi kendisi tarafından. Tam bir deyim bir parçası olarak ifade kullanmanız gerekir.  
  
#### <a name="to-store-a-numeric-value"></a>Sayısal bir değeri depolamak için  
  
-   Aşağıdaki örnekte gösterilmiştir gibi bir değişken için sayısal bir ifade tarafından temsil edilen değer atamak için bir atama deyimi kullanabilirsiniz.  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     Önceki örnekte, eşit işlecinin sağ tarafında ifadesinin değerini (`=`) değişkenine atanan `j` işlecinin sol tarafındaki şekilde `j` 276 için değerlendirir.  
  
     Daha fazla bilgi için bkz: [deyimleri](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Birden çok işleç  
 Sayısal ifade birden fazla işleci içeriyorsa, bunlar değerlendirilme sırasını İşleç önceliği kurallara göre belirlenir. İşleç önceliği kuralları geçersiz kılmak için yukarıdaki örnekte olduğu gibi parantez içinde ifadeler alın; Kapalı ifadeleri önce değerlendirilir.  
  
#### <a name="to-override-normal-operator-precedence"></a>Normal İşleç önceliği geçersiz kılmak için  
  
-   İlk gerçekleştirilmesini istediğiniz işlemleri kapsamak için ayraç kullanın. Aşağıdaki örnek aynı işlenenler ve işleçleri ile iki farklı sonuçlar gösterilir.  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     Önceki örnekte, hesaplama için `j` Toplama işleci gerçekleştirir (`+`) ilk çünkü parantezler `(67 + i)` normal öncelik ve atanan değer geçersiz kılmak `j` 276 (4 kez 69) değil. Hesaplama için `k` kendi normal öncelik işleçleri gerçekleştirir (`*` önce `+`) ve atanan değer `k` 270 (268 artı 2) değil.  
  
     Daha fazla bilgi için bkz: [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşleçler ve ifadeler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Değer karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Deyimleri](../../../../visual-basic/language-reference/statements/index.md)  
 [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Aritmetik işleçler](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [İşleçlerin etkili bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
