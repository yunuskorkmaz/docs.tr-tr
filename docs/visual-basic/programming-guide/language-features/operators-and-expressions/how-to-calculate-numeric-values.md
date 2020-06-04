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
ms.openlocfilehash: 94b02693f308dcfcfa6983f2750a26d9d419f7be
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403465"
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
  
     Önceki örnekte, eşittir işlecinin () sağ tarafındaki ifadenin değeri, `=` `j` işlecin sol tarafındaki değişkenine atanır, bu nedenle `j` 276 olarak değerlendirilir.  
  
     Daha fazla bilgi için bkz. [deyimler](../../../language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Birden çok Işleç  
 Sayısal ifade birden fazla işleç içeriyorsa, değerlendirildikleri sıra, işleç önceliği kurallarına göre belirlenir. İşleç önceliği kurallarını geçersiz kılmak için, ifadeleri Yukarıdaki örnekte olduğu gibi parantez içine almalısınız; içine alınan ifadeler önce değerlendirilir.  
  
#### <a name="to-override-normal-operator-precedence"></a>Normal operatör önceliğini geçersiz kılmak için  
  
- Önce gerçekleştirilmesini istediğiniz işlemleri kapsamak için ayraçları kullanın. Aşağıdaki örnekte, aynı işlenen ve işleçlere sahip iki farklı sonuç gösterilmektedir.  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     Önceki örnekte, için hesaplama, `j` ekleme işlecini () ilk olarak gerçekleştirir, `+` çünkü etrafındaki parantezler `(67 + i)` Normal önceliği geçersiz kılar ve şuna atanan değer `j` 276 ' dir (4 kez 69). İçin hesaplama, `k` işleçleri normal önceliğinde ( `*` önce `+` ) gerçekleştirir ve atanan değer 270 ' `k` dir (268 Plus 2).  
  
     Daha fazla bilgi için [Visual Basic operatör önceliği](../../../language-reference/operators/operator-precedence.md)bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşleçler ve Ifadeler](index.md)
- [Değer Karşılaştırmaları](value-comparisons.md)
- [Deyimler](../../../language-reference/statements/index.md)
- [Visual Basic'de İşleç Önceliği](../../../language-reference/operators/operator-precedence.md)
- [Aritmetik İşleçler](../../../language-reference/operators/arithmetic-operators.md)
- [İşleçlerin Etkili Bileşimi](efficient-combination-of-operators.md)
