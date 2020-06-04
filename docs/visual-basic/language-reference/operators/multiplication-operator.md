---
title: '* Operatör'
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
ms.openlocfilehash: f1a7653fb3006ab3c9736ec168a8c5ea028f4763
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409334"
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
|`number1`|Gereklidir. Herhangi bir sayısal ifade.|  
|`number2`|Gereklidir. Herhangi bir sayısal ifade.|  
  
## <a name="result"></a>Sonuç  
 Sonuç, `number1` ve ürünüdür `number2` .  
  
## <a name="supported-types"></a>Desteklenen türler  
 İmzasız ve kayan nokta türleri de dahil olmak üzere tüm sayısal türler `Decimal` .  
  
## <a name="remarks"></a>Açıklamalar  
 Sonucun veri türü, işlenenlerinin türlerine bağlıdır. Aşağıdaki tabloda, sonucun veri türünün nasıl belirlendiği gösterilmektedir.  
  
|İşlenen veri türleri|Sonuç veri türü|  
|---|---|  
|Her iki ifade de İntegral veri türleridir[(SByte](../data-types/sbyte-data-type.md), [byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [ushort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ulong](../data-types/ulong-data-type.md))|Ve veri türleri için uygun bir sayısal veri türü `number1` `number2` . [Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.|  
|Her iki ifade de [Decimal](../data-types/decimal-data-type.md)|`Decimal`|  
|Her iki ifade de [tek](../data-types/single-data-type.md)|`Single`|  
|İki ifade de kayan nokta veri türü ( `Single` veya [Double](../data-types/double-data-type.md)), ancak her ikisi birden değil `Single` (Not `Decimal` kayan nokta veri türü değildir)|`Double`|  
  
 Bir ifade [hiçbir şey](../nothing.md)olarak değerlendirilirse, sıfır olarak değerlendirilir.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `*`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, `*` iki sayıyı çarpmak için işlecini kullanır. Sonuç iki işlenenin ürünüdür.  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [* = İşleci](multiplication-assignment-operator.md)
- [Aritmetik İşleçler](arithmetic-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Visual Basic'de Aritmetik İşleçler](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
