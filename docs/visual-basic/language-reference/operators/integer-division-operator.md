---
title: '\ İşleci'
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
ms.openlocfilehash: 2b4cca99ed54195162530bb8eb950bd251bfbff9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347115"
---
# <a name="-operator-visual-basic"></a>\ İşleci (Visual Basic)
İki sayıyı böler ve bir tamsayı sonuç döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `expression1`  
 Gerekli. Herhangi bir sayısal ifade.  
  
 `expression2`  
 Gerekli. Herhangi bir sayısal ifade.  
  
## <a name="supported-types"></a>Desteklenen türler  
 İşaretsiz ve kayan nokta türleri ve `Decimal`dahil olmak üzere tüm sayısal türler.  
  
## <a name="result"></a>Sonuç  
 Sonuç, `expression2`tarafından bölünen `expression1` tamsayı bölümüdür ve bu, kalanı atar ve yalnızca tamsayı kısmını korur. Bu, *kesme*olarak bilinir.  
  
 Sonuç veri türü, `expression1` ve `expression2`veri türleri için uygun bir sayısal türdür. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.  
  
 [/İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) , kesir bölümünde kalanı tutan tam bölümü döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bölme işlemini gerçekleştirmeden önce, Visual Basic herhangi bir kayan nokta sayısal ifadesini `Long`dönüştürmeye çalışır. `Option Strict` `On`, bir derleyici hatası oluşur. `Option Strict` `Off`ise, değer [uzun veri türü](../../../visual-basic/language-reference/data-types/long-data-type.md)aralığının dışındaysa bir <xref:System.OverflowException> mümkündür. `Long` dönüştürme işlemi, *banker 'in yuvarlanması*için de tabidir. Daha fazla bilgi için [tür dönüştürme işlevlerinde](../../../visual-basic/language-reference/functions/type-conversion-functions.md)"kesirli parçalar" bölümüne bakın.  
  
 `expression1` veya `expression2` [Nothing](../../../visual-basic/language-reference/nothing.md)olarak değerlendirilirse, sıfır olarak değerlendirilir.  
  
## <a name="attempted-division-by-zero"></a>Sıfıra bölme denendi  
 `expression2` sıfır olarak değerlendirilirse, `\` işleci bir <xref:System.DivideByZeroException> özel durumu atar. Bu, işlenenlerin tüm sayısal veri türleri için geçerlidir.  
  
> [!NOTE]
> `\` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tamsayı bölme gerçekleştirmek için `\` işlecini kullanır. Sonuç, geri kalan atılan iki işlenenin tamsayı bölümünü temsil eden bir tamsayıdır.  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 Yukarıdaki örnekteki ifadeler sırasıyla 2, 3, 33 ve-22 değerlerini döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\\= Işleci](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [/İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
