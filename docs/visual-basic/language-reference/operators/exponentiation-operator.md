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
ms.openlocfilehash: e139becf74ae367266a23513e18d0bdbdd24cdea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371394"
---
# <a name="-operator-visual-basic"></a>^ İşleci (Visual Basic)

Bir sayıyı, başka bir sayının kuvvetine yükseltir.

## <a name="syntax"></a>Sözdizimi

```vb
number ^ exponent
```

## <a name="parts"></a>Bölümler

`number`\
Gereklidir. Herhangi bir sayısal ifade.

`exponent`\
Gereklidir. Herhangi bir sayısal ifade.

## <a name="result"></a>Sonuç

Sonuç `number` `exponent` , her zaman bir değer olarak ' ın gücüne yükseltilir `Double` .

## <a name="supported-types"></a>Desteklenen türler

`Double`. Farklı türdeki işlenenler öğesine dönüştürülür `Double` .

## <a name="remarks"></a>Açıklamalar

Visual Basic her zaman [Double veri türünde](../data-types/double-data-type.md)üs gerçekleştirir.

Değeri `exponent` kesirli, negatif veya her ikisi olabilir.

Tek bir ifadede birden fazla üs gerçekleştirildiğinde, `^` işleç soldan sağa ile karşılaşıldığından değerlendirilir.

> [!NOTE]
> `^`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `^` bir sayının üssünü artırmak için işlecini kullanır. Sonuç ikincinin gücüyle oluşturulan ilk işlenendir.

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

Yukarıdaki örnek aşağıdaki sonuçları üretir:

`exp1`4 (2 kare) olarak ayarlanır.

`exp2`19683 olarak ayarlanır (3 odadır, daha sonra bu değer bir değeri).

`exp3`-125 (-5 odaya) olarak ayarlanır.

`exp4`625 (-5 dördüncü güce) olarak ayarlanır.

`exp5`2 olarak ayarlanır (8 ' in küp kökü).

`exp6`0,5 olarak ayarlanır (1,0, 8 ' in küp köküne bölünür).

Önceki örnekteki ifadelerde parantezlerin önemini dikkate alın. *İşleç önceliği*nedeniyle, Visual Basic normalde `^` işleci diğerlerinden önce, hatta birli `–` işleçle uygular. `exp4`Ve `exp6` parantez olmadan hesaplanmışsa, bunlar aşağıdaki sonuçları üretti:

`exp4 = -5 ^ 4`,-625 ile sonuçlanabilecek – (5 dördüncü üssü) olarak hesaplanır.

`exp6 = 8 ^ -1.0 / 3.0`, 0.041666666666666666666666666666667 ile sonuçlanarak 3,0 ile ayrılmış olan (– 1 güç veya 0,125) olarak hesaplanır.

## <a name="see-also"></a>Ayrıca bkz.

- [^ = İşleci](exponentiation-assignment-operator.md)
- [Aritmetik İşleçler](arithmetic-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Visual Basic'de Aritmetik İşleçler](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
