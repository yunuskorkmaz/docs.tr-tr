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
ms.openlocfilehash: 238c062b2dd0744ba96cf9ba8591c0ef39f81bb3
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592191"
---
# <a name="-operator-visual-basic"></a>/ İşleci (Visual Basic)
İki sayıyı böler ve kayan noktalı bir sonuç döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `expression1`  
 Gerekli. Herhangi bir sayısal ifade.  
  
 `expression2`  
 Gerekli. Herhangi bir sayısal ifade.  
  
## <a name="supported-types"></a>Desteklenen türler  
 İşaretsiz ve kayan nokta türleri ve `Decimal` dahil olmak üzere tüm sayısal türler.  
  
## <a name="result"></a>Sonuç  
 Sonuç, her geri kalanı dahil `expression1` ' ı `expression2` ' in tam bölümü olur.  
  
 [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) , kalanı döndüren tamsayı bölümünü döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Sonucun veri türü, işlenenlerinin türlerine bağlıdır. Aşağıdaki tabloda, sonucun veri türünün nasıl belirlendiği gösterilmektedir.  
  
|İşlenen veri türleri|Sonuç veri türü|  
|------------------------|----------------------|  
|Her iki ifade de İntegral veri türleridir[(SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [ushort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ulong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Tek bir ifade [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) bir veri türüdür ve diğeri [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) değildir|`Single`|  
|Bir ifade [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md) veri türüdür ve diğeri [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) veya [çift](../../../visual-basic/language-reference/data-types/double-data-type.md) değil|`Decimal`|  
|İki ifade de bir [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) veri türüdür|`Double`|  
  
 Bölüm gerçekleştirilmeden önce, tüm integral sayısal ifadeler iletildiklerinde `Double` ' dır. Sonucu bir integral veri türüne atarsanız, Visual Basic sonucu `Double` ' dan bu türe dönüştürmeye çalışır. Bu, sonuç bu türe uygun değilse bir özel durum oluşturabilir. Özellikle, bu Yardım sayfasında "sıfıra bölme yapılmaya çalışıldı" bölümüne bakın.  
  
 Ya da hiçbir şey değerlendirilirse, sıfır olarak değerlendirilir. [](../../../visual-basic/language-reference/nothing.md) `expression1` `expression2`  
  
## <a name="attempted-division-by-zero"></a>Sıfıra bölme denendi  
 @No__t-0, sıfır olarak değerlendirilirse, `/` işleci farklı işlenen veri türleri için farklı şekilde davranır. Aşağıdaki tabloda olası davranışlar gösterilmektedir.  
  
|İşlenen veri türleri|@No__t-0 sıfırsa davranış|  
|------------------------|---------------------------------------|  
|Kayan nokta (`Single` veya `Double`)|@No__t-3 de sıfırsa sonsuz (<xref:System.Double.PositiveInfinity> veya <xref:System.Double.NegativeInfinity>) veya <xref:System.Double.NaN> (sayı değil) döndürür|  
|`Decimal`|@No__t oluşturur-0|  
|Integral (işaretli veya imzasız)|İntegral türler <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity> veya <xref:System.Double.NaN> ' i kabul edemediği için, <xref:System.OverflowException> ' a geri dönüştürme denendi.|  
  
> [!NOTE]
> @No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, kayan nokta bölme gerçekleştirmek için `/` işlecini kullanır. Sonuç iki işlenenin bir bölümü olur.  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 Yukarıdaki örnekteki ifadeler 2,5 ve 3,333333 değerlerini döndürür. Her iki işlenen de tamsayı sabitleri olsa da sonucun her zaman kayan nokta (`Double`) olduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [/= İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [İşleç Sonuçlarının Veri Türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
