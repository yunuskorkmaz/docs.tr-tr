---
title: / İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: d30d871d48bc87e050a072cd01a38065be20616c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933267"
---
# <a name="-operator-visual-basic"></a>/ İşleci (Visual Basic)
İki sayıyı böler ve kayan noktalı bir sonuç döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `expression1`  
 Gerekli. Herhangi bir sayısal ifade.  
  
 `expression2`  
 Gerekli. Herhangi bir sayısal ifade.  
  
## <a name="supported-types"></a>Desteklenen türler  
 İmzasız ve kayan nokta türleri `Decimal`de dahil olmak üzere tüm sayısal türler.  
  
## <a name="result"></a>Sonuç  
 Sonuç, kalanı da dahil olmak üzere `expression1` `expression2`bölünen tam bölüm.  
  
 [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) , kalanı döndüren tamsayı bölümünü döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Sonucun veri türü, işlenenlerinin türlerine bağlıdır. Aşağıdaki tabloda, sonucun veri türünün nasıl belirlendiği gösterilmektedir.  
  
|İşlenen veri türleri|Sonuç veri türü|  
|------------------------|----------------------|  
|Her iki ifade de İntegral veri türleridir[(SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [ushort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ulong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Tek bir ifade [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) bir veri türüdür ve diğeri [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) değildir|`Single`|  
|Bir ifade [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md) veri türüdür ve diğeri [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) veya [çift](../../../visual-basic/language-reference/data-types/double-data-type.md) değil|`Decimal`|  
|İki ifade de bir [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) veri türüdür|`Double`|  
  
 Bölüm gerçekleştirilmeden önce, tüm integral sayısal ifadeler iletildiklerinde `Double`' dir. Sonucu bir integral veri türüne atarsanız, Visual Basic sonucu `Double` bu türe dönüştürmeye çalışır. Bu, sonuç bu türe uygun değilse bir özel durum oluşturabilir. Özellikle, bu Yardım sayfasında "sıfıra bölme yapılmaya çalışıldı" bölümüne bakın.  
  
 Ya da hiçbir şey değerlendirilirse, sıfır olarak değerlendirilir. [](../../../visual-basic/language-reference/nothing.md) `expression1` `expression2`  
  
## <a name="attempted-division-by-zero"></a>Sıfıra bölme denendi  
 Sıfır olarak `/` değerlendirilirse, işleç farklı işlenen veri türleri için farklı davranır. `expression2` Aşağıdaki tabloda olası davranışlar gösterilmektedir.  
  
|İşlenen veri türleri|`expression2` Sıfır ise davranış|  
|------------------------|---------------------------------------|  
|Kayan nokta (`Single` veya `Double`)|Sıfır `expression1` ise,<xref:System.Double.PositiveInfinity> sonsuz <xref:System.Double.NegativeInfinity>(veya) <xref:System.Double.NaN> , ya da (sayı değil) döndürür|  
|`Decimal`|Oluşturur<xref:System.DivideByZeroException>|  
|Integral (işaretli veya imzasız)|İntegral türler, <xref:System.OverflowException> <xref:System.Double.PositiveInfinity>veyakabul edilemediğindenintegraltürünegeridönüştürmedenendi<xref:System.Double.NegativeInfinity>.<xref:System.Double.NaN>|  
  
> [!NOTE]
> İşleç aşırı yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `/` Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, `/` kayan nokta bölme gerçekleştirmek için işlecini kullanır. Sonuç iki işlenenin bir bölümü olur.  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 Yukarıdaki örnekteki ifadeler 2,5 ve 3,333333 değerlerini döndürür. Her iki işlenen de tamsayı sabiti olsa da sonucun her`Double`zaman kayan nokta () olduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [/= İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [İşleç Sonuçlarının Veri Türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
