---
title: ^ İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 2fb52a57a9d96f93c31ab1419e81e7f05967f831
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659728"
---
# <a name="-operator-visual-basic"></a>^ İşleci (Visual Basic)
Bir sayıyı diğer bir sayının başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a>Bölümler  
 `number`  
 Gerekli. Herhangi bir sayısal ifade.  
  
 `exponent`  
 Gerekli. Herhangi bir sayısal ifade.  
  
## <a name="result"></a>Sonuç  
 Sonuç `number` üssünü `exponent`, her zaman olarak bir `Double` değeri.  
  
## <a name="supported-types"></a>Desteklenen türler  
 `Double`. Tüm farklı türündeki işlenenler için dönüştürülür `Double`.  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Basic içinde üs her zaman gerçekleştirir [Double veri türü](../../../visual-basic/language-reference/data-types/double-data-type.md).  
  
 Değerini `exponent` kesir olabilir negatif veya her ikisini de.  
  
 Tek bir deyimde birden fazla üs gerçekleştirildiğinde `^` işleci soldan sağa karşılaşılanaa olarak değerlendirilir.  
  
> [!NOTE]
>  `^` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `^` birkaç üs değerini artırmak için işleci. İkinci üssü birinci işlenenin sonucudur.  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 Yukarıdaki örnekte, aşağıdaki sonuçları üretir:  
  
 `exp1` (2 kare) 4'e ayarlanır.  
  
 `exp2` (3 üssüne, ardından bu değeri üssüne) 19683 için ayarlanır.  
  
 `exp3` -125 (üssüne -5) için ayarlanır.  
  
 `exp4` 625'in (Dördüncü gücüne -5) ayarlanır.  
  
 `exp5` 2 (8 kökünde küpü)'ye ayarlanır.  
  
 `exp6` 0,5 (8'in küpü kök tarafından ayrılmış 1.0) ayarlanır.  
  
 Önceki örnekte ifadelerde parantezler önemini unutmayın. Nedeniyle *İşleç önceliği*, Visual Basic normalde gerçekleştirir `^` işlecinden önce diğer tüm abonelikler, hatta birli `–` işleci. Varsa `exp4` ve `exp6` parantez olmadan, bunlar üretilen aşağıdaki sonuçları hesaplanmadığını:  
  
 `exp4 = -5 ^ 4` (5 – olarak dördüncü güç), hesaplanacaktı-625 içinde sonuçlanır.  
  
 `exp6 = 8 ^ -1.0 / 3.0` (8 – 1 güç veya 0,125) olarak hesaplanacaktı 0.041666666666666666666666666666667 içinde oluşacak 3.0, bölü.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [^= İşleci](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
