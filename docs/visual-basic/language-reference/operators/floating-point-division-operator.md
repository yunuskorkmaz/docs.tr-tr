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
ms.openlocfilehash: 7d9b02a9c997ffcfdd61e277a6ed3779d8821831
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202463"
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
 İmzasız ve kayan nokta türleri dahil olmak üzere tüm sayısal türlerin ve `Decimal`.  
  
## <a name="result"></a>Sonuç  
 Tam sayının bölümünü sonucudur `expression1` bölü `expression2`, bir hatırlatıcı dahil.  
  
 [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) kalan bıraktığı tamsayı bölümü döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Sonuç veri türü işlenenden türlerine bağlıdır. Aşağıdaki tablo sonuç veri türünü nasıl belirlendiğini gösterir.  
  
|İşlenen veri türleri|Sonuç veri türü|  
|------------------------|----------------------|  
|Her iki ifade de tamsayı veri türleri: ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bayt](../../../visual-basic/language-reference/data-types/byte-data-type.md), [kısa](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [tamsayı](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uınteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [uzun](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Bir ifade bir [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) veri türü ve diğer değil bir [çift](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|Bir ifade bir [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md) veri türü ve diğer değil bir [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) veya [çift](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|Her iki ifade bir [çift](../../../visual-basic/language-reference/data-types/double-data-type.md) veri türü|`Double`|  
  
 Bölme işlemi yapıldıktan önce herhangi bir tamsayı sayısal ifadeleri Genişletilmiş `Double`. Visual Basic sonucu bir tam sayı veri türüne atama, sonuç dönüştürmeye çalışır `Double` bu türü. Sonuç türü bu uygun değilse, bunu bir durum oluşturabilir. Özellikle, "Bölüm sıfır olarak çalıştı" Bu Yardım sayfasında bakın.  
  
 Varsa `expression1` veya `expression2` değerlendiren [hiçbir şey](../../../visual-basic/language-reference/nothing.md), sıfır olarak kabul edilir.  
  
## <a name="attempted-division-by-zero"></a>Denenen sıfıra bölme  
 Varsa `expression2` sıfır olarak değerlendirilen `/` işleci farklı işlenen veri türleri için farklı davranır. Aşağıdaki tabloda olası davranışları gösterir.  
  
|İşlenen veri türleri|Davranış, `expression2` sıfırdır|  
|------------------------|---------------------------------------|  
|Kayan nokta (`Single` veya `Double`)|Sonsuz döndürür (<xref:System.Double.PositiveInfinity> veya <xref:System.Double.NegativeInfinity>), veya <xref:System.Double.NaN> (sayı değil), `expression1` de sıfırdır.|  
|`Decimal`|Oluşturur <xref:System.DivideByZeroException>|  
|Tamsayı (işaretli veya işaretlenmemiş)|İntegral türü atar geri dönüştürme yapılmaya <xref:System.OverflowException> tam sayı türleri kabul edemez çünkü <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, veya <xref:System.Double.NaN>|  
  
> [!NOTE]
>  `/` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte `/` kayan nokta bölme gerçekleştirmek için işleci. Sayının iki işlenenden oluşur.  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 Önceki örnekte yer alan ifadeleri, 2.5 ve 3.333333 değerlerini döndürür. Sonucu her zaman kayan nokta olduğunu unutmayın (`Double`), her iki işlenen de tamsayı sabitleri olsa bile.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [/ = İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [İşleç Sonuçlarının Veri Türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
