---
title: '- İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 1a5c47a2f1bc8a8b9e1b0263b90006a0e58e17bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58830675"
---
# <a name="--operator-visual-basic"></a>- İşleci (Visual Basic)
İki sayısal ifadeye veya sayısal bir ifadenin negatif değerini arasındaki farkı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a>Bölümler  
 `expression1`  
 Gerekli. Herhangi bir sayısal ifade.  
  
 `expression2`  
 Sürece gerekli `–` işleci, negatif bir değer hesaplıyor. Herhangi bir sayısal ifade.  
  
## <a name="result"></a>Sonuç  
 Sonuç arasındaki farktır `expression1` ve `expression2`, ya da eksi değeri kadar çevrilerek `expression1`.  
  
 Sonuç veri türü olan veri türleri için uygun bir sayısal tür `expression1` ve `expression2`. "Tamsayı aritmetik" tablolarında bkz [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="supported-types"></a>Desteklenen türler  
 Tüm sayısal türler. Bu imzalanmamış ve kayan nokta türlerini içerir ve `Decimal`.  
  
## <a name="remarks"></a>Açıklamalar  
 Daha önce gösterilen sözdiziminde gösterilen ilk kullanımında `–` işleci *ikili* aritmetik çıkarma işleci iki sayısal ifade arasındaki farkı.  
  
 Daha önce gösterilen sözdiziminde gösterilen ikinci kullanımı `–` işleci *birli* değilleme işleci bir ifadenin negatif değerini için. Bu anlamda işareti ters olan olumsuzlama oluşur `expression1` sonuç pozitif olur böylece varsa `expression1` negatiftir.  
  
 Her iki ifade değerlendirilirse [hiçbir şey](../../../visual-basic/language-reference/nothing.md), `–` işleci, sıfır olarak değerlendirir.  
  
> [!NOTE]
>  `–` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `–` hesaplamak ve iki sayı arasındaki farkı döndürmek için işleç ve bir sayı negatif yapılacak.  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 Bu deyimler yürütülmesinin `binaryResult` 124.45 içerir ve `unaryResult` –334.90 içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-= İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
