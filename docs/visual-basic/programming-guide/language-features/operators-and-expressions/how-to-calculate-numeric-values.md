---
title: 'Nasıl yapılır: Sayısal Değerleri Hesaplama (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: cf24d7259ac04f6901497c81558a4d59b340eec7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649792"
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
  
     Sayısal ifade tam bir Visual Basic deyim tek başına oluşturmuyor olduğunu unutmayın. Tam bir deyim bir parçası olarak ifade kullanmanız gerekir.  
  
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
 [İşleçler ve İfadeler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Değer Karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Deyimler](../../../../visual-basic/language-reference/statements/index.md)  
 [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Aritmetik İşleçler](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
