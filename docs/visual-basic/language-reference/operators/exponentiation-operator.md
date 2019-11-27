---
title: ^ İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: b9860b7b6e076fc9c0288818aa9e4f2c0fc4c356
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331100"
---
# <a name="-operator-visual-basic"></a>^ İşleci (Visual Basic)

Bir sayıyı, başka bir sayının kuvvetine yükseltir.

## <a name="syntax"></a>Sözdizimi

```vb
number ^ exponent
```

## <a name="parts"></a>Bölümler

`number`\
Gerekli. Herhangi bir sayısal ifade.

`exponent`\
Gerekli. Herhangi bir sayısal ifade.

## <a name="result"></a>Sonuç

Sonuç, her zaman bir `Double` değeri olarak `exponent`gücü `number` yükseltilir.

## <a name="supported-types"></a>Desteklenen türler

`Double`. Farklı türdeki işlenenler `Double`dönüştürülür.

## <a name="remarks"></a>Açıklamalar

Visual Basic her zaman [Double veri türünde](../../../visual-basic/language-reference/data-types/double-data-type.md)üs gerçekleştirir.

`exponent` değeri kesirli, negatif veya her ikisi olabilir.

Tek bir ifadede birden fazla üs işlemi gerçekleştirildiğinde, soldan sağa ile karşılaşıldığından `^` işleci değerlendirilir.

> [!NOTE]
> `^` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir sayının üssünü artırmak için `^` işlecini kullanır. Sonuç ikincinin gücüyle oluşturulan ilk işlenendir.

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

Yukarıdaki örnek aşağıdaki sonuçları üretir:

`exp1` 4 (2 kare) olarak ayarlanır.

`exp2`, 19683 (3 odaya, sonra da bu değer) olarak ayarlanır.

`exp3`-125 (-5 odamış) olarak ayarlanır.

`exp4`, 625 (-5 dördüncü güce) olarak ayarlanmıştır.

`exp5` 2 olarak ayarlanır (8. küp kökü).

`exp6`, 0,5 olarak ayarlanır (1,0, 8 ' in küp köküne bölünür).

Önceki örnekteki ifadelerde parantezlerin önemini dikkate alın. *İşleç önceliği*nedeniyle, Visual Basic normalde, birli `–` işleci bile diğer tüm `^` işlecini uygular. `exp4` ve `exp6` parantez olmadan hesaplanmışsa, bunlar aşağıdaki sonuçları üretti:

`exp4 = -5 ^ 4` – (5 dördüncü güce) olarak hesaplanacak ve bu,-625 ile sonuçlanacaktır.

`exp6 = 8 ^ -1.0 / 3.0`, 3,0 ile ayrılmış olan (– 1 güç veya 0,125), 0.041666666666666666666666666666667 ile sonuçlanabilecek şekilde hesaplanır.

## <a name="see-also"></a>Ayrıca bkz.

- [^= İşleci](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
