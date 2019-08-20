---
title: Mod İşleci (Visual Basic)
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
ms.openlocfilehash: c801facd95d93652414409549bb5ff2fa633748b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611530"
---
# <a name="mod-operator-visual-basic"></a>Mod işleci (Visual Basic)
İki sayıyı böler ve yalnızca kalanı döndürür.

## <a name="syntax"></a>Sözdizimi

```vb
result = number1 Mod number2
```
  
## <a name="parts"></a>Bölümler  
 `result`Gerekli. Herhangi bir sayısal değişken veya özellik.

 `number1`Gerekli. Herhangi bir sayısal ifade.

 `number2`Gerekli. Herhangi bir sayısal ifade.

## <a name="supported-types"></a>Desteklenen türler
 Tüm sayısal türler. Bu, imzasız ve kayan nokta türlerini `Decimal`içerir.

## <a name="result"></a>Sonuç

Sonuç, öğesinden `number2`bölündükten sonra `number1` kalanı. Örneğin, ifade `14 Mod 4` 2 olarak değerlendirilir.

> [!NOTE]
> Olumsuz ve mod arasında negatif sayıların farklı sonuçlarıyla birlikte *kalan* ve *mod* arasında bir farklılık vardır. Visual Basic işleci, .NET Framework `op_Modulus` işleci ve temeldeki REM Il yönergesinin hepsi bir geri kalan işlem gerçekleştirir. [](<xref:System.Reflection.Emit.OpCodes.Rem>) `Mod`

Bir `Mod` işlemin sonucu, `number1`bölünün işaretini korur, ve bu nedenle pozitif veya negatif olabilir. Sonuç her zaman (-`number2`, `number2`), hariç değişir. Örneğin:

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
 `number1` Ya`number2` da bir kayan nokta değeri ise, bölmenin kayan nokta geri kalanı döndürülür. Sonucun veri türü, `number1` ve `number2`veri türleri ile bölme işleminden kaynaklanan tüm olası değerleri tutabilecek en küçük veri türüdür.

 Ya da hiçbir şey değerlendirilirse, sıfır olarak değerlendirilir. [](../../../visual-basic/language-reference/nothing.md) `number1` `number2`

 İlgili işleçler şunları içerir:

- [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) bir bölmenin tamsayı bölümünü döndürür. Örneğin, ifade `14 \ 4` 3 olarak değerlendirilir.

- [/İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) , kayan noktalı bir sayı olarak kalanı dahil olmak üzere tam bölümü döndürür. Örneğin, ifade `14 / 4` 3,5 olarak değerlendirilir.

## <a name="attempted-division-by-zero"></a>Sıfıra bölme denendi
 Sıfır olarak `Mod` değerlendirilirse, işlecin davranışı işlenenlerinin veri türüne bağlıdır: `number2`
 - Derleme zamanında belirlenemiyorsa integral <xref:System.DivideByZeroException> bölüm bir `number2` özel durum oluşturur ve derleme zamanında sıfır olarak değerlendirilirse bir `number2` derleme zamanı hatası `BC30542    Division by zero occurred while evaluating this expression` oluşturur.
 - Kayan nokta bölmesi döndürülür <xref:System.Double.NaN?displayProperty=nameWithType>.

## <a name="equivalent-formula"></a>Denk formül
 İfade `a Mod b` aşağıdaki formüllerden birine eşdeğerdir:

 `a - (b * (a \ b))`

 `a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a>Kayan nokta noktasında kesinlik eksikliği
 Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir ondalık gösterimine sahip olmadıkları unutulmamalıdır. Bu, değer karşılaştırması ve `Mod` işleç gibi belirli işlemlerden beklenmeyen sonuçlara neden olabilir. Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="overloading"></a>Aşırı Yükleme
 İşleç aşırı yüklenebilir, yani bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `Mod` Kodunuz, bu tür `Mod` bir aşırı yükleme içeren bir sınıf veya yapının örneği için geçerliyse, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek, iki sayıyı `Mod` bölmek ve yalnızca geri kalanı döndürmek için işlecini kullanır. Her iki sayı de bir kayan noktalı sayı ise sonuç, kalanı temsil eden bir kayan noktalı sayıdır.

 [!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kayan nokta işlenenlerinin olası noktasında kesinlik eksikliği gösterir. İlk ifadede işlenen `Double`ve 0,2, saklı bir değeri 0.20000000000000001 olan sonsuz bir yinelenen ikili kesirdir. İkinci ifadede, değişmez değer türü karakteri `D` her iki işleneni olarak `Decimal`zorlar ve 0,2 kesin bir gösterimine sahiptir.

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
