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
ms.openlocfilehash: 4e2d1000afcf8951e8914335f7b5a278b49f6277
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603632"
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
 İmzasız ve kayan nokta türleri dahil olmak üzere tüm sayısal türler ve `Decimal`.  
  
## <a name="remarks"></a>Açıklamalar  
 Sonuç veri türü işlenen türlerinde bağlıdır. Aşağıdaki tabloda, sonuç veri türü nasıl belirlendiğini gösterir.  
  
|İşlenen veri türleri|Sonuç veri türü|  
|---|---|  
|Her iki ifadelerini tam sayı veri türleri ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bayt](../../../visual-basic/language-reference/data-types/byte-data-type.md), [kısa](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [tamsayı](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uınteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [uzun](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|Veri türleri için uygun bir sayısal veri türü `number1` ve `number2`. "Tamsayı aritmetiğini" tablolarda bkz [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Her iki ifadelerini [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|Her iki ifadelerini [tek](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|Kayan nokta veri türü ya da ifadesidir (`Single` veya [çift](../../../visual-basic/language-reference/data-types/double-data-type.md)) ancak ikisini `Single` (Not `Decimal` bir kayan nokta veri türü değil)|`Double`|  
  
 Bir ifade değerlendirilirse [hiçbir şey](../../../visual-basic/language-reference/nothing.md), sıfır olarak kabul edilir.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `*` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte `*` iki sayının Çarp işleci. Sonuç iki işlenen ürünüdür.  
  
 [!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [*= İşleci](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
