---
title: "/ İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f221e863725b9aeb0b3fa3219b3a881541e2be0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
|`Decimal`|Oluşturur<xref:System.DivideByZeroException>|  
|İntegral (imzalı veya imzasız)|Tam sayı türü atar geri dönüştürme yapılmaya <xref:System.OverflowException> tam sayı türleri kabul edemiyor çünkü <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, veya<xref:System.Double.NaN>|  
  
> [!NOTE]
>  `/` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte `/` işleci kayan nokta bölme gerçekleştirin. İki işlenen sayının sonucudur.  
  
 [!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 Önceki örnekte ifadeleri 2.5 ve 3.333333 değerini döndürür. Sonuç her zaman kayan nokta olduğuna dikkat edin (`Double`), her iki işlenen tamsayı sabitleri olsa bile.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/ = İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [İşleç sonuçlarının veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)  
 [Aritmetik işleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
