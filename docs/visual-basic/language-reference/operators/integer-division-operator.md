---
title: '\ İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: ac306038aefba4ca0e0f13fa2945d01c27c0804d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654691"
---
# <a name="-operator-visual-basic"></a>\ İşleci (Visual Basic)
İki sayıyı böler ve tamsayı sonuç döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `expression1`  
 Gerekli. Herhangi bir sayısal ifade.  
  
 `expression2`  
 Gerekli. Herhangi bir sayısal ifade.  
  
## <a name="supported-types"></a>Desteklenen türler  
 İmzasız ve kayan nokta türleri dahil olmak üzere tüm sayısal türlerin ve `Decimal`.  
  
## <a name="result"></a>Sonuç  
 Tamsayı bölümünü sonucudur `expression1` bölü `expression2`, tüm kalan kısmını atar ve yalnızca tamsayı bölümü korur. Bu olarak bilinir *kesilmesi*.  
  
 Sonuç veri türü olan veri türleri için uygun bir sayısal tür `expression1` ve `expression2`. "Tamsayı aritmetik" tablolarında bkz [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
 [/ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) kesirli bölümü kalanı korur tam bölümü döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bölme işlemi gerçekleştirmeden önce Visual Basic herhangi bir kayan nokta sayısal ifade dönüştürmeye çalışır `Long`. Varsa `Option Strict` olduğu `On`, bir derleyici hatası oluşur. Varsa `Option Strict` olduğu `Off`e <xref:System.OverflowException> değer aralığının dışında ise mümkündür [Long veri türü](../../../visual-basic/language-reference/data-types/long-data-type.md). Dönüştürme `Long` de tabi olduğu *banker yuvarlama*. Daha fazla bilgi için bkz: "Kesirli bölümleri" [tür dönüştürme işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Varsa `expression1` veya `expression2` değerlendiren [hiçbir şey](../../../visual-basic/language-reference/nothing.md), sıfır olarak kabul edilir.  
  
## <a name="attempted-division-by-zero"></a>Denenen sıfıra bölme  
 Varsa `expression2` sıfır olarak değerlendirilen `\` işleci oluşturur bir <xref:System.DivideByZeroException> özel durum. Bu işlenenlerin tüm sayısal veri türleri için geçerlidir.  
  
> [!NOTE]
>  `\` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `\` tamsayı bölme gerçekleştirmek için işleci. İki işlenenden tamsayı bölümü atılır geri kalanı ile temsil eden bir tamsayı sonucudur.  
  
 [!code-vb[VbVbalrOperators#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/integer-division-operator_1.vb)]  
  
 Önceki örnekte yer alan ifadeleri sırasıyla 2, 3, 33 ve -22, değerlerini döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [\\= İşleci](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [/ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
