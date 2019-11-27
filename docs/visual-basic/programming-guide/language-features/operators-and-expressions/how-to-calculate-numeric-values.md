---
title: 'Nasıl yapılır: Sayısal Değerleri Hesaplama'
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
ms.openlocfilehash: d213f6b5a4abf8c52d8872ae36e89796183ff27c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348961"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Nasıl yapılır: Sayısal Değerleri Hesaplama (Visual Basic)
Sayısal değerleri sayısal ifadeler kullanılarak hesaplayabilirsiniz. *Sayısal bir ifade* , sayısal değerleri temsil eden sabit değerler, sabitler ve değişkenleri ve bu değerler üzerinde işlem yapan işleçleri içeren bir ifadedir.  
  
## <a name="calculating-numeric-values"></a>Sayısal değerleri hesaplama  
  
#### <a name="to-calculate-a-numeric-value"></a>Sayısal bir değer hesaplamak için  
  
- Bir veya daha fazla sayısal sabit değer, sabitler ve değişkenleri sayısal bir ifadede birleştirin. Aşağıdaki örnekte bazı geçerli sayısal ifadeler gösterilmektedir.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     İlk üç satır bir sabit değer, bir sabit ve bir değişken gösterir. Her biri kendi kendine geçerli bir sayısal ifade oluşturur. Son satır iki değişmez değer içeren bir değişkenin birleşimini gösterir.  
  
     Sayısal bir ifadenin kendi başına bir Visual Basic deyimi oluşturmadığını unutmayın. Deyimi, tüm deyimin bir parçası olarak kullanmanız gerekir.  
  
#### <a name="to-store-a-numeric-value"></a>Sayısal bir değeri depolamak için  
  
- Aşağıdaki örnekte gösterildiği gibi, sayısal bir ifade ile temsil edilen değeri bir değişkene atamak için bir atama deyimi kullanabilirsiniz.  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     Önceki örnekte, eşittir işlecinin (`=`) sağ tarafındaki ifadenin değeri, işlecin sol tarafındaki `j` değişkenine atanır, bu nedenle `j` 276 olarak değerlendirilir.  
  
     Daha fazla bilgi için bkz. [deyimler](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Birden çok Işleç  
 Sayısal ifade birden fazla işleç içeriyorsa, değerlendirildikleri sıra, işleç önceliği kurallarına göre belirlenir. İşleç önceliği kurallarını geçersiz kılmak için, ifadeleri Yukarıdaki örnekte olduğu gibi parantez içine almalısınız; içine alınan ifadeler önce değerlendirilir.  
  
#### <a name="to-override-normal-operator-precedence"></a>Normal operatör önceliğini geçersiz kılmak için  
  
- Önce gerçekleştirilmesini istediğiniz işlemleri kapsamak için ayraçları kullanın. Aşağıdaki örnekte, aynı işlenen ve işleçlere sahip iki farklı sonuç gösterilmektedir.  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     Yukarıdaki örnekte, `j` için hesaplama, normal önceliği geçersiz kıldığından ve `j` atanan değer 276 (4 kez 69) `(67 + i)` olduğundan, önce ekleme işlecini (`+`) uygular. `k` hesaplama, işleçleri normal önceliğinde (`+`önce`*`) gerçekleştirir ve `k` atanan değer 270 (268 Plus 2) olur.  
  
     Daha fazla bilgi için [Visual Basic operatör önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşleçler ve İfadeler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Değer Karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Deyimler](../../../../visual-basic/language-reference/statements/index.md)
- [Visual Basic operatör önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Aritmetik İşleçler](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
