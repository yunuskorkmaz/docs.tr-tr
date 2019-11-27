---
title: '* İşleç'
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
ms.openlocfilehash: 4f6a8ea2c5f4e23791afdfe98d2a08bf67219048
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348372"
---
# <a name="-operator-visual-basic"></a>* İşleci (Visual Basic)
İki sayıyı çarpar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`number1`|Gerekli. Herhangi bir sayısal ifade.|  
|`number2`|Gerekli. Herhangi bir sayısal ifade.|  
  
## <a name="result"></a>Sonuç  
 Sonuç, `number1` ve `number2`ürünüdür.  
  
## <a name="supported-types"></a>Desteklenen türler  
 İşaretsiz ve kayan nokta türleri ve `Decimal`dahil olmak üzere tüm sayısal türler.  
  
## <a name="remarks"></a>Açıklamalar  
 Sonucun veri türü, işlenenlerinin türlerine bağlıdır. Aşağıdaki tabloda, sonucun veri türünün nasıl belirlendiği gösterilmektedir.  
  
|İşlenen veri türleri|Sonuç veri türü|  
|---|---|  
|Her iki ifade de İntegral veri türleridir[(SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [ushort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ulong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`number1` ve `number2`veri türleri için uygun bir sayısal veri türü. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.|  
|Her iki ifade de [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|Her iki ifade de [tek](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|Her iki ifade `Single` de bir kayan nokta veri türüdür (`Single` veya [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)), ancak her ikisi de değildir (Not `Decimal` kayan nokta veri türü değildir)|`Double`|  
  
 Bir ifade [hiçbir şey](../../../visual-basic/language-reference/nothing.md)olarak değerlendirilirse, sıfır olarak değerlendirilir.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `*` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek iki sayıyı çarpmak için `*` işlecini kullanır. Sonuç iki işlenenin ürünüdür.  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [*= İşleci](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
