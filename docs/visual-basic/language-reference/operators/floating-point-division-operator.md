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
ms.openlocfilehash: 17eb3eddfae3cf7c818514a2fee20f646876a6ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604529"
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
 İmzasız ve kayan nokta türleri dahil olmak üzere tüm sayısal türler ve `Decimal`.  
  
## <a name="result"></a>Sonuç  
 Tam sayının bölümünü sonucudur `expression1` bölü `expression2`, tüm kalan dahil olmak üzere.  
  
 [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) kalan bırakır tamsayı bölümü döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Sonuç veri türü işlenen türlerinde bağlıdır. Aşağıdaki tabloda, sonuç veri türü nasıl belirlendiğini gösterir.  
  
|İşlenen veri türleri|Sonuç veri türü|  
|------------------------|----------------------|  
|Her iki ifadelerini tam sayı veri türleri ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bayt](../../../visual-basic/language-reference/data-types/byte-data-type.md), [kısa](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [tamsayı](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uınteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [uzun](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Bir ifade bir [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) veri türü ve diğer değil bir [çift](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|Bir ifade bir [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md) veri türü ve diğer değil bir [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) veya [çift](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|Ya da ifade bir [çift](../../../visual-basic/language-reference/data-types/double-data-type.md) veri türü|`Double`|  
  
 Tam sayı tüm sayısal ifadeleri devam bölme gerçekleştirilmeden önce `Double`. Bir tam sayı veri türü sonucu atarsanız, Visual Basic sonucundan dönüştürmeye çalışır `Double` bu türü. Sonuç bu tür uygun değilse, bu bir özel durum. Özellikle, "Bölme sıfır tarafından çalıştı" Bu yardım sayfasına bakın.  
  
 Varsa `expression1` veya `expression2` değerlendiren [hiçbir şey](../../../visual-basic/language-reference/nothing.md), sıfır olarak kabul edilir.  
  
## <a name="attempted-division-by-zero"></a>Denenen sıfıra  
 Varsa `expression2` sıfır olarak değerlendirilir `/` işleci farklı işlenen veri türleri için farklı şekilde davranır. Aşağıdaki tabloda olası davranışları gösterilir.  
  
|İşlenen veri türleri|Davranış, `expression2` sıfır|  
|------------------------|---------------------------------------|  
|Kayan nokta (`Single` veya `Double`)|Sonsuz döndürür (<xref:System.Double.PositiveInfinity> veya <xref:System.Double.NegativeInfinity>), veya <xref:System.Double.NaN> (sayı değil), `expression1` de sıfırdır|  
|`Decimal`|Oluşturur <xref:System.DivideByZeroException>|  
|İntegral (imzalı veya imzasız)|Tam sayı türü atar geri dönüştürme yapılmaya <xref:System.OverflowException> tam sayı türleri kabul edemiyor çünkü <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, veya <xref:System.Double.NaN>|  
  
> [!NOTE]
>  `/` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte `/` işleci kayan nokta bölme gerçekleştirin. İki işlenen sayının sonucudur.  
  
 [!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 Önceki örnekte ifadeleri 2.5 ve 3.333333 değerini döndürür. Sonuç her zaman kayan nokta olduğuna dikkat edin (`Double`), her iki işlenen tamsayı sabitleri olsa bile.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/ = İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [İşleç Sonuçlarının Veri Türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)  
 [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
