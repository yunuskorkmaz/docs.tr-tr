---
title: Mod İşleci
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: b7552550d4b0496d6ad7ee76a7327054d544b874
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350912"
---
# <a name="mod-operator-visual-basic"></a>Mod işleci (Visual Basic)

İki sayıyı böler ve yalnızca kalanı döndürür.

## <a name="syntax"></a>Sözdizimi

```vb
result = number1 Mod number2
```

## <a name="parts"></a>Bölümler

`result` \
Gerekli. Herhangi bir sayısal değişken veya özellik.

`number1` \
Gerekli. Herhangi bir sayısal ifade.

`number2` \
Gerekli. Herhangi bir sayısal ifade.

## <a name="supported-types"></a>Desteklenen türler

Tüm sayısal türler. Bu, işaretsiz ve kayan nokta türlerini ve `Decimal`içerir.

## <a name="result"></a>Sonuç

`number1`, `number2`tarafından bölündükten sonra elde edilen sonuç olur. Örneğin, `14 Mod 4` ifade 2 olarak değerlendirilir.

> [!NOTE]
> Olumsuz ve mod arasında negatif sayıların farklı sonuçlarıyla birlikte *kalan* ve *mod* arasında bir farklılık vardır. Visual Basic `Mod` işleci, .NET Framework `op_Modulus` işleci ve temel [kalan REM](<xref:System.Reflection.Emit.OpCodes.Rem>) Il yönergesinin hepsi bir geri kalan işlem gerçekleştirir.

`Mod` bir işlemin sonucu, bölünün işaretini korur, `number1`ve bu nedenle pozitif veya negatif olabilir. Sonuç her zaman Aralık içinde (-`number2`, `number2`) ve dışdır. Örneğin:

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a>Açıklamalar

`number1` ya da `number2` bir kayan nokta değeri ise, bölmenin kayan nokta geri kalanı döndürülür. Sonucun veri türü, `number1` ve `number2`veri türleri ile bölme işleminden kaynaklanan tüm olası değerleri tutabilecek en küçük veri türüdür.

`number1` veya `number2` [Nothing](../../../visual-basic/language-reference/nothing.md)olarak değerlendirilirse, sıfır olarak değerlendirilir.

İlgili işleçler şunları içerir:

- [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) bir bölmenin tamsayı bölümünü döndürür. Örneğin, `14 \ 4` ifade 3 olarak değerlendirilir.

- [/İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) , kayan noktalı bir sayı olarak kalanı dahil olmak üzere tam bölümü döndürür. Örneğin, `14 / 4` ifadesi 3,5 olarak değerlendirilir.

## <a name="attempted-division-by-zero"></a>Sıfıra bölme denendi

`number2` sıfır olarak değerlendirilirse, `Mod` işlecinin davranışı işlenenlerinin veri türüne bağlıdır:

- Bir integral bölüm, derleme zamanında `number2` belirlenemiyorsa <xref:System.DivideByZeroException> bir özel durum oluşturur ve `number2` derleme zamanında sıfıra değerlendirilirse bir derleme zamanı `BC30542 Division by zero occurred while evaluating this expression` hatası üretir.
- Kayan nokta bölme <xref:System.Double.NaN?displayProperty=nameWithType>döndürür.

## <a name="equivalent-formula"></a>Denk formül

`a Mod b` ifadesi aşağıdaki formüllerden birine eşdeğerdir:

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a>Kayan nokta noktasında kesinlik eksikliği

Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir ondalık gösterimine sahip olmadıkları unutulmamalıdır. Bu, değer karşılaştırması ve `Mod` işleci gibi belirli işlemlerden beklenmedik sonuçlara neden olabilir. Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="overloading"></a>Aşırı Yükleme

`Mod` işleci *aşırı*yüklenebilir, yani bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz, bu tür bir aşırı yükleme içeren bir sınıf veya yapının örneğine `Mod` geçerliyse, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, iki sayıyı bölmek ve yalnızca geri kalanı döndürmek için `Mod` işlecini kullanır. Her iki sayı de bir kayan noktalı sayı ise sonuç, kalanı temsil eden bir kayan noktalı sayıdır.

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, kayan nokta işlenenlerinin olası noktasında kesinlik eksikliği gösterir. İlk ifadede, işlenenler `Double`ve 0,2, depolanan bir değeri 0.20000000000000001 olan sonsuz bir yinelenen ikili kesirdir. İkinci ifadede, değişmez değer türü karakter `D` her iki işleneni de `Decimal`zorlar ve 0,2 kesin bir gösterimine sahiptir.

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Veri Türü Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
