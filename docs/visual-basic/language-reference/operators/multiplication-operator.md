---
title: '* İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: a13461d7424415ef553dc9ba00de1bf775fda112
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965325"
---
# <a name="-operator-visual-basic"></a>* İşleci (Visual Basic)
İki sayıyı çarpar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`number1`|Gerekli. Herhangi bir sayısal ifade.|  
|`number2`|Gerekli. Herhangi bir sayısal ifade.|  
  
## <a name="result"></a>Sonuç  
 Sonuç ürünüdür `number1` ve `number2`.  
  
## <a name="supported-types"></a>Desteklenen türler  
 İmzasız ve kayan nokta türleri dahil olmak üzere tüm sayısal türlerin ve `Decimal`.  
  
## <a name="remarks"></a>Açıklamalar  
 Sonuç veri türü işlenenden türlerine bağlıdır. Aşağıdaki tablo sonuç veri türünü nasıl belirlendiğini gösterir.  
  
|İşlenen veri türleri|Sonuç veri türü|  
|---|---|  
|Her iki ifade de tamsayı veri türleri: ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bayt](../../../visual-basic/language-reference/data-types/byte-data-type.md), [kısa](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [tamsayı](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uınteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [uzun](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|Veri türleri için uygun bir sayısal veri türü `number1` ve `number2`. "Tamsayı aritmetik" tablolarında bkz [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Her iki ifade [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|Her iki ifade [tek](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|Bir kayan nokta veri türü ya da ifadesidir (`Single` veya [çift](../../../visual-basic/language-reference/data-types/double-data-type.md)) ancak ikisini birden `Single` (Not `Decimal` bir kayan nokta veri türü değil)|`Double`|  
  
 Bir ifade değerlendirme sonucu [hiçbir şey](../../../visual-basic/language-reference/nothing.md), sıfır olarak kabul edilir.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `*` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte `*` iki sayının çarpılacak işleci. İki işlenenden ürün sonucudur.  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [*= İşleci](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
