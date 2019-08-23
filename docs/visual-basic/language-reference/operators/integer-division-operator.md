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
ms.openlocfilehash: 276071fef3632d1a617f177b6fe18026b290103a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917247"
---
# <a name="-operator-visual-basic"></a>\ İşleci (Visual Basic)
İki sayıyı böler ve bir tamsayı sonuç döndürür.  
  
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
 İmzasız ve kayan nokta türleri `Decimal`de dahil olmak üzere tüm sayısal türler.  
  
## <a name="result"></a>Sonuç  
 Sonuç, `expression1` `expression2`' ın bölünen tamsayı bölümüdür. Bu, kalanı atar ve yalnızca tamsayı kısmını korur. Bu, *kesme*olarak bilinir.  
  
 Sonuç veri türü `expression1` ve `expression2`veri türleri için uygun bir sayısal türdür. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.  
  
 [/İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) , kesir bölümünde kalanı tutan tam bölümü döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bölme işlemini gerçekleştirmeden önce, Visual Basic herhangi bir kayan nokta sayısal ifadesini öğesine `Long`dönüştürmeye çalışır. `Option Strict` İse`On`, bir derleyici hatası oluşur. İse, değer uzun veri türü aralığının dışında ise mümkündür. [](../../../visual-basic/language-reference/data-types/long-data-type.md) `Option Strict` `Off` <xref:System.OverflowException> Dönüşümü `Long` , *banker 'in yuvarlanması*için de tabidir. Daha fazla bilgi için [tür dönüştürme işlevlerinde](../../../visual-basic/language-reference/functions/type-conversion-functions.md)"kesirli parçalar" bölümüne bakın.  
  
 Ya da hiçbir şey değerlendirilirse, sıfır olarak değerlendirilir. [](../../../visual-basic/language-reference/nothing.md) `expression1` `expression2`  
  
## <a name="attempted-division-by-zero"></a>Sıfıra bölme denendi  
 `\` <xref:System.DivideByZeroException> Sıfır olarak `expression2` değerlendirilirse, işleci bir özel durum atar. Bu, işlenenlerin tüm sayısal veri türleri için geçerlidir.  
  
> [!NOTE]
> İşleç aşırı yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `\` Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tam sayı `\` bölümü yapmak için işlecini kullanır. Sonuç, geri kalan atılan iki işlenenin tamsayı bölümünü temsil eden bir tamsayıdır.  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 Yukarıdaki örnekteki ifadeler sırasıyla 2, 3, 33 ve-22 değerlerini döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\\= İşleci](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [/İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
