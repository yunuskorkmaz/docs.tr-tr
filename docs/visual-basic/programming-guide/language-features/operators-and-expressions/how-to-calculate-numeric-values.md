---
title: 'Nasıl yapılır: (Visual Basic) sayısal değerleri hesaplama'
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
ms.openlocfilehash: 33184d9be275f5e777ffd79c6dd4e3182d865de7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825761"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Nasıl yapılır: (Visual Basic) sayısal değerleri hesaplama
Sayısal değerlerin sayısal ifadeler kullanarak hesaplayabilirsiniz. A *sayısal ifadenin* değişmez değerleri, sabitleri ve değişkenleri temsil eden sayısal değerleri içeren ifade ve bu değerleri üzerinde işlem işleçleri.  
  
## <a name="calculating-numeric-values"></a>Sayısal değerlerini hesaplama  
  
#### <a name="to-calculate-a-numeric-value"></a>Bir sayısal değer hesaplamak için  
  
-   Bir veya daha fazla sayısal değişmez değerleri, sabitleri ve değişkenleri sayısal bir ifadenin birleştirin. Aşağıdaki örnek, bazı geçerli bir sayısal ifadeye gösterir.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     Bir sabit değer, bir sabit ve değişken ilk üç satırını gösterir. Her biri geçerli bir sayısal ifade tek başına oluşturur. Son satırı bir değişken iki değişmez değerleri ile birlikte gösterilir.  
  
     Sayısal bir ifadenin tam bir Visual Basic ifade tek başına form değil olduğunu unutmayın. Tam bir deyim bir parçası olarak ifade kullanmanız gerekir.  
  
#### <a name="to-store-a-numeric-value"></a>Sayısal bir değeri depolamak için  
  
-   Aşağıdaki örnekte de gösterildiği gibi bir değişken için bir sayısal ifade tarafından temsil edilen değeri atamak, atama deyiminin kullanabilirsiniz.  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     Yukarıdaki örnekte, eşit işlecin sağ tarafındaki ifadenin değerine (`=`) değişkenine atanan `j` işlecinin sol tarafındaki şekilde `j` için 276 değerlendirir.  
  
     Daha fazla bilgi için [deyimleri](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Birden çok işleç  
 Sayısal ifade birden fazla işleci içeriyorsa, bunlar değerlendirilme sırası İşleç önceliği kuralları tarafından belirlenir. İşleç önceliği kurallarına geçersiz kılmak için yukarıdaki örnekte olduğu gibi parantez içinde ifadeleri alın. Kapalı ifadeleri, ilk olarak değerlendirilir.  
  
#### <a name="to-override-normal-operator-precedence"></a>Normal İşleç önceliği geçersiz kılmak için  
  
-   İlk gerçekleştirmek istediğiniz işlemleri kapsamak için ayraç kullanın. Aşağıdaki örnek, iki farklı sonuçlar aynı işleçler ve işlenenleri gösterir.  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     Yukarıdaki örnekte, hesaplama için `j` toplama işlecini gerçekleştirir (`+`) ilk çünkü parantezler `(67 + i)` atanan değer ve normal öncelik geçersiz kılma `j` 276 (4 kez 69) olan. Hesaplama için `k` içinde normal öncelik işleçleri gerçekleştirir (`*` önce `+`) ve atanan değer `k` 270 (268 artı 2) olan.  
  
     Daha fazla bilgi için [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşleçler ve İfadeler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Değer Karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Deyimler](../../../../visual-basic/language-reference/statements/index.md)
- [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Aritmetik İşleçler](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
