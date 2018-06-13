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
ms.openlocfilehash: 4df8eb3844ed20fd24ca375f77cea46b9c6cee37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604321"
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
 Sürece gerekli `–` işleci negatif bir değer hesaplıyor. Herhangi bir sayısal ifade.  
  
## <a name="result"></a>Sonuç  
 Sonuç arasındaki farktır `expression1` ve `expression2`, veya eksi değeri kadar çevrilerek `expression1`.  
  
 Sonuç veri türü sayısal bir tür veri türleri için uygun değil `expression1` ve `expression2`. "Tamsayı aritmetiğini" tablolarda bkz [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="supported-types"></a>Desteklenen türler  
 Tüm sayısal türler. Bu imzasız ve kayan nokta türleri içerir ve `Decimal`.  
  
## <a name="remarks"></a>Açıklamalar  
 Daha önce gösterilen sözdiziminde gösterilen ilk kullanımında `–` işlecidir *ikili* iki sayısal ifadeye arasındaki farkı aritmetik çıkarma işleci.  
  
 Daha önce gösterilen sözdiziminde gösterilen ikinci kullanımı `–` işlecidir *birli* bir ifadenin negatif değerini değilleme işleci. Bu anlamda işaretini ters değilleme oluşur `expression1` sonucu pozitif olmasını sağlamak, `expression1` negatiftir.  
  
 Ya da ifade değerlendirilirse [hiçbir şey](../../../visual-basic/language-reference/nothing.md), `–` işleci, sıfır olarak değerlendirir.  
  
> [!NOTE]
>  `–` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `–` hesaplamak ve iki sayı arasındaki farkı dönmek için işleci ve ardından bir sayı negate.  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 Bu deyimler yürütülmesinin `binaryResult` 124.45 içerir ve `unaryResult` –334.90 içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [-= İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [aritmetik işleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
